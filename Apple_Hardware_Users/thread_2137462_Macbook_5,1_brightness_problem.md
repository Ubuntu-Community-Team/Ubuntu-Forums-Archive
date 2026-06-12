---
title: "Macbook 5,1 brightness problem"
date: 2013-04-20
forum: Apple Hardware Users
---

### Post by chessmate on 2013-04-20
Hello,

I wrote this before but on the wrong place, sorry about that. Well the problem is still the same, thank you for taking a look at this:

I have a macbook 5,1 and I have ubuntu 12.04 only. Once booted I cannot increase or decrease the brigthness of the screen and mantains at its maximum but the graphics besides that works fine. What shall I do in order to fix that? Well I passed through some posts and did this on the terminal:

```

username@computersname-MacBook:~$ ls /sys/class/backlight
apple_backlight
username@computersname-MacBook:~$ lsmod | grep video
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
username@computersname-MacBook:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=5f59014a-f5f9-4946-986d-652003df4751 ro quiet splash vt.handoff=7
username@computersname-MacBook:~$ sudo nano ect/default/grub

```
the file does not exist

I don't know what to do at this moment because I have almost no experience with linux and IF I want to keep on going with linux (which I will) I need to reduce the brightness of my screen because is killing me

Thank you for your help.!

chessmate

---

### Post by Rxke on 2013-05-04
Hi, I had the same issue, solved with changing  the driver for your graphics card. Don't worry, this does not involve no creepy command line stuff ;-)

go to update manager in preferences *or* start synaptic if installed via menu (under System)  (I cant be more specific, dunno if you use gnome, kde xfce or what...)

there in the preferences of your updater, there's stuff like software sources et c, look for the tab(?) that says 'extra drivers'
I solved it to switching to the free/open version, called 'Nouveau' turned out to work better than the closed versions :)

---

