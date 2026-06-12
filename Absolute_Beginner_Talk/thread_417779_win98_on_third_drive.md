---
title: "win98 on third drive"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by oddcarout on 2007-04-21
Right now I have XP on hd1 and Ubuntu on hd2, I want to add a third drive to run win98. I have my reasons.

how would I do this? I have the drive. 

Also I have a 10gig partition on dhd2 that I could put it on. How would I do that?

I am runing GRUB.

Thanks

---

### Post by bloodniece on 2007-04-22
I wish could help, just because I like the idea that someone wants to install Win 98 on the same machine that has Linux.  BTW, what are your reasons?  Gaming?

A quick Google brought me this.  Good luck.

[http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html")

---

### Post by Patrick K on 2007-04-22
I'm pretty sure W98 will need to be installed on the Primary/Master drive. I don't think it will install anywhere else. Remember it is DOS based. So you will likely need to disconnect the other drives and put the install drive in the P/M position. Once installed, you'll need to tell Grub about it by editing menu.lst. 

As to whether W98 will run from a drive other than P/M, I don't know, I've never tried. If not, you may have to reposition the drives so W98 is on the Primary/Master. Then you'll have to install Grub to that drive, remove it from the other drive and edit menu.lst to reflect the reality of the situation. This could turn into a lot of work. Best to keep the Ubuntu liveCD handy so you can access Linux for editing menu.lst and installing Grub. I'm not sure how to install Grub from the livecd but there should be instructions somewhere.

If you have to run with W98 on the P/M, there may be issues with XP regarding paths since having this drive in the P/M position will change the drive letters. I don't use XP but hear you can change the drive letters so this might be fixable. Good luck.

---

### Post by oddcarout on 2007-04-22
I have some software that I bought when I was a student (that long ago) that is just too expensive when it works just fine, that wont run on XP. I had a box running 98 but the MB died, it is that old and that used.

---

