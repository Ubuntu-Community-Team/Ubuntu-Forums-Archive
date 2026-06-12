---
title: "NTFS write Acces"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Phoenix_World on 2007-07-19
I installed ubuntu 7.04 desktop and my ntfs volumes are mounted at bootup.. but i cant paste files into themm.. i cant change access ermissions for writin even as a ROOT ... doesn ubuntu support writing into ntfs volumes? plz help

---

### Post by SendDerek on 2007-07-19
This is a common misconception for some reason...

Ubuntu itself doesn't support writing to NTFS, but a program called NTFS-3G will support it.  

Just goto add/remove and search for NTFS-3G in "All Available Applications" and install it.  After you do this, goto Applications->System Tools->NTFS Configuration Tools and then check off the drives that you want access to.  It's very easy.

---

### Post by Phoenix_World on 2007-07-19
Thanks... it works but my Add/Remove .. program is hanging once it listeda ll software.. small subwindow keeps blankly open in front of it.. i killed that pprocess "app insta" to close it.... installed softwares only with synaptic package manager /... anyway to correct the add/remove .. problem?

---

### Post by SendDerek on 2007-07-19
This isn't a fix, but more of a workaround...

Try to install it with this command in the terminal (Applications->Accessories->Terminal):

```

sudo apt-get install ntfs-config

```

Punch in your password and it should work.  For more detail, look at the instructions on this page:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=easy+ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=easy+ntfs)

Hope this helps!


Edit:  I just realized that you said "it worked".  So, does this mean that you were able to get NTFS support?  I'm not sure how to help you with your sub-window problem unfortunately.  Your best bet is to create a new thread for that separate problem.

---

### Post by danketchpel on 2007-08-20
> **SendDerek said:**
> This is a common misconception for some reason...

Ubuntu itself doesn't support writing to NTFS, but a program called NTFS-3G will support it.  

Just goto add/remove and search for NTFS-3G in "All Available Applications" and install it.  After you do this, goto Applications->System Tools->NTFS Configuration Tools and then check off the drives that you want access to.  It's very easy.

Thanks, worked perfect!

What tripped me up was that I did another install on a networked system at work and was able to R/W NTFS right from the get go. Maybe "it" made different choices during the install???

---

### Post by hyper_ch on 2007-08-20
I'm not sure if I understand that correctly.

You have to differentiate between your system writing on a harddisk and writing on a networked harddisk.

If you are networked (e.g. samba, ssh, ftp) the writing is not done by your system but by the remote one. You just send the data that shall be written to you the other computer and it will write to it using its system and protocols and stuff.

---

