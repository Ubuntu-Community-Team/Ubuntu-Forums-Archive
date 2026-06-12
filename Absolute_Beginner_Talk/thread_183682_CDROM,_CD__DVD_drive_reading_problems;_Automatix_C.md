---
title: "CDROM, CD / DVD drive reading problems; Automatix CD eject problem"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by quincyjones on 2006-05-28
Hey, 
I had a problem where I thought my disk drive was acting really bizzarly by reading some but not other CD's and DVD's; sometimes 'half' reading them. Turns out that the problem is to do with Ubuntu not unmounting disks when the drive is opened using the eject button on the drive. When I eject it by right clicking the drive on the desktop or by using terminal, *no problems*!
I used Automatix to enable my eject button. So does anyone know how I can ensure that the button has the proper effect (unmounts as well as ejects), not that it's terribly important?

edit:
I've done some research and I'd suggest not using the hack for getting the eject button to work. Check it out for yourself but apparently it can't make the drive unmout and your system can thus get unstable etc.
Incidentally, you can assign a key on your keyboard to eject instead, which won't cause the problem, using: system>preferances>keyboard shortcuts

---

### Post by sup on 2006-09-02
I can confirm that eject button sometimes messes things up. I for example often see only question marks instead of filenames on the CD. BUt unmounting it and remouting it via gnome Disk mounter (see add to panel) usually fix this.

---

