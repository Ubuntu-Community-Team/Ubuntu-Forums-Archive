---
title: "Xubuntu on 2008 Macbook"
date: 2015-01-10
forum: Apple Hardware Users
---

### Post by Peter_Thickett on 2015-01-10
Hi everyone!

I just wiped my macbook and installed a Xubuntu as the sole OS. I was tired of OSX and interested to see how Xubuntu fares, especially since this is an older machine.

Anyway - so far so good, but I do have a couple of minor issues.

Firstly, on startup and shutdown I find that the Xubuntu screen with the rotating circle thing (I assume it is that since I can't really see it) is all corrupted. Typically half the screen is ok, but the top half is all glitched out. I noticed that this was typical even when messing around with live CDs of Ubuntu also.

Secondly, when I go to shutdown, it just hangs on that glitched screen and never turns the laptop off.

Any ideas?

Thanks!

---

### Post by maclenin on 2015-01-10
**Peter_Thickett!**

First - welcome to the forums....

Next - as for the "rotating circle thing" - I have just completed a [very similar install process]("http://ubuntuforums.org/showthread.php?t=2259849") and think this issue could be related to your (start-up) grub / video driver settings. I am still tweaking my set-up - but have had no critical issues with video. As a first step (note: you can always reverse this modification to return to your original settings) - execute this command in the terminal:
```
sudo nano /etc/default/grub
```
Then look for this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Replace "quiet splash" with "nomodeset", hit Ctrl-X and then Y to save.

Update grub via the terminal:
```
sudo update-grub
```
Then enter the command...
```
sudo shutdown -h +0
```
...to hard shutdown the MacBook.

After the MacBook shuts down, press the power button to re-boot the MacBook - it should start - without the "rotating circle thing" screen - and take you straight (after a visible run of a bit of start-up script code) to the login window.

Finally - as for the shutdown issue - are you asking the MacBook to restart (e.g. shutdown -r +0) or hard shutdown (e.g. shutdown -h +0)? I am having a similar issue (as you'll see via the install link above) re: restarting (sudo shutodwn -r +0) my MacBook (late 2009) 64 bit xubuntu install.

Though, all else seems to be working well!

Good luck!

---

### Post by Peter_Thickett on 2015-01-10
Thanks for the reply Maclenin. I did that, and it now starts up with just script rather than the blue thing with the spinny stuff. However it did also change my desktop theme and I think turned AA off? Fonts look a little jaggy now.

The shutdown issue seemed to have gone away the moment I posted my issue to the forum in the first place so I think that was could have been a one-off.

Lastly - I just noticed that my keyboard backlighting isn't functioning. The hotkeys/function keys don't do anything in xubuntu, is there a setting for this somewhere?

EDIT: Looks like it wasn't a change in theme, actually the colors are now inverted on my display LOL. I checked and AA is still on. Any idea what could have caused the display to reverse like this?

Thanks!

---

### Post by maclenin on 2015-01-11
**Peter_Thickett!**

I am afraid I have no quick answers regarding the keyboard / function key questions.... I am performing a similar massage to my set-up and will report any findings / updates to the thread I linked to in my [first reply]("http://ubuntuforums.org/showthread.php?t=2259849").

In the meantime, you might want to "reverse" my grub / nomodeset instructions - to return things to their normal "quiet splash" state - with regard to theme  / colors and font settings, which could have been temporarily altered by the nomodeset toggle.

What are the system stats of your "MacLinux" set-up? I.e. kernel (32 bit, 64 bit?), distro, graphics card, graphics drivers? You might want to install this handy utility ([inxi]("https://code.google.com/p/inxi/wiki/Installation"))...
```
sudo apt-add-repository ppa:unit193/inxi
sudo apt-get update
sudo apt-get install inxi
```
...then enter...
```
inxi -b
```
...to suss those details out, so that folks can give you more tailored guidance.

Happy tweaking!

---

### Post by Peter_Thickett on 2015-01-11
Ok so I was just having some fun last night messing around with some other distros, and tried OpenSuse, but quickly found that it was a little over my head for such a Linux noob. So then I went back to another flavour of Ubuntu and now I have put Mint on here. Obviously all the same issues we discussed above are present - so I think I will hold on to Mint for a while, I would have thought any suggestions that apply to Xubuntu would apply here also.

Anyway I installed that utility, and this is the result of running it:

System:    Host: mintbook Kernel: 3.13.0-37-generic x86_64 (64 bit) Desktop: Gnome Distro: Linux Mint 17.1 Rebecca
Machine:   System: Apple (portable) product: MacBook5 1 version: 1.0
           Mobo: Apple model: Mac-F42D89C8 version: Proto Bios: Apple version: MB51.88Z.007D.B03.0904271443 date: 04/27/09
CPU:       Dual core Intel Core2 Duo CPU P8600 (-MCP-) clocked at 1596.00 MHz 
Graphics:  Card: NVIDIA C79 [GeForce 9400M] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1280x800@60.2hz 
           GLX Renderer: GeForce 9400M/integrated/SSE2 GLX Version: 3.3.0 NVIDIA 331.113
Network:   Card-1: Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller driver: wl 
           Card-2: NVIDIA MCP79 Ethernet driver: forcedeth 
Drives:    HDD Total Size: 240.1GB (2.5% used)
Info:      Processes: 174 Uptime: 25 min Memory: 1522.6/3697.9MB Client: Shell inxi: 1.8.4 


I did find some info about the keyboard backlighting:

[http://ubuntuforums.org/showthread.php?t=1483283](http://ubuntuforums.org/showthread.php?t=1483283)

I will try that a little later.
 
EDIT: I followed those instructions and it worked perfectly. Keyboard backlight now functions and the function keys control it just like in OSX.

The other thing I want to do is test the sleep and wake stuff and see if that is at all reliable. And then finally see if I can find a way to make some form of Google Drive work. Then I will be a all set :)

EDIT: Also I need to try and figure out a way so that when I do a two finger scroll it doesn't select everything on the page at the same time....

---

### Post by maclenin on 2015-01-17
**Peter_Thickett!**

Great work!

Keep posting your findings!

I, unfortunately, had to give up "my" MacBook - to the rightful owner - as the xubuntu install was for a friend - but I / we will be watching your progress in hopes that it may help us untangle any issues that we might encounter.

Again - good luck!

---

