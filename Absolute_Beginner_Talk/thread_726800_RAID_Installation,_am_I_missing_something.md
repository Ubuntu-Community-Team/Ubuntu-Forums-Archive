---
title: "RAID Installation, am I missing something?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by TheBurningCrown on 2008-03-17
Hi, I'm new to Ubuntu (and for that matter Linux) so I hope someone can help me out with this (most likely) obvious simple fix...

I have a RAID array (via the BIOS) and an external HD connected via an e-sata cable to the motherboard.

After installing Linux, the system boots directly to windows on the RAID array, seemingly not even seeing the Linux setup.....

In addition, if I boot Ubuntu with the live disc, it doesn't recognize the RAID array, but rather two separate drives.

Any ideas?

---

### Post by Rocket2DMn on 2008-03-17
RAID installations require the alternate install cd.  I'm no RAID expert, but here are some links to help you out:
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/Installation/RAID1+LVM](https://help.ubuntu.com/community/Installation/RAID1+LVM)
and maybe even [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> RAID installations require the alternate install cd.  I'm no RAID expert, but here are some links to help you out:
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/Installation/RAID1+LVM](https://help.ubuntu.com/community/Installation/RAID1+LVM)
and maybe even [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)Thanks, but most of those links seem to refer to installing Ubuntu onto a RAID array.  I don't think any of them talk about installing it on a drive with a RAID setup in the system not being used for the installation.

---

### Post by Rocket2DMn on 2008-03-17
Ah I guess I misunderstood.  Well I spent the last 10+ minutes looking around for how to properly mount a RAID partition, and it seems to me that the correct way is the same way you mount any other physical drive, the device is just IDed a little differently.
Can you post the output of
```
sudo fdisk -l
cat /etc/fstab
```


Or is it that you can't even boot into Ubuntu?  Is Ubuntu on the external disk?  In this case you would have to change the boot sequence in your BIOS to look for USB Devices above your internal HD.

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> Ah I guess I misunderstood.  Well I spent the last 10+ minutes looking around for how to properly mount a RAID partition, and it seems to me that the correct way is the same way you mount any other physical drive, the device is just IDed a little differently.
Can you post the output of
```
sudo fdisk -l
cat /etc/fstab
```


Or is it that you can't even boot into Ubuntu?  Is Ubuntu on the external disk?  In this case you would have to change the boot sequence in your BIOS to look for USB Devices above your internal HD.
I can't even boot into Ubuntu (unless I use the live CD), as no boot loader appears on startup and the computer continues to boot into Windows.

Yes, Ubuntu is on the external disc. But the external disc is attached via SATA, not USB.

---

### Post by Rocket2DMn on 2008-03-17
Is it possible to move this SATA drive up in the BIOS boot order above everything else?

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> Is it possible to move this SATA drive up in the BIOS boot order above everything else?I think so, let me try that.

UPDATE: Yes, I found the setting.  Once I changed the priority of the drive, upon booting i got an "NTLDR is missing" message.

---

### Post by Rocket2DMn on 2008-03-17
Hrmm... [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)
Maybe it's not set as bootable?  Perhaps reinstalling GRUB can help with that: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Why don't you look more into that and I'll check up on you in the morning.  Post any more details you can and I shall think it over in my sleep.  Good luck.

---

### Post by TheBurningCrown on 2008-03-17
I took a look at both those links, but I'm not sure if I want to continue overwriting the Windows bootloader if the RAID array isn't detected as an array....

Update: I figured what the hell and took the plunge. I followed the steps of the first section of the second link.   Now,GRUB loads on startup (YAY!) but, trying to load Ubuntu using any of the options yields an error message, and there is no option to load windows.....

---

### Post by Rocket2DMn on 2008-03-17
What error does GRUB give you?  We can add the windows option.
Although I've never tried it myself, I've heard really good things about the Super Grub Disk - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) - you might consider giving that a try.

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> What error does GRUB give you?  We can add the windows option.
Although I've never tried it myself, I've heard really good things about the Super Grub Disk - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) - you might consider giving that a try.It gives me error 17 and says that it "cannot mount the selected partition"

---

### Post by Rocket2DMn on 2008-03-17
Have you tried the Super Grub Disk to repair GRUB?
Error 17 means that GRUB does not recognize the filesystem that it is pointing to.
Here is some reading that might help you out:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
There are tons of threads on these forums about GRUB Error #17, so you should run a search.  I could post you some links, but to be honest, I'm not a GRUB pro and it is best that you look for yourself since you know your setup and exactly what happened to get you to where you are now.  I don't want to just show you a narrow list of posts.  
If you find one that you think seems to be the best approach, but have some questions about it - do NOT post the questions on that thread (since those threads are dead).  Link me to the thread and ask your question here and I will be happy to guide you along the chosen path to fixing your GRUB.
Happy hunting.

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> Have you tried the Super Grub Disk to repair GRUB?
Error 17 means that GRUB does not recognize the filesystem that it is pointing to.
Here is some reading that might help you out:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
There are tons of threads on these forums about GRUB Error #17, so you should run a search.  I could post you some links, but to be honest, I'm not a GRUB pro and it is best that you look for yourself since you know your setup and exactly what happened to get you to where you are now.  I don't want to just show you a narrow list of posts.  
If you find one that you think seems to be the best approach, but have some questions about it - do NOT post the questions on that thread (since those threads are dead).  Link me to the thread and ask your question here and I will be happy to guide you along the chosen path to fixing your GRUB.
Happy hunting.Hm, the article you linked to said a bit about GRUB being "confused" because of the hard drive priority level.  Let me reinstall and tweak it a bit...

---

### Post by TheBurningCrown on 2008-03-17
[IMG]http://img444.imageshack.us/img444/985/tempnr9.jpg[/IMG]

.....


I am getting really sick of this *seemingly* nonsensical "stuff"...

I reinstalled twice and messed with the boot order.  With the RAID setup in first position the system loaded windows, and with the other hard drive in first position the system loaded grub, but still had error 17.

Trying to edit things in the Ubuntu terminal is insane.  The only hard drive I can setup grub on is the external one, which is listed as hard drive "1" (I assume it would be better to be on "0").  If I try to setup GRUB on any other hard drive and it results in a "cannot mount" error.

I'm seriously just about ready to give up on Linux..... as ironic as it sounds, Windows seems much easier.

---

### Post by Rocket2DMn on 2008-03-17
Weird, you're right, I got that when I tried your exact search query, too, for Search All Open Forums.  I never liked the UF search function anyway, try using google with a query like
> site:ubuntuforums.org grub error 17

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> Weird, you're right, I got that when I tried your exact search query, too, for Search All Open Forums.  I never liked the UF search function anyway, try using google with a query like
Upon doing some more searching, it appears that the problem has to do with the RAID as setup by the BIOS...

I guess I'm just not destined for Linux :(

---

### Post by Rocket2DMn on 2008-03-17
:( Sorry I wasn't able to help you get it working.  Linux works fine when you install to the RAID.  It should also be able to mount it just fine.  Perhaps the source of the problem is that you're using an external SATA drive.
Don't get too down about it, if you figure it out you can write a great HowTo on it - I bet there are users who would love to read it.
Best of luck.

---

### Post by TheBurningCrown on 2008-03-17
> **Rocket2DMn said:**
> :( Sorry I wasn't able to help you get it working.  Linux works fine when you install to the RAID.  It should also be able to mount it just fine.  Perhaps the source of the problem is that you're using an external SATA drive.
Don't get too down about it, if you figure it out you can write a great HowTo on it - I bet there are users who would love to read it.
Best of luck.Thanks for all the help.

If I ever get a chance to get Linux working on this machine I'll be sure to let you guys know about it :)

---

