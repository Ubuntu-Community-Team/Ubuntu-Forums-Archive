---
title: "Should I see my XP partition in Ubuntu?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ThreeTrees on 2008-03-06
I installed 7.10 on my Windows XP Pro laptop.  Now I can dual boot.  When I'm in the Ubuntu desktop, it shows me my XP partition (i.e. the first partition, the one with the XP OS) as a little disk icon on the left.

[LIST]
[*]Is this normal?
[*]Why doesn't it show my other partitions on the desktop?
[/LIST]

---

### Post by thisiam on 2008-03-06
you have to mount the other partitions.
go to places -> computer and you should see the other partitions. 
you just click on it and then give your password then you can see them on the desktop.
do you have ntfs-3g installed ?

---

### Post by Shazaam on 2008-03-06
1. Yes that is normal and you can remove the icon using gconf-editor if it bothers you.
2. Normally you won't see your Ubuntu partitions on the desktop. When you add other distro's/operating systems/partitions a new icon will pop up on your desktop.

To remove the disk icon(s) from your desktop...

Go to Applications>Accessories>Terminal. When it opens type this in....
```
gconf-editor
```
Go to apps>nautilus>desktop. Uncheck "volumes visible"

---

### Post by hamster_billy on 2008-03-06
It's normal, as far as I'm aware. I think anything that's not part of the Ubuntu OS will show up on the desktop in the same way - other mounted partitions, network drives, USB drives etc. The Ubuntu drive can be accessed through the places menu.

I imagine it'd be possible to make the Ubuntu drive show up on the desktop too, but I suspect most people wouldn't find it useful - it's normally only your own home folder that you'd want to access that way.

---

### Post by ThreeTrees on 2008-03-07
> **Shazaam said:**
> 1. Yes that is normal and you can remove the icon using gconf-editor if it bothers you.

It's not really bothering me; I just thought it was odd that the one partition that you wouldn't want to touch is displayed prominently on the desktop, while others (like my /home and a partition shared between Linux and Windows) make you take an extra step to access them.

But thank you for the gconf-editor info, and thanks to all for the other answers.

By the way, someone mentioned NTFS-3G?  That comes automatically with 7.10 Gutsy.

---

### Post by dcstar on 2008-03-07
> **ThreeTrees said:**
> I installed 7.10 on my Windows XP Pro laptop.  Now I can dual boot.  When I'm in the Ubuntu desktop, it shows me my XP partition (i.e. the first partition, the one with the XP OS) as a little disk icon on the left.

[LIST]
[*]Is this normal?
[*]Why doesn't it show my other partitions on the desktop?
[/LIST]

1: Yes

2: Because the other partitions are listed in your /etc/fstab file - this one isn't (but it was detected on boot up as a non-hidden partition).

Install the **pysdm** package and you can use it to automatically mount the partition to a specific mount point, then it won't appear as an available partition to mount on the desktop.

---

