---
title: "help: Increase the size of my hfs+ partition"
date: 2008-02-02
forum: Apple Intel Users
---

### Post by Phrantik on 2008-02-02
I had a dual boot setup on my MacBook osx and ubuntu but i have run out of space on my OSX partition.  So I backed up all my files and moved ubuntu to a different computer.
I booted using the ubuntu install disk and opened gparted.  I deleted the ext3 partition then tried to resize my hfs+ partition.  It would only allow me to make it smaller but not bigger.
Next I tried using "parted" in terminal. but i kept giving me an error message that says something like:  "unable to fulfill all constraints of partition"
btw- journaling is disabled

any ideas?:confused:

---

### Post by cyberdork33 on 2008-02-03
there is nothing in linux available that can increase the size of an HFS+ partition. OSX utilities are your only options. if you have boot camp, you can use it to create another small partition, then reboot and run bootcamp again, telling it to restore the drive, and it will use the entire free space.


Otherwise you will have to figure out how to use the 'diskutil resizeVolume' command in OSX.
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

---

### Post by Phrantik on 2008-02-04
thanks for the info.

---

