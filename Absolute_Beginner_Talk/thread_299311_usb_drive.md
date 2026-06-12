---
title: "usb drive"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-13
What is the syntax to mount a removable hard drive?

---

### Post by halitech on 2006-11-13
check here

[http://www.ubuntuforums.org/showthread.php?t=287114&highlight=usb]("http://www.ubuntuforums.org/showthread.php?t=287114&highlight=usb")

---

### Post by bodhi.zazen on 2006-11-14
> **saintj0n said:**
> What is the syntax to mount a removable hard drive?

Assuming your usb is /dev/sda1: ```
 pmount /dev/sda1 usb
```

OR

```
sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb
```

Mount options for rw depend of File system.

---

### Post by cyris| on 2006-11-14
i mount my usb drive in linux the same way bodhi.zazen does. pretty straight forward.

---

### Post by saintj0n on 2006-11-14
What can I do to make it so I just type in a word and it mounts (or to make it automount when it plugs in?)

---

### Post by bodhi.zazen on 2006-11-14
> **saintj0n said:**
> What can I do to make it so I just type in a word and it mounts (or to make it automount when it plugs in?)

Add an entry in fstab and add an alias (in ~/.bashrc)

I usually mount by label as the /dev ID changes with usb devices.

for example, label the usb device usb.
See here for how to label: [fstab](http://ubuntuforums.org/showthread.php?t=283131)

Add a line to fstab:> LABEL=usb /media/usb auto <options_here> 0 0Options depend on usb file system.

then, open ~/.bashrc (~ is shorthand for /home/user_name)

Add lines:> # Mount usb
alias usb='mount LABEL=usb'
alias uusb='unmount LABEL=usb'

Now you can, in a terminal or mini command line, mount with usb 

and unmount with uusb 8)

---

