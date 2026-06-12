---
title: "Advice on installing-CD-ROM's dead!"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-17
**CD-ROM working again - please see latest posts-thank you**

Hi everyone,
I'm planning on trying to install Ubuntu in an old Dell Latitude Windows 98 SE (HD...about 4G-about 2.5 free space) using the netboot approach because my CD-ROM's dead! Once the installer downloaded, I can surely delete lots of Windows stuff to make more room.
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I know I should have a bigger HD and more RAM but let's say I want to try it anyway.

Do you think I should give it a try or just forget it?
Is there another lighter distro that can be installed via Internet?
Thank you for your help.

---

### Post by bodhi.zazen on 2006-09-17
Either:[list=number][*]Buy a new CD-ROM.
[*]Better, open you box and "borrow" a CD-ROM from another box (it does not sound as if this is your only box...)[/list]

---

### Post by xyz on 2006-09-17
> **bodhi.zazen said:**
> Either:[list=number][*]Buy a new CD-ROM.
[*]Better, open you box and "borrow" a CD-ROM from another box (it does not sound as if this is your only box...)[/list]

I'd be very surprised if I could buy one even if I wanted to! 
You know, it's one of them old CD-ROM, sort of looks like a drawer that I can remove.
You're right, it's not my only box but the other is much more recent (2 years)..so it's not interchangable.

---

### Post by bodhi.zazen on 2006-09-17
> **xyz said:**
> I'd be very surprised if I could buy one even if I wanted to! 
You know, it's one of them old CD-ROM, sort of looks like a drawer that I can remove.
You're right, it's not my only box but the other is much more recent (2 years)..so it's not interchangable.

Have you tried? I restore/maintain old boxes and I have not had much of a problem with interchanging CD-ROM's.

It does not have to fit into the drive bay, it may not look pretty, but it only has to last as long as the install...

---

### Post by xyz on 2006-09-17
No I haven't tried yet! I just got this baby today, a friend wanted to throw it away.
Did I mention it's a laptop?

---

### Post by bodhi.zazen on 2006-09-17
No, sorry that is different....

---

### Post by xyz on 2006-09-18
[b]The CD-ROM recognizes what's in it again!
A blowdryer and a dust rag did the trick!
BIOS Boot Order can't be changed...too old![/b]
Infos:
Dell Latitude
64 RAM - 4,1 G HD
Pentium -233/MMX
Video Memory 2MB
Windows 98 SE works OKisch but it works!

I no longer need win on there; I only needed it because CD-ROM was busted. Thank you for telling me it I'm on the right track:

-it's got Partition Magic so I could delete Windows partition with it and simply proceed to install a lighter distro?
-I've read somewhere 4,1G HD - 54 RAM isn't egough for Ubuntu?

Any advice?

---

### Post by aleska on 2006-09-18
> **xyz said:**
> [b]The CD-ROM recognizes what's in it again!
A blowdryer and a dust rag did the trick!
BIOS Boot Order can't be changed...too old![/b]
Infos:
Dell Latitude
64 RAM - 4,1 G HD
Pentium -233/MMX
Video Memory 2MB
Windows 98 SE works OKisch but it works!

I no longer need win on there; I only needed it because CD-ROM was busted. Thank you for telling me it I'm on the right track:

-it's got Partition Magic so I could delete Windows partition with it and simply proceed to install a lighter distro?
-I've read somewhere 4,1G HD - 54 RAM isn't egough for Ubuntu?

Any advice?

I think you would be better off running xubuntu on it.  I think you'll find that trying to run either gnome or kde on a machine like that will be frustrating.  xubuntu runs with xfce.  My two cents anyway.

---

### Post by buffy^ on 2006-09-18
How come that no one here has thought of a bootable flash stick?


Oh wait looking at those specks, it wont be able to boot from usb... even if it has any.

Do we do a ubuntu doorstop / paperweight editon :P

-edit- forgot to put anything usefull in the post, sorry.
Ok heres what you do (old win 98 tricks) pull out the HDD, stick on a lappy to normal ide cable, and connect to your PC, dont worry it will already be set as master. Then you can use the CD rom in your drive and install the system. or copy the files to the drive and use a boot floppy.

p.s did you know that win98 and win98SE use differnt CD key sets, but if you put in an old 98 disk in when installing SE when it asks for the SE cd can use your old cd key then swap the disks back.

---

### Post by xyz on 2006-09-18
Thanks folks!
This is beyond my understanding; I wouldn't know where to begin...esp. what's in bold letters:
> Ok heres what you do (old win 98 tricks) pull out the HDD, **stick on a lappy to normal ide cable, and connect to your PC,** dont worry it will already be set as master.

Wouldn't it be simpler to delete the entire  Windows FAT 32 partition, make it nice and clean and, say install, Xubuntu, like aleska says?
I don't need, don't even want windows at all.
Thanks for reading.

---

### Post by xyz on 2006-09-18
Well, I'm downloading Xubuntu and will give it a try after I wipe Windows off the face of the HD!
I've been experimenting with PuppyLinux: [http://www.puppyos.com/](http://www.puppyos.com/)ots
Quite impressive once you've unzipped it into C:\, boots in DOS and asks you if you want win or Linux...amazingly fast on my 'old man' of a computer! I didn't recognize it!

---

### Post by bodhi.zazen on 2006-09-18
[How to install Ubuntu without a CD](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by xyz on 2006-09-18
> **bodhi.zazen said:**
> [How to install Ubuntu without a CD](http://ubuntuforums.org/showthread.php?t=28948)

Yes you're right; that's how it SHOULD've happened but I just had to blow it somehow!  
I worked all day, evening and night (it's nearly 5 AM my time now!) on this and I think I "lost it" at some point.
I removed Windows 98 SE with Partition Magic knowing perfectly well that this 'ole Dell would not boot from CD-ROM nor would it boot from CD-ROM if Diskette and/or HDD boots 'failed'.
 
There is simply NO WAY to boot from CD-ROM in BIOS...and I knew that and went ahead anyways. So now all I've got is a nice and totally empty 4.1 G HD and I suppose I'll have to ask a friend to create some kind of Diskette Boot since it seems to be the only possible thing to boot from... according to unchangable BIOS settings. Hopefully it's still possible to somehow get something installed in that box!

With such a small HD, any Ubuntu versions seem a little too 'heavy'!!
 
 So I should have just popped Doli into the CD-ROM and re-partitioned from Windows since the only good thing this darn CD-ROM does is to recognize what's in it once Windows is (was) on!
 I'm up shit creeck now..so live and learn!
 Thanks all for your help and support, though!  Much appreciated it!

---

