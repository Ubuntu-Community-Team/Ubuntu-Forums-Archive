---
title: "Trying to use .iso file"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by ryan444 on 2006-12-19
Hi guys, 

Sorry if I didn't see it here but I am trying to even open up the .iso file on my xp machine and cannot get it to do ANYTHING. Is there some secret to getting it to work? Thanks guys. BTW version is the same as the current download availible from you.

---

### Post by taurus on 2006-12-19
You need to burn it to your CD so here's a guide...  You can download CDBurn XP for free.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Or

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ryan444 on 2006-12-19
Little bit more info. Thanks for your suggestion however the .iso file is on a cd and i have rebooted the computer several times now. Still quite an intresting problem. Thanks though. :)

---

### Post by taurus on 2006-12-19
You need to burn the ISO image to your CD as an image file.  You cannot just copy it over to a CD and expect it to boot...  It's not going to happen.  So, follow the second link above on how to burn it again.

---

### Post by meng on 2006-12-19
An .iso file is a convenient way of holding a filesystem within a single file. But in order for you to be able to boot from it, you have the write the filesystem to CD, not the unaltered .iso.

---

### Post by ryan444 on 2006-12-19
I have burned the .iso as a burn image following the instructions. Restarted. No dice. Wonder what is messing it up here.

---

### Post by Sef on 2006-12-19
Read [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm?](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm?)


Download [Iso Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

The way Taurus showed you will work fine, so this is just another option in case you have problems understanding anything on his links.

---

### Post by taurus on 2006-12-19
You probably need to look in your BIOS to make sure you set the bootloader to boot from the CD-ROM first instead of the harddrive.

---

### Post by L Campbell on 2006-12-19
> **ryan444 said:**
> I have burned the .iso as a burn image following the instructions. Restarted. No dice. Wonder what is messing it up here.

Is it possible that you burnt it to a RW CD instead of Read only?

I did this several times before I read ALL the instructions.    :-)

---

### Post by meng on 2006-12-19
It should be possible to boot from a CD-RW, so long as your drive is CD-RW-capable. However, all we know about this person's problem is "cannot get it to do anything" and "no dice". What I'd like to know is what exactly is happening? Is it booting into windows? Or is there a message saying "no operating system"? Or something else? Why should we have to guess?

---

### Post by ryan444 on 2006-12-20
Sorry for not being specific. I have tried going into the bios and when telling it to boot from the dvd it is saying No Operating System. Then, if i continue to boot up it boots in windows. It is a read only cd file when i looked at the properties. Should i need to change something? 


Edit: After burning with Infra Recorder as the burn image I booted up my computer. I checked the bios first and saw that the boot order is set to the cd first. I then turned off the computer and restarted it with the cd in the drive waiting for it to boot into unbuntu. However, a straight boot went up.

Computer specs: 

windows 98
256 MB Ram
Pentium 1.6(i believe) processor
DVD Burner added 2/06

---

### Post by ryan444 on 2006-12-21
Sorry to bump. I have also tried creating three new copies with the other alternatives mentioned in previous posts and none seem to be working. I can see the file if i look at it through windows explorer. See my previous post for more information. Thanks

---

