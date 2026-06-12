---
title: "ubuntu installer crashes."
date: 2007-02-23
forum: Apple Intel Users
---

### Post by sammycitrus on 2007-02-23
Ok, so I followed the ubuntu installation directions on the macbook pro ubuntu wiki, and here are the problems i faced

first off, i created the swap file like it was directed, but i had to follow the instructions from [http://wiki.onmac.net/index.php/Trip...t_via_BootCamp](http://wiki.onmac.net/index.php/Trip...t_via_BootCamp)  instead of the ones given in the wiki. coz i had some supercluster error or something along those lines.

then i followed the install to disk instructions and after choosing manual partitioning i couldnt select /dev/sda3 for swap file and /dev/sda3 for root file system ( / ) because (duh!) linux needs two separate partitions for file swap and root. So instead i chose only /dev/sda3 for / and left the rest blank. Now, after this it starts partitioning and 15% into the formatting progress i get an error message saying ext3 cannot be formatted.

So i go back and restart the installation process and this time at the manual partition screen i see my linux partition is labelled ext2 (unlike ext3 from before). SO i still choose /dev/sda3/ for / and this time at 15% it tells me no swap space selected, blah blah, optimal performance, i need to select swap space, but i can continue, so i select continue anyway. The installation resumes and suddenly a couple minutes into it, the installation crashes and they want to send a bug report.

So now i'm stuck, my mn/linux file already exists and the 2 GB swap file i created using directions still exists, and since i know nada about linux i dunno how i can start the whole process from scratch.  So any help on how to proceed with the installation, or what i am doing wrong, or how i can fix things will be greatly appreciated.

thanks in advance

---

### Post by oskarloko on 2007-02-26
Maybe  read this [wiki page]("https://help.ubuntu.com/community/MacBook")

Ok, let's see...
[LIST=1]
[*]Before install, use Gparted / graphical partition utility on live cd
[*]Change your ext2 partition to a ext3 one
[*]Reformat selected partition
[*]when GpParted ends, exit and sync it form a terminal 
[INDENT]```
sudo gptsync /dev/sda && sudo sfdisk -c /dev/sda 3 83
```[/INDENT]
[*]Then begin to install
[/LIST]

Good luck !

---

