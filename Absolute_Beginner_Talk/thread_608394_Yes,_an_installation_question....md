---
title: "Yes, an installation question..."
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Mattaus on 2007-11-09
First up I aplogize whole heartedly if im posting something that has no doubt been covered a gizillion times before.

I am current hard-core windows user and due to some exposure at my new work I have decided to give ubuntu a try. So I downloaded 7.10 about 2 days ago, burnt the iso to a disc as a complete iamge and away I went.

My aim is to install ubuntu to an external HDD and run it along side Vista. (ie, if I want ubuntu I tell bios to boot from an external HDD first.) Everythign goes great and it opens up a live session. I click on the install icon on the desktop and it goes through the motions asking me for details what drive etc etc. I select the drive marked as external and it gets going....except it starts installing but stays at 15% for hours simply saying "scanning file systems". It never goes ANYWHERE.

Im running Vista 64-bit on an intel Q6600 (which shouldnt make any difference!). I have 3 internal HDD's and one external WD Mybook 320G HDD. The external drive is what im trying to install to. I tried unplugging all the internal drives and doing it but I get the same thing happening.

If worse comes to worst i'll install ubuntu to one of the internal drives to see if it works but its means shifting 300G off that onto the external drive so id rather not! Also I wanted to be able to take the ubuntu HDD with me when I go places so the internal drive may make that a little hard.

Again, sorry for treading a beaten path and if this is in the wrong place it was an accident...I am a ubuntu noobie though :confused:


Ive attached a screenie of where it stops at. Hope that helps!

---

### Post by overdrank on 2007-11-10
Hi and welcome I would check the cd for errors and Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rsambuca on 2007-11-10
Did you run the CD integrity check first?

---

### Post by richiewrt on 2007-11-10
Another thing you need to watch out for, since I made this mistake, make sure that grub gets installed to an internal HD and not the external HD or you wont be able to boot into anything.

---

### Post by Mattaus on 2007-11-10
Ok, I did check the CD for errors and it came up fine. Havnt done a check sum though so I guess ill do that next.

As for the grub thing I have a) no idea what that is and b) the instructions mention muckigna round with the grub, but only AFTER its installed...and that is the problem!

I'll do the check sum and get back to. Thanks for the help thus far.

---

### Post by Mattaus on 2007-11-10
OK, the checksum worked out fine. So the iso is OK.

What the then? Spose my next bet is to try the internal drive...though I may wait and talk to the dude from work unless you guys have other ideas? I got all day sunday to try stuff I guess.

Damn :(

---

### Post by Mattaus on 2007-11-11
Ok,

I'm at work now and I fired the whole thing up on a PC currently running fedora.

I brought my external HDD and tried installing ubuntu 7.10 exactly as I did at home. I got the same problem.

So I scratched around and found a copy of ubuntu 6.06 that I KNOW works fine and tried installing that the same way. this time it didnt skip straight to 15%, however I think it got the exact same error as the 7.10 install (6.06 seems to display more information than 7.10)

The picture is attached...I have no idea where to go from here. Its the same eroor on 2 different machines. The only constant is the external drive, and it sure aint broken. Maybe it cant be done to that drive? Or maybe I need to do somethign to be able to install to the external drive?

---

