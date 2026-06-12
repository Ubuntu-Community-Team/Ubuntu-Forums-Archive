---
title: "How do I get rid of windows??"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by the_zoor on 2007-04-26
Hi!

I have both ubuntu and windows installed on my laptop. I've decided to get rid of window$ to get more space to linux. How do I do that??

I tried to demount the partition ( showing itself on the desktop ) but I get a message saying its not accetable since its listed in /etc/fstab. Now... I tried to remove it in fstab but the same message. I've tried to do it through gparted. Same thing.

What do I do wrong? The system recommends me to do this manually. How do I do that through the terminal?

Any help will be appreciated :)

---

### Post by koshari on 2007-04-26
your on the right track, 

remove the fstab entry line  for the windows partition (or comment it out with a hash at the beginning)

then remount the fstab file by running 

```
sudo mount -a
```

then the entry on the desktop should be gone, 

then you simply use gparted to delete the windows partition, 

and create a new ext3 partition in the space or resize an existing on the same disk to take up the slack.

---

### Post by seshomaru samma on 2007-04-26
After you creat a new ext3 partition you have to mount it
[[COLOR="Navy"]instructions[/COLOR]]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by lukew on 2007-04-26
> **the_zoor said:**
> Hi!

I have both ubuntu and windows installed on my laptop. I've decided to get rid of window$ to get more space to linux. How do I do that??

I tried to demount the partition ( showing itself on the desktop ) but I get a message saying its not accetable since its listed in /etc/fstab. Now... I tried to remove it in fstab but the same message. I've tried to do it through gparted. Same thing.

What do I do wrong? The system recommends me to do this manually. How do I do that through the terminal?

Any help will be appreciated :)

the parition is already there you just need to 

```
sudo umount /dev/sdx
```
```
sudo mkfs.ext3 /dev/sdx
```

Then you should chaneg the mount options / fs type within /etc.fstab.

Luke

---

### Post by the_zoor on 2007-04-27
Thank you all for your help.

Worked great! :)

---

