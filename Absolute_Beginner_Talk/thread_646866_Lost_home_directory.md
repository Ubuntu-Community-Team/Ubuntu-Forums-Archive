---
title: "Lost home directory"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by bobosity on 2007-12-21
This is fun....

I did something bad with fsck. Upon rebooting I get something about user directory does not exist.

hda1 is the root system. hda2 is bigger and mounts under 'home'. I tried adding another user and it put him under hda1/home. Reboot again and it won't even recognise the newuser directory. It asks if I want to login as root and then logs me right back out.

I can boot from livecd and see my directories under hda2. 

Where should I look to fix this. I guess I have to mount hda2 but where do I make it happen? I don't want to mess this up more so I thought I'd ask before experimenting.

Thanks

---

### Post by taurus on 2007-12-21
You can still boot into recovery mode from GRUB menu so you don't have to do it from the LiveCD.  

Once you are in recovery mode, post

```
sudo fdisk -l
cat /etc/fstab
ls -la /home
```

---

### Post by bobosity on 2007-12-21
Taurus- I followed your post and it worked. 

But.... how did it work? Those commands just listed info - it was all correct -and when I rebooted, it all worked fine. What happened to the user I created on hda1/home? When I created him I could see the directory but now it's gone and hda2 is back under /home.

Anyway.... Thanks

---

### Post by taurus on 2007-12-21
Is there a $HOME directory for that new user, /home/*username*?

---

