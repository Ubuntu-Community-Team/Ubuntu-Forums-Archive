---
title: "Bulding Own .iso file"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-16
Is there anyway that i can build my own .iso file from what i have installed on my computer right now just not any personal files like like the design and also the Theme and setup?

---

### Post by elctb on 2007-11-16
This is the command I use to create iso files:

mkisofs -allow-lowercase -allow-multidot -d -D -J -joliet-long -R -iso-level 4 -relaxed-filenames -o msc.iso ~/iso

msc.iso is the name of the iso file created.
~/iso is a directory containing all the files I want to include in the iso file.

---

### Post by fedex1993 on 2007-11-16
well is there a program that can get everything off of my filesystem like the programs but not the files not or maybe explain more about the command

---

### Post by Sims2789 on 2007-11-16
> **elctb said:**
> This is the command I use to create iso files:

mkisofs -allow-lowercase -allow-multidot -d -D -J -joliet-long -R -iso-level 4 -relaxed-filenames -o msc.iso ~/iso

msc.iso is the name of the iso file created.
~/iso is a directory containing all the files I want to include in the iso file.

Tell us how to do it in the GUI without emptying an existing .iso and adding what we want.

---

### Post by fedex1993 on 2007-11-16
yes because this is noob chat/begginer so we dont need a command that you dont explain about elctb

---

### Post by fedex1993 on 2007-11-16
so is there a gui program out there that i can use to creat my own .iso file?

---

### Post by fedex1993 on 2007-11-16
*bump**bump*

---

### Post by fedex1993 on 2007-11-16
anyone have an ideas at all about a custom iso maker?

---

### Post by mellowd on 2007-11-16
I think its rather rude to blast someone who has tried to help

---

### Post by fedex1993 on 2007-11-16
well i didnt mean to blast him sorry about that elctb i was just frustrated

---

### Post by -grubby on 2007-11-16
and speaking of which you also don't need to bump every 10 minutes. Bump once every 24 hours if you need to

---

### Post by Gazneth on 2007-11-16
The CD/DVD burning program Brasero will do what you need.  Simply drag files into the burning window. Click the burn button, at the next dialog select burn  to file instead of an optical drive.  The program will create an .iso where you want it.

---

### Post by fedex1993 on 2007-11-16
okay so if i want to make a custom .iso file i will half to drag like my whole intire file system to burn to a file now i am confused i just want to make a backup .iso file or a bckup type of file just with programs but none of my personal files.

---

### Post by Gazneth on 2007-11-16
Ok sounds like you need a backup style program.  Simple backup is available in the repositories and it allows you to back up selected files/directories to a location of your choice. It won't save to an .iso though.  I use Grsync myself, it is a front end for the terminal program rsync.  It is a very configurable and powerful utility but dangerous if not configured carefully.

---

### Post by Sims2789 on 2007-11-16
> **fedex1993 said:**
> okay so if i want to make a custom .iso file i will half to drag like my whole intire file system to burn to a file now i am confused i just want to make a backup .iso file or a bckup type of file just with programs but none of my personal files.

Unless you have strange proprietary programs and have lost their CD's there's little point to this, since most of the software you'll probably use is available via Applications -> Add/Remove.

I just thought of an indirect way to make an .iso, but I don't know if it'll easily back up all your programs:

1) Go to Places -> CD/DVD Creator
2) Drag the files you want into it and burn them to a disc.
3) Re-insert the disc, right-click its icon on the desktop, select "Copy Disc" and copy the disc to "File image."

> **fedex1993 said:**
> well i didnt mean to blast him sorry about that elctb i was just frustrated

Many people who give advice on Linux forums are long-time Linux users and don't remember what it's like to be a "normal computer user." Help that is overly complex to us (for example, ones that unnecessarily involve the command line) is easy for a small fraction of computer users, and many of them actually enjoy toying with their systems in this manner. Because their solutions are beyond the skill of normal computer users, we often perceive them as condescending, arrogant, etc. I admit, some are, but most that I've encountered aren't. They're used to talking with other experienced users so they haven't yet figured out how to offer solutions that are useful to people like us.

---

### Post by fedex1993 on 2007-11-16
well something like but i want it like a backup. on a cd that i can install ubuntu with my preconfigured setup that i have on my laptop

---

### Post by Gazneth on 2007-11-16
What you are describing sounds a little beyond my abilities.  I'm not sure if simply copying  the OS to another machine would work. Some potential problems could be GRUB, video drivers, sound.  A custom built install cd or dvd seems more like what you want, but they sound quite difficult to make.

---

### Post by compmodder26 on 2007-11-16
Partimage sounds like it would work for you: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Sims2789 on 2007-11-16
Yes, this is beyond my abilities too. Another reason why old-school Linux users are perceived as condescending is because, occasionally, the complex way *is* the only way.

---

### Post by dpar on 2007-11-16
I haven't tried this, but it looks interesting........


[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by Gazneth on 2007-11-16
Wow sounds great, hope it works.:guitar:

---

### Post by fedex1993 on 2007-11-16
well has anyone used remasterys project at all?

---

### Post by Gazneth on 2007-11-16
I just tried an install and the package returned an error.  I think I'll watch this for a few days.

---

### Post by dpar on 2007-11-16
There is a link to their forum on the link I gave you. They would be the best place to get info on it, I suppose.

---

### Post by fedex1993 on 2007-11-16
yeah i was just seeing if anyone used it before i trying it. Because right now i dont feal like messing up my whole system since i got it the way i like it finally

---

### Post by gn2 on 2007-11-16
Read this and maybe give it a try yourself: [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

---

### Post by fedex1993 on 2007-11-16
well i just installed it andeverything came back perfectly installed and everything so i dont think there is any error.

---

### Post by fedex1993 on 2007-11-16
okay well i just backed it up and it works perfectly fine so i am happy for gn2 and dpar for helping thanks

---

### Post by ramjet_1953 on 2007-11-16
There is a GUI package in the repositories for making and modifying your own iso's. It's called [COLOR="Blue"]isomaster.[/COLOR]

[COLOR="Red"]sudo apt-get install isomaster[/COLOR]

Here's a link to find more info on it: [http://littlesvr.ca/isomaster/](http://littlesvr.ca/isomaster/)

Another way to approach what you are doing is to use [COLOR="Blue"]AptOnCD[/COLOR].

[COLOR="Red"]sudo apt-get install aptoncd[/COLOR]

Here's a link to check this out: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Regards,
Roger :cool:

---

### Post by Gazneth on 2007-11-16
The remastersys error I had installing was my fault, an invalid user account. Removed the old account now it works perfectly.

---

