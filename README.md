# YCExpandView
- 01.该库介绍
- 02.效果展示
- 03.如何使用
- 04.注意要点
- 05.优化问题
- 06.部分代码逻辑


### 01.该库介绍
- 自定义折叠和展开布局，在不用改变原控件的基础上，就可以实现折叠展开功能，入侵性极低。
- 主要的思路是，设置一个折叠时的布局高度，设置一个内容展开时的高度，然后利用属性动画去动态改变布局的高度。
- 可以设置折叠和展开的监听事件，方便开发者拓展其他需求。可以设置动画的时间。
- 可以支持支持常见的文本折叠，标签折叠等功能。十分方便，思路也比较容易理解，代码不超过300行……


### 02.效果展示



### 03.如何使用
- 设置文本控件
    ```
    <com.ycbjie.expandlib.ExpandLayout
        android:id="@+id/expand"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">
        <TextView
            android:id="@+id/tv"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:padding="10dp"
            android:text=""/>
    </com.ycbjie.expandlib.ExpandLayout>
    ```
- 如何切换展开和折叠
    ```
    //初始化操作
    expand.initExpand(false ,mHeight);
    //设置动画时间
    expand.setAnimationDuration(300);
    //折叠或者展开操作后的监听
    expand.setOnToggleExpandListener(new ExpandLayout.OnToggleExpandListener() {
        @Override
        public void onToggleExpand(boolean isExpand) {
            if (isExpand){
                ivExpand.setBackgroundResource(R.mipmap.icon_btn_collapse);
            }else {
                ivExpand.setBackgroundResource(R.mipmap.icon_btn_expand);
            }
        }
    });
    //折叠view
    expand.collapse();
    //展开view
    expand.expand();
    //查看控件是折叠还是展开状态
    expand.isExpand();
    //这个是置反操作
    expand.toggleExpand();
    ```


### 04.注意要点



### 05.优化问题
- 1.在从折叠状态到伸展状态，或者反之。只要是在动画过程中，则执行动画的过程中屏蔽事件传递
- 2.当控件销毁后，在onDetachedFromWindow方法中，手动销毁动画
- 3.针对折叠和伸展状态之间切换，如果动画在执行中，即使调用多次toggleExpand()方法，避免频繁调用collapse或者expand
- 4.如果开发者使用该折叠控件时，设置折叠时的高度为0，则会抛出异常










