---
title: "LiveCD - Getting Windows files?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2005-12-21
First things first, I beg you all not to laugh at me.

But, I changed my Windows password - and it's so long that when I type it in at the start screen, it all screws up, and now I can't get into Windows.

This could be the godsend I've been waiting for - I could be finally able to install Ubuntu.

I'm using the liveCD right now to make this post - So, how would I get at the files on my HD, to get them onto the network, so they'd be backed up?

Also ( And I'd understand completely if you guys flamed me for this, but my "Ubuntu newbie brew" status, and the fact that I've made around ten posts should make you feel sympathy enough not to ), would it be possible to *coughs* retrieve my password?

If not, who cares. Except my Dad. Heh.

Thanks

Jimmey

---

### Post by aysiu on 2005-12-21
To get the files, boot up the live CD and open a terminal and type ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows
gksudo nautilus
``` This assumes your Windows partition is NTFS (and not FAT32). It also assumes it's at /dev/hda1 of the partition table. To be sure of the filesystem and partition table location, type ```
sudo fdisk -l
```

---

### Post by Danielle on 2005-12-21
[QUOTE=Jimmey]would it be possible to *coughs* retrieve my password?

If not, who cares. Except my Dad. Heh.

Thanks

Jimmey[/QUOTE]
[color=red]EDIT[/color]
forget it. i don't believe you anymore.

---

### Post by Jimmey on 2005-12-22
Could I not just delete the SAM file?
Unfortunately, I'm not an Iron Geek :(

---

### Post by Cprav on 2005-12-22
Okay, forgive the possible hijacking of this thread, but a real newbie question - how do you open a terminal?:oops:

---

### Post by Gadren on 2005-12-22
In GNOME, Applications>Accessories>Terminal will open it.

---

### Post by Cprav on 2005-12-22
Duh, thanks!  I think I looked everywhere except there!  :)  

Thanks again!

---

