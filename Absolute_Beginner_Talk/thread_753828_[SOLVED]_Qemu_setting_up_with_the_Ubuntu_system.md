---
title: "[SOLVED] Qemu setting up with the Ubuntu system"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Damien Kane on 2008-04-13
Hi there!

So, I've been using the Ubuntu 7.10 system for a bit and will be upgrading to the new one in a few weeks. I currently dual-boot Vista and Ubuntu.

I prefer Ubuntu, but my wife likes Windows, so I came across a program called Qemu which I believe installs XP 'into' Ubuntu.

So, I gave it a go and it was quite easy to setup and use. After a few weeks (!!) I even got the mouse working. So, I currently have a working copy of my old XP licence in the Ubuntu system. GREAT!

The problem is, is that none of my hard drives appear. After a bit of searching, I heard of and installed a program called SAMBA. Unfortunately, I still can't figure out how to 'share' my hard drives, or folders.

There are two things I'm trying to do but for the life of me, I can't figure it out:

1. I have a quad core processor with 3gb of memory, but XP in Qemu is still slow. How can I speed it up? When I select more than 1 processor, it doesn't boot, and

2. How can I set up a folder called SHARED which Ubuntu/XP can use (not an image, but an actual folder, because I have a utility in Vista to read the Linux drive).

I'm helplessly lost, and I'm hoping if I can set all this up, I can convince my wife to use Linux all the time and gradually get her off the Windows drug. I've tried lots of tips from other posts, and have probably stuffed up all my configurations! :lolflag:

It's all new and I'm confused. Any ideas?

---

### Post by TenPlus1 on 2008-04-13
Dont get me wrong, Qemu is a fine program, but I prefer VirtualBox for running Windows along-sdie my Ubuntu install, check this out:

[http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml](http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml)

Here is their website to download the LATEST .deb package for install:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

and of course a little fix after you install it, goto Terminal and type:

sudo usermod -G vboxusers -a <username>

...obviously replace <username> with your own, then log-out and back in for Virtualbox to work...

---

### Post by spydon on 2008-04-13
Yeah virtualbox feels much nicer for windows, qemu feels better for like OpenMoko and lighter stuff.

---

### Post by bumanie on 2008-04-13
I too suggest virtualbox. Qemu is a good program for certain uses, but for the usage you plan, virtualbox will certainly perform better. Here is a good 'How to' for installing and setting up virtualbox.
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by Damien Kane on 2008-04-13
Hey, thanks for all your help - you all seem to be unanimous with Virtualbox. I'm just downloading it now and will haveto get my original XP cd to try it - I'll post back in a few days with my thoughts on it. Ubuntu's great, isn't it? So much simpler than Windows. Could be much more popular in the future. I'm amazed at what it can do.

All the best.:)

---

### Post by Damien Kane on 2008-04-14
Hey that's so cool! Would it be wrong if I asked a few more questions if you have the time? I can't believe how much faster than Qemu it is. Does anybody know the answers to these questions?

1. Do I need a Windows Firewall?
2. Do I need a Windows antivirus?
3. When I use anything to do with Ubuntu, the Windows bar disappears. How can it remain permanent (I thought by removing the bottom panel in Ubuntu, it'd be there permanently. Now, even the XP bar doesn't show - duh!)
4. How on earth do I share files? I thought I did it right.

I think I'll have it set up so Windows XP for the wife is in one workspace and at any time, I can switch to Ubuntu in the other and fiddle.

Oh, one more thing: the instructions at [http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml](http://news.softpedia.com/news/Unite-Windows-and-Linux-With-a-Single-Mouse-Click-78535.shtml) were great, however, there's one issue with it. Step 3, Configure the virtual Window, says to click Devices -> Install Guest Addons. This didn't work for me, but I noticed that there was a 5mb drive in the Windows installation which had this as an installer package. Dunno if it helps.

Sorry for the questions, and I appreciate all your help. The speed of XP is far better than Qemu, and if I can get away from Vista, then I'll be happy. Can't believe I bought the darn program.

Many thanks.:popcorn:

---

### Post by Damien Kane on 2008-04-15
OK: found the answers:

1. No.
2. No.
3. Move the bar
4. There's an option in Virtualbox which wouldn't work, then I figured I hadn't shared the folder in Windows Vista. After I did that and went back into Ubuntu:
- Start Virtualbox
- Click the machine you want to use
- Click 'Settings'
- Click 'Shared folders'
- Browse to the folder you want shared and what access you want.

This Virtualdrive is way cool! Will mark this post as solved. Thanks.

---

