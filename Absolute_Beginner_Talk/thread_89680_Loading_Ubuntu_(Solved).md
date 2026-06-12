---
title: "Loading Ubuntu (Solved)"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-11-13
Yesterday I had Ubuntu 5.04 and upgraded to 5.10...

On one of my other PC's I had freshly installed 5.10...and I noticed when I loaded Ubuntu it sort of did a graphical load with a progress bar etc.

But on the PC I upgraded it still does what 5.04 did with the DOS type screen...how can I get the grapical one on the PC I upgraded?

---

### Post by adwait on 2005-11-13
Try
```
sudo rcconf
```
check the box against usplash. Save and quit.

---

### Post by lavarock09 on 2005-11-13
[QUOTE=adwait]Try
```
sudo rcconf
```
check the box against usplash. Save and quit.[/QUOTE]

It doesn't mention usplash

EDIT: Oh yeah, I see it...but It's already checked and it didn't change anything

---

### Post by vruum on 2005-11-13
try to reinstall usplash through synaptic, or in a terminal do 
```
sudo dpkg-reconfigure usplash
```

---

### Post by lavarock09 on 2005-11-13
nope, didn't work

---

### Post by vruum on 2005-11-13
what does the file /boot/grub/menu.lst look like, your ubuntu entry should look something like this
```

title           Ubuntu, kernel 2.6.12-9-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-k7 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-k7
savedefault
boot

```
also, 
[this]("http://ubuntuforums.org/showthread.php?t=76309&highlight=usplash") might apply to you. 
do you know if the usplash daemon is loaded, maybe install bum (boot up manager) and make sure that usplash is started on boot.

---

### Post by lavarock09 on 2005-11-13
I've got it working now...

Thanks for your help...I forgot the page it was but it was somewhere on the forums

---

