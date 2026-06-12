---
title: "New User screwed up computer and needs to get files off before re-installing"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by turiya on 2007-03-12
As the thread name states, I'm new to linux, and I managed to completely screw up ubuntu. I still have recovery mode avaiable to me and I need to get 5 files off of the disk before I re-install.

I can't figure out how to get the system to recognize a writable media from the command line though. It seems to know I have a USB jump drive plugged in, but it's not in the media directory and I can't figure out how else to get access to it. I have a CD burner installed, but as far as I can tell the computer doesn't even know that it's there, I don't think I have the correct drivers installed. It also seems to recognize the USB 3.5 floppy drive, but doesn't give me direct access to that either.

Is there some way of telling it to directly access the drives based on the bus location? Or is there maybe a better way to do this...

Or even possibly a way to upload the files to an ftp server from the recovery command line?

---

### Post by STREETURCHINE on 2007-03-12
what is the error you are getting

---

### Post by turiya on 2007-03-12
well, I think I've screwed it up even further since then but I was getting the file permission on home folder error that many noobs seem to get. Essentially I didn't realize editing file permissions could cause such a bad problem and went ahead and did it...

---

### Post by turiya on 2007-03-12
I think the system is beyond recovery I just need to find a way to get these files off the computer, they're my homework and the only copies I have...

---

### Post by STREETURCHINE on 2007-03-12
i have a 1 gig usb dohicky(sorry the name for it just aludes me at the moment)that i copy to do you have any usb devices you can click and drag to


do you also have the live disk

---

### Post by turiya on 2007-03-12
I don't have a gui interface right now, just command line, and what do you mean by the live disk, is that the install disk? I used a friend's copy to install so I don't really know what's what...

---

### Post by STREETURCHINE on 2007-03-12
yes if you can get the live disk and run that you can then mount your hard drive and move your files to a usb flash drive ..

i dont know of any commands in the command line.

---

### Post by turiya on 2007-03-12
How do I mount the hard drive from the live disk? I looked into that and couldn't figure it out...

---

### Post by STREETURCHINE on 2007-03-12
once you have the live disk running edit your fstab

   ```
gksudo gedit /etc/fstab
```

and ad this to the fstab (i am going to assume it is hda1 just chane it if not)

/dev/hda1    /media/shared       ext3  defaults  0  1

   save and close 

the open terminal

               ```
sudo mkdir /media/shared
sudo mount -a
sudo chmod -R 777 /media/shared
df -h
```
enter the commands on at a time
you should then find the mount point in media under shared

then you should be able to copy your files 

there may be an easier way but i find this works

---

### Post by turiya on 2007-03-12
Thank You, thank you, thank you!!! Full access, exactly what I'd been looking for.

---

### Post by STREETURCHINE on 2007-03-12
no problem i broke mine many times had to do this heaps

enjoy

---

