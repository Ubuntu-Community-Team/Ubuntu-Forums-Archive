---
title: "File systems and NTFS"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by localgod11 on 2007-12-18
I am currently tossing around the idea of building a home server using buntu but I need some help with choosing a filesystem everything I found on the subjest is either very old ( Novell white paper from 2004) or is using old hardware (500mhz P3).

I would like something stable and quick, that can handle files ranging from a few kb to 10 Gb.  It also needs to play nice with NTFS and a winders comp will be using it as a server as well.

I have been leaning towards ext3 as it is the most well know and there a a miriade of recover tools in case it gives up the ghost.

Ideas?

---

### Post by omegamike3 on 2007-12-18
I would got with ext3 as it is definitely one of the better filesystems out there. It also, in my experience, is what works best with Ubuntu at this point in time. Granted, the problems I've had with other filesystems in Ubuntu weren't anything terrible, but still, there's nothing like 'setting and forgetting' :)

---

### Post by Severun on 2007-12-18
Not sure what you mean by "Play Nice with NTFS"

If you use ntfs-3g you can read and write to the Windows partitions on your local machine and you can use smbmount to mount remote NTFS.

As for filesytems, I use ext3 and it works quite nicely, I haven't had any problems with lost files or corruption even with multiple "Hard" boots.  As for stability/reliability, nothing beats a good backup :)

---

### Post by kernel tom on 2007-12-18
If you want it to be easy... FAT32 is the way to go (r/w by mac, linux, windows)

ext3 is not recognizable by windows, you would need a client like samba to do this
ntfs is read/writable under linux, however you can not use anything but ext3 for your /home

-kt

---

### Post by PeterJS on 2007-12-18
> **kernel tom said:**
> 
ext3 is not recognizable by windows


Actually there is an Ext2/3 driver for windows and it isn't half bad:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by kernel tom on 2007-12-18
> **PeterJS said:**
> Actually there is an Ext2/3 driver for windows and it isn't half bad:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

hey if that'll work and you aren't hooking up any mac's to this server, then definately ext3

---

