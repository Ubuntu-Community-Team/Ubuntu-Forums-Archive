---
title: "resizing dapper"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by hellfried on 2006-08-18
moments ago i just resized my ubuntu dapper partition by using the livecd of gparted. i deleted the partition (which used to house suse 10.0) adjacent to dapper. the resizing when without problem. when i booted back into dapper,there was some complaints from dapper about not being able to mount sda4 and i was instructed to do ctrl-d in the root and the bootup continued on. the icon for that suse partition has disappeared from the desktop but whne i go to the system > administrations > disks i still can see the sda4 partition although its status is 'inaccessible' (see the attachment). 
what do i have to do to get rid of it? something in fstab?

---

### Post by taurus on 2006-08-18
You need to edit your /etc/fstab to remove /dev/sda4 from it.  Open a terminal (Applications -> Accessories -> Terminal) and do

```

sudo gedit /etc/fstab
-or-
sudo nano /etc/fstab

```

---

### Post by Iarwain ben-adar on 2006-08-18
Hi,
probably it's your fstab...

Try to change the /dev/sda4 to the one it is called now (you can check via Qtparted)


Iarwain

---

### Post by hellfried on 2006-08-18
> **Iarwain ben-adar said:**
> Hi,
probably it's your fstab...

Try to change the /dev/sda4 to the one it is called now (you can check via Qtparted)


Iarwain

sda4 should not even exist now as i have incorporated it into sda3 (dapper partition). so i just remove the entry for sda4 in fstab and save?

---

### Post by taurus on 2006-08-18
Yes!  Just follow my previous post to remove it if it doesn't exist anymore...

---

### Post by hellfried on 2006-08-18
> **taurus said:**
> Yes!  Just follow my previous post to remove it if it doesn't exist anymore...

thank you guys! worked perfectly.

---

