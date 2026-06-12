---
title: "an iMac G4 distro-hopping binge. february 2014"
date: 2014-02-22
forum: Apple Hardware Users
---

### Post by virtualsim on 2014-02-22
So it bit me again, I had to install a modern OS on my 10 years old iMac, which I keep (as the leftmost part of my triple "screen" synergy setup) mostly because its such an interesting object.

It's a 17 inch model from 2003 with USB 2.0 ports (fairly modern as these things go). 

Detailed specs :
Model : PowerMac 6,1
G4e 7445 1.25GHz w/ 256kb cache
1GB RAM
nvidia Geforce Go5200 w/64M VRAM
10/100 networking
160GB PATA hard drive
Triple-boot setup (Linux, OSX Leopard, OSX Tiger)


I kept some notes as I went along, I'm sharing in the hope somebody might find it interesting.

The original idea was to try to reproduce Crunchbang Waldorf (based on Wheezy), which is the distribution I have been looking for since 1998, on the clunker.

I first started with the obvious :

Debian 7 Wheezy powerpc
=========================
Minimal install without a hitch. 
Installed a lot of packages, mostly in an effort to reproduce crunchbang. 
Was going well but got stumped by weird window redraw bug in geany text control when scrolling. 
Upper part of text field would stay unchanged and lower part would turn to garbage. 
I don't even know where to start looking.

This is usually where I loose all common sense and start distro-binging instead of fixing the darned problem. Lets see what we can find... 

Lubuntu 13.10
=============
Nice alternate-iso powerpc image. (I prefer the good-ole debian installer, call me a Luddite.)
Super-Modern Kernel. No support for Suspend-to-Ram in kernel :-(
Installed without a hitch. 
Small glitch in lightDM : It only shows in the upper left quarter of the screen (regular desktop is showing underneath, no biggy). 
Beautiful, simple desktop. 
Put the panel at the top where it belongs. 
Had to resize all fonts down 1 step. 
Disabled icons in menus and on buttons. 
Easy to restore openbox right-click menu behaviour. 
Very fast, low memory usage. 
Might be the best for this old mac.

I remember having been very well served with old Ubuntu LTS releases (8.04 and 10.04) so why not try the latest one?

Xubuntu 12.04
=============

Downloaded 12.04 mini-iso powerpc. Only mirror was in UK. Not really a problem. 
Selected Xubuntu in installer. 
Gorgeous desktop. I like Thunar. 
No support for Suspend-to-Ram in kernel :-(
Tiger and Leopard partition auto-mounted and were fully accessible from thunar. 
Excellent useful Right and Middle click menu on the desktop. 
Super annoying delay (3 full seconds) before appearance of right click menu (middle-click was instant). This was so weird I hunted in all the config panels for a setting thinking maybe this was working as intended (though misguided). Disabling application icons in the menu makes it MUCH faster.

Weird compositing bug with some applications (Sticky Notes, the default Terminal, Gnome-Terminal, Konsole and my cherished Terminator unfortunately). These apps would not draw to the bottom half of the screen. Would disappear when dragged down. Disabling compositing fixes this, but makes all window dragging a slow, tragic affair with extensive smearing, yuck!

Other apps (thunar, leafpad, kate, k3b, xfburn) did not exhibit this problem, so Xubuntu might be fully usable. Aterm was fine, so with tmux, might stand-in for terminator. Aterm did not show in Xubuntu menu however. 


Kubuntu 12.04
=============
kdm is very nice, then login and boots to a completely black screen, with a nicely shaded mouse cursor. Switched to another console and rebooted.


Conclusion
===========
So  I'm back to Lubuntu 13.10 for now. 
I will try Xubuntu 13.10 to see if I still get the compositing bug. 
I will also try to reproduce crunchbang from the Lubuntu base (starting from plain openbox), might be the ultimate thing.

---

### Post by rsavage on 2014-02-22
> **virtualsim said:**
> 
The original idea was to try to reproduce Crunchbang Waldorf (based on Wheezy), which is the distribution I have been looking for since 1998, on the clunker.

A request for this comes up quite often if you read around powerpc forums (which I'm sad enough to do).  I don't see what the big deal is though, surely you just need to add the crunchbang repository and download the packages (looking at [http://packages.crunchbang.org/waldorf/pool/main/](http://packages.crunchbang.org/waldorf/pool/main/) they are mostly 'all' debs so should work on powerpc).  Compile any architecture specific packages.  Have a look at [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_compile_a_package.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_compile_a_package.3F)

> 
Super-Modern Kernel. No support for Suspend-to-Ram in kernel :-(

Are you implying that debian has suspend?  If that is the case (and it is important to you) then I'm fairly certain that you can get suspend working in Ubuntu.  See [https://wiki.ubuntu.com/PowerPCFAQ#Power_preferences.2BAC8-suspend.2BAC8-screen_brightness.2BAC8-multimedia_keys](https://wiki.ubuntu.com/PowerPCFAQ#Power_preferences.2BAC8-suspend.2BAC8-screen_brightness.2BAC8-multimedia_keys) and [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) .  Debian has the legacy framebuffers still built in to the kernel, but according to all the documentation this should break KMS (the nouveau video driver).

> 
Weird compositing bug with some applications (Sticky Notes, the default Terminal, Gnome-Terminal, Konsole and my cherished Terminator unfortunately). These apps would not draw to the bottom half of the screen. Would disappear when dragged down. Disabling compositing fixes this, but makes all window dragging a slow, tragic affair with extensive smearing, yuck!

I'm not sure if this is the same as a problem people have described with Firefox.  See [https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards](https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards) for a solution.

---

### Post by virtualsim on 2014-02-23
@rsavage : Thank you very much for the reply. I will definitely investigate the recompiling of crunchbang packages. I had wanted to do that, but didn't know where to start.

Now for an update :

Xubuntu 13.10
=============
Installed from Lubuntu base with apt-get install xubuntu-desktop.
First load was very long before desktop was ready, possibly related to Thunar initialization.
Right-click menu appears instantly, with default settings (yeah!).
Suspend-to-Ram will disconnect the network, then fail and reconnect network (same as in Lubuntu 13.10, as expected)
Whole desktop feels MUCH more responsive than Xubuntu 12.04, much improved.
Compositing bug is gone, all windows from applications that previously had problems can now be positioned anywhere on-screen, maximized, without problem. This is major.
This is a perfectly usable desktop, very well done and fast. My new favorite.

So far I would readily recommend 13.10 version of both Lubuntu or Xubuntu on this machine. Lubuntu has the advantage of having a native powerpc liveCD and alternate CD, but Xubuntu can be easily installed in a single command from a mini ISO or any other 13.10 ubuntu installation.

---

