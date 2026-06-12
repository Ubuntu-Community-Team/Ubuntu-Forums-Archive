---
title: "On boot up."
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Ludwig7666 on 2007-01-01
long time no type ubuntu peeps. :P

I was just wondering this. I have been using ubuntu for about 4-5 months now but I always seen this certain screen. It shows the grub 1.5 something something, then loading up the linux kernal screen. It would normaly show that some kind of media isn't being found. I for some reason didn't think much about that. Well now i have linux on a 120 Sata HDD and windows on a Uata Hdd. I don't have a multi boot screen, so I just hit F8 on startup then pic the drive (OS) I want to work. Both work just fine it seems. Windows and Ubuntu. Anyways. Just lately I've noticed another ubuntu bootup screen. It shows something about IDE something error, then it shows the same line again. Some other failors then ubuntu starts up. 

One thing I noticed is that ubuntu can't read the Uata HDD and windows can't seem to find the Sata HDD. I might of placed Sata in the Sata 2 on the motherboard. Uata is setup on Secondary I believe to. Does Sata realy have to be master on Sata 1? or it don't matter cause there is only 1 Sata. Also I dunno if I switch it would I need to reformat Ubuntu? Cause of HDD changes.

Dunno. Kinda consiter myself as a newb to computers. Only a 4ish years but a gamer so didn't do much of actuall learning of the computer.

Hopefully that's enough infomation?

---

### Post by Ludwig7666 on 2007-01-01
ohh almost forgot. When starting up my computer Ubuntu starts up without going through the F8 function. 

Dunno if that's any good info. :P

---

### Post by Ludwig7666 on 2007-01-01
*Bump* 
another way of puting it.


So what startup screens should I be seeing only?

---

### Post by Ludwig7666 on 2007-01-02
*Bump* Again

9 hours went by and no one posted. :(

---

### Post by MkfIbK7a on 2007-01-02
we are sorry for not posting 
just can you clarify your question a little bit?

---

### Post by riven0 on 2007-01-02
> **Ludwig7666 said:**
> ohh almost forgot. When starting up my computer Ubuntu starts up without going through the F8 function. 

Dunno if that's any good info. :P

Do you mean Ubuntu boots up without having to hit escape and make your kernel selection? This is quite normal. 

As for Ubuntu not detecting the HDD. I'm not sure; can you see it when you run this command in the terminal?:

> fdisk -l

---

### Post by Ludwig7666 on 2007-01-02
Ubuntu starts up as defualt OS. if I want windows to boot up then just after the Asus AI screen I just use the F8 to open the boot HDD choice. Or whatever it's called. 

for the fdisk -l. It's finding my exturnal HDD. 80GB HDD. I tried just fdisk and it came up with first IDE and third SCSI? Shouldn't there be something in there, a second maybe?

two 120GB and 1 80GB HDD for this computer.
Hated the duel booting on one HDD, so I went with two HDD's. Thought it would be easier. Plus I am running out of room :P
Lately torrent, torrent, torrentsssss....

---

### Post by Ludwig7666 on 2007-01-02
ohh and thanks for posting. at least it's something. And yes people have a hard time understanding me. Or maybe I have a hard time understanding people's way of thinking.

---

### Post by riven0 on 2007-01-02
If you have both hd's plugged into the motherboard, fdisk -l should list both, (and also the external, but we won't worry about that). 
Have you checked the jumper settings on the hd's? If I remember correctly, Ubuntu should be the primary and XP should be the secondary. 

Anyone else remember? I haven't done this in so long.

---

### Post by Sef on 2007-01-02
> If I remember correctly, Ubuntu should be the primary and XP should be the secondary.

Anyone else remember? I haven't done this in so long.

Vice-versa.  XP needs to be the primary, so Ubuntu has to be the secondary.

---

### Post by Malta paul on 2007-01-02
As you have both a SATA and a IDE hard disk like I have. I would check that your BIOS setting are correct,
it took me a little experimenting before I got it to work OK.

Enter your BIOS on boot up, and check your settings in:
'Standard COMOS Features'
'Advance BIOS Features'
'Integrated Peripherals'  (IDE config.)

Your BIOS may be different from above, but the principle is the same.

Then when in Ubuntu check Fdisk -l as 'riven0' said. and post your findings here.

Good luck, hope this is of some help :)

---

