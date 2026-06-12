---
title: "mount internal harddrive to recover data after gnome failure"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-09-24
!@#$ computer screwed again
just got a new harddrive, spent 40 hours over the weekend setting up ubuntu and downloading music again, then did an update and was told to restart the x server
did thet but wound up in text based mode, tried various things to fix but none worked, so now i wanna reinstall but dont want to lose my current data, i want to mount the harddisk on the live boot disk, access my music data which is on my account desktop and burn it to cd
the only thing is i do not know how to mount a internal harddisk under the live boot disk
can i get a tutoreal please?
it is a ultra ide 250 gb seagate
my account was called bluefoxx and computer was azurE-prIDE

---

### Post by 99bluefoxx on 2007-09-24
any help please?

---

### Post by bone2006 on 2007-09-24
it's pretty easy, open up nautilus and look on the left side with a list of partitions and click on it once and it's mounted, click on it twice and you are accessing it.  With the liveCD just click on top and select home and you'll see your partitions/drives on the left side.

---

### Post by benerivo on 2007-09-24
I think if you run GParted from the live cd (it's in the main menu somewhere), then you can mount and unmount individual drives and partitions using that. When mounted, a drive icon should automatically appear on your desktop.

---

### Post by 99bluefoxx on 2007-09-24
it shows up it gparted but doesnt mount on the desktop
and it also doesnt show in nautilus

---

### Post by 99bluefoxx on 2007-09-24
any other ideas?

---

### Post by benerivo on 2007-09-24
Presuming that your drive is known as /dev/hda1 (it will have shown you in gparted), then you can try these two lines in a terminal...

```
sudo mkdir /media/drive

sudo mount /dev/hda1 /media/drive
```

---

### Post by 99bluefoxx on 2007-09-24
tried it
heres result
```
root@ubuntu:~# sudo mount hda
mount: can't find hda in /etc/fstab or /etc/mtab
root@ubuntu:~# sudo mkdir /media/drive
root@ubuntu:~# sudo mount /dev/hda1 /media/drive
root@ubuntu:~# sudo mount /dev/hda /media/drive
mount: you must specify the filesystem type
root@ubuntu:~# sudo mount /dev/hda1 /media/drive
mount: /dev/hda1 already mounted or /media/drive busy
mount: according to mtab, /dev/hda1 is already mounted on /media/drive
root@ubuntu:~#
```
however, when i check /media/drive i found nothing

---

### Post by 99bluefoxx on 2007-09-24
> **99bluefoxx said:**
> tried it
heres result
```
root@ubuntu:~# sudo mount hda
mount: can't find hda in /etc/fstab or /etc/mtab
root@ubuntu:~# sudo mkdir /media/drive
root@ubuntu:~# sudo mount /dev/hda1 /media/drive
root@ubuntu:~# sudo mount /dev/hda /media/drive
mount: you must specify the filesystem type
root@ubuntu:~# sudo mount /dev/hda1 /media/drive
mount: /dev/hda1 already mounted or /media/drive busy
mount: according to mtab, /dev/hda1 is already mounted on /media/drive
root@ubuntu:~#
```
however, when i check /media/drive i found nothing
nvm i found it, it was a folder called "home">>
didnt look hard enugh thanks for help^^

---

### Post by 99bluefoxx on 2007-09-24
ok while rifling around in my account i found a txt file containing the following
/```
etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bluefoxx"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/91keytouch-acpid_launch: 1: /usr/bin/keytouch-acpid: not found
/etc/X11/Xsession.d/92keytouchd_launch: 1: /usr/bin/keytouchd: not found
SESSION_MANAGER=local/azurE-prIDE:/tmp/.ICE-unix/4596
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 49166 1190790000 1190740834
evolution-alarm-notify-Message:  Wed Sep 26 00:00:00 2007

evolution-alarm-notify-Message:  Tue Sep 25 10:20:34 2007

Unable to open desktop file file:///usr/share/applications/kde/kaffeine.desktop for panel launcher: No such file or directory
Unable to open desktop file file:///usr/share/applications/banshee.desktop for panel launcher: No such file or directory
java.lang.ClassNotFoundException: irc.plugin.
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:164)
    at irc.IRCApplication.loadPlugin(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@12c8fa8
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
    at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
    at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
    at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
    at irc.IRCApplication.sourceCreated(Unknown Source)
    at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
    at irc.IRCApplication.newServer(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@12c8fa8
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
    at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
    at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
    at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
    at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
    at irc.IRCApplication.sourceCreated(Unknown Source)
    at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
    at irc.IRCApplication.newServer(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@12c8fa8
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.Source.report(Unknown Source)
    at irc.IRCServer.sendStatusMessage(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCApplication.newServer(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@12c8fa8
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.Source.report(Unknown Source)
    at irc.IRCServer.sendStatusMessage(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCApplication.newServer(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@12c8fa8
current thread is Thread[main,5,main]
please submit a bug report to [EMAIL="bugs@frostwire.com"]bugs@frostwire.com[/EMAIL] with the following information :
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
    at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
    at irc.ListenerGroup.sendEventEx(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.ListenerGroup.sendEvent(Unknown Source)
    at irc.Source.report(Unknown Source)
    at irc.IRCServer.sendStatusMessage(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCServer.connect(Unknown Source)
    at irc.IRCApplication.newServer(Unknown Source)
    at irc.IRCApplication.init(Unknown Source)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
    at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
    at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
    at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
    at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
    at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
    at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:585)
    at com.limegroup.gnutella.gui.Main.main(Main.java:44)
attempt to provide package tls 1.5 failed: package tls 1.50 provided instead
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2a0002b specified for 0x2a0002f (Tip of the).
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e810) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16cf10) D3D Initialization failed for WineD3DDevice 0x190898
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e760) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16d5a8) D3D Initialization failed for WineD3DDevice 0x1df060
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x1def08) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e7f8) D3D Initialization failed for WineD3DDevice 0x301d638
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bae8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x306bf08
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bd58) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x30ba318
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16dea8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:ntdll:RtlpWaitForCriticalSection section 0x7e9e4000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e9db000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e810) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16cf10) D3D Initialization failed for WineD3DDevice 0x190898
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e760) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16d5a8) D3D Initialization failed for WineD3DDevice 0x1df060
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x1def08) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e7f8) D3D Initialization failed for WineD3DDevice 0x301d638
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bae8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x306bf08
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bd58) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x30ba318
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16dea8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
wine: Critical section 7e9db000 wait failed at address 0x7efaddf0 (thread 000c), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000011 
    00000012    0
0000000a (D) (null)
    0000000c    0
    0000000b    0
00000008 
    00000009    0
wine client error:b: write: Bad file descriptor
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x3400007
  Serial number of failed request:  348
  Current serial number in output stream:  349
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x3400007
  Serial number of failed request:  348
  Current serial number in output stream:  349
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x3400007
  Serial number of failed request:  348
  Current serial number in output stream:  349
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6d0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6d0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e810) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16cf10) D3D Initialization failed for WineD3DDevice 0x190898
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e760) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16d5a8) D3D Initialization failed for WineD3DDevice 0x1df060
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x1def08) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e7f8) D3D Initialization failed for WineD3DDevice 0x301d638
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bae8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x306bf08
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bd58) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x30ba318
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16dea8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
err:ntdll:RtlpWaitForCriticalSection section 0x7e9e4000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e9e4000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e810) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16cf10) D3D Initialization failed for WineD3DDevice 0x190898
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e760) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16d5a8) D3D Initialization failed for WineD3DDevice 0x1df060
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x1def08) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e7f8) D3D Initialization failed for WineD3DDevice 0x301d638
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bae8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x306bf08
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bd58) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x30ba318
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16dea8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e810) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16cf10) D3D Initialization failed for WineD3DDevice 0x190898
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16e760) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16d5a8) D3D Initialization failed for WineD3DDevice 0x1df060
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x1def08) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e7f8) D3D Initialization failed for WineD3DDevice 0x301d638
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bae8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x306bf08
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x306bd58) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x30ba318
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16dea8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x1defa0) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:ntdll:RtlpWaitForCriticalSection section 0x7e9db000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Link points to "/tmp/ksocket-bluefoxx"
can't create mcop directory
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e9db000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d6c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d6c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eedc,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6e8,0x00000000), stub!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x192630) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e078) D3D Initialization failed for WineD3DDevice 0x192a38
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x191df0) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e078) D3D Initialization failed for WineD3DDevice 0x3010020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x191d18) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x191ee0) D3D Initialization failed for WineD3DDevice 0x30510a0
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16ed28) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x192378) D3D Initialization failed for WineD3DDevice 0x3093550
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16fa98) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e8f8) D3D Initialization failed for WineD3DDevice 0x30d45d0
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x16fcb8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x16e8f8) D3D Initialization failed for WineD3DDevice 0x3120020
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Xlib:  extension "GLX" missing on display ":0.0".
err:ntdll:RtlpWaitForCriticalSection section 0x7e9e4000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0011, blocked by 0010, retrying (60 sec)
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-terminal' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :0.0 host broken (explicit kill or server shutdown)
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gksu' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

/usr/lib/jvm/java-1.5.0-sun/jre/bin/
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
```

i think that somewhere in there is the reason gnome failed, like i said it was a x error relating to nvidia-glx
can i get some moar help please?

---

