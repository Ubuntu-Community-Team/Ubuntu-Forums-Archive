---
title: "very dissapointed"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by rephil1000 on 2006-09-07
I have recently downloaded and ran ubuntu.  So far the quality of the product is below standards.  I am installing on a PII 450 with 384M ram.  I cannot change the very low screen resolution of 640x480.  Also, when trying to install the product on my hardrive I am not able to see the confirmation or abort buttons on the installation forms.  This is all after a week of trying to get my wireless network card to work with opensuse 10.1 (atleast this was successful with ubuntu).  Also, many have boasted about the virtues of Linux, my first experiences however (with opensuse), have showed an operating system with poor performance and inconsistent documenataion (regarding the wireless card atleast).  Both systems have proven to be sluggish and cumbersome to configure even the most basic hardware.  Can anyone recommend something that will change my mind?

---

### Post by xpod on 2006-09-07
Taking it up with your hardware supplier seems to be way to go.....
Or mabey coming on here and "asking" for help..I find THAT always works.

PS: hardware probably dont come much more basic than the couple of heaps o junk i use and after two weeks using ubunto and kubunto i can safely say 
There great.....works at the speed o light unlike windows which runs like clocklwork

---

### Post by FakeOutdoorsman on 2006-09-07
I've found this forum a great resource to finding the many questions I have about Ubuntu.  Most of my questions have already been asked here.  Another good resource is [ubuntuguide.org]("http://ubuntuguide.org").

Ubuntu still needs work but it's getting better with every release.  If you have any questions just ask this forum.

---

### Post by meng on 2006-09-07
The reality is that Linux isn't for everyone. I don't feel bad about that, and neither should you or anyone else.

On the other hand, if you want help, ask for it. Some of the members here like offering help in response to complaining posts. Many don't bother, since everyone's time is valuable and there are many other posts that ask for help and don't whine.

---

### Post by bodhi.zazen on 2006-09-07
As a new Linux user hardware problems can be very daunting. My advice is to consider and research an alternate distro.

I am not sure about wireless. Consider BLAGG/Fedora, PCLinuxOS, Mepis, ....

---

### Post by nickpaton on 2006-09-07
Hi Rephil1000 and welcome to Ubuntu and the forums here.

I'm not sure about the minimum CPU specification, but you do have over the minimum memory requirement of 256Mb.

Bear in mind that you do have a relatively slow processor, and it will only run as fast as the processor allows.

However there are one or two things to try.

First you will need to open the Terminal.  This is found under Applications>Accessories and click on the Terminal Icon.

We need to open the Grub program:

Do a copy / paste of the following into the Terminal:

```
gksudo gedit /boot/grub/menu.lst
```

It will ask for your password - the same as when you logged on when Ubuntu started.

After a few seconds you will get an error message within Terminal, but a couple of secs later you will get the Grub script in a separate window.

Scroll down to the line which looks something like this:

> title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


At the end of the 'kernel' line add 

> noapic  

This should help speed up Ubuntu.
You may also want to add

> VGA=791 

before noapic.  This will give you slightly smaller Ubuntu loading and shut down text.

Save that and Quit.

Close the Terminal.

Regarding the screen resolution, please could you post the following to us.

Again in the Terminal type / copy / paste:

```
sudo nano -B /etc/X11/xorg.conf
```

This is the X11 Script, and is the set up for all your PC's components, including the available screen resolutions.

When you post it, please could you put it between Quotes using the Quote symbol at the top of the posting window.  Makes it easier to read.

Close the script.

Also please advise the make model of your screen, and what resolution you would like.

Once again welcome! Ubuntu is a fantastic package and it's worth persisting with it.

---

### Post by bodhi.zazen on 2006-09-07
1. If you want to post /etc/X11/xorg.conf use gedit, easier to cut from gedit then nano.
```
gksudo gedit /etc/X11/xorg.conf
```

2. It may be easier to use this:

In a terminal type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
restart X -> Ctrl-Alt-Backspace.
This should re-configure X and hopefully fix your resolution problem.

If not -> Monitor? Graphics card? .....

---

### Post by rahelvey on 2006-09-07
It has taken me a while to Linux up to what I like.
Ubuntu has been the best yet if a bit harder to get up to speed than some others.
These forums have allowed me setup all my old pc.fromm 233 to 1.5 ghz.
Hand in. Takes time.

---

### Post by nalmeth on 2006-09-07
xubuntu might be just right for your system, if it seems slow.

To get the extra resolutions, use the:
```
sudo dpkg-reconfigure xserver-xorg
```
command in the terminal.. pick defaults for everything unless you know better, and when you get to resolutions pick the ones you need.

---

### Post by bodhi.zazen on 2006-09-07
> **nalmeth said:**
> xubuntu might be just right for your system, if it seems slow.

To get the extra resolutions, use the:
```
sudo dpkg-reconfigure xserver-xorg
```
command in the terminal.. pick defaults for everything unless you know better, and when you get to resolutions pick the ones you need.

FYI:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` re-configures X (re-writes xorg.conf, saves a back up of original). **-phigh** skips all options but but resolution.

---

### Post by rephil1000 on 2006-09-08
thank you all for the suggestions.  my apologies for the negative attitude.

---

