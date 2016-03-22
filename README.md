# CircleMenu
自定义ViewGroup实现的圆形旋转菜单，支持跟随手指旋转以及快速旋转。
图标请勿商用。

用法
=====
1、布局文件中声明控件

	<com.zhy.view.CircleMenuLayout
		android:id="@+id/id_menulayout"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:padding="100dp"
		android:background="@drawable/circle_bg3" >
	</com.zhy.view.CircleMenuLayout>

2、Activity的onCreate中|Fragment的onCreateView中

	public class CircleActivity extends Activity
	{
		private CircleMenuLayout mCircleMenuLayout;

		private String[] mItemTexts = new String[] { "安全中心 ", "特色服务", "投资理财",
				"转账汇款", "我的账户", "信用卡" };
		private int[] mItemImgs = new int[] { R.drawable.home_mbank_1_normal,
				R.drawable.home_mbank_2_normal, R.drawable.home_mbank_3_normal,
				R.drawable.home_mbank_4_normal, R.drawable.home_mbank_5_normal,
				R.drawable.home_mbank_6_normal };

		@Override
		protected void onCreate(Bundle savedInstanceState)
		{
			super.onCreate(savedInstanceState);
			
			//自已切换布局文件看效果
			setContentView(R.layout.activity_main02);

			mCircleMenuLayout = (CircleMenuLayout) findViewById(R.id.id_menulayout);
			mCircleMenuLayout.setMenuItemIconsAndTexts(mItemImgs, mItemTexts);
		}

	}

3、添加点击事件

	mCircleMenuLayout.setOnMenuItemClickListener(new OnMenuItemClickListener()
	{
		@Override
		public void itemClick(View view, int pos)
		{
			Toast.makeText(CircleActivity.this, mItemTexts[pos],
					Toast.LENGTH_SHORT).show();

		}
		@Override
		public void itemCenterClick(View view)
		{
			Toast.makeText(CircleActivity.this,
					"you can do something just like ccb  ",
					Toast.LENGTH_SHORT).show();
		}
	});

效果图
=====

CircleMenuSample

![Sample Screenshots][1]

CCBSample 注：千万别问我为什么少一块，建行就是这样的。

![Sample Screenshots][2]


关于yuanzuozhe
=====

我的博客地址[3]
========================================
1、概述

今天打开建行看存款，一看伤心欲绝，再看：我擦，这个圆形菜单挺炫。于是，为了掩盖我悲痛的心情，我决定是实现这个效果。好了，其实还有个原因，记得我初学android那会我做的应用被鄙视了，说我的菜单没有建行的好看，那么今天，证明自己的时刻到了。我决定用我做的圆形菜单的控件，32s实现个建行的菜单给他看看，顺便教教他~~

玩笑开完，直接看下效果图：



ok，这个就是我们今天的主要的效果了~~直接跟随手指滚动，直接快速滚动，直接点击Item~~~

这个效果的背景是在我在跪了2个多小时后，爱歌花了32s给我做的，再次感谢爱歌。

接下来，就是使用该控件实现建行那个圆形菜单~~



ok，分分钟搞定~~

就是有点恶心的地方，尼玛建行左边那个介绍和右边菜单的背景是两个图，想要做到无缝连在一起的效果，在我们圆形菜单的测量中还多写了几行代码，这个属于后话。

2、使用方式

简单看下使用方式，有个直观的了解

1、MainActivity

Java

package com.zhy.ccbCricleMenu;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.Toast;

import com.zhy.view.CircleMenuLayout;
import com.zhy.view.CircleMenuLayout.OnMenuItemClickListener;

public class MainActivity extends Activity
{

	private CircleMenuLayout mCircleMenuLayout;

	private String[] mItemTexts = new String[] { "安全中心 ", "特色服务", "投资理财",
			"转账汇款", "我的账户", "信用卡" };
	private int[] mItemImgs = new int[] { R.drawable.home_mbank_1_normal,
			R.drawable.home_mbank_2_normal, R.drawable.home_mbank_3_normal,
			R.drawable.home_mbank_4_normal, R.drawable.home_mbank_5_normal,
			R.drawable.home_mbank_6_normal };

	@Override
	protected void onCreate(Bundle savedInstanceState)
	{
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main02);

		mCircleMenuLayout = (CircleMenuLayout) findViewById(R.id.id_menulayout);
		mCircleMenuLayout.setMenuItemIconsAndTexts(mItemImgs, mItemTexts);
		
		

		mCircleMenuLayout.setOnMenuItemClickListener(new OnMenuItemClickListener()
		{
			
			@Override
			public void itemClick(View view, int pos)
			{
				Toast.makeText(MainActivity.this, mItemTexts[pos],
						Toast.LENGTH_SHORT).show();

			}
			
			@Override
			public void itemCenterClick(View view)
			{
				Toast.makeText(MainActivity.this,
						"you can do something just like ccb  ",
						Toast.LENGTH_SHORT).show();
				
			}
		});
		
	}

}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
package com.zhy.ccbCricleMenu;
 
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.Toast;
 
import com.zhy.view.CircleMenuLayout;
import com.zhy.view.CircleMenuLayout.OnMenuItemClickListener;
 
public class MainActivity extends Activity
{
 
	private CircleMenuLayout mCircleMenuLayout;
 
	private String[] mItemTexts = new String[] { "安全中心 ", "特色服务", "投资理财",
			"转账汇款", "我的账户", "信用卡" };
	private int[] mItemImgs = new int[] { R.drawable.home_mbank_1_normal,
			R.drawable.home_mbank_2_normal, R.drawable.home_mbank_3_normal,
			R.drawable.home_mbank_4_normal, R.drawable.home_mbank_5_normal,
			R.drawable.home_mbank_6_normal };
 
	@Override
	protected void onCreate(Bundle savedInstanceState)
	{
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main02);
 
		mCircleMenuLayout = (CircleMenuLayout) findViewById(R.id.id_menulayout);
		mCircleMenuLayout.setMenuItemIconsAndTexts(mItemImgs, mItemTexts);
		
		
 
		mCircleMenuLayout.setOnMenuItemClickListener(new OnMenuItemClickListener()
		{
			
			@Override
			public void itemClick(View view, int pos)
			{
				Toast.makeText(MainActivity.this, mItemTexts[pos],
						Toast.LENGTH_SHORT).show();
 
			}
			
			@Override
			public void itemCenterClick(View view)
			{
				Toast.makeText(MainActivity.this,
						"you can do something just like ccb  ",
						Toast.LENGTH_SHORT).show();
				
			}
		});
		
	}
 
}
2、布局文件


<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg"
    android:gravity="center_vertical"
    android:orientation="horizontal" >

    <com.zhy.view.CircleMenuLayout
        android:id="@+id/id_menulayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:padding="100dp"
        android:background="@drawable/circle_bg3" >

        <RelativeLayout
            android:id="@id/id_circle_menu_item_center"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" >

            <ImageView
                android:layout_width="104.0dip"
                android:layout_height="104.0dip"
                android:layout_centerInParent="true"
                android:background="@drawable/turnplate_center_unlogin" />

            <ImageView
                android:layout_width="116.0dip"
                android:layout_height="116.0dip"
                android:layout_centerInParent="true"
                android:background="@drawable/turnplate_mask_unlogin_normal" />
        </RelativeLayout>
    </com.zhy.view.CircleMenuLayout>

</LinearLayout>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg"
    android:gravity="center_vertical"
    android:orientation="horizontal" >
 
    <com.zhy.view.CircleMenuLayout
        android:id="@+id/id_menulayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:padding="100dp"
        android:background="@drawable/circle_bg3" >
 
        <RelativeLayout
            android:id="@id/id_circle_menu_item_center"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" >
 
            <ImageView
                android:layout_width="104.0dip"
                android:layout_height="104.0dip"
                android:layout_centerInParent="true"
                android:background="@drawable/turnplate_center_unlogin" />
 
            <ImageView
                android:layout_width="116.0dip"
                android:layout_height="116.0dip"
                android:layout_centerInParent="true"
                android:background="@drawable/turnplate_mask_unlogin_normal" />
        </RelativeLayout>
    </com.zhy.view.CircleMenuLayout>
 
</LinearLayout>
布局文件的CircleMenuLayout中的一个控件为我们圆形菜单的中间的那个View，当然了你可以不设置~

整个控件的使用，不要太简单，一行代码：setMenuItemIconsAndTexts去设置文本和图片就行~~~

如果你需要监听click事件，通过setOnMenuItemClickListener接口即可。

ok，不知道大家有没有注意到，我们的布局中间的view设置的id是这样的： android:id=”@id/id_circle_menu_item_center” ，维萨呢，因为我们的自定义控件依赖于我们的id，所以这个id我不希望用户自己去指定，而是提前定义些id，让用户去使用。其实这样的也很常见，大家在使用一些控件时，某些id也需要这么做，具体哪些控件，忘了~

那么如何定义这样的id资源呢？

在res/values下面去新建一个ids.xml文件：


<?xml version="1.0" encoding="utf-8"?>
<resources>

    <item name="id_circle_menu_item_image" type="id"/>
    <item name="id_circle_menu_item_text" type="id"/>
    <item name="id_circle_menu_item_center" type="id"/>

</resources>
1
2
3
4
5
6
7
8
<?xml version="1.0" encoding="utf-8"?>
<resources>
 
    <item name="id_circle_menu_item_image" type="id"/>
    <item name="id_circle_menu_item_text" type="id"/>
    <item name="id_circle_menu_item_center" type="id"/>
 
</resources>
可以看到里面写了3个id，前两个后面会用到，见到的时候别忘了，在这定义过。

3、简单的分析

对于上述的效果，我们决定自定义一个ViewGroup叫做CircleMenuLayout；

至于菜单项，文本+图片，支持设置其中任何一项，或者全部~~那么我们只需要在CircleMenuLayout的layout中去设置他们的位置就行了。

当然了在layout()之前，我们需要去进行onMeasure去测量，设置自己的宽高，和item的宽高；

最后就是和用户交互了滚动了：

我们重写dispatchTouchEvent事件，在其中编写跟随手指移动的代码~~我为什么不再onTouchEvent里面写，因为如果我在onTouchEvent里面写，用户触摸item时，我们的菜单无法移动，因为item是可点击，会作为我们的targetView，然后消耗掉我们的MOVE事件~~~关于事件分发：具体参考：Android ViewGroup事件分发机制 。

当然了还有很多细节，如何快速滚动，什么时候应该触发item的click事件等等。

如果不清楚，请先跳过~~继续往下看~~

4、CircleMenuLayout之onMeasure

在测量之前，我们先看看公布出去的setMenuItemIconsAndTexts，这个应该在测量之前。

Java

/**
	 * 设置菜单条目的图标和文本
	 * 
	 * @param resIds
	 */
	public void setMenuItemIconsAndTexts(int[] resIds, String[] texts)
	{
		mItemImgs = resIds;
		mItemTexts = texts;

		// 参数检查
		if (resIds == null && texts == null)
		{
			throw new IllegalArgumentException("菜单项文本和图片至少设置其一");
		}

		// 初始化mMenuCount
		mMenuItemCount = resIds == null ? texts.length : resIds.length;

		if (resIds != null && texts != null)
		{
			mMenuItemCount = Math.min(resIds.length, texts.length);
		}

		addMenuItems();

	}
	
	/**
	 * 添加菜单项
	 */
	private void addMenuItems()
	{
		LayoutInflater mInflater = LayoutInflater.from(getContext());

		/**
		 * 根据用户设置的参数，初始化view
		 */
		for (int i = 0; i < mMenuItemCount; i++)
		{
			final int j = i;
			View view = mInflater.inflate(R.layout.circle_menu_item, this,
					false);
			ImageView iv = (ImageView) view
					.findViewById(R.id.id_circle_menu_item_image);
			TextView tv = (TextView) view
					.findViewById(R.id.id_circle_menu_item_text);

			if (iv != null)
			{
				iv.setVisibility(View.VISIBLE);
				iv.setImageResource(mItemImgs[i]);
				iv.setOnClickListener(new OnClickListener()
				{
					@Override
					public void onClick(View v)
					{
						
						if (mOnMenuItemClickListener != null)
						{
							mOnMenuItemClickListener.itemClick(v, j);
						}
					}
				});
			}
			if (tv != null)
			{
				tv.setVisibility(View.VISIBLE);
				tv.setText(mItemTexts[i]);
			}

			// 添加view到容器中
			addView(view);
		}
	}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
/**
	 * 设置菜单条目的图标和文本
	 * 
	 * @param resIds
	 */
	public void setMenuItemIconsAndTexts(int[] resIds, String[] texts)
	{
		mItemImgs = resIds;
		mItemTexts = texts;
 
		// 参数检查
		if (resIds == null && texts == null)
		{
			throw new IllegalArgumentException("菜单项文本和图片至少设置其一");
		}
 
		// 初始化mMenuCount
		mMenuItemCount = resIds == null ? texts.length : resIds.length;
 
		if (resIds != null && texts != null)
		{
			mMenuItemCount = Math.min(resIds.length, texts.length);
		}
 
		addMenuItems();
 
	}
	
	/**
	 * 添加菜单项
	 */
	private void addMenuItems()
	{
		LayoutInflater mInflater = LayoutInflater.from(getContext());
 
		/**
		 * 根据用户设置的参数，初始化view
		 */
		for (int i = 0; i < mMenuItemCount; i++)
		{
			final int j = i;
			View view = mInflater.inflate(R.layout.circle_menu_item, this,
					false);
			ImageView iv = (ImageView) view
					.findViewById(R.id.id_circle_menu_item_image);
			TextView tv = (TextView) view
					.findViewById(R.id.id_circle_menu_item_text);
 
			if (iv != null)
			{
				iv.setVisibility(View.VISIBLE);
				iv.setImageResource(mItemImgs[i]);
				iv.setOnClickListener(new OnClickListener()
				{
					@Override
					public void onClick(View v)
					{
						
						if (mOnMenuItemClickListener != null)
						{
							mOnMenuItemClickListener.itemClick(v, j);
						}
					}
				});
			}
			if (tv != null)
			{
				tv.setVisibility(View.VISIBLE);
				tv.setText(mItemTexts[i]);
			}
 
			// 添加view到容器中
			addView(view);
		}
	}
比较简单，拿到两个数据，算出菜单的个数；然后去遍历，根据我们预设的R.layout.circle_menu_item，把值设上就可以。

看一眼我们的R.layout.circle_menu_item


<?xml version="1.0" encoding="UTF-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center"
    android:orientation="vertical" >

    <ImageView
        android:id="@id/id_circle_menu_item_image"
        android:layout_width="wrap_content"
        android:visibility="gone"
        android:src="@drawable/home_mbank_1_clicked"
        android:layout_height="wrap_content" />

    <TextView
        android:id="@id/id_circle_menu_item_text"
        android:layout_width="wrap_content"
        android:visibility="gone"
        android:layout_height="wrap_content"
        android:textColor="@android:color/white"
        android:text="保险"
        android:textSize="14.0dip" />

</LinearLayout>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
<?xml version="1.0" encoding="UTF-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center"
    android:orientation="vertical" >
 
    <ImageView
        android:id="@id/id_circle_menu_item_image"
        android:layout_width="wrap_content"
        android:visibility="gone"
        android:src="@drawable/home_mbank_1_clicked"
        android:layout_height="wrap_content" />
 
    <TextView
        android:id="@id/id_circle_menu_item_text"
        android:layout_width="wrap_content"
        android:visibility="gone"
        android:layout_height="wrap_content"
        android:textColor="@android:color/white"
        android:text="保险"
        android:textSize="14.0dip" />
 
</LinearLayout>
其实就是一个布局文件，里面一个tv一个iv；注意里面的两个id，我们之前说过了哈~~

这里大家会不会有疑问，为什么我要独立出一个布局呢，咋不在代码里面写死~~~

嗯，是这样的，我不是任性，假设我代码里面写死了，现在的需求是左边是文本右边是图标，你咋办，去改源码？我们独立出来以后呢？用户自己改改布局就行了~~~当然了，还可以把这个布局通过一个方法公布出来，setMenuItemLayoutId这样的方法。

对了上面还涉及到点击事件，这个so easy了，几行代码：

Java

/**
	 * MenuItem的点击事件接口
	 * 
	 * @author zhy
	 * 
	 */
	public interface OnMenuItemClickListener
	{
		void itemClick(View view, int pos);

		void itemCenterClick(View view);
	}

	/**
	 * MenuItem的点击事件接口
	 */
	private OnMenuItemClickListener mOnMenuItemClickListener;

	/**
	 * 设置MenuItem的点击事件接口
	 * 
	 * @param mOnMenuItemClickListener
	 */
	public void setOnMenuItemClickListener(
			OnMenuItemClickListener mOnMenuItemClickListener)
	{
		this.mOnMenuItemClickListener = mOnMenuItemClickListener;
	}
/**
	 * MenuItem的点击事件接口
	 * 
	 * @author zhy
	 * 
	 */
	public interface OnMenuItemClickListener
	{
		void itemClick(View view, int pos);
 
		void itemCenterClick(View view);
	}
 
	/**
	 * MenuItem的点击事件接口
	 */
	private OnMenuItemClickListener mOnMenuItemClickListener;
 
	/**
	 * 设置MenuItem的点击事件接口
	 * 
	 * @param mOnMenuItemClickListener
	 */
	public void setOnMenuItemClickListener(
			OnMenuItemClickListener mOnMenuItemClickListener)
	{
		this.mOnMenuItemClickListener = mOnMenuItemClickListener;
	}
没撒说的吧，大家见了无数次了~~

好了，接下来看我们声明的变量和onMeasure

Java

public class CircleMenuLayout extends ViewGroup
{
	private int mRadius;
	/**
	 * 该容器内child item的默认尺寸
	 */
	private static final float RADIO_DEFAULT_CHILD_DIMENSION = 1 / 4f;
	/**
	 * 菜单的中心child的默认尺寸
	 */
	private float RADIO_DEFAULT_CENTERITEM_DIMENSION = 1 / 3f;
	/**
	 * 该容器的内边距,无视padding属性，如需边距请用该变量
	 */
	private static final float RADIO_PADDING_LAYOUT = 1 / 12f;

	/**
	 * 当每秒移动角度达到该值时，认为是快速移动
	 */
	private static final int FLINGABLE_VALUE = 300;

	/**
	 * 如果移动角度达到该值，则屏蔽点击
	 */
	private static final int NOCLICK_VALUE = 3;

	/**
	 * 当每秒移动角度达到该值时，认为是快速移动
	 */
	private int mFlingableValue = FLINGABLE_VALUE;
	/**
	 * 该容器的内边距,无视padding属性，如需边距请用该变量
	 */
	private float mPadding;

	/**
	 * 布局时的开始角度
	 */
	private double mStartAngle = 0;
	/**
	 * 菜单项的文本
	 */
	private String[] mItemTexts;
	/**
	 * 菜单项的图标
	 */
	private int[] mItemImgs;

	/**
	 * 菜单的个数
	 */
	private int mMenuItemCount;

	/**
	 * 检测按下到抬起时旋转的角度
	 */
	private float mTmpAngle;
	/**
	 * 检测按下到抬起时使用的时间
	 */
	private long mDownTime;

	/**
	 * 判断是否正在自动滚动
	 */
	private boolean isFling;

	

	public CircleMenuLayout(Context context, AttributeSet attrs)
	{
		super(context, attrs);
		// 无视padding
		setPadding(0, 0, 0, 0);
	}

	/**
	 * 设置布局的宽高，并策略menu item宽高
	 */
	@Override
	protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec)
	{
		int resWidth = 0;
		int resHeight = 0;

		/**
		 * 根据传入的参数，分别获取测量模式和测量值
		 */
		int width = MeasureSpec.getSize(widthMeasureSpec);
		int widthMode = MeasureSpec.getMode(widthMeasureSpec);

		int height = MeasureSpec.getSize(heightMeasureSpec);
		int heightMode = MeasureSpec.getMode(heightMeasureSpec);

		/**
		 * 如果宽或者高的测量模式非精确值
		 */
		if (widthMode != MeasureSpec.EXACTLY
				|| heightMode != MeasureSpec.EXACTLY)
		{
			// 主要设置为背景图的高度
			resWidth = getSuggestedMinimumWidth();
			// 如果未设置背景图片，则设置为屏幕宽高的默认值
			resWidth = resWidth == 0 ? getDefaultWidth() : resWidth;

			resHeight = getSuggestedMinimumHeight();
			// 如果未设置背景图片，则设置为屏幕宽高的默认值
			resHeight = resHeight == 0 ? getDefaultWidth() : resHeight;
		} else
		{
			// 如果都设置为精确值，则直接取小值；
			resWidth = resHeight = Math.min(width, height);
		}

		setMeasuredDimension(resWidth, resHeight);

		// 获得半径
		mRadius = Math.max(getMeasuredWidth(), getMeasuredHeight());

		// menu item数量
		final int count = getChildCount();
		// menu item尺寸
		int childSize = (int) (mRadius * RADIO_DEFAULT_CHILD_DIMENSION);
		// menu item测量模式
		int childMode = MeasureSpec.EXACTLY;

		// 迭代测量
		for (int i = 0; i < count; i++)
		{
			final View child = getChildAt(i);

			if (child.getVisibility() == GONE)
			{
				continue;
			}

			// 计算menu item的尺寸；以及和设置好的模式，去对item进行测量
			int makeMeasureSpec = -1;

			if (child.getId() == R.id.id_circle_menu_item_center)
			{
				makeMeasureSpec = MeasureSpec.makeMeasureSpec(
						(int) (mRadius * RADIO_DEFAULT_CENTERITEM_DIMENSION),
						childMode);
			} else
			{
				makeMeasureSpec = MeasureSpec.makeMeasureSpec(childSize,
						childMode);
			}
			child.measure(makeMeasureSpec, makeMeasureSpec);
		}

		mPadding = RADIO_PADDING_LAYOUT * mRadius;

	}

public class CircleMenuLayout extends ViewGroup
{
	private int mRadius;
	/**
	 * 该容器内child item的默认尺寸
	 */
	private static final float RADIO_DEFAULT_CHILD_DIMENSION = 1 / 4f;
	/**
	 * 菜单的中心child的默认尺寸
	 */
	private float RADIO_DEFAULT_CENTERITEM_DIMENSION = 1 / 3f;
	/**
	 * 该容器的内边距,无视padding属性，如需边距请用该变量
	 */
	private static final float RADIO_PADDING_LAYOUT = 1 / 12f;
 
	/**
	 * 当每秒移动角度达到该值时，认为是快速移动
	 */
	private static final int FLINGABLE_VALUE = 300;
 
	/**
	 * 如果移动角度达到该值，则屏蔽点击
	 */
	private static final int NOCLICK_VALUE = 3;
 
	/**
	 * 当每秒移动角度达到该值时，认为是快速移动
	 */
	private int mFlingableValue = FLINGABLE_VALUE;
	/**
	 * 该容器的内边距,无视padding属性，如需边距请用该变量
	 */
	private float mPadding;
 
	/**
	 * 布局时的开始角度
	 */
	private double mStartAngle = 0;
	/**
	 * 菜单项的文本
	 */
	private String[] mItemTexts;
	/**
	 * 菜单项的图标
	 */
	private int[] mItemImgs;
 
	/**
	 * 菜单的个数
	 */
	private int mMenuItemCount;
 
	/**
	 * 检测按下到抬起时旋转的角度
	 */
	private float mTmpAngle;
	/**
	 * 检测按下到抬起时使用的时间
	 */
	private long mDownTime;
 
	/**
	 * 判断是否正在自动滚动
	 */
	private boolean isFling;
 
	
 
	public CircleMenuLayout(Context context, AttributeSet attrs)
	{
		super(context, attrs);
		// 无视padding
		setPadding(0, 0, 0, 0);
	}
 
	/**
	 * 设置布局的宽高，并策略menu item宽高
	 */
	@Override
	protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec)
	{
		int resWidth = 0;
		int resHeight = 0;
 
		/**
		 * 根据传入的参数，分别获取测量模式和测量值
		 */
		int width = MeasureSpec.getSize(widthMeasureSpec);
		int widthMode = MeasureSpec.getMode(widthMeasureSpec);
 
		int height = MeasureSpec.getSize(heightMeasureSpec);
		int heightMode = MeasureSpec.getMode(heightMeasureSpec);
 
		/**
		 * 如果宽或者高的测量模式非精确值
		 */
		if (widthMode != MeasureSpec.EXACTLY
				|| heightMode != MeasureSpec.EXACTLY)
		{
			// 主要设置为背景图的高度
			resWidth = getSuggestedMinimumWidth();
			// 如果未设置背景图片，则设置为屏幕宽高的默认值
			resWidth = resWidth == 0 ? getDefaultWidth() : resWidth;
 
			resHeight = getSuggestedMinimumHeight();
			// 如果未设置背景图片，则设置为屏幕宽高的默认值
			resHeight = resHeight == 0 ? getDefaultWidth() : resHeight;
		} else
		{
			// 如果都设置为精确值，则直接取小值；
			resWidth = resHeight = Math.min(width, height);
		}
 
		setMeasuredDimension(resWidth, resHeight);
 
		// 获得半径
		mRadius = Math.max(getMeasuredWidth(), getMeasuredHeight());
 
		// menu item数量
		final int count = getChildCount();
		// menu item尺寸
		int childSize = (int) (mRadius * RADIO_DEFAULT_CHILD_DIMENSION);
		// menu item测量模式
		int childMode = MeasureSpec.EXACTLY;
 
		// 迭代测量
		for (int i = 0; i < count; i++)
		{
			final View child = getChildAt(i);
 
			if (child.getVisibility() == GONE)
			{
				continue;
			}
 
			// 计算menu item的尺寸；以及和设置好的模式，去对item进行测量
			int makeMeasureSpec = -1;
 
			if (child.getId() == R.id.id_circle_menu_item_center)
			{
				makeMeasureSpec = MeasureSpec.makeMeasureSpec(
						(int) (mRadius * RADIO_DEFAULT_CENTERITEM_DIMENSION),
						childMode);
			} else
			{
				makeMeasureSpec = MeasureSpec.makeMeasureSpec(childSize,
						childMode);
			}
			child.measure(makeMeasureSpec, makeMeasureSpec);
		}
 
		mPadding = RADIO_PADDING_LAYOUT * mRadius;
 
	}
首先说一下变量：其实都有注释，mRadius是我们整个View的宽度；几个常量，分别为我们menu item的宽度占据mRadius的比例；RADIO_PADDING_LAYOUT为内边距占据的比例；剩下的自己看注释~~

测量呢？

首先我们根据widthMeasureSpec、heightMeasureSpec分别获取宽高的值和模式~~~

会不会有人会问这个值是什么玩意？怎么就能通过它拿到宽和高，没关系，恰好我们是ViewGroup，我们需要去测量子View，刚好要传这两个参数：

你往下看：child.measure(makeMeasureSpec, makeMeasureSpec);传入了两个值，你在看这两个值如何形成的，

makeMeasureSpec = MeasureSpec.makeMeasureSpec(childSize,childMode);是通过MeasureSpec将尺寸和模式封装到一起的~~好了，不能再扯了，有机会独立写篇自定义控件的总结博客细说这些。

拿到尺寸和模式以后呢，我们去判断模式，是否是EXACTLY（如果你对三种模式不了解，请参考：Android 手把手教您自定义ViewGroup（一））

如果是EXACTLY那么简单，直接取两者的最小值即可。

如果不是，不是，那么根据设置的背景图的尺寸，如果没有背景图，那么取默认的尺寸，默认其实就是屏幕宽和高中的小值；

Java

/**
	 * 获得默认该layout的尺寸
	 * 
	 * @return
	 */
	private int getDefaultWidth()
	{
		WindowManager wm = (WindowManager) getContext().getSystemService(
				Context.WINDOW_SERVICE);
		DisplayMetrics outMetrics = new DisplayMetrics();
		wm.getDefaultDisplay().getMetrics(outMetrics);
		return Math.min(outMetrics.widthPixels, outMetrics.heightPixels);
	}

/**
	 * 获得默认该layout的尺寸
	 * 
	 * @return
	 */
	private int getDefaultWidth()
	{
		WindowManager wm = (WindowManager) getContext().getSystemService(
				Context.WINDOW_SERVICE);
		DisplayMetrics outMetrics = new DisplayMetrics();
		wm.getDefaultDisplay().getMetrics(outMetrics);
		return Math.min(outMetrics.widthPixels, outMetrics.heightPixels);
	}
得到父控件的尺寸后，我们setMeasuredDimension设置下~~然后根据父控件的宽高，集合我们的预设常量的那些比例，去为我们的menu item设置宽和高：

没撒说的，计算出宽度，这里我们的宽度是精确值，所以我们设置menu item的模式为：EXACTLY，最后通过MeasureSpec封装，传入给child.measure(makeMeasureSpec, makeMeasureSpec);即可。

测量完成以后，那么准备布局吧~~

5、CircleMenuLayout之onLayout

我们在onLayout中将menu item设置到指定位置，理论上，我们的圆形菜单的样子就搞定了~~

Java

	/**
	 * 设置menu item的位置
	 */
	@Override
	protected void onLayout(boolean changed, int l, int t, int r, int b)
	{
		int layoutRadius = mRadius;

		// Laying out the child views
		final int childCount = getChildCount();

		int left, top;
		// menu item 的尺寸
		int cWidth = (int) (layoutRadius * RADIO_DEFAULT_CHILD_DIMENSION);

		// 根据menu item的个数，计算角度
		float angleDelay = 360 / (getChildCount() - 1);

		// 遍历去设置menuitem的位置
		for (int i = 0; i < childCount; i++)
		{
			final View child = getChildAt(i);

			if (child.getId() == R.id.id_circle_menu_item_center)
				continue;

			if (child.getVisibility() == GONE)
			{
				continue;
			}

			mStartAngle %= 360;

			// 计算，中心点到menu item中心的距离
			float tmp = layoutRadius / 2f - cWidth / 2 - mPadding;

			// tmp cosa 即menu item中心点的横坐标
			left = layoutRadius
					/ 2
					+ (int) Math.round(tmp
							* Math.cos(Math.toRadians(mStartAngle)) - 1 / 2f
							* cWidth);
			// tmp sina 即menu item的纵坐标
			top = layoutRadius
					/ 2
					+ (int) Math.round(tmp
							* Math.sin(Math.toRadians(mStartAngle)) - 1 / 2f
							* cWidth);

			child.layout(left, top, left + cWidth, top + cWidth);
			// 叠加尺寸
			mStartAngle += angleDelay;
		}

		// 找到中心的view，如果存在设置onclick事件
		View cView = findViewById(R.id.id_circle_menu_item_center);
		if (cView != null)
		{
			cView.setOnClickListener(new OnClickListener()
			{
				@Override
				public void onClick(View v)
				{

					if (mOnMenuItemClickListener != null)
					{
						mOnMenuItemClickListener.itemCenterClick(v);
					}
				}
			});
		// 设置center item位置
		int cl = layoutRadius / 2 - cView.getMeasuredWidth() / 2;
		int cr = cl + cView.getMeasuredWidth();
		cView.layout(cl, cl, cr, cr);
		}
			

	}

	/**
	 * 设置menu item的位置
	 */
	@Override
	protected void onLayout(boolean changed, int l, int t, int r, int b)
	{
		int layoutRadius = mRadius;
 
		// Laying out the child views
		final int childCount = getChildCount();
 
		int left, top;
		// menu item 的尺寸
		int cWidth = (int) (layoutRadius * RADIO_DEFAULT_CHILD_DIMENSION);
 
		// 根据menu item的个数，计算角度
		float angleDelay = 360 / (getChildCount() - 1);
 
		// 遍历去设置menuitem的位置
		for (int i = 0; i < childCount; i++)
		{
			final View child = getChildAt(i);
 
			if (child.getId() == R.id.id_circle_menu_item_center)
				continue;
 
			if (child.getVisibility() == GONE)
			{
				continue;
			}
 
			mStartAngle %= 360;
 
			// 计算，中心点到menu item中心的距离
			float tmp = layoutRadius / 2f - cWidth / 2 - mPadding;
 
			// tmp cosa 即menu item中心点的横坐标
			left = layoutRadius
					/ 2
					+ (int) Math.round(tmp
							* Math.cos(Math.toRadians(mStartAngle)) - 1 / 2f
							* cWidth);
			// tmp sina 即menu item的纵坐标
			top = layoutRadius
					/ 2
					+ (int) Math.round(tmp
							* Math.sin(Math.toRadians(mStartAngle)) - 1 / 2f
							* cWidth);
 
			child.layout(left, top, left + cWidth, top + cWidth);
			// 叠加尺寸
			mStartAngle += angleDelay;
		}
 
		// 找到中心的view，如果存在设置onclick事件
		View cView = findViewById(R.id.id_circle_menu_item_center);
		if (cView != null)
		{
			cView.setOnClickListener(new OnClickListener()
			{
				@Override
				public void onClick(View v)
				{
 
					if (mOnMenuItemClickListener != null)
					{
						mOnMenuItemClickListener.itemCenterClick(v);
					}
				}
			});
		// 设置center item位置
		int cl = layoutRadius / 2 - cView.getMeasuredWidth() / 2;
		int cr = cl + cView.getMeasuredWidth();
		cView.layout(cl, cl, cr, cr);
		}
			
 
	}
测量，无非是遍历，然后去计算left 和 top ，当然了，我们这里是圆形，所以会使用到一些数学知识。tmp*cosa 即menu item中心点的横坐标，tmp * sina 即menu item的纵坐标。关于这样的计算可以参考：Android SurfaceView实战 打造抽奖转盘 。 当然了，我也给大家绘制了一个图：



假设小圆是我们的menu item，那么他的坐标就是mRadius / 2 + tmp * coas , mRadius / 2 + tmp * sina 。

如果，你只需要实现一个圆形菜单，并不需要跟随手指滚动神马的，到此就可以了，拿走不谢。

我们继续往下看滚动。

6、CircleMenuLayout之dispatchTouchEvent

Java

/**
	 * 记录上一次的x，y坐标
	 */
	private float mLastX;
	private float mLastY;

	/**
	 * 自动滚动的Runnable
	 */
	private AutoFlingRunnable mFlingRunnable;

	@Override
	public boolean dispatchTouchEvent(MotionEvent event)
	{
		float x = event.getX();
		float y = event.getY();

		Log.e("TAG", "x = " + x + " , y = " + y);

		switch (event.getAction())
		{
		case MotionEvent.ACTION_DOWN:

			mLastX = x;
			mLastY = y;
			mDownTime = System.currentTimeMillis();
			mTmpAngle = 0;

			// 如果当前已经在快速滚动
			if (isFling)
			{
				// 移除快速滚动的回调
				removeCallbacks(mFlingRunnable);
				isFling = false;
				return true;
			}

			break;
		case MotionEvent.ACTION_MOVE:

			/**
			 * 获得开始的角度
			 */
			float start = getAngle(mLastX, mLastY);
			/**
			 * 获得当前的角度
			 */
			float end = getAngle(x, y);

			// Log.e("TAG", "start = " + start + " , end =" + end);
			// 如果是一、四象限，则直接end-start，角度值都是正值
			if (getQuadrant(x, y) == 1 || getQuadrant(x, y) == 4)
			{
				mStartAngle += end - start;
				mTmpAngle += end - start;
			} else
			// 二、三象限，色角度值是付值
			{
				mStartAngle += start - end;
				mTmpAngle += start - end;
			}
			// 重新布局
			requestLayout();

			mLastX = x;
			mLastY = y;

			break;
		case MotionEvent.ACTION_UP:

			// 计算，每秒移动的角度
			float anglePerSecond = mTmpAngle * 1000
					/ (System.currentTimeMillis() - mDownTime);

			// Log.e("TAG", anglePrMillionSecond + " , mTmpAngel = " +
			// mTmpAngle);

			// 如果达到该值认为是快速移动
			if (Math.abs(anglePerSecond) > mFlingableValue && !isFling)
			{
				// post一个任务，去自动滚动
				post(mFlingRunnable = new AutoFlingRunnable(anglePerSecond));

				return true;
			}

			// 如果当前旋转角度超过NOCLICK_VALUE屏蔽点击
			if (Math.abs(mTmpAngle) > NOCLICK_VALUE)
			{
				return true;
			}

			break;
		}
		return super.dispatchTouchEvent(event);
	}
/**
	 * 记录上一次的x，y坐标
	 */
	private float mLastX;
	private float mLastY;
 
	/**
	 * 自动滚动的Runnable
	 */
	private AutoFlingRunnable mFlingRunnable;
 
	@Override
	public boolean dispatchTouchEvent(MotionEvent event)
	{
		float x = event.getX();
		float y = event.getY();
 
		Log.e("TAG", "x = " + x + " , y = " + y);
 
		switch (event.getAction())
		{
		case MotionEvent.ACTION_DOWN:
 
			mLastX = x;
			mLastY = y;
			mDownTime = System.currentTimeMillis();
			mTmpAngle = 0;
 
			// 如果当前已经在快速滚动
			if (isFling)
			{
				// 移除快速滚动的回调
				removeCallbacks(mFlingRunnable);
				isFling = false;
				return true;
			}
 
			break;
		case MotionEvent.ACTION_MOVE:
 
			/**
			 * 获得开始的角度
			 */
			float start = getAngle(mLastX, mLastY);
			/**
			 * 获得当前的角度
			 */
			float end = getAngle(x, y);
 
			// Log.e("TAG", "start = " + start + " , end =" + end);
			// 如果是一、四象限，则直接end-start，角度值都是正值
			if (getQuadrant(x, y) == 1 || getQuadrant(x, y) == 4)
			{
				mStartAngle += end - start;
				mTmpAngle += end - start;
			} else
			// 二、三象限，色角度值是付值
			{
				mStartAngle += start - end;
				mTmpAngle += start - end;
			}
			// 重新布局
			requestLayout();
 
			mLastX = x;
			mLastY = y;
 
			break;
		case MotionEvent.ACTION_UP:
 
			// 计算，每秒移动的角度
			float anglePerSecond = mTmpAngle * 1000
					/ (System.currentTimeMillis() - mDownTime);
 
			// Log.e("TAG", anglePrMillionSecond + " , mTmpAngel = " +
			// mTmpAngle);
 
			// 如果达到该值认为是快速移动
			if (Math.abs(anglePerSecond) > mFlingableValue && !isFling)
			{
				// post一个任务，去自动滚动
				post(mFlingRunnable = new AutoFlingRunnable(anglePerSecond));
 
				return true;
			}
 
			// 如果当前旋转角度超过NOCLICK_VALUE屏蔽点击
			if (Math.abs(mTmpAngle) > NOCLICK_VALUE)
			{
				return true;
			}
 
			break;
		}
		return super.dispatchTouchEvent(event);
	}
ok，代码并不长~~DOWN的时候，记录下mLastX,mLastY,当前的时间，以及重置mTmpAngle为0，如果当前在自动滚动，停止该操作。

ACTION_MOVE的时候，根据mLastX,mLastY得到一个角度，再根据当前的x,y再获得一个调度，不断去改变mStartAngle，重新布局接口。

当然了getAngle(x, y);方法，获得的角度在如果是一、四象限，则直接end-start，角度值都是正值，在二、三象限，end-start角度值是负值，所以倒着减一下。

UP的时候，计算每秒移动的角度， 如果达到mFlingableValue的大小，则认为需要自动滚动，post(mFlingRunnable = new AutoFlingRunnable(anglePerSecond));去执行。

如果当前旋转角度超过NOCLICK_VALUE屏蔽点击，屏蔽点击就是return true即可。为撒呢？因为子view的点击触发在super.dispatchTouchEvent(event);里面，我们直接return了。

那么我们看上面说的一些方法，先看：getAngle:

Java

/**
	 * 根据触摸的位置，计算角度
	 * 
	 * @param xTouch
	 * @param yTouch
	 * @return
	 */
	private float getAngle(float xTouch, float yTouch)
	{
		double x = xTouch - (mRadius / 2d);
		double y = yTouch - (mRadius / 2d);
		return (float) (Math.asin(y / Math.hypot(x, y)) * 180 / Math.PI);
	}

/**
	 * 根据触摸的位置，计算角度
	 * 
	 * @param xTouch
	 * @param yTouch
	 * @return
	 */
	private float getAngle(float xTouch, float yTouch)
	{
		double x = xTouch - (mRadius / 2d);
		double y = yTouch - (mRadius / 2d);
		return (float) (Math.asin(y / Math.hypot(x, y)) * 180 / Math.PI);
	}
还是画图来说：



Math.sqrt( x * x + y * y )是斜边长，乘以 sin a 就是 y 的长度；

反之求a的角度：即Math.asin(y / Math.hypot(x, y) ； [ hypot是x * x + y * y ]

这样我们移动的角度计算就ok了~~

不同象限，以为因为start-end的值可能为负值，所以需要改变减法的顺序，因为我们最后角度需要正值；

关于判断象限的代码：

Java

/**
	 * 根据当前位置计算象限
	 * 
	 * @param x
	 * @param y
	 * @return
	 */
	private int getQuadrant(float x, float y)
	{
		int tmpX = (int) (x - mRadius / 2);
		int tmpY = (int) (y - mRadius / 2);
		if (tmpX >= 0)
		{
			return tmpY >= 0 ? 4 : 1;
		} else
		{
			return tmpY >= 0 ? 3 : 2;
		}

	}

/**
	 * 根据当前位置计算象限
	 * 
	 * @param x
	 * @param y
	 * @return
	 */
	private int getQuadrant(float x, float y)
	{
		int tmpX = (int) (x - mRadius / 2);
		int tmpY = (int) (y - mRadius / 2);
		if (tmpX >= 0)
		{
			return tmpY >= 0 ? 4 : 1;
		} else
		{
			return tmpY >= 0 ? 3 : 2;
		}
 
	}
自己拿坐标代入，立马就理解了~~~

最后还剩什么呢？

看我们的自动AutoFlingRunnable，自动滚动的任务~~

我们通过post(mFlingRunnable = new AutoFlingRunnable(anglePerSecond));去触发的

Java

/**
	 * 自动滚动的任务
	 * 
	 * @author zhy
	 * 
	 */
	private class AutoFlingRunnable implements Runnable
	{

		private float angelPerSecond;

		public AutoFlingRunnable(float velocity)
		{
			this.angelPerSecond = velocity;
		}

		public void run()
		{
			// 如果小于20,则停止
			if ((int) Math.abs(angelPerSecond) < 20)
			{
				isFling = false;
				return;
			}
			isFling = true;
			// 不断改变mStartAngle，让其滚动，/30为了避免滚动太快
			mStartAngle += (angelPerSecond / 30);
			// 逐渐减小这个值
			angelPerSecond /= 1.0666F;
			postDelayed(this, 30);
			// 重新布局
			requestLayout();
		}
	}

/**
	 * 自动滚动的任务
	 * 
	 * @author zhy
	 * 
	 */
	private class AutoFlingRunnable implements Runnable
	{
 
		private float angelPerSecond;
 
		public AutoFlingRunnable(float velocity)
		{
			this.angelPerSecond = velocity;
		}
 
		public void run()
		{
			// 如果小于20,则停止
			if ((int) Math.abs(angelPerSecond) < 20)
			{
				isFling = false;
				return;
			}
			isFling = true;
			// 不断改变mStartAngle，让其滚动，/30为了避免滚动太快
			mStartAngle += (angelPerSecond / 30);
			// 逐渐减小这个值
			angelPerSecond /= 1.0666F;
			postDelayed(this, 30);
			// 重新布局
			requestLayout();
		}
	}
代码比较短，我们传入每秒移动的角度这个值，然后根据这个值去增加mStartAngle，然后requestLayout();就是自动滚动了~~当然了需要越滚越慢和停止，所以需要

// 逐渐减小这个值angelPerSecond /= 1.0666F; 以及最后移动很慢的时候，我们就停下来：

Java

// 如果小于20,则停止
if ((int) Math.abs(angelPerSecond) < 20)
{
isFling = false;
return;
}

// 如果小于20,则停止
if ((int) Math.abs(angelPerSecond) < 20)
{
isFling = false;
return;
}
到此，所有代码解析完毕~~~嘿嘿~
========================================

[1]: https://github.com/hongyangAndroid/CircleMenu/blob/master/sample_zhy_CircleMenu/screen_shot.gif
[2]: https://github.com/hongyangAndroid/CircleMenu/blob/master/sample_zhy_CircleMenu/ccb.gif
[3]: http://blog.csdn.net/lmj623565791
