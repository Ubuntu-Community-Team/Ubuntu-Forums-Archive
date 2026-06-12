---
title: "Holy Crap, I'm about to give Help, please."
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by CCCody on 2006-07-12
Okay, I tried CD Burner XP, Nero, Fireburner, and something else, (It doesn't matter it didn't work)

CD Burner XP Succesfully made a bootable disk, my Bios are set to CD ROM booting first, ect, ect. Whenever I try and boot from the disk I get some stupid DR DOS/XM enviorment followed by an A:/ symbol

WHAT AM I DOING WRONG? I'm so freaking frustrated and I'm SOOO tired of Windows. 

Please, please help me. 

Thank you in advance for your reply, every little bit helps by now. 
](*,) [-o<

---

### Post by Wolki on 2006-07-12
> **CCCody said:**
> 
CD Burner XP Succesfully made a bootable disk, my Bios are set to CD ROM booting first, ect, ect. Whenever I try and boot from the disk I get some stupid DR DOS/XM enviorment followed by an A:/ symbol

WHAT AM I DOING WRONG? I'm so freaking frustrated and I'm SOOO tired of Windows. 

OK, do not use winRAR or something else to unpack the iso, you need the complete, unaltered ISO file. Do not make the CD you burn bootable.

Simply follow the instructions here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And try to burn at a low speed if you have problems.

Have fun with Ubuntu :)

---

### Post by orb9220 on 2006-07-12
Ok in nero did you select burn an iso?

Did you burn an iso to an cd -r +r or rw

rw's are problematic

What is the name of the .iso?

More info please?

---

### Post by T700 on 2006-07-12
What drive letter is associated with your CD drive.  Very commonly, the A is associated with a floppy drive.  Is there by chance a floppy in the drive?  Can you successfully boot with a Windows install disk in the CD drive?

Paul

---

### Post by CCCody on 2006-07-12
Okay.

1. I have No floppy drive, they are out-of-date peices of crap, imo. It's called USB. 

2. My ROM drive is labeled E:

3. And with CD Burner XP, why wouldn't I make it bootable?

4. Also with CD Burner XP, is it imparitive that I check finalize disk because in order for me to do that (get to that check box) I have to select, "burn disk" is there another way to check the box without having to cancel the burn before it starts?

5. Thanks, for all the help you guys are really great. 8)

---

### Post by GuitarHero on 2006-07-12
I dont know if CD burner XP makes bootable data disks.  I have NERO and the way i do is just go into the program and choose make a bootable data disk.  You just download the .iso from the ubuntu site and burn that as a bootable cd.  Then just change your boot device priority in bios to cd rom(like you said you did) and then reboot with the cd in.  It *should* work.

Oh and floppy drives aren't useless.  They're great for diagnostics and quick, small file transfer, if you have no USB thumb drive or internet connection.  Also older computers dont have USB.

---

### Post by Wolki on 2006-07-12
> **CCCody said:**
> 
3. And with CD Burner XP, why wouldn't I make it bootable?


Cause you want to burn a cd image. It already contins everything needed to make it bootable if it's not unpacked. Making a cd bootable with such a burning program means that they put some sort of DOS on it which gets booted, which is not what we want.

You just point the burning program's "Burn image" thing at the complete iso file, and it should know everything it has to do from then on.

> 4. Also with CD Burner XP, is it imparitive that I check finalize disk because in order for me to do that (get to that check box) I have to select, "burn disk" is there another way to check the box without having to cancel the burn before it starts?


TBH, i don't know. It might work without. I used this program on someone else's pc some time ago, iirc there is a n option to stop it from starting to burn automatically, but i forgot where it is :-/

---

### Post by CCCody on 2006-07-12
CD Burner XP does make bootable disks, but I don't understand why I wouldn't make it bootable.. :-k

EDIT: select the, "Make disk bootable" option.

---

### Post by ubuntu27 on 2006-07-12
CCCody: Follow this guide: 

[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by qdvubun on 2006-07-12
do you happen to have NTI CD-DVD maker? it just burn the ISO when you double click on the downloaded file right away.

---

### Post by Frank Golden on 2006-07-12
[http://isorecorder.alexfeinman.com/v2.htm](http://isorecorder.alexfeinman.com/v2.htm) try this tool.
When installed you right click iso and choose "copy image to CD".

---

### Post by T700 on 2006-07-12
> **CCCody said:**
> CD Burner XP does make bootable disks, but I don't understand why I wouldn't make it bootable.. :-k

EDIT: select the, "Make disk bootable" option.

Because you're not making a boot disk.  You're burning an ISO for installation of an OS.  You've got to carefully follow the guides and understand how to use your burner or this isn't going to work.  The other option is to order a disk, but that will take a month or more to arrive.

Paul

---

### Post by fhqwhgads on 2006-07-12
You have nero, use it!

Open Burning ROM, select "recorder" from the toolbar, select "burn image", find the ISO, click burn. That's from memory, but I'm pretty sure it's correct.

That's it. Don't make it harder than it must be,

---

### Post by Frank Golden on 2006-07-13
> **fhqwhgads said:**
> You have nero, use it!

Open Burning ROM, select "recorder" from the toolbar, select "burn image", find the ISO, click burn. That's from memory, but I'm pretty sure it's correct.

That's it. Don't make it harder than it must be,
That is you best bet if you have Nero. You got a good memory fhqwhgads.
On my install I have to close the compilation wizard that opens
with Nero burning rom before I can access the toolbar.

Update: just figured out how to open Nero burning rom without 
the "new compilation" Wizard opening too.

---

### Post by feathers on 2006-07-13
> **CCCody said:**
> CD Burner XP does make bootable disks, but I don't understand why I wouldn't make it bootable.. :-k

EDIT: select the, "Make disk bootable" option.

It has already been answered: The iso file is an image of the disk, it therefore contains everything that has to be put on the CD. The image contains all the boot information that is needed. If you burn a bootable CD, you boot into something like DOS and then you have the iso image as a file on the CD. This will not work. Unless you do as the others told you and just burn the image to the CD, you will not successfully install Ubuntu.

---

### Post by Coburn on 2006-12-28
I had this same problem when I tried to install Ubuntu the first time.

I couldn't get any of the standard XP programs (Nero, etc.) to burn an ISO image correctly to my disk. ](*,)  It usually burned as a folder with the ISO image or files in it.

What I ended up doing was using a little free program called Silent Night Microburner.   It is straightforward and has many features.  I always use it when I have to burn CD's on Windows, because it does not have an idiotwall.  It does not lock you out of options.

Silent Night (probably named after the Christmas carol, which was first performed with guitar accompaniment because the organ bellows got chewed by a mouse) also fits on one floppy.  When I got Breezy, I downloaded on my neighbor's wireless, and ran SNM from floppy to make myself a useable disk.  In fact, it worked better for me than the Ubuntu ShipIt CD.

Hope this info helps somebody out there 8)

---

