---
title: "Cant boot anything xept Ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-26
My PC starts up, and I pres F8 and a list comes up, and I choose to boot from the CD drive, but it boots my HD istalled Ubuntu!?Anyway I can fix this?
Seams that Ubuntu takes top priority and wont allow other stuff to boot.

---

### Post by TheLions on 2008-03-26
are you sure that you had inserted bootable CD? 

can you please explain better your problem?

---

### Post by munch3 on 2008-03-27
I insert WindowsXP CD in my CD Drive.
On startup, I press F8 and a list shows up asking me about the media from which I wish to boot.
I choose the CD drive where WindowsXP is.
Ubuntu that is installed on the hard drive boots.

---

### Post by Tomatz on 2008-03-27
Download this and burn it to disc:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

It will allow you to boot any m$/linux os on your system and repair boot issues.

You might want to check **/boot/grub/menu.lst** to see if the windows entry is pointing to the correct drive/partition :)

---

