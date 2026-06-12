---
title: "need help with access share drive in Windows XP on different hard drive"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-12
I read all over different guides but dont understand much, my other hard drive currently have Windows XP with a share drive. When I logon Ubuntu witch is on a different hard drive and go into places then computer, I see the share drive on windows xp but cannot mount it. Then installed samba on ubuntu but got lost with the tutorial. Please help!:-?

---

### Post by aysiu on 2006-07-12
If it's another hard drive on the same computer, then you don't need Samba.

Just follow this tutorial and post back any questions you may have:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by qdvubun on 2006-07-12
when I type in sudo fdisk -1 and hit enter
it ask for password but I can't type in anything.

---

### Post by aysiu on 2006-07-12
You can type it in. You just won't see anything. No asterisks. Nothing.

Supposedly, this is for security reasons, but anyone who would be looking over your shoulder could also look over your keyboard and see what you're typing.

Just type and press **Enter**. Your password will be accepted.

---

### Post by qdvubun on 2006-07-12
I think i'm very close to getting it to work. Now the Share drive is regconized is mounted and I followed that guide, but when I open the drive in Places --> computer--> share drive it said no permision?

---

### Post by aysiu on 2006-07-12
After you edited the /etc/fstab, did you try this? ```
sudo umount /dev/hda8
sudo mount -a
``` and then look in the /tmp/disks-conf-hda8 directory?

By the way, you can copy and paste text from the terminal. You don't need to upload screenshots of the terminal output.

---

### Post by qdvubun on 2006-07-12
ok got it working now, Thanks 
now it showed both the same share directories on the desktop, is there a way to delete one?

The windows and doc is from sudo mkdir /media/windows and mkdir /media/doc
the share drive and my document also point to the same directory

---

### Post by aysiu on 2006-07-12
I didn't quite understand your last statement. Can you post the output of these commands? (Just copy and paste straight from the terminal): ```
cd ~/Desktop
ls
df -h
cat /etc/fstab
cd /media
ls
```

---

### Post by qdvubun on 2006-07-12
oops sorry ok this is the result

---

### Post by scxtt on 2006-07-12
anything mounted to /media will show up on your desktop when mounted ... if you don't want this to happen, mount the devices somewhere else ...

if you don't want /media/windows to show up on the desktop, mount it to /mnt/windows (edit /etc/fstab too) ...

---

### Post by aysiu on 2006-07-12
Thanks for the output. It just means I'm confused. I don't know where the share icon and the My Document icon are coming from.

They're not on your desktop, and they're not mounted anywhere...

---

### Post by qdvubun on 2006-07-12
yup it worked now, both share partitions on the other hard drive can be access, I just dont know why it display the each partiton as 2 drives (duplicate)

thanks

---

