---
title: "Updating messed with grub etc."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by ballyhoo on 2006-12-21
I installed the updates.  Now there is a lot of entries in grub and will not load 2.6.15-23-386 that was the default before updating.

Any ideas?

---

### Post by taurus on 2006-12-21
I guess you must have been updating a kernel because your /boot/grub/menu.lst has been modified!  What kind of error message when you try to boot from the old kernel?

---

### Post by jbayone on 2006-12-21
Try booting with the live cd and installing GrubEd.  It's a pretty easy way to go about it.

---

### Post by ballyhoo on 2006-12-21
> **taurus said:**
> I guess you must have been updating a kernel because your /boot/grub/menu.lst has been modified!  What kind of error message when you try to boot from the old kernel?

Failed to start X server.

Followed the howto from [http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

This has worked in the past but this time there exists the same problem.

---

### Post by taurus on 2006-12-21
Are you any change using/installing nVidia driver for your graphic card?  What happens if you boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by ballyhoo on 2006-12-21
> **jbayone said:**
> Try booting with the live cd and installing GrubEd.  It's a pretty easy way to go about it.

I scrolled thru the list of options in grub (this update added 14 entries) and loaded the one listed before (2.6.15-23-386) and received the same X server error.

Question--re-installing a fresh grub would accomplish the same as scrolling thru and picking the one that use to work, wouldn't it?

---

### Post by Aberrix on 2006-12-21
I had a similar issue a week ago, ran an update that required a reboot... didnt pay much attention then my xserver was broke :/ left if for a week because I didn't want to screw with it. finally looked into it and I run the generic kernel and when I updated I got the new i386 kernel and that didnt want to boot for me (nvidia drivers + beryl, etc), once I picked my generic kernel everything booted again, when into my bootlist and made sure to remove the i386 kernel. all is well now.

---

### Post by ballyhoo on 2006-12-21
when I start typing (after choosing recovery mode) I receive an error message about  unknown key pressed (translated set 2, code 0xd9 on isa 0060/serio0).

It doesn't allow me to finish typing.

---

### Post by taurus on 2006-12-21
Can you be a little more specific?  What are you trying to type from a console and which key gave that error message?

---

### Post by jbayone on 2006-12-21
Sorry, I thought you couldn't boot and wanted to change your default boot OS.  
I had the same problem with x server not starting.  I ran dpkg-reconfigure xserver-xorg and just went through the autodetect.  All that happened after updating also.

---

### Post by ballyhoo on 2006-12-21
> **taurus said:**
> Can you be a little more specific?  What are you trying to type from a console and which key gave that error message?

that was in recovery mode.

i rebooted and just kept trying the different kernels (is this the correct term) until i found one that let me boot up.

now the question--i did a search under synaptic pack. man. for "linux" and found the various linux-images.  do i uninstall the incorrect images?

---

### Post by ballyhoo on 2006-12-21
i can remove the different images from grub.  but is this all i should do?

---

### Post by ballyhoo on 2006-12-21
if i remove the different linux-images from my system will this cause any problems?

---

### Post by ballyhoo on 2006-12-21
is there any council on this?

---

