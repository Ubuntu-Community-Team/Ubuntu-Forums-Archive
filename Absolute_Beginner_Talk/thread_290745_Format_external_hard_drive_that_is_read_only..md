---
title: "Format external hard drive that is read only."
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by mbstrlbstr on 2006-11-01
I'm runnig Edgy Eft on a laptop. I had an 120 gig internal hard drive that has windows on it. I bought a cheap enclosure, and hooked it up. I wanted to delete everything on it, but I'm not sure how I can. Ubuntu recognises it and everything, but it is read only.

---

### Post by Chayak on 2006-11-01
Have you tried sudo chown to change the ownership to yourself?

sorry I'd give you the command line but I'm on a work windows computer.

---

### Post by mbstrlbstr on 2006-11-01
No I haven't tried that. When you are able, could you post the code, or point me to a site with the usage of the code?

---

### Post by Chayak on 2006-11-01
I will but I'm fairly sure with this crowd someone will post it before I even have a chance to reach my Ubuntu machine. ;)

As a basis what is the drive mounted as? (the path)
gparted should do what you want
```
sudo apt-get install gparted
```
then it should be in your admin menu.

---

### Post by annda on 2006-11-01
also, you can try the command line (terminal) if you don't feel too uncomfortable with it.

```
mount
```

will the tell you the device name, e.g. **/dev/sdb1** on **/media/usbdisk** type ext3 (rw)

then go unmount the drive before reformatting:

```
sudo umount YOUR_DRIVE
```

and then format it:

```
sudo mkfs.ext3 /dev/sdSOMETHING_FROM_YOUR_MOUNT_INFO
```

that way you should get a healthy ext3 drive ready for all your files. good luck and post back.

---

### Post by mbstrlbstr on 2006-11-02
Hey Thanks for your help guys, I ended up using parted. Great program.

---

