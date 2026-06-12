---
title: "Ubuntu wiped my Mac OS X partition!"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by DOn Lupo on 2007-12-08
I installed Ubuntu on a 7Gb partition on my Mac Mini and, after a little play on Ubuntu, rebooted into Mac OS.

Did some stuff on there and rebooted back into Ubuntu.

From that point, the Ubuntu partition is now 53Gb and totally wiped the Mac OS partition.

Any ideas as to wtf happened? :confused:

Lupo  :(

---

### Post by tiiim on 2007-12-08
> **DOn Lupo said:**
> I installed Ubuntu on a 7Gb partition on my Mac Mini and, after a little play on Ubuntu, rebooted into Mac OS.

Did some stuff on there and rebooted back into Ubuntu.

From that point, the Ubuntu partition is now 53Gb and totally wiped the Mac OS partition.

Any ideas as to wtf happened? :confused:

Lupo  :(


Sounds strange, OSes dont just suddenly grow and take space after installation.. can you advised the following:

How did you install ubuntu? what installation options/documentation did you use? Partition did you set up?
What settings did you touch in OS X?
What happped when you booted into Ubuntu?

Messages? Errors? etc 
any help will let us see what happened :)

---

### Post by DOn Lupo on 2007-12-08
> **tiiim said:**
> Sounds strange, OSes dont just suddenly grow and take space after installation..
You can imagine I was quite shocked. :)

> can you advised the following:

How did you install ubuntu?
Used Bootcamp to create a partition for Win32, burnt ubuntu to CD and followed the instalation UI.

>  what installation options/documentation did you use?
I'm trying to locate the page...obviously I got there in Mac OS, so can't look through history :) The only thing it pointed out was to delete the win32 partition created by bootcamp and to create 2 partitions for ubuntu and swap. The rest of the installation rattled off without any major decisions to make.

> Partition did you set up?
I removed the win32 partition and created a 7gb ext3 partition and the rest ~1gb for swap. This was using the disc partitioning GUI in the ubuntu installation.

It seemed to install fine with the expected partitions, and the system rebooted to boot ubuntu from the HD. After a while, I went back to mac os and that was ok.

> What settings did you touch in OS X?Didn't change any settings...just used some music software while I was there. Nothing out of the ordinary happened.

> What happped when you booted into Ubuntu?In the second ubuntu session to boot from HD, I fancied testing the hibernate function. During hibernation, a hell of a lot of messages were echoed to the screen (I don't know if that's normal or not), and then the machine powered off. When I booted it up, it got to the initial ubuntu progress bar and halted a small way in (~2%). I left it for around 10 minutes, but it didn't progress, so I power-cycled the mac and booted up again. It booted up a fresh instance of ubuntu and I wasn't too bothered about losing the hibernation state,

It was after I left this instance of ubuntu that I found I had no Mac partition anymore, since BootCamp only reported the Windows (i.e. ubuntu) partition.

Is it possible that the failed hibernation did something strange?

Thanks in advance for any help or advice anyone can offer.

---

### Post by xeth_delta on 2007-12-08
A couple of ideas.

Do you pehaps have several kernels installed on your machine? If so, you have to always make sure you boot using the same kernel you used when hibernating. Not doing so can indeed lead to data loss.

Maybe your partition table ws somehow managed, can you please post the output to the following commands:
```
sudo fdisk -l
df -h
mount
```

Xeth

---

### Post by cyberdork33 on 2007-12-09
my guess is that you deleted the OSX partition (or formatted it)during the install.

You will have to start fresh I am afraid. Install OSX, but partition the drive to leave space for Ubuntu. Then install normally.

when you boot the Ubuntu CD for installation, delete the extra partition you made in the 'partition editor' (under the admin menu). Then start the installer indicating that you want to use the 'free space'.

---

### Post by DOn Lupo on 2007-12-09
> **cyberdork33 said:**
> my guess is that you deleted the OSX partition (or formatted it)during the install.'.

At what point? After installing Ubuntu, I returned to OSX...only after returning to Ubuntu did the partition disappear (albeit after a botched hibernation attempt). If I had accidentally formatted it during the Ubuntu installation, there would be no way I could have booted into OSX after it.

Anyway...It's all gone now...including Ubuntu. I'll put it down to bad luck.

---

### Post by cyberdork33 on 2007-12-09
> **DOn Lupo said:**
> At what point? After installing Ubuntu, I returned to OSX...only after returning to Ubuntu did the partition disappear (albeit after a botched hibernation attempt). If I had accidentally formatted it during the Ubuntu installation, there would be no way I could have booted into OSX after it.

Anyway...It's all gone now...including Ubuntu. I'll put it down to bad luck.

you could have altered the partition table, and the MBR and GPT didn't sync, so that data existed in the right place, but the partition table said it did not. then after booting into OSX, the tables synced up, and now no OSX partition. I can't explain it fully and I am really just guessing, but partitions do not just randomly disappear, as was already stated.

---

