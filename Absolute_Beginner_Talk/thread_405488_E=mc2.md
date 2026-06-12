---
title: "E=mc2"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-04-09
I understand that being able to copy a document to a floppy disk is one of the more elementary functions that a computer is SUPPOSED to be able to perform without the user being an Alfred Einstein. Right?

Well.......mine does not!

And just in case you might be interested, I get this error box:

 Could not mount Floppy Drive
Unable to mount the floppy drive. There is probably no floppy in the drive.:
mount: /dev/fd0 is not a valid block device

Now I know that there are many of you Einsteins online right now, and you're probably very busy thinking, BUT....do you suppose you could put the pipe down a second and give me a theory on this?

---

### Post by ffxr on 2007-04-09
didnt FDDs' die out round about the same time as Mr. Einstein..?

---

### Post by aktiwers on 2007-04-09
Maybe the filesystem on the disc is created on a Microsoft computer and somehow is not supported by Linux? I dont know..

Let me ask you this..  what filesystem is on the floppy disc?

---

### Post by Maestro23 on 2007-04-09
[https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone?highlight=%28floppy%29](https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone?highlight=%28floppy%29)

---

### Post by rgp-02 on 2007-04-09
thanks Maestro23 

i just did that exhausting procedure and i still get the same error box:

Could not mount Floppy Drive
Unable to mount the floppy drive. There is probably no floppy in the drive.:
mount: /dev/fd0 is not a valid block device

ANYBODY ELSE WANT TO TAKE A /fstab AT THIS?

---

### Post by ComplexNumber on 2007-04-09
does any light show up on the floppy drive when you try to access it?

---

### Post by rgp-02 on 2007-04-09
YES!

i open document........ click:   file>save as>floppy drive    and light goes on for a second.

kinda like “The lights are on but nobody's home”.

---

### Post by ComplexNumber on 2007-04-09
hmmm ok. sorry that you're having these problems with the floppy. it looks like i may be able to help afterall - i've just clicked on "floppy" after double clicking on the Computer icon on my desktop, and it gives the following:
> mount: /dev/ is not a block device:D

and i know why, sort of. when you double click the Computer icon, does it give you more than 1 floppy device? i have "floppy" and "floppy1".

---

### Post by rgp-02 on 2007-04-09
JUST ONE

i click PLACES > COMPUTER and i find only one floppy drive alongside CD-RW drive and file system.

---

### Post by ComplexNumber on 2007-04-09
this is what i have for the entry for my floppy in fstab:
[I]/dev/ /media/floppy0 auto rw,user,noauto 0 0

[/I]
what does your fstab give?


also, can you go to /media and tell me what the names are of the "floppy" directories in there? i have the following:

floppy (link)
floppy0
floppy-1

---

### Post by rgp-02 on 2007-04-09
thank you ComplexNumber

but i have to get to bed now

getting late here in CT

will check in again tomorrow

---

### Post by Meir on 2007-04-09
Is that the type of error that would show up if the write protect swicth is flipped on the disk?
[IMG]http://physinfo.ulb.ac.be/cit_courseware/hf100/images/floppy1.jpg[/IMG]

---

### Post by rgp-02 on 2007-04-10
thank you for responding (all yez)

i never even knew about those little switch-ees, so i tried them in both the locked & unlocked positions and get the same error message:

Could not mount Floppy Drive
Unable to mount the floppy drive. There is probably no floppy in the drive.:
mount: /dev/fd0 is not a valid block device

ALSO, when there is no floppy in drive, and i try to access it, the drive lights up for a second and makes the same little grunt that it does when a floppy IS in the drive (if that means anything).


entry for floppy fstab:
/dev/fd0           /media/floppy0  auto    rw,user,noauto,fmask=111,dmask=000  0       0

/media:
floppy (link)
floppy0

---

### Post by rgp-02 on 2007-04-10
HEY!

What happened to all my support?

C,mon now!

Surely one of you geniuses can handle a simple problem like this. This would be a cakewalk for you!

Let's wake up and get with the program!

Give ole Alfred Einstein something to rejoice over!

---

### Post by maddog39 on 2007-04-10
Well the graphical interface for mounting FDDs has a history of not working (at least in my case). My guess is probably a corrupted file system on the disk. The last resort is probably to do (try) it manually from the command line.

Go to: Applications > Accessories > Terminal  and type the following 2 commands:
```

sudo mkdir -p /mnt/floppy
sudo mount -t vfat /dev/fd0 /mnt/floppy

```Then if that works, you  will probably be able to use it as normal. Go ahead and try it.

---

### Post by l951b951 on 2007-04-10
> **rgp-02 said:**
> HEY!

What happened to all my support?

C,mon now!

Surely one of you geniuses can handle a simple problem like this. This would be a cakewalk for you!

Let's wake up and get with the program!

Give ole Alfred Einstein something to rejoice over!


I swear it's Albert, but anyway.  One question no one has asked:  have you tested the floppy in another device?  Bad disks can put you in a world of hurt.

---

### Post by rgp-02 on 2007-04-10
thanks for your responses, people.

tried:

sudo mkdir -p /mnt/floppy
sudo mount -t vfat /dev/fd0 /mnt/floppy

get:

mount: /dev/fd0 is not a valid block device


floppy disks work in my other computer.
 

anyway, gotta say nitey nite now
check in tomorrow.

---

### Post by ComplexNumber on 2007-04-10
what happens when you set the floppy entry in fstab to either of the following:
[I]/dev/ /media/floppy0 auto rw,user,noauto 0 0

[/I]*dev/fd0 /media/floppy0 auto rw,user,noauto 0 0*

---

### Post by rgp-02 on 2007-04-11
thank you ComplexNumber and all of you others for being so kind. i have tried the other combos in /fstab and get the same results, so i've decided to put this problem on hold for a while until i am discharged from the mental hospital. ok....time for sedatives now......see y'all when i get out..........yeeeeeehaaaaaaa!

---

