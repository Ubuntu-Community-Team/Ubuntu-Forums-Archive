---
title: "Dual boot issue"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by jewbilee on 2006-10-17
Hey guys, I need a way to dual boot both Ubuntu and Windows from my laptop.  I intend to keep Windows as my primary OS but would like to experiment with Ubuntu often as well.  So heres my deal, I can dual boot both from my one harddrive but I want to be able to have windows on my internal and ubuntu on an external.  So if i install Ubuntu onto the secondary drive, and unplug it from the laptop, will i get any errors while im on the move?

Last time i tried this with Mandriva, anytime i didnt have my external connected I would get an error from GRUB or LILO and it wouldnt let me proceed because it couldnt find linux, any suggestions?

---

### Post by adwait on 2006-10-17
Yes that would still be the case. I think installing GRUB to the first sector of the partition instead of the MBR would be an option, but I don't think the standard Ubuntu installer gives that option anymore...

---

### Post by deadgobby on 2006-10-17
You may have the same trouble, but here is ubies wiki link and see and try it out if it works
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Bachstelze on 2006-10-17
It does, if you use an Alternate CD but personnally, I'd do this :

Install Ubuntu on the external **but** create a separate partition for /boot, which will go on the internal - it won't take much diskspace, 32 megabytes is enough. So GRUB won't complain if the external is unplugged at boot-time (all the files it needs are on /boot) and it will search for the main Ubuntu files (on the external) only if you choose to boot it.

---

### Post by jewbilee on 2006-10-17
Ill see what I can do about that boot thing, Im really new to linux  so ill have to see how it goes..

---

