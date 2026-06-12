---
title: "live cd doesn't install after I press install"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by iatpia5 on 2007-12-10
Hi everyone. This is my first post here. I'm new to linux and honestly not that good with computers in general. I have read an awful lot of stuff on the net and this forum trying to solve my problem but I can't seem to figure it out on my own.
I downloaded the live cd for ubuntu 7.10 from softpedia because it was the fastest download I can get. I mention this because I read a thread about download the official cd and doing a check sum but I wasn't able to download from the links posted for some reason.
My problem is that I boot from the cd, I see the ubuntu logo, the screen comes up which asks me if I want to start or install from live cd, install in safe graphics mode etc, I choose the first option and the screen goes black with a blinking "_" in the top left corner. The computer makes no noise and just stays on this screen until I shut it off with the power button. I tried waiting over an hour but nothing happens. I also tried the other options i.e. safe graphics mode, but I get the same result. 
I also downloaded a kubuntu live cd and the exact same thing happened. I also tried xubuntu 7.04 from a magazine I bought and the same thing happens again. 
Funny thing is that the ubuntu 7.10 desktop i386 live cd ISO installed fine as a virtual machine running on vmware workstation. the thing is that I don't want to run windows at all. I am sick of all it's problems and don't want it messing up my new laptop.

My laptop has intel core 2 duo processor t7250 with 2 gig ram and 200 gig hard disk.

I should also mention that I tried several other ways of dual booting like Wubi and easyBCD I think they're called but none of them worked either. They just messed up my booting process and have complicated things more i.e. when I open the laptop it asks me if I want to boot from windows vista or ubuntu, but I deleted the ubuntu partition after I wasn't able to install through those dual boot programs. Anyway I just choose vista and it boots properly. Even though, all this happened after trying to install the live cd and it continues when I boot from the live cd now (the black screen with the flashing "_" I mean)

Hope that's not as messy and confusing as it seems. Any help would be great. Thanks to everyone in this great community and thanks for reading this.

---

### Post by coolbrook on 2007-12-10
Have you tried the alternate CD?

---

### Post by iatpia5 on 2007-12-10
Wow! That was fast! No I haven't. It seemed a little more complicated but I will download and try it now and get back here. Thanks so much for the speedy suggestion.

---

### Post by rkd on 2007-12-10
I don't have any experience installing Ubuntu yet, so I'm going out on a limb speculating, but from the symptoms you describe, it seems to me that one likely explanation for your problem is that Ubuntu can't handle some important piece of hardware in that computer and gets stuck because of that.

If the hardware causing the problem is the graphics interface hardware, then you might be able to install from the alternate CD, since I believe that uses only text mode.  But you might hit the problem again when you try to start X to get to the graphical desktop.  Still, once you have the basic system installed, you might be able to install the right drivers for your graphics interface hardware and then get everything working, so trying the alternate CD seems like a good idea to me.  Good luck!

---

### Post by iatpia5 on 2007-12-10
Thanks friend! I'm downloading right now. Will tell what happened when I boot it... text mode sounds scary!!!

---

### Post by dptxp on 2007-12-10
To know about installation from alternate CD -

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by iatpia5 on 2007-12-10
Thanks dptxp! That is just what I needed! Great link!

---

### Post by iatpia5 on 2007-12-10
OK so I tried the alternate cd and I got the exact same thing: ubuntu screen came up, chose install in text mode and I got the eternal black screen with the blinking cursor on the top left corner. The new thing is that after I shut off the computer and rebooted I got this message :"BOOTMGR is missing Press Ctrl+Alt+Delete to restart" . When I do I get the same exact message. So I cn't even get to vista now! I will have to boot from cd and restore it I guess. Any other suggestions are welcome still but I think I might give up soon! Thanks for all the help everyone!


Update: this is hilarious: I tried the fix boot problem from the boot cd of vista and it gave me the the classic windows message:" Windows can not fix the problem. Sending more information to microsoft may help find a solution. Would you like to send this information to microsoft?" (translated from greek)
I don't even have an operating system up, never mind an internet connection and they give me this! Reminds me why I want to get rid of windows in the first place.

---

### Post by Partyboi2 on 2007-12-10
you could try and add "noapic" to your boot option to see if that works
I have never used the alternate cd so not sure how to do it with that one.
but to do it with the normal cd when you get to the menu.
Press F6
then you will see a command line with some options at the end of it add "noapic" (with out quotes)
then press enter
then b to boot

---

### Post by culae on 2007-12-11
hi! i'm VERY new too. and i get a similar problem. after i hit install it pop-up the ybuntu logo with the sliding bar and the the black screes with:
[I][B]"BusyBox v1.1.3...
/bin/sh: can't acces tty; job control turned off
(initramfs)_[/B][/I]"
waiting for a command. what command should i do?
thank you
i use a laptop
asus l300
256mb of ram
p4 1.6ghz

culae

---

### Post by dptxp on 2007-12-12
> **culae said:**
> hi! i'm VERY new too. and i get a similar problem. after i hit install it pop-up the ybuntu logo with the sliding bar and the the black screes with:
[I][B]"BusyBox v1.1.3...
/bin/sh: can't acces tty; job control turned off
(initramfs)_[/B][/I]"
waiting for a command. what command should i do?
thank you
i use a laptop
asus l300
256mb of ram
p4 1.6ghz

culae

I do not know if your problem is related to this, but 256 MB RAM is low for Live CD.
Live CD shall not run, if it does it shall not install.
Make a SWAP partition of 1 GB first with GPARTED at end of the drive. This can not
be altered by Live CD later. Else use alternate CD or XUBUNTU.

---

