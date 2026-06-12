---
title: "DigiKam (photo management)"
date: 2007-05-19
forum: Art &amp; Design
---

### Post by borahshadow on 2007-05-19
ok I was looking for good photo management and saw the normal digikam/f-spot/gthumb/etc

I heard a lot of stuff about digikam and f-spot needing to import all the photos into their own database (what a waste of disk space to have 2 copies when you already have them all organised)

In winxp I did/do it very simply. organize the pictures into folders, view with thumbnails in my computer and the super basic windows pic and fax viewer print with photo printing wizard/gimp

I am using kde and I can view files fine with konqueror and such but I thought there probably was a better way
as for printing I could not find any way to print well (besides gimp) I wanted somekind of wizard 

I always thought winxp's was too simple but it was the best I could find
 
I decided to look at digikam besides the things I had heard

come to find out I actually like it alot I just set it's database up to be my picture folder and every folder is an album/ sub album no double copies it will read my directory structure and not put it in some database yay (correct me if I am wrong I have not tried it on my entire collection for time and safety sake)

but edgy it only has version .8.2 I was looking and version .9.x looks lots better (why not update the repos:confused:)

so I thought I've compiled plenty of things I'll just compile the newest or at least .9.1
well HOLY COW I don't think I have had a harder time compiling anything in my life.

I've typed ./configure make and sudo makeinstall so many times I want to hide any time I see those commands (J.K)

so I went through and installed the dependency's (or so I thought) and I got configure to give me the ok but it would always crash with make

I tried 9.2-beta1(It claims to be production ready despite the name) and same thing 
I tried manually compiling newer versions of some of the dependency's some of those with their own problems still no good 

I found this [http://ubuntuforums.org/showthread.php?t=322165&highlight=digikam+packages]("http://ubuntuforums.org/showthread.php?t=322165&highlight=digikam+packages")
(I am running 64bit)

but the first set of packages are broken links
The trick to delete the /usr/include/kde/digikam folder didn't work because that folder didn't exist for me to remove lol

I tried the packages at the end on page 3 but the dependency's that were flagged on those were way higher then the ones that digikam said 
but I thought it won't hurt to have newer versions but I had all the most recent from the repos and most of the most recent compiled from source but it wanted even the newest kdelibs and I'm not going to try to basically compile kde from source which is almost what it wanted

I have tried many things that I'm not going to go into detail here about because they all didn't work and I tried too many things to list them all here

as a side note I also could not get the latest kipi plugins to compile

so I finally decided to just bag it and reinstall .8.2 from synaptic but I would prefer to have .9 if anyone could help

ps I don't want to run make again just to copy exactly where it chokes but if I remember right it chokes around exiv2 or something of which I have compiled the newest from source for

I looked at f-spot but it does not seem to be able to read my folders like digikam

as for printing I saw the kipi plugin for printing which is almost EXACTLY what I want it is almost like the one in winxp but with some more options and it even allows me to export it to gimp or a .jpg for even more tweaking if I want PERFECT it thank goodness does run in the 8.2 version of digikam
I'm sure I could use some of the other newest kipiplugins but I could not get those to compile ether

the only thing I wish digikam could do would be to look in two or more places for the database so I could have it look at the family's pictures and mine (I'll probably just put my pictures in the family folder though)

If anybody can correct me abput digikam if it won't do what I think it does please do
and if anybody could help me get the newest version installed I would be very happy
(I was tempted to force install those packages with the high dependencys due to mine being very close should I try it if so what is the exact command dpkg something)

Ps sorry if this is hard to read/follow/understand I tend to not be the best with spelling and grammar

---

### Post by bailout on 2007-05-20
Lokk at this page and simply add the repos to your source list. It has packaged 9.1 for edgy and digikam and kipi plugins.

[http://www.digikam.org/?q=download/binary/](http://www.digikam.org/?q=download/binary/)

---

### Post by borahshadow on 2007-05-20
is that 64bit? I can't see anywhere I'm guessing it is 32 like all the repositories I have seen would it be a problem to install the 32bit version?

EDIT I just looked again and those are 32Bit I would prefer 64 even if the 32 bit would work

---

### Post by bailout on 2007-05-21
Sorry, quickly scanned your post and missed the 64 bit. In that case you are probably best joining the digikam mailing list ( see digikam site for details) and asking there. There are often posts about compiling latest test versions and the developers are very active there.

---

