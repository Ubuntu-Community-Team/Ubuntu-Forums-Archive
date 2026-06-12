---
title: "Linux live cd wont boot on imac g4"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by mattpenguin09 on 2009-01-18
Well just got the ppc ubuntu cd for 5 bucks.So i put it into my imac g4 i hold down c it comes up i pres enter then i chosse that im from nz the the keybroad layout etc then this message pops up the i dont have a normal cd rom drive and askeds me to put in a floppy with drives on them but i wont have a floppy so i select no then it tells me which part of the install i want to skip too have tryed all of then it fails. Please help and sorry about the english im in a rush lol

BTW the sepcs of my mac are 15 inch 768mb ram 80gb hard drive and osx tiger.

If you are wondering why i paid for the ubuntu cd for ppc my internet speed is like 50kbps Internet is not good in new zealand.

Thanks for your help i really want to try ubuntu

---

### Post by McFrostey on 2009-01-18
its just a little bug once it ask you to select from the list (youll see like CDROM and DEV" hit CTRL ALT F2 then you will se a command prompt type in "modprobe ide-scsi"
thats all then hit CTRL ALT F1 if it still doesnt work it will take you to the installation menu just try again and IT WILL WORK

The same thing happened to me with my iMac G4 Kudos

---

### Post by McFrostey on 2009-01-18
o and my internet download speed is 56-61kbps and it took three hours
I just started the download before I went to school and when I came home it was done

---

### Post by stream303 on 2009-01-18
For those cases where you may have limited bandwidth, and it just takes forever to download, or if you are rate or bandwidth limited, you may be interested in the netboot minimal image:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It has enough to get your started and will download the latest updates right from the start - via text-mode, but full gui afterwards.

This way, you don't end up downloading a release, and then end up downloading *another* 200mb or so of immediate updates like with the standard full-cd releases.

Be sure to select 32-bit ppc for anything that's not a G5, (64-bit for the G5's)

---

### Post by mattpenguin09 on 2009-01-18
it just says FATAL could not find moudle ide and when i go back it sitll wont work.

---

### Post by mattpenguin09 on 2009-01-18
re 303 are those live cds??

---

### Post by mattpenguin09 on 2009-01-18
o great the delovper of ubuntu for ppc have just told me theres no live cd thing anymore...........

---

