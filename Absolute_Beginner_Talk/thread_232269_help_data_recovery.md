---
title: "help: data recovery??????"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-08-08
i did some stupid things - on accodent - and now my ubuntu is dead.   i get one of these ```
/bin/sh: can't access tty; job control turned off
```  from searcning the forum i gather there is no fixing it.  but i have some important files on that harddisk.

so, does anybody know anything about data recovery???

it's ext3 and a sata drive.  i tried mounting it in a live cd; didn't work.  i checked the drive with a gparted livecd:  it reports there is less data on there than i know there it (or at least use to be:( ).

what shouldi do?  is there any linux based software?  free software?  non-free software?  should i take it to a shop?

---

### Post by zxee on 2006-08-08
You can check out the list of data recovery programs on freshmeat;
[http://freshmeat.net/search/?q=data+recovery&section=projects&Go.x=0&Go.y=0](http://freshmeat.net/search/?q=data+recovery&section=projects&Go.x=0&Go.y=0)
If the system is really hosed and you absolutely need those files then a lab is probably the best way to go. Good luck.

---

### Post by insub2 on 2006-08-08
> **zxee said:**
> You can check out the list of data recovery programs on freshmeat;
[http://freshmeat.net/search/?q=data+recovery&section=projects&Go.x=0&Go.y=0](http://freshmeat.net/search/?q=data+recovery&section=projects&Go.x=0&Go.y=0)


have you used any of those?  any recomendations?

thank you for your help!

---

### Post by zxee on 2006-08-08
> **insub2 said:**
> have you used any of those?  any recomendations?

thank you for your help!

I've used dd from commandline do man dd. I don't know if that will help you though. I've tried some other gui tools out there but nothing really worked very well. I actually don't want to be a PIA because losing data is no joke, and, having a backup is the best chance for recovering files after a mishap.

---

### Post by insub2 on 2006-08-23
A friend told me about Explore2fs ([http://www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs")) which did the trick.  you'll need another harddrive with windows installed on it and then download the program.  it's pretty cool.

---

### Post by steve.horsley on 2006-08-23
My first reaction would be to use a live CD to mount the disk, and copy the data somewhere safe before reinstalling - burn to CD/DVD, copy to another hard drive, to a USB drive, FTP server etc.

Note that one reason for keeping /home on a separate partition is so that you can reinstall the OS on / without overwriting any of your /home data. You can also share /home between multiple installations of Linux, so you can try out different distros. Bear this in mind when you reinstall.

---

### Post by anindya_m on 2006-08-23
Check out this link which worked for me:

Linux Ext2fs Undeletion mini-HOWTO
[http://www.tldp.org/HOWTO/Ext2fs-Undeletion.html](http://www.tldp.org/HOWTO/Ext2fs-Undeletion.html)

---

