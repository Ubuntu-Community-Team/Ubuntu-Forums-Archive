---
title: "How to access documents in a crashed HDD?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by berniedd on 2007-12-24
I ran Ubuntu 7.06 for 6 months and then it crashed. Couldn't get past the initial splash screen. I want the saved documents in it, so I got another hard drive and installed 7.10 in it. Then I connected the failed hard drive as a slave and booted from the 7.10. The thing is, I can't see the older hard drive to copy my files off it. Even the PLACES tab at the top of the desktop doesn't show my old hard drive. Any ideas, guys? 

BTW,I also have WinXP installed for this computer in a third separate hard drive. Any way I can use it to recover my old files?

---

### Post by spiderbatdad on 2007-12-24
what does this show:  ```
sudo lshw -C Disk
```

---

### Post by erginemr on 2007-12-25
If your native attempts from within Linux do not work, you may also try installing the following freeware application:
[http://www.dirfile.com/diskinternals_linux_reader.htm](http://www.dirfile.com/diskinternals_linux_reader.htm)

to view your Linux (ext2 / ext3) hard disks and extract the needed files from within Windows.

---

### Post by nick_h on 2007-12-25
> BTW,I also have WinXP installed for this computer in a third separate hard drive. Any way I can use it to recover my old files?
You could install an ext3 driver for Windows XP such as [fs-driver.org](http://www.fs-driver.org/index.html). It is quick and easy to install and works well.

---

### Post by berniedd on 2007-12-25
> **erginemr said:**
> If your native attempts from within Linux do not work, you may also try installing the following freeware application:
[http://www.dirfile.com/diskinternals_linux_reader.htm](http://www.dirfile.com/diskinternals_linux_reader.htm)

to view your Linux (ext2 / ext3) hard disks and extract the needed files from within Windows.

Thanks, it worked like a charm. Got the documents back.

---

### Post by berniedd on 2007-12-25
> **spiderbatdad said:**
> what does this show:  ```
sudo lshw -C Disk
```

Thanks but I haven't tried it yet, since the hdd that's on the computer is the one running Win XP. I'll give it a try,just for curiosity's sake, later.

---

