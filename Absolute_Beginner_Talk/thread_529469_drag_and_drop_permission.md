---
title: "drag and drop permission?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-19
I can't drag and drop to an external USB drive. I typed sudo nautilus, but it won't allow me to drop the files to the USB drive. I'm lost on a simple task, or so I thought.

---

### Post by MenZa on 2007-08-19
First of all, when using GUI programs, do not use sudo; instead, use **gksudo <target>** for GTK applications (GNOME) and **kdesudo <target>** for Qt/KDE applications.

I suggest you set the permissions on the drive, so that not only root may write to the drive, but regular users too.

You can do this by modifying the file /etc/fstab and add the *users* flag to your device.

If you know anything about fstab, you should be able to add that pretty easily. If not, I suggest you read [this](http://www.tuxfiles.org/linuxhelp/fstab.html) really good article about fstab, what it does and how it works.

---

### Post by mikex on 2007-08-19
> **MenZa said:**
> First of all, when using GUI programs, do not use sudo; instead, use **gksudo <target>** for GTK applications (GNOME) and **kdesudo <target>** for Qt/KDE applications.

I suggest you set the permissions on the drive, so that not only root may write to the drive, but regular users too.

You can do this by modifying the file /etc/fstab and add the *users* flag to your device.


What the heck is my device? I looked in that directory and I see lots of stuff. How do I know what my device is? Ugh. My god all I want to do is copy files from my own HD to my own USB drive. Why is it made so difficult?

---

### Post by MenZa on 2007-08-19
Your device is located in /dev---a device is, in this case, a hard drive, a cd/dvd-rom drive or a floppy drive.

Could you try and paste the output of the command *sudo fdisk -l* here? (that's a lower-case "L")

---

### Post by mikex on 2007-08-19
> **MenZa said:**
> Your device is located in /dev---a device is, in this case, a hard drive, a cd/dvd-rom drive or a floppy drive.

Could you try and paste the output of the command *sudo fdisk -l* here? (that's a lower-case "L")

Thanks for the help MenZa, I appreciate it a lot, and I know all this seems easy for all of you, however, right now I am beat down with the whole process. All i want to do is copy a file and I've been at it for 45 minutes. I have to re-evaluate why I am doing any of this. Sorry for the whining...

---

### Post by MenZa on 2007-08-19
> **mikex said:**
> Thanks for the help MenZa, I appreciate it a lot, and I know all this seems easy for all of you, however, right now I am beat down with the whole process. All i want to do is copy a file and I've been at it for 45 minutes. I have to re-evaluate why I am doing any of this. Sorry for the whining...

It's quite alright; I think most of us were pretty frustrated when we started out with Linux. I know I was, and I even made the mistake to switch back to Windows before trying Ubuntu out again.

Now, could you please type "sudo fdisk -l" (lower-case L) in a terminal and paste the output here? Thanks!

---

### Post by mikex on 2007-08-19
> **MenZa said:**
> It's quite alright; I think most of us were pretty frustrated when we started out with Linux. I know I was, and I even made the mistake to switch back to Windows before trying Ubuntu out again.

Now, could you please type "sudo fdisk -l" (lower-case L) in a terminal and paste the output here? Thanks!

I can't right now because I'm restoring a previous image I made of Ubuntu to get back to what I had before the latest issues I have had. Thank goodness for Acronis backup software. I'll PM you later and if you have the time. Thanks again.

---

### Post by MenZa on 2007-08-19
I'd prefer it if you posted in this thread, so that others can benefit from it as well ;). Nothing personal :D

---

