---
title: "nVidia GForce 4 MX (NV17): Nouveau driver almost works"
date: 2014-05-10
forum: Apple Hardware Users
---

### Post by gsahli on 2014-05-10
PowerMac G4 MDD/867, graphics card nVidia GForce 4 MX (NV17).
Installed Lubuntu 14.04 from alternate install CD. After install, boot progress:
No yaboot menu, get about 10 lines of text, and a change from black background to white,
get simplified blue background (lunubtu) plymouth (plain text and 4 small dots for the animation).
Error message across the plymouth screen: "nouveau: invalid ROM content," plus, "nouveau returns -22"
screen goes black, with mouse pointer only visible.
No other activity. I can get to terminal with Ctrl-Alt-F1.
When I try to run sudo Xorg -configure, It crashes with DRM: failed to load device (maybe related to above errors?)

I'm not desperate - yet! 
But, I have never been able to successfully boot to X with any distro that uses nouveau instead of nv driver.
The only reasonably-current distro I can get to work right now is Debian 6.0.9 with nv.
I've tried nomodeset as yaboot/kernel option - no change.

I'm really hoping that some nouveau expert can help me get to a modern distro!!!

---

### Post by slooksterpsv on 2014-05-10
Xorg -configure will crash if you can see your mouse pointer on TTY7 (not what it's called but can't think of the name). The reason it crashes is cause there's already video loaded there, you'll need to kill the window manager and then run it. lxwm I think... Run sudo killall lxwm it may be lxsession - kill those, run Xorg and try again.

Also, please don't double post, I think your internet may have lagged and Post got clicked twice, it happens to me.

---

### Post by gsahli on 2014-05-10
Thanks, I'll try it tomorrow.

---

### Post by gsahli on 2014-05-11
killing lightdm didn't change the Xorg -configure result.

~/Documents/ubuntu_PPC$ egrep 'EE|WW' Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    57.062] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    57.062] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    57.062] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    57.062] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    57.062] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    57.069] Initializing built-in extension MIT-SCREEN-SAVER
[    57.187] (EE) [drm] failed to open device
[    57.187] (EE) No devices detected.
[    57.189] (WW) Warning, couldn't open module nvidia
[    57.189] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    57.193] (WW) Warning, couldn't open module modesetting
[    57.193] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    57.215] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    57.215] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    57.296] (EE) [drm] failed to open device
[    57.842] (EE) AIGLX: reverting to software rendering

---

### Post by gsahli on 2014-05-12
More info:
I can now get an X session (when I had mouse pointer only on screen, I could find the place to input my password). It's very poor quality, 1024x768 and maybe 4 bit depth. (this particular monitor does 1280x1024 when used with OS X, and also did 1280x1024 on Debian 6.0.9 with nv driver)
Still get error nouveau: ROM content invalid; nouveau returns -22.
run xrandr (my user and root) - it says "Can't open display."

So, I think Xorg and nouveau can't identify card or monitor and can't configure X. 
Any ideas for more troubleshooting? Will an xorg.conf with correct entries work? documentation on xorg.conf is widely scattered/incomplete!

---

### Post by slooksterpsv on 2014-05-13
The xorg.conf documentation is very thorough, I wouldn't say incomplete. Here's what you can do:

Boot into recovery mode in Ubuntu and drop to a bash prompt run the commands I gave you earlier:

Xorg -configure
mv ./xorg.conf.new /etc/X11/xorg.conf

Then try to boot.

---

### Post by gsahli on 2014-05-13
Sorry, I thought I made it clear that I had to kill lightdm (not lxwm), then I ran Xorg -configure (after sudo su).
It made an xorg.conf.new, but after copying it to /etc/X11/xorg.conf, there was no change in boot and X startup.
And the log I trimmed above was the result from startup.

Do you know how I can figure out what port my monitor is connected to? I'm still thinking an explicit xorg.conf might help, because I believe nouveau isn't finding my nVidia or my monitor - not sure which, but the xorg.conf.new has No details about monitor/screen.

Here's the tail of the Xorg -configure:
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
(EE) Server terminated with error (2). Closing log file.

---

