---
title: "Cannot Dual-Boot Ubuntu in Mac System"
date: 2010-07-06
forum: Apple Hardware Users
---

### Post by Jackson Tan on 2010-07-06
Hi all,

I've been using Ubuntu on my PCs and laptops for quite a while. Recently, I've been allocated a Mac for use in my lab. It is a PowerPC G5 running on Mac OS X 10.4.11. I've installed Ubuntu on one of the two hard disks available, the other one being the disk which Mac is installed in.

There was no problems with the installation, but I cannot get Ubuntu to boot. Basically, when I restart the system, it boots into Mac straight away. There is no boot loader or GRUB.

I've tried holding down the options key when the system starts, but for some unknown reasons, the monitor cannot find a signal, so I cannot see what is going on. The monitor can only pick up a signal after Mac starts to boot (or, when I was installing Ubuntu, after the virtual Ubuntu has loaded).

Am I suppose to expect GRUB or some other boot loader? Any help on how to fix my problem?

Cheers,
Jackson

---

### Post by linuxopjemac on 2010-07-07
You need to have a good look at yaboot.
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by Jackson Tan on 2010-07-07
Hi linuxopjemac,

Thanks for your reply. I looked up on Yaboot, and it appears to me that I need to install Yaboot before installing Mac OS, because of the need to change the partition of the disk.

This may be a problem for me because I'm inheriting a system with Mac OS already installed in it. I do not have the installation disk for the OS. I'm also hesitant to wipe out Mac OS because I may need some programs that are already installed.

Nonetheless, if I were to remove Mac OS, do I still need to install Yaboot? Or will Ubuntu automatically boot since it is the only OS on the system?

Thanks again for your help!

Cheers,
Jackson

---

### Post by linuxopjemac on 2010-07-08
If you install Ubuntu, it will automatically install the yaboot boot loader.

---

### Post by Jackson Tan on 2010-07-08
Hmm... that's strange. I'm pretty sure nothing went wrong with the Ubuntu installation.

Mac OS boots from one of the hard disks, and I installed Ubuntu in the other. Could this be the reason why Yaboot did not load when the system starts up?

---

### Post by linuxopjemac on 2010-07-08
You have to have yaboot on the disk where Linux resides. I guess you need to boot with the option key pressed (Alt key) to make your Mac give you the option to choose both disks.

---

### Post by Jackson Tan on 2010-07-08
Ah!... That's probably my issue, but yet another problem arises as I've mentioned in my first post.

For some reason, the monitor does not pick up any signal until Mac OS boots. So if I hold down the Option key, I'll just go into a blank screen as my monitor searches for a signal. I've no idea why this is so...

Is there any key combination that I can input through the blank screen to get Ubuntu to boot? Something like, Right Arrow Key then Enter? I've never seen the boot option screen before, so I have no idea how to select when blind.

Thanks a lot for your help!

---

### Post by linuxopjemac on 2010-07-09
This shouzld work, as I told you with the Option key. Other than that, you have to repair the yaboot boot loader from a liveCD or so.

You will have to chroot your way into the system. Just google that word "chroot" in this forum and you will find some posts by me about fixing yaboot.

---

### Post by Jackson Tan on 2010-07-12
Sorry for the delay in replying. I've been busy over the weekends and have no time to fix this problem.

Anyway, I prodded around and it appears that Mac OS cannot see the hard drive containing Ubuntu. It does not turn up in the Startup Disk, and neither does it seem to appear in Startup Manager when I boot with the Option key (the latter was guessed by trial-and-error, since I cannot see what goes on with a blank screen).

Reinstalling Ubuntu doesn't seem to help a single bit. I suspect for it to work properly, I will have to remove Mac OS, install Ubuntu and then reinstall Mac OS. That is something I don't want to go into.

So I'm afraid I'll have to leave it there. Thanks for all the help so far!

---

### Post by linuxopjemac on 2010-07-12
Maybe you have to switch the drives. Maybe Apple sees the Master only to boot from, or something like that.

---

### Post by Jackson Tan on 2010-07-12
Quite possibly, in all honesty, I've pretty much given up on this desktop that is assigned to me and started using my personal laptop (which has Ubuntu in it).

To shed some light on my irritation, while I was attempting to get Ubuntu going on the system, I was also trying to get MatLab, netCDF and NCView going, all of which I need for my work. To that I got varying degrees of success after spending a good whole week on that.

Meanwhile, this morning I brought my laptop and fixed those three programs up in less than half an hour. They ran perfectly well.

So all in all, thanks a million, linuxopjemac, for your help. I'm sorry this ended up unresolved.

---

### Post by linuxopjemac on 2010-07-13
You are always welcome.

---

