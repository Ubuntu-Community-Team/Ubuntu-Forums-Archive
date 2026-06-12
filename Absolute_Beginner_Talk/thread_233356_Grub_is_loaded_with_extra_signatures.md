---
title: "Grub is loaded with extra signatures"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by bobpur on 2006-08-10
I have an old Compaq that I dual boot Ubuntu with. I have two hard drives and each one has some form of Ubuntu Dapper on it.
As my signature states, I'll work on one or the other until I can't fix it then I'll re-install it.
Now the grub screen offers several choices to boot from. I guess this is what is called a kernel signature. Anyhow, several groups of lines are present each group has three lines 1) shows the kernel 2) shows safe mode and 3) says mem test. 
I don't know if I have 7 or 8 copies of an OS on two hard drives (I don't really think so) or just 3 or 4 ways on each hard drive to the one OS present.
These signatures are all different forms of Dapper using the same kernel signature. 
I tried following the instructions under the screen for editting the grub using the "E" and "D" commands and that didn't work.
This computer usually works flawlessly but lately its got problems(besides me). 
Can anyone tell me what to do about fixing this? I've read a few posts about grub problems but nothing about my specific problem. 
                        Thanks

---

### Post by stinerman on 2006-08-10
If you've updated your kernel through the repositories, you will have serveral kernels in the boot menu.

Technically speaking, you don't "upgrade" the kernel.  The package manager just installs a new one to /boot.

If they are bothing you, you can always remove an older kernel using synaptic by finding the old kernel image and removing it.

---

### Post by bobpur on 2006-08-10
I don't know? I reload off the same three Ubuntu disks (K,X,Ubuntu Dapper) and the first thing I do after is enable the repositories and update after that then download Automatix or Easy Ubuntu. All signatures have the same kernel number(s).
I found something in the forums from Tomosaur. a script for editting Grub that I'm looking at real hard.
Thanks

---

### Post by stinerman on 2006-08-10
Post your /boot/grub/menu.lst file and I'll see if I can diagnose the problem.

---

### Post by Tomosaur on 2006-08-10
Multiple kernel options isn't unusual, Grub is set by default to list all the kernels it comes across, and, thankfully, it's easy to make it find just one. Multiple memtest86 options is a bit weird. I can't really tell from your first post, but I take it you have TWO memtest86 options in the Grub menu? If so, that would be expected from having two /boot/grub/ directories (one on each linux install). I see you found my script - I was concerned that people were having this kind of problem (more than one installation of grub), and hopefully I can update the script with some features which will help people with your problem out.

If you can post the following two things up here, it'd be a big help:

1) The results of the following command:
```

sudo fdisk -lu

```

2) The contents of /boot/grub/menu.lst from BOTH installations of grub (please label which is which)

Thanks a lot, and I hope my script helps you out.

---

### Post by Snowmayne on 2006-08-10
> **bobpur said:**
> I don't know? I reload off the same three Ubuntu disks (K,X,Ubuntu Dapper) and the first thing I do after is enable the repositories and update after that then download Automatix or Easy Ubuntu. All signatures have the same kernel number(s).
I found something in the forums from Tomosaur. a script for editting Grub that I'm looking at real hard.
Thanks

It can be found at [http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

---

### Post by bobpur on 2006-08-10
I'm not at home right now and might not make it back until tomorrow. I'll post the required info as soon as I get back. 
Thanks for the responses.

---

