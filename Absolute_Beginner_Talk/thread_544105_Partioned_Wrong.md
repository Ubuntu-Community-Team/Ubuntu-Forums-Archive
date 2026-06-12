---
title: "Partioned Wrong"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-09-05
Alright. Strange issue. Well stupid issue. When I was installing Ubuntu I somehow made my / partion only 10 gigs but my usr/local/ 60. So now my home folder is only about 6 gigs and my usr/local is huge. Any issues with this? Such as if I were to run out of space in the home folder. Is there a way to give the extra space out of my usr/local partion to my home folder?

---

### Post by tuxcantfly on 2007-09-05
reboot into a liveCD (or the ubuntu desktop CD)

mount the /usr/local partition

move all of the contents of the partition into the folder /usr/local in the partition used as the root filesystem

move all of the contents within of the /home folder in the partition used as root to the partition that was formerly mounted as /usr/local

edit /etc/fstab and change the mountpoint of the partition from /usr/local to /home

---

### Post by toasty_ghosty on 2007-09-05
Thanks but one question, whats a program that I can burn bootable iso's with?

---

### Post by alienexplorers on 2007-09-06
You can use K3B or Gnomebaker.

---

### Post by bigboy_pdb on 2007-09-06
Just download the iso from the Ubuntu site, right click on the file (once it has downloaded), select "Write to Disc...", in the "Write to Disc" drop down menu (in the "Write to Disc" window) select your CD/DVD-RW drive that the empty CD has been inserted into, and click the "Write" button.

Although if you've installed Ubuntu, you should already have a Live CD.

---

### Post by alienexplorers on 2007-09-06
Make sure you use write as iso and just don't copy it to the disk.  Only write as iso will allow the disk to boot and work.

---

### Post by toasty_ghosty on 2007-09-06
Alright, I used poweriso back when I was using Windows and I didnt know a Linux equal. Thanks for the help.

---

