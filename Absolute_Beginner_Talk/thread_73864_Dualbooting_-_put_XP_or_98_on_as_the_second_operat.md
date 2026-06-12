---
title: "Dualbooting - put XP or 98 on as the second operating system for gaming?"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Hobbsee on 2005-10-10
Hey all.

To give some background information, I'm looking to convert the windows partition of my laptop into a gaming machine.  I have the option of putting 98 on there, or a copy of XP.  This laptop has a 40 gig HD, and 512mb ram. It is dual booting XP and kubuntu at the moment.

No, sims 2 does not yet run under cedega, according to their site, so I cant use that option.

The question is, which should I put on there for a gaming partition, seeing as neither would be connected to the internet?  Which would give better performance?

The second question: will grub pick up that I am running windows 98 during the install, and what would the /boot/grub/menu.lst look like, compared to what it looks like with XP?  

I know it's a rather windows-y question, so i'm not exactly sure where this should be...but any thoughts would be appreciated :)

---

### Post by erikpiper on 2005-10-10
Don't most games not work with 98? XP is easier to install, and if you have room, I would reccomend it.

Also, I have never heard of it being possible to install windows without touching linux. You may have to install windows, then linux. 




TRATOR!!!    (jk) :p

---

### Post by KeithO on 2005-10-10
i'm not certain on whats used currently but a couple years back i had a dual boot setup with XP and Red Hat.  I had to install linux second on its own partition and it used LiLo to give the boot options.  I could be wrong but I think Grub is used now and would require linux installed second.

on a side note, after getting annoyed with Red Hat 7, I uninstalled it but the mbr was still looking for LiLo so I had to do fixmbr and all was fine.  This may or may not help you later on.

---

### Post by sardopsycho on 2005-10-10
From my experiences - and granted I am a beginner with Linux / Ubuntu, but I am former Double Agent of Geek Squad.  I saw alot in that time, and I will say that I found dual boot with Windows XP, whether the Linux install is sitting on the same harddrive in a differnet partition, or on an additional harddrive, is just a bad idea all around, and is highly unrecommended.  Since I am not a Linux expert yet, what I heard was that Windows XP does something to additional partitions and harddrives which causes instability and sometimes will make it not work at all.

I am not sure about this information, but I have always heard Windows / Linux dual boot = bad all over.

---

### Post by Kapre on 2005-10-10
[QUOTE=Hobbsee]Hey all.
The question is, which should I put on there for a gaming partition, seeing as neither would be connected to the internet?  Which would give better performance?[/QUOTE]

For your gaming, I would suggest the M$XP. Better performance will depend on what apps are you going to run/use.

> The second question: will grub pick up that I am running windows 98 during the install, and what would the /boot/grub/menu.lst look like, compared to what it looks like with XP?
During the install, GRUB will definitely pick up all the OS and advise you of all OS that it finds  (I'm quad booting as of now) and all the OS have been picked up.  

K

---

### Post by Hobbsee on 2005-10-10
To clarify, XP and kubuntu play fairly nicely together, at least on my machine.  I've had to reinstall either operating system (XP or ubuntu/kubuntu) many times, and am not particularly afraid of dual booting - i've had plenty of practice!

I'll make a backup of my /home partition before i do anything, so i'm not particularly worried about reinstalling both kubuntu and windows.  I know how to reinstall grub, so that's not really a problem either.

This machine is already a dual boot - so i'm already a trator :P  Dad would be most annoyed if I got rid of the paid-for firewall/antivirus completely yet!

98 will play all the games that I'm looking to play, and seems to play them with better performance than XP...well, apart from all the linux games that is..

The question I want to know now is, does anyone have any experience in dual booting with 98, and does it cause any problems that dual booting with XP doesnt?

---

### Post by KeithO on 2005-10-10
I'm pretty sure its all handled before either 9x or XP even load anything.

---

### Post by SilentCacophony on 2005-10-10
I've not had any problems at all dual-booting with Windows 98. Keep in mind that Windows likes to be on the first partition of the first drive (though there are ways around that.) Grub will set it up just as it does XP, as well.

I've often read that games usually perform better on Windows 98 than XP, myself. I tend to use a slimmed-down Windows 98, myself (I rip out the stuff I don't like manually... ;) ) I also refuse the WinXP license agreement, though.

---

### Post by Hobbsee on 2005-10-10
SilentCacophony: thankyou very much for your input!

The windows is on the first section of the drive, i knew that much, so did it correctly to start with :)

Excellent news about grub too - if the windows partition is in the same place, does the grub need to be updated, apart from the name?  

And out of curiousity, what parts of 98 did you remove?

---

### Post by SilentCacophony on 2005-10-11
> Excellent news about grub too - if the windows partition is in the same place, does the grub need to be updated, apart from the name?

Shouldn't need to change anything but the name, no. They both have to use the chainload option.

> And out of curiousity, what parts of 98 did you remove?

Mostly the so-called 'internet integration' which makes 98 so much less stable than 95. Losing it disables windows-update, but if you have a proper firewall setup, shouldn't be too big a deal for most. Not for the faint-of-heart, though ;) See this site, which has much more content on other matters regarding Windows: 

[http://www.annoyances.org/exec/show/article03-001](http://www.annoyances.org/exec/show/article03-001)

There is also some good info for tweaking Windows here:

[http://www.mdgx.com/](http://www.mdgx.com/)

And a product with a free preview to let you choose what you want installed with Windows 98:

[http://www.litepc.com/98lite.html](http://www.litepc.com/98lite.html)

---

### Post by Hobbsee on 2005-10-12
cool, thanks for that.

Losing windows update wouldnt be too much of a problem, seeing as windows 98 isnt even supported any more is it?  I'd only need the internet to get directx 9.0c, and could probably go and grab that before i reinstalled the windows section...

---

### Post by SilentCacophony on 2005-10-12
Yes, it does break directx downloads (and pretty much any other MS download) if you remove the internet integration. If it's possible to download the entire directx install package and store it locally, that would probably be best. I seem to remember that there was some ftp access to grab MS updates and such manually, but I don't remember the address now.

You can still use the internet fine in general with firefox instead of IE, though. :)

---

### Post by Hobbsee on 2005-10-12
mmm...true...with the useragent extension, as the windows update site wont let you use firefox to browse it...

I'll definetly look into that...in a month or so when my exams are over and i have time to play (more) with my laptop.  Seeing as windows is rather tempramental, and likes taking up the whole drive if it possibly can...

---

### Post by BLTicklemonster on 2005-10-12
[QUOTE=Kapre]For your gaming, I would suggest the M$XP. Better performance will depend on what apps are you going to run/use.


During the install, GRUB will definitely pick up all the OS and advise you of all OS that it finds  (I'm quad booting as of now) and all the OS have been picked up.  

K[/QUOTE]

I find that, if tweaked and trimmed, games play every bit as well on xp as they did on 98, though I would prefer 98 to xp any day... xp just comes with all those wonderful drivers!!!. Anyway, I gots a question about Grub and using two operating systems.

Let's say I have two hard drives, one with xp, one with Ubuntu. (all together now... "I have two hard drives, one with xp, one with Ubuntu" :razz:  )

If I put the Ubuntu drive as master, and the xp drive as slave, will grub see it and allow me to chose from which I'd like to boot.. from? Man, I butchered that. Will I get a choice like that, or do I need to put them both on the same hd? I have xp on a hd that is about totally maxxed out, and I have tons of developmental stuff that I don't want to lose, or mess with (more than will fit on a dvd...) so I'd like to leave it alone, and I'm too lazy to ghost it to a new partition on the Ubuntu hd. So basically, I'm asking if Grub allows for lazy slobs like me?

---

### Post by SilentCacophony on 2005-10-12
> Let's say I have two hard drives, one with xp, one with Ubuntu. (all together now... "I have two hard drives, one with xp, one with Ubuntu"  )

If I put the Ubuntu drive as master, and the xp drive as slave, will grub see it and allow me to chose from which I'd like to boot.. from? Man, I butchered that. Will I get a choice like that, or do I need to put them both on the same hd? I have xp on a hd that is about totally maxxed out, and I have tons of developmental stuff that I don't want to lose, or mess with (more than will fit on a dvd...) so I'd like to leave it alone, and I'm too lazy to ghost it to a new partition on the Ubuntu hd. So basically, I'm asking if Grub allows for lazy slobs like me?

First, a warning: I once changed a Windows HD ide configuration by swapping cables, and it went completely belly-up mid-way through booting. It seemed that the OS installation had hardcoded the device addresses upon installation. I don't remember the details, so not sure if it'd apply in your case.

Also, in my experience, Windows doesn't much like being on anything but the first partition of the first harddrive. That said, grub does have a *map* option to get around that.

I'm not really clear on what your setup *was*, but if you're going to install ubuntu after rearranging the drives, it should set grub up correctly.

Grub would generally need to be installed on the MBR of the first bootable harddrive, and should ask if that's what you wish to do. In that case, the MBR (grub stage 1) points to the ubuntu partition to read the /boot/grub/menu.lst file, which will contain your booting choices.

In any case, if the menu.lst is incorrect, it can be edited, even from a rescue cd or live cd. For example, if you needed to add an option to boot WinXP from the second HD, you could add this to the /boot/grub/menu.lst:

[HTML]title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1[/HTML]

Note that (hd1,0) means second drive, first partition, and that the map commands would fool XP into thinking it's on the first drive.

EDIT- typos

---

### Post by BLTicklemonster on 2005-10-12
Cool, I'll try that. I can recover data, so if the xp drive Windowed out on me, I could still get my uc files and meshes.

---

### Post by Angry penguin on 2005-10-12
I have been dual booting my desktop with win98 and ubuntu for a while, playing hl2 in it. recently i started having what appeared to be hardware issues in windows, then soon after my ubuntu partition became plagued with "hardware" issues.(general instability and sluggishness out of the blue). I've since reformatted and am back to 100% linux. 

in my opinion, windows and linux do not play well together, i've dual booted multiple times and this always happens after about a month.

I think that if you install windows after ubuntu or split the ubuntu partition to make room for windows, you have to reinit the bootloader. this is where lilo becomes nice. im not very experienced with grub  but reinit with grub was very confusing for me. with lilo you just boot with a live cd, open up a terminal, type lilo and your done. so install windows first if you can, to avoid that whole thing.

good luck

---

