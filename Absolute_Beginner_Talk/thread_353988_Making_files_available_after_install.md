---
title: "Making files available after install"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by manuva on 2007-02-05
Howdy,

I have just installed Ubuntu having gone the shrink my Windows partition route.

Can someone please advise me how i might now create another partition that i can then move my collection of music and movies onto that could be read/written to by both Windows and Ubuntu.

cheers!

---

### Post by riven0 on 2007-02-05
You can do this through gparted. If you can't find it under System >> Administration, then install it through Synaptic or:

> sudo apt-get install gparted

Then, all you do is partition some space, either from your Linux partition or Windows partition, and make sure it's labeled as fat32. Then once Gparted is done, you'll want to mount it on Ubuntu to be able to read/write to it.

---

### Post by rocknrolf77 on 2007-02-05
You can make a partition with the ext 3 file system. If you download this driver : [http://www.fs-driver.org/](http://www.fs-driver.org/)  You can read and write this partition from windows. :)

---

### Post by manuva on 2007-02-06
thanks guys..

i'm shiny new to all this so i appreciate the help!

---

