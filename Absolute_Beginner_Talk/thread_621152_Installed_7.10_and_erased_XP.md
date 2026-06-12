---
title: "Installed 7.10 and erased XP"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-23
I have tried searching the forums but if my question is best answered in another thread, I apologize for wasting the time. I will happily follow any offered links to relevant threads.

No big deal, I had burned all of my photos and whatever to a DVD before installing so I am not too concerned about having lost the XP install, but I do have a question about going forward.

My lappy is a year and a half old Compaq Presario V2000, nothing special, but I lost the Windows Disks that came with the computer a long time ago. My understanding is that I can re-install XP and then enter the codes from the sticker and be back in business if I want to dual-boot. The thing is, I think I would rather run XP as a virtual machine so that I can open up an instance of Windows in a, um, window and run any needed windows aps from the, uh, window.

I know that I do not really know what I am talking about. I have read enough blurbs about something called VMware to think that might be what I want. 

I have done some searches on this topic and from what I can tell it matters that my Windows license was OEM, not a site or volume license. I would also like to know how much achieving what I want is going to cost me. Would I need to buy a new copy of Windows? Does the virtualization software cost money? If I have to spend more than like $20 I won't bother.

---

### Post by spiderbatdad on 2007-11-23
VMware is available through synaptic package manager i believe. I had it up and running on Dapper awhile back and it worked great. It took a little fiddle around to get everything going, but it did work and it the cost was only time.

---

### Post by jken146 on 2007-11-23
I dual boot myself, so I don't know anything about VMWare.  But you can try these links:

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

---

### Post by banewman on 2007-11-23
There are always torrents for windows if cost is a concern but there is also a program called "wine" for running window applications. :)

---

### Post by spiderbatdad on 2007-11-23
found VMware player in Add/Remove

---

### Post by drabzz on 2007-11-23
Have you really lost your XP installation or do you get a GRUB error when you try to launch XP?

You can fix the GRUB error usually by rewriting the Master Boot Record (MBR). You will need a rescue disk or a bootable floppy or CD with FDISK on it. Enter FDISK /MBR at the command prompt and you should then be able to boot to XP again.

If you Google 'rescue CD', you can select from a wide choice of free CD images to download.

---

### Post by subs on 2007-11-23
vmware allows users to run multiple instances of x86-compatible operating systems


u can try this...
> [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

windows xp may be within ur budget... however it is very very unlikely that you will get a licensed version of vista for that much

---

### Post by bluepowder7 on 2007-11-23
i dual-boot as well.  actually, i'm triple-booting by now on the desktop (win2k, winxp, and ubuntu).  i did have a not-fully-legal version of xp but i decided that since all my other software is free (freeware / shareware, nothing illegal), i could cough up the $100 or so to get a proper legal version of XP at least once in my life.

that aside, since you DID have authentic keys at one point in time, you could try to borrow a winxp install cd from a friend or neighbour, and use your key to activate it.  i'm not sure if microsoft is gonna balk at that and deny it, but it's worth a shot.

i've read posts that running windows from within linux is gonna be a doubly-high load on your resources (ram mostly).  depending on how much power your laptop currently has, it might end up being a royal pain in the **** to get things to run smoothly and quickly.

---

### Post by NightCrawler03X on 2007-11-23
It doesn't matter where you get your XP disc, so long as you hvae the correct version for your product key.

But like other people have said, wine.

---

### Post by boriquajake on 2007-11-23
> **drabzz said:**
> Have you really lost your XP installation or do you get a GRUB error when you try to launch XP?

You can fix the GRUB error usually by rewriting the Master Boot Record (MBR). You will need a rescue disk or a bootable floppy or CD with FDISK on it. Enter FDISK /MBR at the command prompt and you should then be able to boot to XP again.

If you Google 'rescue CD', you can select from a wide choice of free CD images to download.

I am pretty sure that when I installed 7.10 I overwrote all of the HDD and lost anything Windows related. Is there a way for me to be sure?

If I download a rescue CD and activate it using the keys on my machine will it be legitimate or would Redmond consider that stealing? I am just curious.

---

### Post by boriquajake on 2007-11-23
By the way, can I just say how cool this all is? I mean seriously, when you combine the Ubuntu distro's philosophy of trying to get things to just work with the incredible support available on forums like this it is amazing. Once I have spent more time playing with this and have read a few books on the fundamentals of linux I am going to convert my small business all the way over to Ubuntu.

---

### Post by boriquajake on 2007-11-23
I followed the link that was posted about using VMware and it is perfect. Thank you very much. I only have one or two small questions for this thread.  Actually, now that I think about it my only real remaining question is about wine. Could someonw please post a link to the best thread explaining the basics of wine and how to use it?

Thank you all in advance.

---

### Post by bluepowder7 on 2007-11-23
> **boriquajake said:**
> ....my only real remaining question is about wine. Could someonw please post a link to the best thread explaining the basics of wine and how to use it?

Thank you all in advance.


10 open bottle
20 drink contents
30 open another bottle
40 goto 20

---

### Post by ptn107 on 2007-11-23
I have a v2000z (which is essentially the same thing as yours).  If you wish I can post a link so you can re-download the restore and/or driver DVD s as ISO s.  I think its OK considering you own one and just misplaced them (and getting replacements is a hassle trust me).  It would be wise to have them lying around in case something similar happens again.

[email]ptn107@gmail.com[/email]

---

### Post by boriquajake on 2007-11-23
> **ptn107 said:**
> I have a v2000z (which is essentially the same thing as yours).  If you wish I can post a link so you can re-download the restore and/or driver DVD s as ISO s.  I think its OK considering you own one and just misplaced them (and getting replacements is a hassle trust me).  It would be wise to have them lying around in case something similar happens again.

[email]ptn107@gmail.com[/email]


I guess the only question I have left is if once I have a copy of windows again will the key code from my computer work in VMware or because it is (to the software at least) a "new" machine will the whole activation thing not work and would that mean that my only option is to dual boot?

---

### Post by Paulmd on 2007-11-23
> **boriquajake said:**
> I have tried searching the forums but if my question is best answered in another thread, I apologize for wasting the time. I will happily follow any offered links to relevant threads.

No big deal, I had burned all of my photos and whatever to a DVD before installing so I am not too concerned about having lost the XP install, but I do have a question about going forward.

My lappy is a year and a half old Compaq Presario V2000, nothing special, but I lost the Windows Disks that came with the computer a long time ago. My understanding is that I can re-install XP and then enter the codes from the sticker and be back in business if I want to dual-boot. The thing is, I think I would rather run XP as a virtual machine so that I can open up an instance of Windows in a, um, window and run any needed windows aps from the, uh, window.


I know that I do not really know what I am talking about. I have read enough blurbs about something called VMware to think that might be what I want. 

I have done some searches on this topic and from what I can tell it matters that my Windows license was OEM, not a site or volume license. I would also like to know how much achieving what I want is going to cost me. Would I need to buy a new copy of Windows? Does the virtualization software cost money? If I have to spend more than like $20 I won't bother.

Games requiring hardware accelleration are not compatible with VMs. Otherwise you'll be fine.

Microsoft requires 1 licence for each instance of the operating system. Including VMs. As long as you're not ALSO dual booting, your existing licence is fine.

Some virtualizers... the better ones, require money. There are (at least) 2 that are free and open source. and really pretty OK.  VirtualBox which I've personally used, is pretty decent. And VMware, which I haven't, bit others have said is OK..

---

### Post by boriquajake on 2007-11-23
> **Paulmd said:**
> Games requiring hardware accelleration are not compatible with VMs. Otherwise you'll be fine.

Microsoft requires 1 licence for each instance of the operating system. Including VMs. As long as you're not ALSO dual booting, your existing licence is fine.

Some virtualizers... the better ones, require money. There are (at least) 2 that are free and open source. and really pretty OK.  VirtualBox which I've personally used, is pretty decent. And VMware, which I haven't, bit others have said is OK..


Man, I feel ignorant, but then again, this is the "absolute beginners" forum, eh. Anyway, how will Windows know that my virtual instance of Windows is the only one that is using the key? Won't I fail the activation process because up until a month or so ago my key was being used on this laptop?

---

### Post by Paulmd on 2007-11-24
> **boriquajake said:**
> Man, I feel ignorant, but then again, this is the "absolute beginners" forum, eh. Anyway, how will Windows know that my virtual instance of Windows is the only one that is using the key? Won't I fail the activation process because up until a month or so ago my key was being used on this laptop?


Up to a certian (undisclosed/variable and controlled by Microsoft) number of re-activations you won't  trigger alarm bells. Even on different hardware. Sometimes activation does indeed fail, and you have to call Microsoft and explain to some Indian that you're now running your XP on a virtual machine. At which point they will give you the horrendously long string of numbers to manually activate. It takes about 5 minutes, and it's WAY more effective than some hacker BS that you download and get a virus from. 

Just be polite and truthful (the Indians barely qualify as Microsoft employees, and just want to make their night go better... yes this is the graveyard shift you get to talk to), and windows will be activated, and legit.

---

### Post by sstusick on 2007-11-24
If you must use Virtualization, try Virtual Box, it's free.  [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by drabzz on 2007-11-27
> **boriquajake said:**
> I am pretty sure that when I installed 7.10 I overwrote all of the HDD and lost anything Windows related. Is there a way for me to be sure?

If I download a rescue CD and activate it using the keys on my machine will it be legitimate or would Redmond consider that stealing? I am just curious.


If you overwrote all of the HDD then it is beyond recovery. If you get a GRUB error at startup, you may be in with a chance; GRUB by default only writes to your MBR on Windows dual boot setups.

Ermm... most Rescue CDs are in the public domain, so I'm sure you will not be yomping all over anyone's rights! Check the EULA to be sure.

---

