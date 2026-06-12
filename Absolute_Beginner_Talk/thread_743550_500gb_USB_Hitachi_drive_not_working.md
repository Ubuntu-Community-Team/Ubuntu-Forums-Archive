---
title: "500gb USB Hitachi drive not working"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by pawnrocket on 2008-04-02
I was in best buy the other day, and there is was a 500gb hard drive for $95.00 I bought it, I thought for one second, maybe I should ask, but I didn't, I just left. 

I got home, removed the 320gb my book and put the 500gb in its usb slot. I didn't get anything. I installed the ntfs-config package, selected read option, still nothing. I ran gparted, and it didn't even see it. Eventually the computer started lagging quite a bit and I had to restart.I plugged  it into my roommates Vista, and BAM! 500 accessible gigs. 

I am using Gutsy on an old 2.0ghz Intel - 1gb ram - internal 40gig hard drive - nvidia fx5200 

I looked through the forum and didn't find any info - does anyone have any ideas? PLEASE?

---

### Post by amazingtaters on 2008-04-02
ya know, similar thing happened to my 160 Gig MyBook just the other day. I dot a ton of stuff, but in the end what fixed it for me was booting up with my Hardy live cd (which detected the drive fine), finding out that even as root in the live cd I can't copy files to my internal hdd, and the rebooting to my normal install. You also might want to install usbview, it is a little package that has a gui and can show you what your computer sees as attached thru the usb ports.

---

### Post by pawnrocket on 2008-04-02
Thanks for the reply, I really love this site. I installed usbview, but at the moment I am moving everything off the Mybook and onto the Hitachi. I will post back when I can plug the Hitachi into the port. 

Thanks again. ..

---

### Post by pawnrocket on 2008-04-02
sorry --- moving it on my roommates windows box.

---

### Post by amazingtaters on 2008-04-02
Right I know how it is. I use my roommates XP lappy when I'm having trouble (seemed to have my fair share lately, but it's been smooth sailing for the past day and everything looks good). Also, usbutils and usbmount would be good to install too. It can't hurt anyway.

---

### Post by Tatty on 2008-04-02
Plug in the drive, then post the output of ```
sudo fdisk -l
``` and ```
lsusb
```

---

### Post by amazingtaters on 2008-04-02
If gparted doesn't see the drive as existing, I don't think fdisk or lsusb will even note it's existence... call it a hunch based on personal experience from yesterday.

---

### Post by pawnrocket on 2008-04-02
After I moved the data from Mybook, the Hitachi Started right up (and showed up on the desktop) when I plugged it into my Ubuntu Box, I don't know why...

---

