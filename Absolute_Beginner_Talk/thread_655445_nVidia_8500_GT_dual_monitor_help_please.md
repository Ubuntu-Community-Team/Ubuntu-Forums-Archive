---
title: "nVidia 8500 GT dual monitor help please"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by yaru22 on 2008-01-01
Hi, 

I bought a desktop (with nVidia 8500 GT graphic card) and two Samsung Syncmaster 932BF monitors.

I'm trying to set up dual monitors for this system, but I'm having difficulties doing so.

I installed nVidia graphic card driver downloaded from nvidia website. Currently, I can use one monitor (connected to dvi port).

When I run nvidia-settings, I notice that it detects the first monitor (connected to dvi port) as syncmaster but the second one (connected to vga port) as just CRT-1. And if I try to set configuration as TwinView, then the second monitor's resolution can only go up to 640*480. Also, if I apply the settings there, it says  it failed to set metamode.

So I'm stuck at this stage and cannot setup the dual monitor system. Can anyone shed some light on this? Thank you.

- Brian

---

### Post by LordTyrans on 2008-01-01
Hi regarding your problem,

Maby you should try the x configuration utility if you haven't already (I'm not sure which settings you were talking about).
To do this type gksudo nvidia-settings into the terminal, the terminal can be found in the applications/accessories menu.This should work for most nvidia cards using the 9.xxx drivers. I believe this should let you configure the duel monitors. Just for reference this is where i got the information from.

"http://ubuntuforums.org/showthread.php?t=221174" 

And 

"http://ubuntuforums.org/showthread.php?p=1773584"

---

### Post by yaru22 on 2008-01-01
I ran nvidia-settings on terminal and when the windows pops up, I noticed that DFP-0 is correctly identified as Samsung Syncmaster but CRT is just identified as CRT. Since the monitor is not identified correctly, I can't set the resolution of CRT monitor (which is also Samsung Syncmaster) higher than 640x480.

---

### Post by LordTyrans on 2008-01-03
Huum 

I will look into this more next weekend, at the moment i am quite busy.

But after a quick look i have found out that there are quite a few problems with this monitor on Linux, but that might just be coincidence, But then that means there should be allot of answers to your problem as most seem to be resolution related.

I Also Suspect that it wont be the graphics card that is causing the problem So that makes it even easier.

One thing to try is typing "sudo dpkg-reconfigure xserver-xorg" into the Terminal, That should make the PC automatically configure the x-window config file which may solve the problem.

[Here]("http://ubuntuforums.org/showthread.php?t=280683&page=3") is a form that is about a smiler problem to yours.

One last thing, Check how many Hz it it running at, it should be running at 60hz for a high resolution... otherwise it wont go much over 640x480.

---

### Post by LarryJ2 on 2008-01-15
Hi Brian,

If you don't have your dual monitor set up running yet, give this a try.  Your setup is similar to mine (nVidia G7300GS  driving two SyncMaster 216BWs (Left one analog CRT mode and right hand one in  digital dvi DFP mode) in twinview or desktop span mode which is working fine here.

1. Use  Adept Manager to install   nvidia-glx-new and nvidia-xconfig. 

2.  In a terminal acting with admin privileges (root) enter
sudo nvidia-xconfig  
Close the terminal after you have confirmation that a new xorg.conf has been written.  Note the backup(your old xorg.conf renamed)  incase you have to re-install the old xorg.conf should this scheme not work and you want to go back to where you were.

3. reboot

4.  In another terminal, enter
gksu nvidia-settings

That hopefully will bring up nvidia settings where the X Server Information at the top left of the window shows nvidia driver 100.14.19.   From htere just set up Xserver Display Configuration -> Configuration ->TwinView with the appropriate resolutions.   Attached is a screen shot of my Nvidia X Server Settings window.  Also I'm attaching the nvidia portion of my xorg.conf  which runs twin view with the two syncmasters described above.   After getting all set in the nvidia-settings,  exit and save a copy to xorg.conf, again remember the name of the backup or renamed current xorg.conf file incase you want to move back to it.

Hope this helps.   I've been struggling with this for days.   Apparently when intially  installing, we must force the installer to use the VESA graphic driver   or use one of the text mode installation CDs.
Larry

---

### Post by glaurens on 2008-01-24
Found the solution:

just add the line

Option "ConnectedMonitor" "CRT,CRT"


under the relative device section. Obviously if you are only running one monitor per GPU then use only one CRT.

Now I'm off to go and play with the different modes since it boots up with the incorrect resolution now, but at least it works.

The link where I found this is:

[http://gentoo-wiki.com/HOWTO_Dual_Mo...fter_X_startup](http://gentoo-wiki.com/HOWTO_Dual_Mo...fter_X_startup)

G

---

