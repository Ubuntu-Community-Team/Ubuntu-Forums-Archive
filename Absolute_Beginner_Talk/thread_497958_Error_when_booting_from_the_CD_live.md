---
title: "Error when booting from the CD live?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by `Jon on 2007-07-10
Okay, so, I downloaded Ubuntu 7.04, and extracted the files with Winrar. I burnt the files with Nero in the "bootable disk" format.

I changed my first boot device to CD-Rom, put the disk in and tried to boot from the disk. When my computer tried to boot from the disk, I got an error saying that one of the .exe files couldn't be executed and to restart my computer.

Did I burn the files the wrong way or something?

Thanks.

---

### Post by FleetAdmiral74 on 2007-07-10
I *think* you use it, and burn it as an image. No need to change any other settings. It is under the backup tab I think...

---

### Post by Inxsible on 2007-07-10
> **`Jon said:**
> Okay, so, I downloaded Ubuntu 7.04, and extracted the files with Winrar. I burnt the files with Nero in the "bootable disk" format.
 
I changed my first boot device to CD-Rom, put the disk in and tried to boot from the disk. When my computer tried to boot from the disk, I got an error saying that one of the .exe files couldn't be executed and to restart my computer.
 
Did I burn the files the wrong way or something?
 
Thanks.
Yes you burnt them wrong. You have to burn the CD as an .iso image. You do not need to extract any files from the iso.
 
Also make sure you burn the iso at low speeds. Recommended speeds is 4x or less

---

### Post by p_quarles on 2007-07-10
Yeah, you did a few things wrong. First off, the files on the Ubuntu live CD are not compressed. If you somehow got a .rar archive, you downloaded from the wrong place. Download the CD from the official Ubuntu site.

Second, you need to burn the file that you downloaded as an image. This means that you need to select the option that says "Burn as image" or "Burn as .ISO" No un-raring, unzipping or anything else is necessary between download and burn. 

There are dozens of tutorials out there, easily found on Google, so try searching those if you aren't sure how to do this.

---

### Post by randytuggle on 2007-07-10
actually, the page where you downloaded the ISO file at Ubuntu's site lists some free programs that you can download in order to burn your ISO file to a CD.

---

### Post by `Jon on 2007-07-10
Thanks for all the help, it's working now.

And I mean't IsoBuster, not Winrar. XD;;

---

### Post by `Jon on 2007-07-11
Okee. New problem.

I've got my computer to boot in Ubuntu fine. I'm just having a bit of trouble installing Irssi. I have no clue what to do. Can anyone help?

---

### Post by macogw on 2007-07-11
sudo apt-get install irssi
in applications > accessories > terminal

---

### Post by `Jon on 2007-07-11
This may sound like a really idiotic question, but how do I run Irssi after I've done that?

---

