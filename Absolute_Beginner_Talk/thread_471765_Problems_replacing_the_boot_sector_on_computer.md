---
title: "Problems replacing the boot sector on computer"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by afropete14 on 2007-06-12
Ok sadly I had to get rid of Ubuntu last night so I formatted it and it didn't boot so I put a post up here and someone told me to restore off of my windows xp disk and i had heard that from another fourm so i tried it and it said this 
press any key to boot from cd(so I pressed a key then it showed this). . . . . . . brub loading stage 1.5
Grub loading please wait
error 17

is there another way to replace the boot sector?

---

### Post by overdrank on 2007-06-12
> **afropete14 said:**
> Ok sadly I had to get rid of Ubuntu last night so I formatted it and it didn't boot so I put a post up here and someone told me to restore off of my windows xp disk and i had heard that from another fourm so i tried it and it said this 
press any key to boot from cd(so I pressed a key then it showed this). . . . . . . brub loading stage 1.5
Grub loading please wait
error 17

is there another way to replace the boot sector?

Hi, they gave you the right answers in your other post
[http://ubuntuforums.org/showthread.php?t=471717](http://ubuntuforums.org/showthread.php?t=471717)
:(

---

### Post by CLI-Linux on 2007-06-12
It sounds like it's still booting off of the boot sector and not the CD.  I would make sure that your keyboard takes input on startup.  Also, some questions to find out more of what your system looks like.

Is this a dual boot machine?  Is that why your using the win xp disk?  what version of ubuntu was installed?  What do you mean by formatted it?  Does that mean you try reinstalling ubuntu?  Or win xp?

Please update.  Thanks.

---

### Post by afropete14 on 2007-06-12
I know they gave me the right answer in the other post but it is just not working.

It is a dual boot machine so I had this program that formated the E: drive(ubuntu part) and then I restarted it so that I could delete the E: sector and give it all to the C:drive (Windows) part but it never would reboot again.  Oh and it will take keyboard inputs on startup.

---

### Post by afropete14 on 2007-06-12
Oh and I had the latest version of Ubuntu, I have no idea what one that is.  I just had it sent to me from a site.

---

### Post by LaRoza on 2007-06-12
Use the Super Grub Disk, it works.

[http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso](http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso)

---

