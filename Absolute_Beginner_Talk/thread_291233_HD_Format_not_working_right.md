---
title: "HD Format not working right"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by AdNZL on 2006-11-02
I'm trying to format my 200GiB HD using the Disks Manager.

So far, every time I have tryed to format it (3 times in ex3, then once in ex2 and another time in ReiserFS) the Disks Manager at First displays the HD with the new file format, but if I reboot or even just close then re-open the Disks Manager it displays the Disk as NTFS again, even though all the files on the Drive now apear to be wiped.

So far any problems I've run into with Ubuntu have been easy to fix and normally just a silly mistake on my part... but this one really has me stumped. (proberbly doesnt help that its almost 2am :p )

---

### Post by EriktheUnready on 2006-11-02
Did you apply?
I assume u r using gparted.
Have you tried using fdisk or cfdisk?
By default only root has permissions to write to extra disks.
An excellent way to see how things work is: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

let us know if you DONT come right.

---

### Post by AdNZL on 2006-11-02
> **EriktheUnready said:**
> Did you apply?
I assume u r using gparted.



Ok Now I'm a little confused. Are you saying that the Disk Manager in Ubuntu doesn't work and that I need to use gparted?

---

### Post by taurus on 2006-11-02
If you want to format the whole harddrive to ext3, do it from a prompt, one command and everything is good...

---

### Post by bodhi.zazen on 2006-11-02
FYI: I wrote a how-to that covers how to format from the CLI [here](http://ubuntuforums.org/showthread.php?t=282018)

---

