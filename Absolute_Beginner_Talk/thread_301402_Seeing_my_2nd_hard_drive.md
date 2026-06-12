---
title: "Seeing my 2nd hard drive"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by khaledih on 2006-11-17
Greetings:

I have installed Ubuntu (Edgy), but I am having a problem with seeing the partitions on my second hard drive.. (it sees the first, but not the others).  I think it is something to do with mounting etc. 

I also need full r/w access to these partitions, these are either fat32 or ntfs..

TIA,
KHaled.
ps: you may want to e-mail me..  khaledih attt googlemail dott kom  (plz correct..)

---

### Post by biffta on 2006-11-17
I had similar problems with my recent edgy install. Coming from a KDE background there were plenty of tools to view and mount additional drives. I have not been able to find any such graphical tools in gnome (not saying they're not there, just I couldn't find them!).

So instead I just mounted my second disk from the command line. First off type this:
sudo fdisk -l
This will list info on all your connected drives. Your second drive will "probably" be called 
/dev/hdb
If like mine it is, this is what I did next.
sudo mkdir /storage
sudo gedit /etc/fstab
Add this line to the end:
/dev/hdb1       /storage        reiserfs        defaults        0       1
sudo mount -a

You will need to change apects of this to suit your needs, this link might help you further.
[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

