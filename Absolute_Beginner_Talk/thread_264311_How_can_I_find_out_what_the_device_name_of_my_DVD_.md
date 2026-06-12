---
title: "How can I find out what the device name of my DVD drive is?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-09-24
I basically want to copy a DVD to my Hard Drive so I can put it on my iPod, but Vive and cpdvd won't detect my DVD.  I'm pretty sure the problem arises from it trying to use the wrong device, so is there any way I can find out what the name is?

---

### Post by bulldog on 2006-09-24
Look in your /media folder.

or type in your terminal

cat /etc/fstab

If that is what you're looking for.

---

### Post by crazybrit4967 on 2006-09-24
Yeah, sort of.  But my DVD drive isn't mentioned in fstab.  Also, I know the mount point (/media/cdrom-1); it's just that Vive and cpdvd ask for the device name as well.

---

### Post by got_nix on 2006-09-24
oh your dvd drive isn't auto mounted.

here's an example of my mount point in my fstab file

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

you did check your media or mnt dir as well right? withe very laptop i've used 4 different models so far all running linux my cdrom has alwasy been auto mounted as cdrom0, onlything i had to mount manually is my ntfs partition back in my dual booting days:|

---

### Post by crazybrit4967 on 2006-09-24
> **got_nix said:**
> oh your dvd drive isn't auto mounted.

here's an example of my mount point in my fstab file

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

you did check your media or mnt dir as well right? withe very laptop i've used 4 different models so far all running linux my cdrom has alwasy been auto mounted as cdrom0, onlything i had to mount manually is my ntfs partition back in my dual booting days:|No, that's not the problem either.  It mounts automatically (and it's mounted at cdrom-1; cdrom0 is my cd-rw drive), and I can play the DVD and everything, it's just that Vive doesn't detect it for some reason, so I thought the problem could be the wrong device name. 

So does anyone have any ideas as to what could be causing this?

---

### Post by bulldog on 2006-09-24
I'm a noob in this but I should say pop in the dvd-->go to your media folder and open the dvd-->copy it's contents to a folder on your hdd-->done.

But I'm sure you have thought this by yourself :D

---

### Post by crazybrit4967 on 2006-09-24
Yeah, you can't just do that because of copy protection.

---

