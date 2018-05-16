# Vue-development-pit-trip--5
关于 vuex 报错 Do not mutate vuex store state outside mutation handlers.

在使用vuex 时，有时候 我们在mutation中定义好方法，在页面或组件提交时

有可能经常会遇到这个错误：---->>Do not mutate vuex store state outside mutation handlers.


The reason is that arrays are stored as references in Javascript and payload.items is likely to be changed outside Vuex. So we should just use a fresh copy of payload.itemsinstead.
原因是数组被存储为JavaScript和PayLoad中的引用。项目可能在Vuex之外进行更改。所以我们只需要使用一个新的PayLoad。

state: {
  obj: [],
  obj1: {}
}

[types.SELECTE_EXCLUSIVE_ADVISER]: (state, res) => state.exclusiveAdviser = res；
                              ↓
[types.SELECTE_EXCLUSIVE_ADVISER]: (state, res) => state.exclusiveAdviser = Object.assign({}, res),
