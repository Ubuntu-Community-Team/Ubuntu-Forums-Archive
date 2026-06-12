---
title: "System good enough for Ubuntu?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by starcraft2fan on 2007-06-11
Hello,

I am new to Ubuntu, though I have a bit of experience in the user interface level in Gnome before (~1-2yrs back)

I would like to ask if the following system is good enough to run Ubuntu in a small office environment with only symmetric DSL access to the internet (direct connection; no network)

AMD Athlon 64 X2 3600+
MSI K9N6SGM with onboard Geforce 6100
Kingston DDR2-667 1Gb RAM
Seagate 80Gb SATA II hard disk
no graphics card
CD-ROM
CD Burner
Cooler Master 380W
Cooler Master 340 Casing

Note: printer is HP Deskjet 840

The computer is (primarily) used to access a dBase III (or IV) program which used to be run on WinME, as well as the usual Office programs, to surf the net and SMTP email and to burn CDs as well.

I can only think of the following "conversions":
OpenOffice to replace Office 2000
Thunderbird to replace Outlook

I do not have any experience in database programs in linux. I only have heard that OpenOffice Base component is for databases, much like Microsoft Access. Can this read the dBase III database? How do I migrate the data to the new program? How about MySQL?

I need help on programs which can do the tasks previously mentioned, as well as whether the new computer mentioned above is sufficient to run Ubuntu (7.04) for at least the next few years without problems.

Thanks in advance!

---

### Post by mlentink on 2007-06-11
Your system looks ok to me.

If you want that database to perform, I'd look at converting it to MySQL rather than OpenOffice Base. MySQL is more scaleable as well. Be prepared to learn some new things, but the rewards will be there. Your could think about rewriting your database app to a web-application ( with PHP).

Edit: If you're no experienced with databases, you might be in for a steep learning curve.  What was used to write your current app? Or are you using the database with dBase commands?
Data-conversion is almost always possible. You might check if your current database allows for CSV export of the tables

---

### Post by Kobalt on 2007-06-11
You will get very very good performances on such a machine using Ubuntu. 

Welcome to Ubuntu :) !

---

### Post by Tomosaur on 2007-06-11
By 'no graphics card', do you mean 'integrated graphics card'? This could be a problem for you - you would do well to find out what is actually driving your graphics capabilities, and checking whether that works on Linux. Everything else looks fine.

The great thing about Ubuntu is that you can try it without installing it. Download the LiveCD, boot from it, and see if everything works. It will run very slowly since it's running from the CD, but it will let you test your hardware and get a feel for Ubuntu. If it works in the LiveCD, it'll work once it's installed.

---

### Post by starcraft2fan on 2007-06-11
WOW people... this is absolutely amazingly one of the quickest responses I've ever seen to a thread in a linux beginner's forum.

To add on to my 1st post,
no graphics card = not needed since there is onboard 6100 and it is an office computer; not meant for games.
1Gb ram = 1 stick only to (potentially) expand to 2Gb and beyond next time when prices fall even more; 1 stick of 1Gb costs less than 2 sticks of 512MB, and the performance hit is not that significant I think.

@mlentink:
What's the meaning of a "scaleable" base? I know I'm in for some learning, but the database was brought in from an old Pentium in need of upgrading, and when it loads, it's in some "oldish" MS-DOS style program called dBase III / IV. You see, the database format the company uses is old but the details inside are not; it's just in a very bad need of upgrading since the Pentium can die anytime, and WinME is not the safest OS out there. We are currently evaulating open source software, to save hundreds of Redmond's licensing. (It's a fact)

@Kobalt:
Thanks! I'm interested to know more about Ubuntu. I've touched Gentoo a longgggggg time back as well, come to think of it. But that was 2-3yrs ago, and that's where my Gnome expertise came from. And Mr Shuttleworth apparently has done wonders for this Ubuntu Linux as well, and even Mr Dell. Things now are so much different. And I'm new to apt-get, though Portage has it's own merits as well.

@Tomosaur:
Yes, I meant integrated graphics. And sorry, I don't have the machine with me yet; it's still in proposal stages, with all the costs factored in. Yes, Ubuntu is free but it requires migration techniques not meant for the average soul. (Though Microsoft Access needs migration as well, but they have support built into the licensing, only that it costs way too much, much more than a nuclear missile. =) )

@The rest of the Ubuntu community:
I am amazed by the wonderful treatment us newcomers are shown, keep it up!

---

### Post by thevenerablez on 2007-06-11
I have experienced the same instant help as a newcomer. I just wanted to echo and say thanks!\

_zach

---

### Post by starcraft2fan on 2007-06-11
Can I use DOSBox to emulate dBase and run it in linux to avoid migration horror instead?

Or does dBase work in XP, might even save all the trouble.

What's the most hassle free way to using that old dBase program and its database on new hardware, like the system mentioned above?

---

