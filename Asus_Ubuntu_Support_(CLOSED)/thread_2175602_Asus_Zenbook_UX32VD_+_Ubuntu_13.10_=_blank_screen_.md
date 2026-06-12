---
title: "Asus Zenbook UX32VD + Ubuntu 13.10 = blank screen on boot/install"
date: 2013-09-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Poleh on 2013-09-20
Hi folks

I have a Zenbook UX32VD which I have been running with 13.04 (and prior) for a long time - works brilliantly.

I recently wanted to try out 13.10 - realizing it was in alpha and now "beta" - but figured I would be ok as I have been good so far with other early releases.

Unfortunately not.

If I try the Install or Try Ubuntu options, the system hangs with a blank screen (backlight is on). I don't even get any flicker of the splash screen or similar. The system is completely unresponsive to everything except a hard power-off.

I tried editing advanced kernel params as follows: nomodeset nosplash (I deleted quiet) and this got me a little further. It booted to the installation, but the top status bar was duplicated about 6 times, consuming about half the screen and it pushed the wizard windows off the bottom of the screen. The result of this was that I couldn't get passed the "Ubuntu One" screen, as the button that you need to click to "log in later" cannot be navigated to with the keyboard, and because it was off-screen, I couldn't hit it with the mouse.

I eventually managed to load up a console by hitting CTRL-ALT-1, I sudo su'd and launched light-dm. This allowed me to progress through the installation successfully as I could move windows around.

After the installation completed successfully (no errors), the machine boots to a blank screen (no backlight) though I DO hear the Ubuntu drums on startup. I cannot open any kind of console / TTY (the CTRL-ALT-1/2/3/4/etc keys don't do anything.

I should say that this situation has persisted through about 2 weeks of daily builds, as well as the milestone builds for alpha (and I think beta, though that may be wrong).

I did a bunch of googling to see if I could get the desktop to even launch in some kind of safe mode, but have had no luck. I am reasonably good navigating around both the console and linux desktop, but am no guru - so a lot of the deeper trouble-shooting is beyond me.

If anyone is able to help me with some trouble-shooting, I would be most grateful - as I mentioned, given instructions, I am quite comfortable negotiating my way around the command-line, editing config files etc.

Here's to hoping! thanks in advance.

[edit] For what it's worth, today's SERVER nightly installed without a hitch...
D

---

### Post by carl4926 on 2013-09-20
Can we assume you have used the Current live image as the Ubuntu 13.10 beta has not been published yet?

---

### Post by Poleh on 2013-09-21
> **carl4926 said:**
> Can we assume you have used the Current live image as the Ubuntu 13.10 beta has not been published yet?

Yes that is correct - I have in fact been using the daily builds for some time.

Some further information - I re-installed 13.04 last night - as expected, all went really well. Did a full sudo apt-get update/upgrade and again everything went fine through the reboots.

I then grabbed the latest mainline kernels from the Ubuntu download site, specifically:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.1-saucy/)

Installed them with dpkg -i ./*.deb which all went as expected until I rebooted. At this point, the exact same symptoms described above ocurred - the machine boots, I hear the startup "drums" but the screen is blank.

If I boot through advanced options and select the 3.8.x kernel, I get to my full desktop no problem.

So there's something in the Saucy kernel causing this, would that likely be something to do with the Intel Ivybridge video drivers?

Does anyone have any further recommendations on how I diagnose this?

Thanks in advance.

---

### Post by Poleh on 2013-09-25
Ok, a bit more research on this issue has turned up a likely Kernel bug:
[https://bbs.archlinux.org/viewtopic.php?pid=1308477](https://bbs.archlinux.org/viewtopic.php?pid=1308477)

This thread describes the issue exactly as I have it, and goes into a lot of detail on patching the kernel to fix it. This is a little beyond me, and given it's looking like a kernel bug, what would the next steps be? How do I report this issue to the Ubuntu dev team? Are they even the right people to be notifying?

---

### Post by carl4926 on 2013-09-26
> **Poleh said:**
> Ok, a bit more research on this issue has turned up a likely Kernel bug:
[https://bbs.archlinux.org/viewtopic.php?pid=1308477](https://bbs.archlinux.org/viewtopic.php?pid=1308477)

This thread describes the issue exactly as I have it, and goes into a lot of detail on patching the kernel to fix it. This is a little beyond me, and given it's looking like a kernel bug, what would the next steps be? How do I report this issue to the Ubuntu dev team? Are they even the right people to be notifying?

Check here
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by tahdas on 2013-09-26
> **Poleh said:**
> Hi folks

I have a Zenbook UX32VD which I have been running with 13.04 (and prior) for a long time - works brilliantly.

May i ask what you used to install it? Ie: Usb thump drive, sd card from camera, external dvd drive. did you have to dissable anything to get it to boot? 

Im having trouble get ubuntu to live boot on mine.

thanks,
tahdas

---

### Post by Poleh on 2013-09-26
> **tahdas said:**
> May i ask what you used to install it? Ie: Usb thump drive, sd card from camera, external dvd drive. did you have to dissable anything to get it to boot? 

Im having trouble get ubuntu to live boot on mine.

thanks,
tahdas

What version are you trying to boot into a live cd?

I have always used a USB stick that I created with the Universal USB Installer from the ISO media - all versions except 13.10 have worked perfectly with this method. 13.10 won't boot by default, from the installer on a USB stick, CDROM, or DVD. And this is with multiple downloads of daily's so it wasn't a bad download.

If you're trying earlier version (I just re-installed 13.04) one thing I did find is that if you use the left-hand side USB port, you get all sorts of errors on boot for the installation / live media. I always use the right-hand side port, furtherest away from you (closest to the power plug) and it works fine.

You also need to ensure you install the latest BIOS and disable all secure boot options in the BIOS. Check out the WIKI for our model here: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

If you continue to have issues, please create a new thread and I will be happy to help you - I would like to keep this thread for my issue above.

---

### Post by tahdas on 2013-09-27
new thread: [http://ubuntuforums.org/showthread.php?t=2176979&p=12799880#post12799880](http://ubuntuforums.org/showthread.php?t=2176979&p=12799880#post12799880)

---

### Post by Poleh on 2013-09-30
OK, so I have been installing various mainline kernels to see where this issue occurs. I tested it using 13.04, and then installing the kernels.

Everthing works fine on 3.9.11, and the issue manifests in 3.10.03

I haven't been able to report a bug, as this is my only machine and the debugging requirements on the ubuntu kernel bug tracker need me to post a bunch of things I cannot collect. I am hoping some admins/senior folks can help me out with the bug report. There's also the issue of this being a mainline kernel and ubuntu suggesting that this needs to be reported upstream.

Googling "intel i915 kernel 3.10" brings up a number of results with this exact issue - various distros seem to have fixes and kernel patches to fix it, so hopefully the ubuntu kernels get a fix soon. I will do what I can to help.

---

### Post by Uzi on 2013-10-21
I have clevo 370em with radeon crossfire setup and the same problem. It appears ubuntu is not for everyone. Or maybe 13.10 is not tested properly :(. Going back to windows

---

### Post by y-mail-x on 2013-10-22
I have exactly the same problem on my UX32VD. Ubuntu 13.04 works fine.
If I try to upgrade to 13.10, then I have a black screen after upgrade. Trying to boot from USB - same problem.
Secure Boot is disabled.

But author says that he has unresponsive system.

My system boots fine, except the screen. For expample, in live-USB I can press next combinations:
1) CTRL+ALT+F1
2) "ubuntu"
3) "sudo reboot"
4) After ~5-6 seconds pressing any key
The system reboots normally.

If I choose "Install Ubuntu" on boot screen, I can hear loading sound after Live-USB loads. So the system works fine.

I've tried 13.10, 14.04  daily images but the problem still happenings.

---

### Post by 7ql6 on 2013-10-23
The correct bug ticket is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229686](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229686) (and it has medium priority?)

---

### Post by onlyteo on 2013-11-01
I believe this to be a 3.10.x kernel issue. Had same problem with my UX32VD on Fedora, when going from 3.9.x to 3.10.x. No solution found yet.

---

