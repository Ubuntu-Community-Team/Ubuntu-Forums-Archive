---
title: "how do I mount newly created partitions"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-03-06
I just resized 2 large ntfs partitions to make room for 2 large fat32 partitions, I rebooted and I cant fugiure out how to get the 2 new partions to mount so I can use them in ubuntu edgy.  Please help, thanks.

---

### Post by overdrank on 2007-03-06
> **Jive Turkey said:**
> I just resized 2 large ntfs partitions to make room for 2 large fat32 partitions, I rebooted and I cant fugiure out how to get the 2 new partions to mount so I can use them in ubuntu edgy.  Please help, thanks.

Hi try this link. It is from another post. Good luck
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jive Turkey on 2007-03-06
I got it to work.  The psychocats link above covered most of it but one also need to get the UUID for the new partition using the cammand:[PHP]sudo vol_id -u[/PHP] </dev/hd**> 
I guess UUID was recently added to fstab

---

### Post by overdrank on 2007-03-06
> **Jive Turkey said:**
> I got it to work.  The psychocats link above covered most of it but one also need to get the UUID for the new partition using the cammand:[PHP]sudo vol_id -u[/PHP] </dev/hd**> 
I guess UUID was recently added to fstab

Glad it worked for you. :KS

---

### Post by dahas on 2007-03-20
some time i see no link for new partition i make on the /dev/disk/by-uuid
this is special case when u make a raid disk alos and have to make 1 more command to be complete /etc/fstab file and working
*vol_id -u /dev/mdxx*
*[COLOR="Red"]ln -s /dev/mdxx /dev/disk/my-uuid/"code u got from vol_id"[/COLOR]*
Hope this will help some who try to make a new raid disk and cant mount it using uuid.
Replace xx with your raid device number.

---

