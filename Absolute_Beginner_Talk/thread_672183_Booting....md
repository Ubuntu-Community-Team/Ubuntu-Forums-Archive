---
title: "Booting..."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by ccabrita on 2008-01-19
First of all, i need to explain my system....

I got an Pentium4 3.0GHz with two HD... one with 250G (with windows) other with 80G (with ubuntu)

An friend gave me an old motherboard+processor, and i decided to make another pc...i bought everything i needand put hands to work... 

Everything went well until the booting question... i put both drives onthe same  pc... it works...

i put only the windows drive it gaves me an error 21 of GRUB...

i put only the ubuntu drive... it gaves an booting error...


My objectives is to have an pc with the windows drive and another with the ubuntu drive....

How do i do it?  i must not lose information... that is an must :s

---

### Post by Pevichaey5 on 2008-01-19
that means, that the grub boot manager can't find the other partitions/HDD's, if i understand what you are saying, if so, can you boot normally if both hard drives are plugged in?

---

### Post by spiderbatdad on 2008-01-19
start by backing up all the information you must not lose onto a media source other than a hard drive.

---

### Post by ccabrita on 2008-01-19
I don't think you understand...

at the moment everything is ok... but the drives are on the same pc...

i need to put one drive in one pc... and the other in another pc...

The problem is when i split the drives... with the windows drive only... grub gives an error... with the ubuntu drive only, the ubuntu gives an booting error...

i only want to put the windowds drive login into windows straight and the ubuntu drive straight to ubuntu ;)

every help is welcome ;)

---

### Post by spiderbatdad on 2008-01-19
haven't tried this myself, but sounds like you would need to fixmbr of the windows disk, using a recovery cd. Then edit grub...or possibly reinstall. Maybe your boot or swap partition is on the other disk?

---

### Post by torgrot on 2008-01-19
PUt the windows drive in the computer that you want to run windows on.  Boot off the windows CD and select recovery console.  Run fixmbr  take the CD out and reboot.  Windows should just boot now.

Put the ubuntu drive in the computer that you want to run ubuntu on and then boot off a live CD.  Then follow the instruction in this link [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

torgrot

---

### Post by mister_pink on 2008-01-19
On the windows one you'll need to put your windows CD and reinstall the bootloader to the mbr. This should be an option somewhere if you look carefully I think.

On the ubuntu box, boot to the live cd. Open a terminal and do "sudo grub", then:
```
root (hd0,0)
setup (hd0)
quit
```

Restart and all might be almost there....

---

