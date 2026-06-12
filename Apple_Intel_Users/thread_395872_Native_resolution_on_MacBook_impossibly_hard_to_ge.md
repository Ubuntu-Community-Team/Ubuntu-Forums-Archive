---
title: "Native resolution on MacBook impossibly hard to get"
date: 2007-03-28
forum: Apple Intel Users
---

### Post by Solenoid on 2007-03-28
Hi,

I'm a complete newbie with Ubuntu, I have considered to switch for a long time and I must say it really pleases me, also the hours spend configuring and figuring out what the hell a "terminal" is gives a good sense of satisfaction, given that you get what you want... and here's my problem:

I installed Ubuntu on my MacBook with Parallels, but I can't get the full screen resolution of 1280x800, I must've had Googled it a million times, but with no success. What I've succeeded so far is installing 915resolution package and configuring it to MODE="5c", the XRESO=1280 and YRESO=800. I also tried the vesa and the i810 drivers (by entering [FONT="Courier New"][COLOR="Gray"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR][/FONT] in the terminal), but once I get to choose the resolution with the space bar and check the 1280x800 the next time it boots I get a little BSOD telling me there's an error. I'm sure one of you must know what I'm missing. Basically it doesn't recognize the chipset of the graphics card, [FONT="Courier New"][COLOR="Gray"]sudo 915resolution -l[/COLOR][/FONT] says "Unknown chipset type and unrecognized bios", while I have an Intel 800/900 series and 915resolution works only with 800/900 series... wait a minute...

My MacBook: 1.83GHz, 512MB RAM

My research bibliography (I wasn't going to put everything):
[LIST]
[*][http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)
[*][http://good-for-nothing.org/page.php?17](http://good-for-nothing.org/page.php?17)
[*][http://www.ubuntuforums.org/showthread.php?t=375782](http://www.ubuntuforums.org/showthread.php?t=375782)
[/LIST]

---

### Post by PictureThis on 2007-03-28
My guess is you ran into trouble with the virtual display driver Parallel provides. Parallel will not allow you to directly access your MacBook's hardware, you're running a **virtual** Ubuntu version.

---

### Post by Solenoid on 2007-03-28
> **PictureThis said:**
> My guess is you ran into trouble with the virtual display driver Parallel provides. Parallel will not allow you to directly access your MacBook's hardware, you're running a **virtual** Ubuntu version.

What would you suggest? I'm all out of everything.

---

### Post by PictureThis on 2007-03-28
Well, if you don't mind getting you hands dirty you could go for [this](https://help.ubuntu.com/community/MacBook). Instead of a virtual install you will have to repartition your system and make room for a "genuine" install.

It's a great learning experience but don't expect it to be too easy. :) 

Or... you can wait until you see your version of Ubuntu is (fully) supported under Parallels. Watch [this page](http://www.parallels.com/en/products/desktop/os/). It seems currently v5.04 is currently supported. Which version did you install?

---

### Post by cyberdork33 on 2007-03-28
6.10 works fine under parallels. 

You have to understand that installing in parallels (a Virtual Machine) is not the same as installing on the Mac itself (a real machine). As far as I know, the virtual video device just shows up as a generic vga controller. there is no special driver for it.There should not really be any configuration needed. To enable other resolutions you will need to add them to the xorg.conf so that they can be used in gnome.

---

### Post by mustang on 2007-03-28
Hi Solenoid,

I'm tempted to say that you have a parallels related problem. Both under Edgy and Fiesty, installing the 915resolution package and crtl-alt-backspace was enough.  No additional tweaking was required.

---

### Post by Solenoid on 2007-03-29
I configured the xorg.conf file and I Ctrl+Alt+Backspaced, but the I get the login screen and when I login it throws me back.

---

### Post by cyberdork33 on 2007-03-29
> **Solenoid said:**
> I configured the xorg.conf file and I Ctrl+Alt+Backspaced, but the I get the login screen and when I login it throws me back.

Then you most likely did something that X doesn't like and it is crashing...

---

### Post by Chrisj303 on 2007-03-29
It IS a known issue with parallels. They have yet to release Parallels tools for linux - until that happens, your stuck.
If i was in the same situation, i would ditch parallels, and use VMware Fusion beta - the tools have been part and parcel of it since day one. Under Fusion, amongst other things, you do not have to click in and out of the VM to focus the cursor, and it has better support for dualcore emulation.
The Linux forums for parallels desktop for mac have slowed down BIG TIME since Fusions release - a sign that a lot of users have already jumped ship.

Parallels seem to be focusing mainly on running windows on a Mac - which is a shame, as the ability to install a new distro for a few days as a test run, is REALLY handy. 
cheers,
chrisj303

---

### Post by Solenoid on 2007-03-29
Oh well, I gained some experience (points) from that, the idea was to try it virtually before moving on to my PC (I'm a TriOS). Thanks.

---

