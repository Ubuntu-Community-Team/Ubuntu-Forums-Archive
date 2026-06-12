---
title: "Running Windows XP within Ubuntu"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-11-03
I was wondering if it is possible to run Windows XP within Ubuntu virtually. I don't play games, so that is not a concern. It is to run Office 2003 without exiting Ubuntu.

As great as OpenOffice and Wine are, I still need a very good Powerpoint program. Thanks!

---

### Post by Esben Kramer on 2006-11-03
You could try VMware, which lets you run Windows XP, or other operating systens inside Ubuntu.

---

### Post by Ashton K. on 2006-11-03
There's no real need to do that. Check out Wine, (if it's not in apt-get, check sourceforge.net), it'll help run Office for you (it is not an emulator though, it just tries to add functionality to windows executables and .dlls).

PS. In Sourceforge, the name will be "Wine is not an emulator".

---

### Post by apres on 2006-11-03
Yes. You have a number of options. VMWare or Parallels Workstation would probably be your two fastest options. VMWare Server is free. If you want to go the free AND open source route, QEMU is pretty fast and free as well. You can also use KQEMU in conjunction with QEMU to speed up emulation further.

---

### Post by amitroy5 on 2006-11-03
I am trying to use QEMU. I am in the process of installing Windows XP. However, I got stuck here. Windows XP asks me to create a partition, but when I try, it does not let me. It does detect the 6 GB of "unpartitioned" space that I created with QEMU, but I cannot format that space for Windows XP. What should I do? Is there any other way to "format" it? Thanks!

---

### Post by amitroy5 on 2006-11-04
I was wondering how I can install QEMU Accelerator? Thanks!

---

### Post by tphuocthai on 2007-03-03
> **amitroy5 said:**
> I was wondering how I can install QEMU Accelerator? Thanks!
You can take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=361528](http://www.ubuntuforums.org/showthread.php?t=361528)

---

### Post by esaym on 2007-03-03
Well there is vmware, everyone knows about that.  But what about Virtualbox?  It is open source and free.  Anyone know if it is better then vmware for making Virtual computers?

---

### Post by kodoku on 2007-03-03
I tried VirtualBox, and it's really fast (almost native speeds), but it would randomly abort for no reason whatsoever if I try to do anything except leaving it idle.  VMWare Server (free also) is a tad bit more sluggish, but its rock solid for me.  I can leave it running day and night playing games, downloading and encoding video and it still runs.

---

### Post by ramjet_1953 on 2007-03-03
I've been using VirtualBox for some time now, with no problems at all.

The main thing to remember with any virtualisation software is that you will probably need plenty of RAM, as you will be running Linux, the virtualisation engine, Windows and then the Windows application.

I would suggest that some of the complaints with lockups are a result of low system memory.

Check-out the attached screen shot.

Regards,
Roger :cool:

---

### Post by kodoku on 2007-03-04
> **ramjet_1953 said:**
> 

I would suggest that some of the complaints with lockups are a result of low system memory.


Well, I have 1.5 Gb of RAM, so I really don't think its a memory issue (for virtualbox, I alotted 512 mb of RAM..)

Ramjet, which version of VirtualBox are you using, the GPL version or the proprietary one?

---

