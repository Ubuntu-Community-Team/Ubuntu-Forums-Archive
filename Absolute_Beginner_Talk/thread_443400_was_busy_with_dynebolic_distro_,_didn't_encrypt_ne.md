---
title: "was busy with dynebolic distro , didn't encrypt nest , had intruder  ,"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-14
hi, i kind of new to linux, learning fast

i was checking out dynebolic distro, cause of a low-latency kernel that enhances recording , and it does , for anybody who is interested,


but i had to make a nest and encrypt it , i didn't (dumb move)


when i suddenly decided to install it on the hdd , seems like and intruder messed-up the whole proces 

can't get into any accouts i made , there not in the home directory where they're suppose to be

and i do see the intruder login name 

i wanted to start all over , but can't seem to delete any of the two 'nests' (nesting is a way so that the boot cd recognises where you saved your work) 

one is encrypted , but i still don't trust it

want a clean start , now i know how to do the rest, but can't delete nests :confused:

---

### Post by MrKlean on 2007-05-14
It's hard to believe you had an intruder that quickly, but for safeties sake... I wouls format the drive.. erasing everything.. and start over .. that's just me though ; )

---

### Post by Cypher on 2007-05-14
I think you're asking about specific things about the Dyne:Bolic distro and you might get better help from any forums dedicated to that distro. This is for Ubuntu which doesn't using "Nesting" and other techniques.

(I had to actually look up the site and a read a bit about that distro before responding, sounds like an interesting distro)..

---

### Post by firedancer on 2007-05-14
i tried reformatting the two patitions but , 

but was unsuccesful somehow 

maybe it's better in the terminal then with one of the partitioning tools

maybe i better use the gparted cd i made , see if that will help and then start all over , it was going alrite until this "taschino" intruded am got hold of one of the nests

i tried dynebolic forums but came across a weird one !


i 'll try using the gparted cd then ! 

anybody else has suggestions let me know, cause this choice takes too long  !

intruder crashed my xp boot section a week ago with norton (imagine):(

---

### Post by justin whitaker on 2007-05-14
> **firedancer said:**
> i tried reformatting the two patitions but , 

but was unsuccesful somehow 

maybe it's better in the terminal then with one of the partitioning tools

maybe i better use the gparted cd i made , see if that will help and then start all over , it was going alrite until this "taschino" intruded am got hold of one of the nests

i tried dynebolic forums but came across a weird one !


i 'll try using the gparted cd then ! 

anybody else has suggestions let me know, cause this choice takes too long  !

intruder crashed my xp boot section a week ago with norton (imagine):(

Use this:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It boots the system, and completely wipes the drive..you will need to reformat from the ground up, but it's worth it for piece of mind.

---

### Post by esoterica on 2007-05-14
Open up your case so you can physically see your Hard Drive, don't trust any applications to correctly report it for you!

Once you know who made your hard drive and what exact model number drive it is do a web search to find that specific manufacturers web site. All hard drive manufacturers have utilities you can download for free on their web sites for their specific drives that will let you do what's called zero fill on the hard drive.

DO NOT USE some generic program to do this!

DO NOT USE some utility for a different model hard drive than what you actually have!

Find the specific utility made for your exact hard drive model, there will be one, if you don't you could make your hard drive so it never works again, no matter what you do to try and fix it. I CAN NOT STRESS THIS ENOUGH.

Your probably going to find that the utility may be in a floppy specific ISO or image file. Since most modern computers no longer even have floppy drives every single manufacturer I've ever seen also has info on how you can place the utilities onto a bootable CD.

Once you boot to the CD it's very simple to use the utilities, some mistakingly call this "Low Level Formatting" the hard drive, it's more often now refered to as "Zero Fill" on the hard drive so find the utility option that either Zero Fills or Low Level Formats the drive and run it.

Make sure your running it on the correct drive incase you have more than one Hard Drive installed, for safety I usually unplug additional hard drives just to be sure.

Depending on the size of your drive it could take well over an hour to completely zero fill the entire drive, just let it run and don't mess with it or interrupt it while running.

This will completely wipe the drive 100% clean and make it as fresh as the day it was first purchased, a normal format on a drive by any Operating System be it Linux, Windows or anything else will not do this for you.

I've been using these utilities on hundreds of different drives for many many years now and never had a problem. It's something I always do if I plan to wipe a drive and do a new install anyhow because it completely removes all the disk information like Master Boot records and everything else a normal formatting will not do for you. It's always a good idea to do this since there are some virus files that can write to portions of your drive like the master boot record which would otherwise not be removed by just reformatting the hard drive by traditional means. "Junkie" is one such virus I can think of off the top of my head just as an example.

The hardest part in doing all of this for beginners is understanding how to make the CD bootable or write the ISO or image file properly to the CD, then setting the BIOS to boot to the CD instead of the hard drive. There's plenty of good information out there on how to do all of this if a person searches and it's very good info every single person should know how to do anyhow. The good part is if you can't figure out how to boot to the utilities then they just won't work at all so your safe.

---

### Post by aldreis on 2007-05-14
> **firedancer said:**
> it was going alrite until this "taschino" intruded am got hold of one of the nests

It seems that taschino is just the name of the software doing this 'nesting' thing.

> if the problem comes while doing the nesting, you should have a look in /var/log/setup/nidifica.log which is the log of *"taschino", the software doing the nesting.*

Found [here](http://lab.dyne.org/Nesting).

---

### Post by firedancer on 2007-05-15
well thnx for the info & insight 


well i reformatted the hdd and made three new partitions , but Gparted doesn't let me add the mountpoints and now i don't have acces to them , i know there is a code for , i did something like this already but forgot


well i was kind of paranoia, because my dual xp boot was crashed the day after i noticed i had a spyware that norton wasn't able to detect nor remove, this was recent (10 days ago)

so now i have a total ubuntu system , got a friend of mine hooked on it to , so now we share some info too

esoterica i know how to make a bootable disk , installed ubuntu with this proces (have been busy intensively)

but i will still check your advise, Q: what's the best way to find out wether you're somebody's target. i have this system getting to know it enjoying, but can't loose info. i'm a graduate student working on two final projects now ! 

one of my hdd already is broken ! maybe hardware or something else, so now i'm left with two of 40 GB


well the dyne distro installed it but now i'm not so happy, cause now it doesn't detect the soundcard which it did the first time , which i use for recording 


so thnx fellow ubuntubu's :popcorn:

---

### Post by esoterica on 2007-05-17
> 
esoterica i know how to make a bootable disk , installed ubuntu with this proces


Wishful thinking on your part, it's not the same thing, you installed Ubuntu from an ISO file that was already made bootable for you. There's a big difference in actually putting files on a CD and then making that CD bootable yourself.

---

### Post by firedancer on 2007-05-17
ooh !


pardon me 


good , letting me know there is a difference , i follow you :KS

---

