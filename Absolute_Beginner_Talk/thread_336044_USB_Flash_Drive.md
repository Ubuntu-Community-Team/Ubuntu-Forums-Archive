---
title: "USB Flash Drive"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by LinuxSon on 2007-01-11
How do I change the "Write" permission on a USB Flash Drive so that I can write data to it?
Please help!! ](*,) 


Linuxson

---

### Post by maxamillion on 2007-01-11
you technically shouldn't need to but 

```
sudo chmod +rw /media/usbDrive
```

your machine might not see it as usbDrive .. that's just an example... do this first
```
cd /media/
ls
```

and just see what the usb thumb drive is being referred to as and replace usbDrive with whatever your machine calls it in that command up top

---

### Post by icedwater on 2007-01-12
Hi, I seem to have a similar problem as LinuxSon..

I tried to chmod the usbdisk (that's what it's called on my system) but I got this message.

chmod: changing permissions of `/media/usbdisk': Read-only file system

even with sudo! 

Hmm... any help? I would really like to use my SD card both as a camera memory device and a portable drive to hold some documents.. the trouble is, if I format it using FAT32 on Linux, my camera can't read it, and vice versa.

I'm using a Casio Exilim EX-Z50, if that helps. I'm on Ubuntu Dapper.

Thanks in advance for any advice!

---

### Post by alinuxfan on 2007-01-26
I am having the same problem too.
It was working and then I did a complete re-install. 
I cut and pasted files from it while my system was getting updates and now it doesnt work.
I think that something I installed with synaptic messed it up
](*,)

---

### Post by alinuxfan on 2007-01-27
I found a solution...
I copied everything and then I reformatted it.
Somewhere I read that a FAT32 filesystem can only hold so many folders/files and that when one deletes a folder/file the file still adds that one to the number.
I reformatted...it works..now I created a directory  "documents" and .I will place everything
in there from now on!

---

### Post by icedwater on 2007-03-17
Hmmm... it's something to think about. I'll try that, thanks :)

---

