---
title: "Installing Drapper"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-26
Hi everybody

When I installed Drapper the first time, I erased xp (I wish I couldn't, but even if I paid any attention and tried it with the help of a guide ...); now I'd like to install Drapper on a PC which runs on windows'98 and I wish I could keep it.

So please, help me in the following step:

Disk space to partition
-Resize IDE1 master, partition # (hda1) and use freed space
-Erase entire disk: IDE1 master (hda) 20.5 GB WD205B1
-Erase entire disk and use LVM IDE1 master (hda) 20.5 GB WD205B1
-Manually edit partition table

If I'm right I think that hda is the hard disk; I would keep 10 GB for windows and 10 for Drapper (128 RAM)

Which step am I supposed to take?

Thanks for any help

---

### Post by catlett on 2006-11-26
You should install XP first and then install Dapper. If you install Dapper and then install Dapper, you will loose the linux bootloader and you will have to do soem "intermediate" level stuff to get the bootloader back.
What to do is install XP. Then reboot into the Dapper install disk and choose 
> -Resize IDE1 master, partition # (hda1) and use freed space
That option allows you to shrink the XP portion of the hard drive and then the installer will install Dapper in the free space.

---

### Post by drphilngood on 2006-11-26
> **catlett said:**
> You should install XP first and then install Dapper. If you install Dapper and then install **Windows 98/XP**, you will loose the linux bootloader and you will have to do soem "intermediate" level stuff to get the bootloader back...

T,FTFY;)
I was just starting to post something similar.

---

### Post by helphope on 2006-11-26
Thanks for answering, but maybe I didn't explain clearly what I want to do.
I've got 2 computers; one xp and one with windows '98. The one with xp is dead because when I installed Drapper I erased everything (I wish I couldn't, but I'm happy all the same with drapper). Now I want to install drapper on the pc with windows '98 but I want to keep windows '98.

So > 
Quote:
-Resize IDE1 master, partition # (hda1) and use freed space
That option allows you to shrink the XP portion of the hard drive and then the installer will install Dapper in the free space is this what I have to do? How much space will I have have for linux?

Thanks

---

### Post by xpod on 2006-11-26
> If I'm right I think that hda is the hard disk; I would keep 10 GB for windows and 10 for Drapper (128 RAM)

You may struggle if its "ubuntu" dapper your trying to install with that little amount of memory.

Mabey Xubuntu would be a better option.If your not already trying it that is.

---

### Post by drphilngood on 2006-11-26
> **helphope said:**
> Thanks for answering, but maybe I didn't explain clearly what I want to do.
I've got 2 computers; one xp and one with windows '98. The one with xp is dead because when I installed Drapper I erased everything (I wish I couldn't, but I'm happy all the same with drapper). Now I want to install drapper on the pc with windows '98 but I want to keep windows '98.

So  is this what I have to do? How much space will I have have for linux?

Thanks

Resize the partition with **´98** on it(you can decide how much space to allocate) and install Dapper on the freed space.

---

### Post by aysiu on 2006-11-26
With 128 MB of RAM, I'd use the Alternate CD instead of the Desktop CD... or is that what you *are* using already?

And I agree with xpod--you're better off with Xubuntu (or even IceWM or Fluxbox).

But, yes, you should resize and use the free space.

---

### Post by helphope on 2006-11-26
> **drphilngood said:**
> Resize the partition with **´98** on it(you can decide how much space to allocate) and install Dapper on the freed space.

What do you mean? The hard disk has one partition; do I have to give it one more, so that I have c:\ and D:\?

Thanks

---

### Post by aysiu on 2006-11-26
I think you should take a look at this guide:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by drphilngood on 2006-11-26
> **helphope said:**
> What do you mean? The hard disk has one partition; do I have to give it one more, so that I have c:\ and D:\?

Thanks
Follow the instructions of aysiu.
Good luck!

---

### Post by catlett on 2006-11-26
> **helphope said:**
> Thanks for answering, but maybe I didn't explain clearly what I want to do.
I've got 2 computers; one xp and one with windows '98. The one with xp is dead because when I installed Drapper I erased everything (I wish I couldn't, but I'm happy all the same with drapper). Now I want to install drapper on the pc with windows '98 but I want to keep windows '98.

So  is this what I have to do? How much space will I have have for linux?

Thanks

Choose > -Resize IDE1 master, partition # (hda1) and use freed space I would give ubuntu 10gb but you could get away with 5gb. Technically you only need a little less than 3 gb to run it but if you want to add applications and store lots of files etc. you will need more space. Go with 10gb if you can afford to give up the space.
Ubuntu can run on 128mb but 256mb is preferred. If you install and find ubuntu to be sluggish, you can switch desktop managers from gnome to xfce. XFCE is a desktop that uses less memory than gnome amd works very well with 128mb of ram.  When Dapper uses xfce as a desktop, the distro is then called xubuntu. So if you want to install xfce/xubuntu after you install ubuntu, just enter this command 
```
sudo aptitude install xubuntu-desktop
``` You can keep gnome and xfce (or ubuntu/xubuntu) and choose between them at the login window. If you like xubuntu and dislike ubuntu, you can remove ubuntu after you have installed xubuntu-desktop with 
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by helphope on 2006-11-26
:D :D :D 

Thanks a lot and my compliments for you clear and exhaustive Explanation

---

