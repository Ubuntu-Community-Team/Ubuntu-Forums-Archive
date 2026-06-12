---
title: "USB pen drive"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by umontu on 2008-02-18
I have a usb pen drive which was 3.9GB but its now 3.3 gb Fat32 and a 600 mb linux swap drive Ive tried removing it and it says its been removed but then i fdisk it again and i got the same partitions, How can remove it perminantly?

I know how to fdisk drives btw but i dont know why this isnt working.

---

### Post by mmb1 on 2008-02-18
Have you tried using gparted?

---

### Post by Discov3ry on 2008-02-18
Can you post the output of:

```
sudo fdisk /dev/your_usb_stick
```

---

### Post by umontu on 2008-02-18
Is that included in ubuntu?

---

### Post by umontu on 2008-02-18
Unable to open /dev/your_usb_stick

---

### Post by mmb1 on 2008-02-18
No, but it is available through synaptic, and I find it to be the best for working with partitions.  It might be worth a try.

---

### Post by umontu on 2008-02-18
lol i start synaptic and i get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by mmb1 on 2008-02-18
Well, that's a whole new problem in itself, and it's one I have no idead about.  Sorry, but you 're going to have find someone who knows more than me.

---

### Post by umontu on 2008-02-18
Oh well thanks for the help

Il just deal with it for now I dont need the whole pen drive atm anyways

but I want to use it for MCN live at college

---

### Post by Discov3ry on 2008-02-19
> **umontu said:**
> Unable to open /dev/your_usb_stick

/dev/your_usb_stick should be replaced with /dev/ACTUAL_USB_STICK_BLOCK_DEVICE

In this case, can you post:

```
sudo fdisk -l
```

---

### Post by Mud.Knee.Havoc on 2008-02-19
> **umontu said:**
> lol i start synaptic and i get

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Silly question, but you did run 'dpkg --configure -a' like it asked you to, right?

---

### Post by bodhi.zazen on 2008-02-19
Well, for the error message, you need to use sudo :

```
sudo dpkg --configure -a
```

Not sure if the source of your original question is fstab :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

