# Thinking-in-UML

## 一. RUP 4+1视图模型
1995年，Philippe Kruchten在《IEEE Software》上发表的《The 4+1 View Model of Architecture》
https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf

![alt RUP 4+1视图](images/4_1_view.jpg)


![alt UML ](images/4+1ViewModel.png)

## 二. UML
![alt UML ](images/UML.png)
### 1. 关系 Relationship

![alt UML ](images/Relationships.png)

#### 关联关系 Association

**关联关系** 是静态关系，是由“常识“，“规则”，“法律”等决定。
关联表明两个模型元素之间有关系，通常用在一个类中被实现为一个实例变量。

![alt UML ](images/Associations.GIF)

```java
class Team {   
    Player player;   
}
```
#### 聚合关系 Aggregation

**聚合关系** 通常被用来描述由更小的组件所构成的元素，是整体与部分的关系。

![alt UML ](images/Aggregation.png)
```java
class Team {   
    public Player player;   
    public void Team(Play player)
    {
        this.player = player;
    }
}
```
#### 组合关系 Composition

**组合关系**是一种强依赖的特殊聚合关系，如果整体不在了，部分也将消亡。

![alt UML ](images/Composition.png)
```java
class Person {   
    public Head head;   
    public Body body;   
    public Hands hands;   
    public Foots foots;   
    public void Person()
    {
        this.head = new Head();
        this.body = new Body();
        this.hands = new Hands();
        this.foots = new Foots();
    }
}
```
#### 依赖关系 Dependency

**依赖关系** 描述一个对象在运行时会使用另外一个对象的关系。
与关联关系不同，是一种临时关系，在运行期间产生，随着场景不同而变化。

![alt UML ](images/Dependency.png)
```java
class Person {   
    public void drive(Car car)
    {
        car.run();
    }
    public void fly()
    {
        Plane plane = new Plane();
        plane.run();
    }
}
```
* * *

**聚合和组合都属于关联关系，区别就是生命周期的差异。**

> 国际关系比喻 
* 欧盟关系是聚合；
* 台海关系是组合；
* 各国和中东的关系是依赖；
* 一带一路的关系是关联；
> 代码体现 
* 一个类的对象是另外一个类的成员变量，是关联
     * 这个对象是参数传递进来是聚合
     * 这个对象是内部实例化的是组合 
* 一个类的对象是另外一个类的局部变量，是依赖


#### 泛化关系 Generalization
**泛化关系**一般元素和特殊元素之间的分类关系

![alt UML ](images/Generalization.png)
#### 实现关系 Realization

![alt UML ](images/Realization.png)

### 2. 图 Diagrams

#### 用例图 Use Case Diagram
用例图描述了一组用例,参与者以及它们之间的关系,它包含一下内容: 
* 1.用例   Use Case
* 2.参与者 Actor : 系统之外与系统交互的某人或某事物.
* 3.参与者与用例直接的关系 : 泛化关系,包含关系,扩展关系等
* 4.系统边界

##### 用例图的误区：
  ###### 1.确定系统边界，找出真正的Actor

> 例子： 小王到银行去开户，向大堂经理询问了办理手续，填写了表单，交给了柜台职员，拿到了银行卡。在这个场景中，谁是Actor？

> 问两个问题，找出Actor。
  - 谁对系统有着明确的目标和要求并且主动发出动作？
  - 系统是为谁服务的？

>所以，小王才是Actor，大堂经理和柜台职员都在系统内部，属于业务工人（business worker）,同时系统边界也明确了。 

  ###### 2. 找出真正的有效usecase
  > 误区1. 将结构当用例

  > 误区2. 将功能当用例

  > 误区3. 将步骤当用例

  ######  用例和功能的区别：
  - a、用例是描述使用者愿望的，描述的是使用者对系统的使用要求，用用例来看待系统的团队，则是从使用者角度出发，说明使用者在系统里能做什么。功能则是脱离使用者的愿望而存在的。
  - b、用例是系统性的，它描述谁在什么情况下通过什么方式得到什么样的结果。功能描述的是一个个点，如果要达成一个特定的目标，必须要再额外加上一个顺序的过程把点串联起来才能完成一个系统性的工作。而用例描述的是一个系统性的工作，这个系统性的工作非常明确地去达成一个特定的目标。
  - c、用例可以理解为一系列完成一个特定目标的“功能”的组合，针对不同的场景，这些“功能”体现不同的组合方式。

![alt UML ](images/usecase.png)

#### 类图 Class Diagram
类之间常用的关系进行了简单的描述，主要有：关联关系、泛化、依赖、聚合和组合。
![alt UML ](images/class_diagram.png)

#### 活动图 Activity Diagram
> 活动图包含的图形元素有动作状态，活动状态，动作流，分支与合并，分叉与汇合，泳道和对象流等。

![alt ActivityDiagram](images/ActivityDiagram.jpg)

#### 时序图 Sequence Diagram
时序图（Sequence Diagram）是显示对象之间交互的图，这些对象是按时间顺序排列的。顺序图中显示的是参与交互的对象及其对象之间消息交互的顺序。时序图中包括的建模元素主要有：对象（Actor）、生命线（Lifeline）、控制焦点（Focus of control）、消息（Message）等等。
![alt UML ](images/sequence.png)

#### 组件图 Component Diagram
组件图通常包含3中元素，组件（Component），接口（interface）和依赖关系（dependency）。
![alt UML ](images/component.png)

### 3. 流程
![alt UML ](images/4_1.png)
#### 1. 【Use Case View】用例图 Use Case Diagram   
> 深入理解需求，找出actor，use case，和系统边界
#### 2. 【Logical View】类图 Class Diagram
> 根据用例，找出实体和实体关系
#### 3. 【Process View】活动图 Activity Diagram [option]
> 验证用例和类图
#### 4. 【Process View】时序图 Sequence Diagram
> 用动态行为图，确认主要流程，验证类图
#### 5. 【Development View】组件图 Component Diagram
> 明确最终系统结构，指导开发，解决组件重用。 
#### 6. 【Physical View】部署图 Deployment Diagram
> 明确物理部署