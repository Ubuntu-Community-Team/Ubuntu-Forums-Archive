---
title: "How to boot backup hd after hd1 failure"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-12-05
It final happened,My hd failed, or wouldn't boot. I have an internal backup hd using *Simple Backup* but I don't have a clue as how I access that drive. I'm writing this with the "start/install" on my 7.10 iso cd. I don't know whether I've actually had a drive failure or the grub boot has been corrupted. I'll appreciate any advice you can give me.

Jerry

---

### Post by vikram on 2007-12-05
did you boot from the live CD ?

see if you can mount the HD and check if you can access the data.
in the terminal

sudo fdisk -l
(to get drive name like /dev/hda1 )

sudo mkdir /myoldhd

sudo mount dervename /myoldhd

---

### Post by lakelovers on 2007-12-05
I did boot from a live disk. I tried the "sudo fdisk -l" and got no response. Does that mean I'm out of luck?

Jerry

---

### Post by quandary on 2007-12-05
> **lakelovers said:**
> 
I did boot from a live disk. I tried the "sudo fdisk -l" and got no response. Does that mean I'm out of luck?

Jerry


Sounds so. You have a backup ?

---

### Post by lakelovers on 2007-12-05
yes, I have a backup of the full hard drive, on a second drive. That's what I'm trying to access. What happened when the failure happed was that I had just finished update a web site with Quantas., and about three quarters of the screen went black. Ubuntu's splash screen on the top one-quarter of the screen. I turned the computer off via the power button, then turned it back on, and got the error message that there was a drive failure

I have a older Dell, Dimenstion 2300. Can't afford a new computer, so If I install a new primary drive, I suppose I can reinstall simple backup and access the backup drive. The live CD does not have Sbackup installed and I don't see it on Synaptic Maybe I'll try apt-get simple backup. What do you think? I'm not sure of the proper name of Sbackup, but I guess I could give it a try.

Jerry

---

### Post by quandary on 2007-12-05
> **lakelovers said:**
> yes, I have a backup of the full hard drive, on a second drive. That's what I'm trying to access. What happened when the failure happed was that I had just finished update a web site with Quantas., and about three quarters of the screen went black. Ubuntu's splash screen on the top one-quarter of the screen. I turned the computer off via the power button, then turned it back on, and got the error message that there was a drive failure

I have a older Dell, Dimenstion 2300. Can't afford a new computer, so If I install a new primary drive, I suppose I can reinstall simple backup and access the backup drive. The live CD does not have Sbackup installed and I don't see it on Synaptic Maybe I'll try apt-get simple backup. What do you think? I'm not sure of the proper name of Sbackup, but I guess I could give it a try.

Jerry

Hmm, didn't realize the economy in Texas is that bad that people can't afford a new computer anymore...

But, yes, just install a new primary drive, and copy the data back over. that's all you have to do.

---

### Post by meierfra on 2007-12-05
Give testdisk a try.  (See my signature)

---

### Post by lakelovers on 2007-12-05
>  Hmm, didn't realize the economy in Texas is that bad that people can't afford a new computer anymore...
 

Well it's matter of priority . . . plus Christmas. . . pluse I'm not getting a lot out of computers anymore . . . plus over the years I've put way too many $$$ into computers. I started out with a Commodor that had no disk drive (that was an add-on), no installed programs except Dos, and less memory than a digital watch. I think I paid around $1,200 for that package of crap. This Dell cost me around $400. Anyway, thanks for your help.

Jerry

---

### Post by quandary on 2007-12-07
> **lakelovers said:**
> Well it's matter of priority . . . plus Christmas. . . pluse I'm not getting a lot out of computers anymore . . . plus over the years I've put way too many $$$ into computers. I started out with a Commodor that had no disk drive (that was an add-on), no installed programs except Dos, and less memory than a digital watch. I think I paid around $1,200 for that package of crap. This Dell cost me around $400. Anyway, thanks for your help.

Jerry

You're welcome ;-)

---

