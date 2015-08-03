# sinavideo_playersdk
##项目的由来



##集成步骤
集成一个播放器需要几步？三步<br/>
1. 设置一个播放列表 

        info = new VDVideoInfo();
        info.mTitle = "这就是一个测试视频0";
        info.mPlayUrl = "http://wtv.v.iask.com/player/ovs1_vod_rid_2015052841_br_3_pn_weitv_tn_0_sig_md5.m3u8";
        infoList.addVideoInfo(info);
		// 初始化播放器以及播放列表
        mVDVideoView.open(SinaVideoActivity.this, infoList);
        // 开始播放，直接选择序号即可
        mVDVideoView.play(0);
        
2. 从demo里面copy一份layout出来

    `<com.sina.sinavideo.sdk.VDVideoView
        android:id="@+id/vv1"
        android:layout_width="match_parent"
        android:layout_height="240dp"
        android:layout_alignParentTop="true"
        android:background="#000000"
        app:layerAttrs="@array/sv_videoview_layers2" >
    </com.sina.sinavideo.sdk.VDVideoView>`

3. 设置一下layout中的素材，比如文字、颜色，图片，大小等等

然后，就可以提交上线了
##组件说明：

1. VDVideoView，统一的接口类
2. VDVideoViewController，使用EventBus方式来处理的消息控制中心
3. ***widgets***，自定义的组件库
4. ***Containers***，自定义的容器类，包裹widgets用得

###VDVideoView
VDVideoView是提供给客户端用的，客户端只需使用VDVideoView就能完成视频的播放的功能；VDVideoView封装了视频播放的View和 控制层UI，提供了横竖屏切换和播放视频的接口。
其中 layerAttrs属性用于设置小屏和全屏的播放器控制层UI。
open(Context context, ArrayList<VDVideoInfo> pathList)  该方法用于设置视频列表。

play(int index)， 该方法用于播放视频列表里的第几个视频

setIsFullScreen(boolean isFullScreen) 该方法用来设置全屏或小屏

stop() 该方法停止播放视频

release() 该方法销毁播放器，
###VDVideoInfoList
播放列表，用来设置需要播放的流
###VDVideoViewController
封装了播放器控制行为操作，例如 手势，按钮点击事件。一般情况下，请不要直接调用
###***widgets***
详细的参考：doc/使用说明书
###***containers***
详细的参考：doc/使用说明书
##一些提示
###我如何安排集成播放器的开发节奏？
我们推荐的开发进程安排如下：


我们自定义了一个layer概念，用于分别堆放不同用途的container与widget。在复杂模式下，一般一个layer表示一个确定的功能，比如：控件层、显示层。系统默认，最下面一层是Videiview层，用来播放视频。

