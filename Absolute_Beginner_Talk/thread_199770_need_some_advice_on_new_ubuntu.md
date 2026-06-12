---
title: "need some advice on new ubuntu"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by mrgreaper on 2006-06-19
ok im moving from suse 10 to ubuntu on the advice of several forums but ....
well im a noob at all this and would like to know a few things
i used suse for ;
webpages hosted over my local area network and the internet (php pages)
file storage for my local machines (using samba to connect it to my network)
i use severay scripts (#!/bin/sh is how they start if that helps)
counterstrike source server
vnc (it has no monitier so this is extremely important ..hell there all important)

those were the main things i really need to know if i can do them with ubuntu latest desktop release i use a hardware fire wall so want to open all the ports on ubuntu by default but would like to retain the abilitie to close specific prots as my hardware fire wall cant do that (a link to a tutorial on closing ports in complete noobie language would be useful too please)

thank you in advance i shant begin installing for another couple of hours as im backing data up at mo i`m kinda figuring it will do all the above by default as suse 10 does but if it cant please please please warn me as i`ll be checking here before i install (a nod would be good as well if it does do all that)

---

### Post by localzuk on 2006-06-19
All those things will run fine.

Ubuntu has no ports open by default. They are opened when applications are installed which use them.

---

### Post by mrgreaper on 2006-06-19
thank you fir prompt reply 
i was a little worried i`d have to go and find the apps and install them etc

how do i open ports manualy ? could you point me in the direction of an idiot proof tutorial please

---

### Post by localzuk on 2006-06-19
What do you mean open ports manually?

---

### Post by mrgreaper on 2006-06-19
well it sure wasnt easy to install 
the first bit that asls you what language you want ...
well i kept clicking english
nothing hapened
i hit return
nothing
grrrrrrrrrrrrrrrrrrr
finaly i clicked right mouse and choose move
turns out th install window is bigger then the screen!!!!! 
i looked at resulotion and its 640x 480 and cant seem to be changed
now i managed to guess my way through the first few panels and its now creating a ext3 partition
but seems silly to make the install gui bigger then the screen i hope i aint done ought wrong in install 
i`m assuming it will leave the primary windows partition alone by default
just wish i could of read all the options

---

### Post by mrgreaper on 2006-06-19
by open ports manually 
well my counterstrike source server needs ports open so i want to open them 
my router has an in built fire wall and i have to open the ports there and direct them to the correct pc all thats done but i`ll need to open them on linux pc as well 
> Protocol	Port Range	Translate To ...	Trigger Protocol	Trigger Port	



UDP	1200 - 1200	1200 - 1200	-	-


UDP	27000 - 27015	27000 - 27015	-	-


TCP	27030 - 27039	27030 - 27039	-	-


Any	27500 - 27500	27500 - 27500	-	-

taken from my router

im now wiping this from my system 

@localzuk 
it doesnt do any of what i need it to do out of the box no apache no mysql, thats not a flame or me being nasty perhaps the version you are using does include those at install

i have found this to be most user unfriendly 
[http://ubuntuforums.org/showthread.php?t=199916](http://ubuntuforums.org/showthread.php?t=199916) explains my reasons for leaving to go back to suse 10 i should of guessed really when i realised this is only one cd that it couldnt posibly have the apps i needed (i assumed it would stream them of the net but bah)

---

### Post by localzuk on 2006-06-19
I think you must be having issues with the disc. Try selecting a resolution at startup (there is an option at the initial boot menu to do this).

The ports will open themselves when an application uses them - they aren't open, but aren't being blocked from use.

---

### Post by uzi09 on 2006-06-19
about ports:
they'll open themselves, just make sure that if you're running any firewalls (hardware or software wise) you open the ports in them.
you router should probably keep all the current settings, so that shouldn't be a problem.
ubuntu doesn't have a built in firewall, so it shouldn't be a problem either.

about vnc:
it's built into ubuntu, just enable it from the systems menu :D

about install:
that's really weird, i've never heard of that happening. sorry.

in general:
welcome to ubuntu...well sort of (still got that install going ;))
the best thing you'll see about ubuntu is its community. you'll get fast replies from very helpful people. feel free to post up any questions you're having....

cheers
uzi

---

