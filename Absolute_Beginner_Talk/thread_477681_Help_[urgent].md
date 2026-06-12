---
title: "Help? [urgent]"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Lokito on 2007-06-18
Alright, here's the story.  Was downloading Wubi, sibling hit something they shouldn't have.  Essentially killed my PC.  I don't exactly know what the problem is, because the computer was whisked away before I could really get a chance to look at it.  All I know is that it's something to do with a RAID error.  The grunts who tried to extract my data said they used something similar to a boot CD to try to get the information (don't you love it how these guys always think what they do is over your head and can't just tell you what they're doing), but they could only get 47%.  After that it would stop or freeze (they weren't exactly specific), so they couldn't get anything off my PC (they're program needs to extract 100% in order to write it to a disk, apparently).  

Now a DELL guy is scheduled to show up and wipe the computer, putting it back to factory settings.  I only have a day or so to figure something out before I'll lose everything I had on there.  I'm no expert on linux or boot disks, so can someone help me out and point me to a boot disk that will be able to restore my data?  I'm running windows XP.

So far I've been referred to [http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm")

---

### Post by aktiwers on 2007-06-18
Sorry If I completely misunderstand your question.. but is the problem that you cant boot?

Have you tried booting with a LiveCD and then save your files?

---

### Post by Gimpy_Rob on 2007-06-18
Download knoppix.

Its a version of linux that will boot straight off the CD drive, and should allow you to get at your files.  You'll need somewhere to put them, like a backup external drive or something.  Don't know what these guys were trying to do, but probably something that just did a full image of the drive.  You know your files, I suggest going into your home directory and grabbing everything you want.

---

### Post by Lokito on 2007-06-18
> **aktiwers said:**
> Sorry If I completely misunderstand your question.. but is the problem that you cant boot?

Have you tried booting with a LiveCD and then save your files?This is "Absolute Beginner Talk" after all, so I hope I won't be killed for my ignorance.  Using a LiveCD, how do I retrieve the files I want?  Also, I'm not at liberty to download Linux onto said computer, so is there a way to restore my windows to the way it was (functioning) before the Wubi install?

---

### Post by Lokito on 2007-06-18
> **Gimpy_Rob said:**
> Download knoppix.

Its a version of linux that will boot straight off the CD drive, and should allow you to get at your files.  You'll need somewhere to put them,** like a backup external drive or something**.  Don't know what these guys were trying to do, but probably something that just did a full image of the drive.  You know your files, I suggest going into your home directory and grabbing everything you want.Which I unfortunately don't have.  

I don't think they were - they said something rather about not having the tools for it.

---

### Post by aktiwers on 2007-06-18
Just download Knoppix, burn it as Image on a disc and boot up your computer from it.

Then it should show your harddrives on the desktop and you can copy/burn or however you like the files to a save disc/harddrive.

---

### Post by mlentink on 2007-06-18
> **Lokito said:**
> Also, I'm not at liberty to download Linux onto said computer, so is there a way to restore my windows to the way it was (functioning) before the Wubi install?
You were not allowed to install Linux on that computer? But that is precisely what you were trying to do. Wubi ia a Ubuntu installer to make it unnecessary to set up dual-boot (never mind if you do not know what that is).
E LiveCD lets you boot the CD, NOT the harddisk of the computer, and therefore will not change anything on it.

You can download the image of such a cd form the ubuntu website. Burn it using the 'burn an image' option of your cd-burning software, stick it in the cd-drive and reboot.  You might have to change BIOS setting for your computer to be able to boot (start up) your computer from cd

---

### Post by Lokito on 2007-06-18
> **mlentink said:**
> You were not allowed to install Linux on that computer? But that is precisely what you were trying to do. Wubi ia a Ubuntu installer to make it unnecessary to set up dual-boot (never mind if you do not know what that is).
E LiveCD lets you boot the CD, NOT the harddisk of the computer, and therefore will not change anything on it.

You can download the image of such a cd form the ubuntu website. Burn it using the 'burn an image' option of your cd-burning software, stick it in the cd-drive and reboot.  You might have to change BIOS setting for your computer to be able to boot (start up) your computer from cdI *was* then.  I know what Wubi is (in fact, I only installed it because it allowed me to use ubuntu without partitioning and all that jazz).  

I didn't see that anywhere on the Ubuntu site.  Mind providing a link?

---

### Post by Lokito on 2007-06-18
Can I use a Windows setup boot disk to do the same thing?

---

### Post by aktiwers on 2007-06-18
Windows doesn't have LiveCD's.

---

### Post by mlentink on 2007-06-18
> **Lokito said:**
> I didn't see that anywhere on the Ubuntu site.  Mind providing a link?

[Here it is]("http://www.ubuntu.com/getubuntu/download") Choose a desktop version, latest one is fine. Then select your computer type (Most likely a 'standard personal computer'), select a location near to you and hit the start download button. Please remember it's a 650Meg download!

As soon as you've downloaded is, strat up your cd-burning software and brun the download to a cd, using the 'burn as an image' option. This is very important, your disk will not work if you burn it other that as an image.

Then boot this cd, and after a while you&#314;l be running Ubuntu albeit off of the cd. You can look at your harddisk and try to salvage your files.

The Knoppix cd, as mentioned above, works similarly.

You can report back as soon as you have it running (I may be in bed by then though, but there are others who will try to help)

---

### Post by mlentink on 2007-06-18
> **aktiwers said:**
> Windows doesn't have LiveCD's.

Unfortunately, Windows is a "user-friendly" operating system, so it is felt that something as geeky as a Live-CD is not needed. PLease be aware that this is a feature, not a disadvantage.

;-)

---

### Post by Lokito on 2007-06-18
> **aktiwers said:**
> Windows doesn't have LiveCD's.I just found my original windows software crap, which includes a setup CD that will boot the computer regardless of how badly you screwed it up.  Will that just automatically wipe any preexisting data?

---

### Post by aktiwers on 2007-06-18
Yes I think it will.. or at least the data on your Windows Partition.

---

### Post by Lokito on 2007-06-18
> **mlentink said:**
> [Here it is]("http://www.ubuntu.com/getubuntu/download") Choose a desktop version, latest one is fine. Then select your computer type (Most likely a 'standard personal computer'), select a location near to you and hit the start download button. Please remember it's a 650Meg download!

As soon as you've downloaded is, strat up your cd-burning software and brun the download to a cd, using the 'burn as an image' option. This is very important, your disk will not work if you burn it other that as an image.

Then boot this cd, and after a while you&#314;l be running Ubuntu albeit off of the cd. You can look at your harddisk and try to salvage your files.

The Knoppix cd, as mentioned above, works similarly.

You can report back as soon as you have tit running (I may be in bed by then though, but there are tohers who will try to help)

The computer I'm using right now is unfamiliar to me, so I'll have to look for the burning options. Once I'm running the cd, do I just insert a blank CD and pull the stuff I want off (it doesn't seem like it's that simple)?

EDIT: And yes, once I have tit running, I'll post again. ;)

---

### Post by aktiwers on 2007-06-18
Have a look here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Or more precise 
[http://www.psychocats.net/ubuntu/iso#burning](http://www.psychocats.net/ubuntu/iso#burning)

---

### Post by mlentink on 2007-06-18
> **Lokito said:**
> Once I'm running the cd, do I just insert a blank CD and pull the stuff I want off (it doesn't seem like it's that simple)?

Ehh. Does your computer have wired access to a network? Or could you borrow a USB-drive with enough capacity? That would be easiest. I don't really remember if the Live-CD has cd-burning software installed on it, I'd have to find my own copy. Because you would obviously need burning software to burn your files....

---

### Post by Lokito on 2007-06-18
I don't have access to usb devices or external hard drives, only CDs.  I've been looking at the Knoppix FAQ, but it doesn't say anything about whether it includes CD burning capabilities.  Do any of you know of a LiveCD that you know has this?

---

### Post by Lokito on 2007-06-18
I've been looking around the computer I'm using for CD burning software, and I found it.  It uses Sonic DigitalMedia.  What I don't know is how to actually use it.  It has a "burn image to disk" option - it asks you to browse for an image to burn.  I already need the .iso file on my computer in order to burn it.

---

### Post by phr0ze on 2007-06-18
If windows is screwed up and you have an install CD, You can install windows back on that drive and it will not affect your documents and other data. You just have to be absolutely sure you do not choose to format the drive. I have done this dozens of times without problems. (Windows installer will say it will wipe out your data but this is not true, as long as you don't choose to format or partition).

Another alternative, if you can still get somewhere in the windows boot process, is to push F8 after the bios has loaded and windows is starting to load. All I do is press f8 about once every second after the BIOS done. Then you get a menu which should let you choose 'Last Known good configuration'.

---

