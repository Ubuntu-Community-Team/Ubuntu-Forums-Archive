---
title: "[SOLVED] Kernel Panic after Boot Splash Install"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-22
Hello i just followed this install instructions here

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

Its for this very famous boot splash U-Fingerprint
[http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

This command from the install instructions
```
sudo update-initramfs -u
``` i belive is causeing a kernel panic?

> kernel panic not syncing VFS unable to mount root ffs on unknown block 0,0!
first i used the Logon Manager to install *.so splash screens, but after i had visual errors with stable and alpha version of this splash i used the manual instructions.

I got the GRUB SUPER DISC or i thought about using the LIVE CD (recovery mode isnt workeing either) to change the boot splash. 

But id liek first to change the above command back, can someone please give me a hint howto do this?

Thanks

---

### Post by shareMenaPeace on 2007-12-22
Cannot boot from LIVE CD either ...recovery mode doesnt works and i have no old kernel ... vista still boots

---

### Post by shareMenaPeace on 2007-12-22
Ok ..LIVE CD works lol ther ewas somethign on the CD ....omg

---

### Post by jken146 on 2007-12-22
[http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002) is the similar problem that I had a while back.  There are a couple of other threads linked to in there that may be useful as well.

Best of luck.

---

### Post by shareMenaPeace on 2007-12-22
Hmm how can i use root from the LIVE CD ... recovery mode isnt working ...

---

### Post by shareMenaPeace on 2007-12-22
This has somethign todo with initrd.img but i dont know how to fix this.


[http://www.debianhelp.org/node/4940](http://www.debianhelp.org/node/4940)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/83629](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/83629)

I will enable show all kernels in menu.lst

AND i got a initrd.img-2.6.22-14-generic.dpkg-bak

---

### Post by jken146 on 2007-12-22
Read through the thread I gave you (and the ones in the links in my thread).  There are instructions for rebuilding initrd.img.

You can use sudo from the live CD just the same as in a normal installation.  It just doesn't ask you for a password.

---

### Post by shareMenaPeace on 2007-12-22
Hmm can you have a look into your /boot/config-2.6.22-14-generic? 
And tell me please if its liek this

 config_initramfs_source" "

line
377

And i got a bak of this file you mentioned.

thx

---

### Post by jken146 on 2007-12-22
Yes it is like that, but on line 376.  I don't remember having to edit that though.

---

### Post by shareMenaPeace on 2007-12-22
How can i edit /boot/grub/menu.lst ?

I try gksudo gedit but it looks into the virtual ubuntu from the live cd.
Do i need to create a new mount point as in your topic descirbed to alter this?

...omg this sux :)

---

### Post by shareMenaPeace on 2007-12-22
BTW from your link this guy posted in your topic and has exactly the same problem as me...
[http://ubuntuforums.org/showthread.php?t=620860](http://ubuntuforums.org/showthread.php?t=620860)

---

### Post by shareMenaPeace on 2007-12-22
OK THE FIX IS as mentioned above ...to find ....exactly

[http://ubuntuforums.org/showthread.php?p=3999157#post3999157](http://ubuntuforums.org/showthread.php?p=3999157#post3999157)

here!


:) haha

Thx jken146 to pointing me to the topic :)

puuuuuh :)=


Cheers

---

