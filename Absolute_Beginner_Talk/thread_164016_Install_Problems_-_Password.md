---
title: "Install Problems - Password"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by grahamd0 on 2006-04-22
Hello everyone,

So obviously, I'm totally new to linux. I just installed a dual-boot system with win2k/ubuntu.

During the install, the installer kept going to through the user creation screen over and over again, but it was showing the info I'd typed previously in each instance. There were some other screens like this, notably the video card bus screen. I finally got through the whole installer, and Ubuntu is on my system, but it won't let me log in.

It keeps saying I'm typing an incorrect password. I know I'm typing it correctly, caps lock is off, and I've tried dozens of times now.

Basically, my questions are:

Is the repetition of the user creation screen in the installer normal, did I screw something up?

Is there anything I can do to rememdy the situation without a reinstall?

Any help would be appreciated.

-Graham

---

### Post by MrXerxes on 2006-04-22
Graham I had the exact same problem!

After searching around in Recovery mode (hit ESC when GRUB is loading), I found something that led me to believe my username had gotten lost in the install process, and Ubuntu had given me the default username of OEM.

Try this:


username = oem
password =   <whatever you believe you entered during the install>


That worked for me. :)

---

### Post by mcmillan on 2006-04-22
What format is your home directory? I had this problem when I tried installing my home on a fat32 partition. Apparently it doesn't like that because it can't set permissions the same way. If you need to share files with a windows writable format, use a small home directory in something like ext3 and make symbolic links to the fat partition

---

### Post by grahamd0 on 2006-04-22
[QUOTE=mcmillan]What format is your home directory? I had this problem when I tried installing my home on a fat32 partition. Apparently it doesn't like that because it can't set permissions the same way. If you need to share files with a windows writable format, use a small home directory in something like ext3 and make symbolic links to the fat partition[/QUOTE]

Thanks. I'll try that.

Obviously something is screwy. I booted to the command line as root and tried to change my password and it said there was no user with that name. I tried add a new user account and it added it (on my FAT32 home directory) then immediately deleted it. I think you hit the nail on the head.

-Graham

---

