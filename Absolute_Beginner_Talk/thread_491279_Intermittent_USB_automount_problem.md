---
title: "Intermittent USB automount problem"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Acksys on 2007-07-03
I'm having a problem that's similar to, but different from, the USB problems that most users are having.

When I first boot my computer, a Dell Inspiron 6000 running Feisty 7.04, the USB devices that I insert (key, camera, iPod mini, external HDD, etc.) are recognized and will mount automatically.

However, after the machine has been running for awhile, something happens that stops it from automatically mounting these devices. When I plug them in, they are still recognized and can be mounted manually, but will not automount.

Is this a known problem, and is there a solution? Thanks in advance.

---

### Post by Inxsible on 2007-07-03
> **Acksys said:**
> I'm having a problem that's similar to, but different from, the USB problems that most users are having.
 
When I first boot my computer, a Dell Inspiron 6000 running Feisty 7.04, the USB devices that I insert (key, camera, iPod mini, external HDD, etc.) are recognized and will mount automatically.
 
However, after the machine has been running for awhile, something happens that stops it from automatically mounting these devices. When I plug them in, they are still recognized and can be mounted manually, but will not automount.
 
Is this a known problem, and is there a solution? Thanks in advance.
 
you should use pmount to mount all external drives. It mounts your drive under /media and I have never had a problem with the automount. It always mounts the moment I connect the device.

---

### Post by Rocket2DMn on 2007-07-03
Actually, I have that problem, too.  I unmount and turn off my external HD when I'm not using it, and after awhile it won't automount anymore, but I can do it manually.

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> Actually, I have that problem, too. I unmount and turn off my external HD when I'm not using it, and after awhile it won't automount anymore, but I can do it manually.
 
Do you use the regular mount or pmount ?

---

### Post by Rocket2DMn on 2007-07-03
I have an entry in /etc/fstab for my external drive, so when I turn it on to remount, i use "sudo mount -a".

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> I have an entry in /etc/fstab for my external drive, so when I turn it on to remount, i use "sudo mount -a".
 
You can put in an "auto" keyword as one of the options in the fstab file to have it automount everytime. OR better yet, simply use pmount and NOT have any entries for external drives in the fstab :)

---

### Post by Rocket2DMn on 2007-07-03
I'm not in front of my ubuntu laptop as I am at work right now, but I think I do have the auto in there since it normally mounts automatically when I turn it on, hence the problem.  I keep an fstab entry because I need the drive to mount at a specific location so my backup software will function properly.

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> I'm not in front of my ubuntu laptop as I am at work right now, but I think I do have the auto in there since it normally mounts automatically when I turn it on, hence the problem. I keep an fstab entry because I need the drive to mount at a specific location so my backup software will function properly.
 
At the risk of sounding like harping on pmount too much, pmount will mount it to one particular location too under /media. This mount point is any name that you select. However it will always be under /media.
 
But if you are happy the way you are currently setup ...then well. To each his own!! :)

---

### Post by Rocket2DMn on 2007-07-03
Ok, well I'll consider giving that a try, I knew about it, just never gave it much thought.  How can I configure the system to use pmount but always automatically mount the drive to /media/usbdisk every time I turn the drive on (since this is the original problem)?

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> Ok, well I'll consider giving that a try, I knew about it, just never gave it much thought. How can I configure the system to use pmount but always automatically mount the drive to /media/usbdisk every time I turn the drive on (since this is the original problem)?
 
If you dont  have pmount installed already
```
sudo aptitude install pmount
```
 
Then to mount a device
```
sudo pmount /dev/Xd*? MOUNT POINT
``` where X = s or h
* = a,b,c....
? = 1,2,3...
 
so something like ```
sudo pmount /dev/sdb1 usbdisk
``` This will mount it under /media/usbdisk

---

### Post by Rocket2DMn on 2007-07-03
Will this store information somewhere so the drive will automatically mount to this location every time after I do this setup and initial pmount?  Or will I have to mount it every time with something like
```
sudo pmount -a
```
It doesn't seem to me like this is advancing my situation any.

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> Will this store information somewhere so the drive will automatically mount to this location every time after I do this setup and initial pmount? Or will I have to mount it every time with something like
```
sudo pmount -a
```
It doesn't seem to me like this is advancing my situation any.
 
No you dont have to do a sudo pmount-a  at all. Also remove/comment out the entries in fstab that you currently have so as not to cause confusion over two things trying to mount the same thing at the same time.
 
Your drive will always get mounted at /media/usbdisk the moment you connect it

---

### Post by Rocket2DMn on 2007-07-03
Bad*ss. I'll give that a try when I get home this evening.  You'll certainly here back from me if it doesn't work, but I'll try to inform you if it does as well.  Thanks, I appreciate the support.

---

### Post by Inxsible on 2007-07-03
> **Rocket2DMn said:**
> Bad*ss. I'll give that a try when I get home this evening. You'll certainly here back from me if it doesn't work, but I'll try to inform you if it does as well. Thanks, I appreciate the support.
 
you are quite welcome !

---

### Post by Rocket2DMn on 2007-07-03
OK well it didn't let me have permission to access the drive, so I'm just gonna stick with what I got.  Thanks man.

---

### Post by ~sparkles~ on 2007-07-03
> **Rocket2DMn said:**
> OK well it didn't let me have permission to access the drive, so I'm just gonna stick with what I got.  Thanks man.

I got the same problem with pmount. Needed root permission to access, read, write etc. Fstab at least works some of the time...

---

