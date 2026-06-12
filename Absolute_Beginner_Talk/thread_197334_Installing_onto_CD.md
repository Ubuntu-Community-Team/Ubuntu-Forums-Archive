---
title: "Installing onto CD"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by PricklySponge on 2006-06-15
I am having trouble in the instalation of ubunu. 

I have installed WinImage and can view the files/folders from the LiveCD download I did. I dont know what to do next, am I supposed to burn it to disk? If so, I have CDBurnerXP Pro installed and would appreciate it if somone could give me some sort of walkthrough

-PricklySponge,
Thanks:)

---

### Post by bruenig on 2006-06-15
you need to burn the iso to a disk as an image, you can do this with nero or with almost any other burning software you have.

---

### Post by PricklySponge on 2006-06-15
so, I assume CDBurner XP pro would work. When I click to burn an ISO image it gives me the normal list of hard drives, cd drives and folders etc..., where would the ISO image be on my hard drive?

---

### Post by PricklySponge on 2006-06-15
edit: I found where the image is located, and burned it. I'll put in my comp and restart it

---

### Post by PricklySponge on 2006-06-15
well, I supposedly have it on CD. Now, I put it in on startup, right? Because I had it in on startup and It didnt do anything, it just started windows. What do I do?

---

### Post by truoc444 on 2006-06-15
make sure you didn't just burn the .iso file to a cd that you actually burned the "image".  usually in the menu there's an option to burn cd image or burn dvd image.  the other thing you could try is right click on the .iso, select open with, then select cdburnerxp pro and let it open it that way.

also make sure your bios is set to boot from the cd before the hard drive.

---

### Post by PricklySponge on 2006-06-15
So I need to extract the files before I burn them? Where should I extract them to?

---

### Post by The Cosmic Hobo on 2006-06-15
You don't extract anything... your CD burning software knows what an .iso file is and how to convert it to a CD. You just need to tell it to burn the CD from the .iso, and *not* burn the .iso to the CD as a datafile.
I think in CDBurner XP, when you start the program, there are three options - the top one should be something like "create iso or data CD". Click that, and then on one of the toolbars is a "burn" icon that has a drop-down attached to it; I've a feeling that you can select something like "burn iso", which then asks you for the file you want to use (which you can find by browsing).

I hope that helps. I only used that software once, and that was to burn Ubuntu ;)

---

### Post by PricklySponge on 2006-06-15
do I use "ISO level 1" or "ISO level 2" when burning

---

### Post by bruce89 on 2006-06-15
Follow this - [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by bmoney017 on 2006-06-15
PricklySponge, did you ever get the cd to burn correctly? I am also using cdbrunerxp, and I cant seem to figure out how to burn the image. I am gonna keep trying different things, but so far I am on my 4th cd :-x

---

### Post by jimmyt on 2006-06-15
PricklySponge, have you changed your BIOS such that your pc boots from the cd drive rather than the hard drive?

---

### Post by catlett on 2006-06-15
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) Once again Aysiu has foreseen this issue and has created a graphical how to download the ubuntu iso and  burn it using CDBurnerXP.

---

### Post by PricklySponge on 2006-06-16
[QUOTE=jimmyt]PricklySponge, have you changed your BIOS such that your pc boots from the cd drive rather than the hard drive?[/QUOTE]
yes, I have

---

### Post by Mikeynewbie on 2006-06-17
If you burned the iso image correctly you shouldn't have to change Bios to boot the cd.  all you should have to do is on start up hit F2 and the you should boot from disk.  If you don't boot from disk then i assume the iso is burned improperly.  I use to use nero, very easy to set up iso burns, never used the program you are using.

---

### Post by Mikeynewbie on 2006-06-17
Here is site that has a breif explanation of how to write the iso file with burner xp pro.  Try these instructions on a new burn of the iso file.  The instructions you need are at the bottom of the page.  [http://www.damnsmalllinux.org/wiki/index.php/Burning_a_Bootable_CD](http://www.damnsmalllinux.org/wiki/index.php/Burning_a_Bootable_CD)

---

### Post by Bartender on 2006-06-17
Easy way to check to see if you just copied the iso as data (wrong thing to do) or successfully created a bootable CD is toss the finished CD in a Windows machine and explore the CD.    If you see just one file it wasn't done correctly.  You should see several folders and three or four files.

---

