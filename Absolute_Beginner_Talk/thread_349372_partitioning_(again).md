---
title: "partitioning (again)"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by ramster on 2007-01-30
have just figured out how to read the answers!? thanks to housam and others including one with zs in the name. still not successful as the book cds give me the four partitions but I dont know how to resize them. I found the button but one partition says 8mb minimum and maximum and another 94mb min and max. First partition is ntfs (windows) 9.8gb others 'unallocated', 'ext3' and something else i forget. never do I see a slide and they wont move beyond their maximum.
On board 256 ram, 40gb drive, Mandriva installed (partitions supplied!!) but program not satisfactory. Also had Suse installed before this. ubuntu must sort out partition install in their feisty falcon or whatever when it appears. Still a tyro.
                                                                                       ramster

---

### Post by eilu on 2007-01-30
Your drives have to be unmounted before you can edit the partitions; think of it as taking off your clothes before you wash them. May I suggest trying the gparted LiveCD? [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by hal10000 on 2007-01-30
you can also use the ubuntu live cd (it has gparted).
Please post your partition table (from a terminal window run [COLOR="Red"]sudo fdisk -l[/COLOR] ---> this is a lower case L)

If someone should help, then it's important to know something about your partition layout.

You can mark the output with your mouse and simply paste it with the middle mouse button to your browser (or editor).

---

