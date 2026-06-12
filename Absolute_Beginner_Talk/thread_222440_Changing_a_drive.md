---
title: "Changing a drive"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by davidY on 2006-07-25
Hi guys!
When I installed ubuntu, i made a partition to be mounted as media/sda1 .... that seems to make it look like I will always get the drive mounted, and I dont know how to unmount it.

can somebody tell me how to move this drive away from /media/sda1 to something like /useless

thanks

---

### Post by davidY on 2006-07-25
Changed situation: i figured out how to change the name: it was in System>administrator>disk

but still I cant unmount or delete the icon from the desktop.. any help?

---

### Post by davidY on 2006-07-25
Lol... I am pretty stupid... I now use the same program and changed the mode to non-accessable. so it does not bother me anymore

---

### Post by OU812 on 2006-07-25
Your post is a little unclear to me: Are you trying to keep the partition, but change it to noauto mount? Are you simply trying to rename it? Or are you trying to delete it? If you're trying to delete it, in a terminal try

rm /path

and if root owns the file

sudo rm /path

john

---

