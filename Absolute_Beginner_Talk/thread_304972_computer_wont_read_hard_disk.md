---
title: "computer wont read hard disk"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-22
i have a windows os running on another comp, and i need to transfer a few large files (cant fit on dvd). so i plugged my HD into the computer, but windows couldnt read it for some reason. i know that it worked when i had windows on this HD, but now with ubuntu, windows wont read it. Am i doin sumtin wrong? please help

---

### Post by Tilex on 2006-11-22
Windows does not 'see' ext3 file systems.  It does not understand them and doesn't want to.  

I know there's a nice application that you can download in Windows which allows you to read ext3 file systems in Windows.  You can download it there:
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

I'm not sure though if it's going to work since it's another hard disk you're trying to read and not another partition...just try it out it's a very small program...

---

### Post by JShadow on 2006-11-22
Ubuntu uses a filesystem called EXT3 which Windows cannot read. If you're trying to transfer the files from Ubuntu to Windows, a driver is available here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Personally, if the PCs are near each other, I would think it would be easier to transfer the files via Samba or FTP over a crossover cable rather than moving hard drives around though.

---

### Post by Cardmaster91 on 2006-11-22
thanx tilex, taht looks like it will work

---

