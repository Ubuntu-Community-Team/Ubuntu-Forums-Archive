---
title: "Format harddrive with GParted"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-12
I have problems with GParted. I have two harddrives, 300 GB and 160 GB that got NTFS. I will format them to ext3 because I will use Ubuntu now instead of Windows. I have manage to format and convert the 300 GB harddrive to filesystem ext3. When I did that I first selected the harddrive, then in menu, Device -> Set disklabel, after that I unmounted the harddrive and rightclicked and selected "New". I checked all the information about new size, filesystem: ext3, etc and then I started it. It was no problem but when I try to do the same for the 160 GB I got problem. I do the exact step, which means:

"When I did that I first selected the harddrive, then in menu, Device -> Set disklabel, after that I unmounted the harddrive and rightclicked and selected "New". I checked all the information about new size, filesystem: ext3, etc and then I started it."

After I have started to create a new partition, it mount itself during the "installation" of the new partition, and I got error:
"Error while creating /dev/sdd1
Be aware that the failure to apply this operation could affect other operations on the list."

Why does it automatically mount when I have unmounted it and how do I solve the problem?

Thanks in advance.

---

### Post by Bartender on 2007-02-12
I've done several weird experiments with [GParted]("http://gparted.sourceforge.net/livecd.php").  By that I mean the GPartedLiveCD, not GParted on the Ubuntu install CD.

I'm not sure what the set disklabel thingie does.  I've never used it, and have installed several different Linux distros to the partitions I made.  What happens with that second HDD if you just skip the set disklabel step?

---

### Post by OBnascar on 2007-02-12
> **Bartender said:**
> By that I mean the GPartedLiveCD, not GParted on the Ubuntu install CD.

I agree..........

Yes, you should try the Gparted Live CD, there you will not have any mount or unmount issues. I think I would pass on the disk label option also.

---

