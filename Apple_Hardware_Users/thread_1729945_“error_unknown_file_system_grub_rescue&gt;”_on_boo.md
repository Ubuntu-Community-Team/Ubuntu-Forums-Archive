---
title: "“error: unknown file system grub rescue&gt;” on boot"
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by gtr053 on 2011-04-15
I previously had Ubuntu installed on my MBR. I  deleted that partition (32 GB), resized my Mac partition back up to (250  GB), and then reduced it to 200 GB and created a new one with 50 GB via  BootCamp to install Windows 7 from a DVD that I burnt (I got a Windows  executable from [MSDNAA]("http://msdn.microsoft.com/en-us/academic/bb250591") that I used with Wine to obtain the ISO image. Insert rant about having to download Windows with a Windows executable here.).

  I've tried burning two different DVDs. I used [Burn]("http://burn-osx.sourceforge.net/Pages/English/home.html")  on my Mac to burn a data DVD+R with the HFS+ and Joliet filesystems (I  think) and then tried again with the ISO9660 and UDF filesystems. The  latter has not shown any signs of working besides mounting on OS X. The  first DVD would not boot whenever I held 'C' down at time of boot. So I  went into BootCamp and clicked "Start Installation". It restarted my  computer and this is where the real confusion comes up. I think that it  tried booting via the empty partition. The reason I say this is that  there are remnants of GRUB and when I boot, I get a screen that says  this:

  [FONT=Courier New]error: unknown filesystem
grub rescue>[/FONT]

The only command that I have found to work is ls. For  the time being, I have booted back to the OS X partition by holding the  "option" key on boot. I have no idea where to go from here. Any pointers  will be much appreciated.

---

### Post by handy on 2011-04-25
This is how to burn a bootable disk in OS X:

[http://hints.macworld.com/article.php?story=20060619181010389](http://hints.macworld.com/article.php?story=20060619181010389)

Whilst I'm here you may or may not find this link helpful also, I know I do:

[http://www.danrodney.com/mac/](http://www.danrodney.com/mac/)

Good luck with it.

---

