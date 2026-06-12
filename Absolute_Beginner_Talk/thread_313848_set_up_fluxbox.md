---
title: "set up fluxbox"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by smile_sunshine on 2006-12-06
Hi,
I downloaded fluxbox via synaptic but when I load it there are no menus for opening my programs - I cant even load a terminal screen or anything??
how do i set it up please??

Thanks :)

---

### Post by yabbadabbadont on 2006-12-06
Fluxbox doesn't display a menu by default, you have to right-click the desktop to bring up the menu.  Are you saying that there is no menu when you right-click?

---

### Post by smile_sunshine on 2006-12-06
yes

---

### Post by yabbadabbadont on 2006-12-06
Make sure that menu and menu-xdg are installed.  Then try running, "sudo update-menus" and see if it helps any.  If not, please post the output of "ls -l ~/.fluxbox" and the contents of your ~/.fluxbox/init and ~/.fluxbox/menu files.

---

### Post by bodhi.zazen on 2006-12-06
[Collection of fluxbox how-to's](http://community.fluxbuntu.org/index.php?PHPSESSID=3upcm1l6drpv8rebut8s8pb3j7&board=18.0)

---

### Post by smile_sunshine on 2006-12-06
thanks :)

possibly something went wrong when i installed it using synaptic since amule that i downloaded at the same time isn't configured either???

(sudo update-menus didnt work :() 

.fluxbox/menu: 
> [begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]


ls -l /.fluxbox
> drwxr-xr-x 2 user1 user1 4096 2006-12-06 21:39 backgrounds
-rw-r--r-- 1 user1 user1 8570 2006-12-06 21:42 fluxbox-menu
-rw-r--r-- 1 user1 user1 3470 2006-12-06 21:45 init
-rw-r--r-- 1 user1 user1  306 2006-12-06 21:39 keys
-rw-r--r-- 1 user1 user1   66 2006-12-06 21:39 menu
-rw-r--r-- 1 user1 user1 8053 2006-12-06 21:42 menudefs.hook
drwxr-xr-x 2 user1 user1 4096 2006-12-06 21:39 pixmaps
-rwxr-xr-x 1 user1 user1 1040 2006-12-06 21:39 startup
drwxr-xr-x 2 user1 user1 4096 2006-12-06 21:39 styles


.fluxbox/init
> 
session.screen0.window.focus.alpha:	255
session.screen0.window.unfocus.alpha:	255
session.screen0.menu.alpha:	255
session.screen0.toolbar.tools:	workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
session.screen0.toolbar.widthPercent:	66
session.screen0.toolbar.placement:	BottomCenter
session.screen0.toolbar.height:	0
session.screen0.toolbar.onTop:	False
session.screen0.toolbar.visible:	true
session.screen0.toolbar.onhead:	0
session.screen0.toolbar.autoHide:	false
session.screen0.toolbar.alpha:	255
session.screen0.toolbar.maxOver:	false
session.screen0.toolbar.layer:	Desktop
session.screen0.iconbar.wheelMode:	Screen
session.screen0.iconbar.mode:	WorkspaceIcons
session.screen0.iconbar.iconTextPadding:	10l
session.screen0.iconbar.iconWidth:	70
session.screen0.iconbar.alignment:	Left
session.screen0.iconbar.deiconifyMode:	Follow
session.screen0.iconbar.usePixmap:	true
session.screen0.overlay.lineWidth:	1
session.screen0.overlay.lineStyle:	LineSolid
session.screen0.overlay.joinStyle:	JoinMiter
session.screen0.overlay.capStyle:	CapNotLast
session.screen0.tab.height:	16
session.screen0.tab.width:	64
session.screen0.tab.placement:	Top
session.screen0.tab.alignment:	Left
session.screen0.tab.rotatevertical:	True
session.screen0.slit.onhead:	0
session.screen0.slit.placement:	BottomRight
session.screen0.slit.autoHide:	false
session.screen0.slit.direction:	Vertical
session.screen0.slit.layer:	Dock
session.screen0.slit.maxOver:	false
session.screen0.slit.onTop:	False
session.screen0.slit.alpha:	255
session.screen0.windowPlacement:	RowSmartPlacement
session.screen0.rootCommand:	
session.screen0.fullMaximization:	false
session.screen0.windowMenu:	
session.screen0.workspaces:	4
session.screen0.resizeMode:	Bottom
session.screen0.tabFocusModel:	ClickToTabFocus
session.screen0.sloppywindowgrouping:	true
session.screen0.workspaceNames:	one,two,three,four,
session.screen0.decorateTransient:	false
session.screen0.focusNewWindows:	true
session.screen0.strftimeFormat:	%k:%M
session.screen0.imageDither:	false
session.screen0.desktopwheeling:	true
session.screen0.showwindowposition:	true
session.screen0.colPlacementDirection:	TopToBottom
session.screen0.followModel:	Ignore
session.screen0.clickRaises:	true
session.screen0.edgeSnapThreshold:	0
session.screen0.autoRaise:	false
session.screen0.windowScrollAction:	
session.screen0.focusModel:	ClickFocus
session.screen0.menuDelayClose:	0
session.screen0.workspacewarping:	true
session.screen0.focusLastWindow:	true
session.screen0.menuDelay:	0
session.screen0.opaqueMove:	false
session.screen0.windowScrollReverse:	false
session.screen0.menuMode:	Delay
session.screen0.antialias:	true
session.screen0.rowPlacementDirection:	LeftToRight
session.titlebar.left:	Stick 
session.titlebar.right:	Minimize Maximize Close 
session.numLayers:	13
session.menuFile:	~/.fluxbox/menu
session.useMod1:	true
session.cacheLife:	5l
session.focusTabMinWidth:	0
session.tabs:	true
session.autoRaiseDelay:	250
session.doubleClickInterval:	250
session.styleFile:	/usr/share/fluxbox/styles/Meta
session.imageDither:	True
session.appsFile:	~/.fluxbox/apps
session.tabsAttachArea:	Window
session.slitlistFile:	~/.fluxbox/slitlist
session.forcePseudoTransparency:	false
session.tabPadding:	0
session.cacheMax:	200l
session.keyFile:	~/.fluxbox/keys
session.ignoreBorder:	false
session.opaqueMove:	False
session.colorsPerChannel:	4
session.groupFile:	~/.fluxbox/groups
session.iconbar:	true



---

### Post by smile_sunshine on 2006-12-06
fixed  :) :)

I copied /etc/X11/fluxbox/fluxbox-menu  to ~./fluxbox/menu

thanks for the help :)

will have a look at those how-tos now to learn how to use it - thanks :)

---

### Post by yabbadabbadont on 2006-12-06
The menu file you had should have worked...  :-k 

Your solution works too though.  You just need to be aware that newly installed programs might not show up.  If they don't, just copy the file from /etc/X11/... again.  Or you could make ~/.fluxbox/menu be a symbolic link that points to /etc/X11/fluxbox/fluxbox-menu

---

### Post by kerry_s on 2006-12-06
[begin] (Fluxbox)

[exec] (Files) {emelfm} 

[exec] (Terminal) {xterm} 
 
[submenu] (Net)
 [exec] (Seamonkey) {seamonkey}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Mplayer) {gmplayer}
 [exec] (Wmix) {wmix}
 [exec] (Kill-Wmix) {killall wmix}
[end]

[submenu] (Tools)
 [exec] (XFburn) {xfburn}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Files) {gksu emelfm}
 [exec] (Terminal-Root) {gksu xterm}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {fbrun}
[exec] (Keyboard) {xvkbd -no-keypad}

[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exec] (Screen Off) {/home/user/.screen-off}
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

---

### Post by yabbadabbadont on 2006-12-07
This is my fluxbox menu file from when I was using Gentoo.  It was created by running a modified version of the fluxbox-generate_menu script that comes with the fluxbox source code.  (I don't believe that it is included in the Debian/Ubuntu packaging of Fluxbox)

```
# Generated by fluxbox-generate_menu
#
# If you read this it means you want to edit this file manually, so here
# are some useful tips:
#
# - You can add your own menu-entries to ~/.fluxbox/usermenu
#
# - If you miss apps please let me know and I will add them for the next
#   release.
#
# - The -r option prevents removing of empty menu entries and lines which
#   makes things much more readable.
#
# - To prevent any other app from overwriting your menu
#   you can change the menu name in .fluxbox/init to:
#     session.menuFile: /home/you/.fluxbox/my-menu
[begin] (Fluxbox)
      [exec] (uxterm) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000} 
      [exec] (firefox) {firefox} </usr/share/pixmaps/firefox-icon.png>
      [exec]   (Run) {fbrun } 
[submenu] (Terminals)
      [exec]   (xterm) {xterm} 
      [exec]   (Eterm) {Eterm} 
[end]
[submenu] (Net)
[submenu] (Browsers)
      [exec]   (firefox) {firefox} </usr/share/pixmaps/firefox-icon.png>
      [exec]   (links-graphic) {links -driver x forums.gentoo.org} </usr/share/pixmaps/links.xpm>
      [exec]   (links) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e links forums.gentoo.org} 
[end]
[submenu] (Mail)
      [exec]   (thunderbird) {thunderbird} </usr/share/pixmaps/thunderbird-icon.png>
[end]
[end]
[submenu] (Editors)
      [exec]   (gvim) {gvim} </usr/share/pixmaps/gvim.xpm>
      [exec]   (evim) {evim} 
      [exec]   (nano) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e nano} 
      [exec]   (vim) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e vim} 
      [exec]   (vi) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e vi} 
[end]
[submenu] (File utils)
      [exec]   (thunar) {thunar} 
[end]
[submenu] (Multimedia)
[submenu] (Graphics)
      [exec]   (gimp) {gimp} </usr/share/pixmaps/gimp.png>
      [exec]   (gimp-2.2) {gimp-2.2} 
      [exec]   (gqview) {gqview} </usr/share/pixmaps/gqview.png>
      [exec]   (gcolor2) {gcolor2} </usr/share/pixmaps/gcolor2/icon.png>
      [exec]   (twf) {twf} 
      [exec]   (gtkam) {gtkam} </usr/share/pixmaps/gtkam.png>
      [exec]   (cinepaint) {cinepaint} </usr/share/pixmaps/cinepaint.png>
      [exec] (blender) {blender -w} </usr/share/pixmaps/blender.png>
[end]
[submenu] (Audio)
      [exec]   (audacious) {audacious} </usr/share/pixmaps/audacious.png>
      [exec]   (alsamixer) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e alsamixer} 
[end]
[submenu] (Video)
      [exec]   (xine) {xine} </usr/share/pixmaps/xine.xpm>
      [exec]   (gmplayer) {gmplayer} </usr/share/pixmaps/mplayer.xpm>
[end]
[submenu] (X-utils)
      [exec]   (xfontsel) {xfontsel} 
      [exec]   (xclock) {xclock} 
      [exec]   (gkrellm2) {gkrellm2} </usr/share/pixmaps/gkrellm.xpm>
      [exec] (Reload .Xdefaults) {xrdb -load /home/bubba/.Xdefaults} 
[end]
[end]
[submenu] (Office)
      [exec]   (xclock) {xclock} 
      [exec]   (xpdf) {xpdf} 
      [exec]   (xchm) {xchm} </usr/share/icons/hicolor/16x16/apps/xchm.xpm>
[end]
[submenu] (Games)
      [exec]   (scummvm) {scummvm} </usr/share/pixmaps/scummvm.xpm>
[end]
[submenu] (System Tools)
[submenu] (Burning)
      [exec]   (nero) {nero} </usr/share/nero/pixmaps/nero.png>
[end]
      [exec]   (vmware) {vmware} </usr/share/pixmaps/vmware.png>
      [exec]   (top) {uxterm -bg gray25 -fg gray -fn "-xos4-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*" -geometry 125x50+0+0 -sl 3000 -e top} 
[end]
[submenu] (fluxbox menu)
      [config] (Configure) 
[submenu] (Styles)
      [include] (/usr/share/fluxbox/menu.d/styles/) 
[end]
      [workspaces] (Workspace List) 
[submenu] (Tools)
      [exec]   (gtk-chtheme) {gtk-chtheme} 
      [exec]   (nvidia-settings) {nvidia-settings} </usr/share/pixmaps/nvidia-settings.png>
      [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center} 
      [exec] (Screenshot - JPG) {import screenshot.jpg && display -resize 50% screenshot.jpg} 
      [exec] (Screenshot - PNG) {import screenshot.png && display -resize 50% screenshot.png} 
      [exec] (Run) {fbrun } 
      [exec] (gtk-theme-switch) {switch} 
      [exec] (gtk2-theme-switch) {switch2} 
      [exec] (Regen Menu) {fluxbox-generate_menu-hacked -is -ds} 
[end]
      [commanddialog] (Fluxbox Command) 
      [reconfig] (Reload config) 
      [reloadstyle] (Reload style) 
      [restart] (Restart) 
      [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center} 
      [separator] 
      [exit] (Exit) 
[end]
[end]

```

---

