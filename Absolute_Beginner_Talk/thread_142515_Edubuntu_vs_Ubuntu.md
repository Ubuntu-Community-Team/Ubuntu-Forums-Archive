---
title: "Edubuntu vs Ubuntu"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-03-10
Can someone explain the difference between these two operating systems?

Are they the same but differ only in style and presentation? i.e. edubuntu having a kiddies look with perhaps extra educational programs. What otherwise are the differences?

Just burned an iso image but it won't boot. Don't know what that's about 

cheers,

sophtpaw

---

### Post by m.musashi on 2006-03-10
There seem to be a fair amount of problems with getting CDs to boot. The standard questions seem to be:

1. Did you burn an ISO (you need soft that will do this and not all will). Making a data disk won't work.
2. Did you burn too fast? Subjective yes but slower seems to be better?
3. Did you verify the download by checking the md5 sum?

As for edubuntu vs ubuntu, I installed ubuntu and then added the edubuntu-desktop (sudo apt-get install edubuntu-desktop). I didn't notice much different except I now have a bunch of education related apps - mostly games. A splash screen might have also changed but it didn't change the wallpaper. My kids had already set their own so maybe that's why. I kind of expected the standard edubuntu wallpaper.

If there are other differences I couldn't tell.

---

### Post by Brunellus on 2006-03-10
[QUOTE=m.musashi]There seem to be a fair amount of problems with getting CDs to boot. The standard questions seem to be:

1. Did you burn an ISO (you need soft that will do this and not all will). Making a data disk won't work.
2. Did you burn too fast? Subjective yes but slower seems to be better?
3. Did you verify the download by checking the md5 sum?

As for edubuntu vs ubuntu, I installed ubuntu and then added the edubuntu-desktop (sudo apt-get install edubuntu-desktop). I didn't notice much different except I now have a bunch of education related apps - mostly games. A splash screen might have also changed but it didn't change the wallpaper. My kids had already set their own so maybe that's why. I kind of expected the standard edubuntu wallpaper.

If there are other differences I couldn't tell.[/QUOTE]
edubuntu also seems to be the locus for most of the LTSP/thin-client work in Ubuntu.

---

### Post by sophtpaw on 2006-03-10
thx musashi, 

for the feedback and sharing your experience. Sounds like Edubuntu is better then - the normal ubuntu with extra games or educational apps thrown in. 

well, yes, i burned the .iso image on k3b and yes, made sure it wasn't data but '.iso image' set. I have done this successfully in the past, so i don't see what is different this time. Md5 sum was checked iwth  positive result.

I'm downloading it again, so lets see
--

sophtpaw

---

### Post by sophtpaw on 2006-03-10
Ltsp/thin client???

can you briefly explain please, if possible, thank you!


--
sophtpaw

---

### Post by m.musashi on 2006-03-10
Didn't mean to ask dumb questions. It's hard to tell a newbie from an expert sometimes. Maybe I should check your beans :). Could just be a bad disk. I've had a few of those.

I can't say if edubuntu is the same as ubuntu with the extra games or not. I installed ubuntu and added the edubuntu desktop. It's possible edubuntu has some stripped out that kids wouldn't need but that's just a guess. It could be the same.

---

### Post by Brunellus on 2006-03-10
[QUOTE=sophtpaw]Ltsp/thin client???

can you briefly explain please, if possible, thank you!


--
sophtpaw[/QUOTE]
essentially, the whole point of the edubuntu project is to enable schools to deploy computer labs very quickly at minimal cost.  Since individual computers are expensive, and there are many old but serviceable computers available, it is possible to put all the programs on a single server and use old, obsolete (possibly donated) machines as "thin clients"--terminals which do no computing on their own except render the graphical environment.

The "thin clients" are upgraded with a bootable network interface (about 40 bucks, US), connected to a network.  Then they boot and run as "heads,' if you like, of a the "body" that is the server.

Advantages:  low cost, tight control.  You buy one new server and use donated machines to get a "new" computer lab for a half dozen to a dozen (or more, depending on the capabilities of the server!) students.

IMO, it's this, not the suite of education-centred software, that makes edubuntu such a big deal.  Other distros have done it in the past (skolelinux) and other projects have moved forward with elements of this (the original LTSP project, k12linux), but edubuntu is really aimed at dropping right in and being usable (eventually) without massive investments in computer training.

---

### Post by m.musashi on 2006-03-10
[QUOTE=Brunellus]edubuntu also seems to be the locus for most of the LTSP/thin-client work in Ubuntu.[/QUOTE]
We will probably go with edubuntu on our thin client experiment but I'm not the network admin so I could get overridden.

I can't say what LTSP actually stands for but the thin client model as I understand it is just using essentially dumb terminals (usually no HD) and boot and run off a server. We are going to reclaim old computers for this but there are thin client boxes. They look like a cable modem and often have no moving parts.

[Here](http://newsvac.newsforge.com/newsvac/06/03/08/0242256.shtml)  is a link someone sent me.

EDIT - oops, too slow.

---

### Post by kittycatsexycat on 2006-03-10
Can i just say that i ordered some ubuntu cd's off the internet from Ubuntu and all 5 of them were bust... they all had a line going across all of them... (i was trying to turn the isle of man linux instead of microsoft) \\:D/

---

### Post by m.musashi on 2006-03-10
[QUOTE=kittycatsexycat]Can i just say that i ordered some ubuntu cd's off the internet from Ubuntu and all 5 of them were bust... they all had a line going across all of them... (i was trying to turn the isle of man linux instead of microsoft) \\:D/[/QUOTE]
And you only needed 5? :)

---

### Post by xXx 0wn3d xXx on 2006-03-10
If your cd won't run (I went through 3 cds) burn it at a slower speed. Like 8x, it should work after that.

---

