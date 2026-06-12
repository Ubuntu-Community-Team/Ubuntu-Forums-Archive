---
title: "Errrrrrr)(*&amp;$)_@&amp;$"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-10
And I used to think I was SEMI-computer literate.....

I have spent 4 days (minus time I'm at work) trying to load UBUTU 6.10. Have finished instaling it about 5 or 6 times, only to get a grub error every time I remove the CD and re-boot.

C Drive 60GIG  fat32 Winblows 2k
D Drive 125 GIG EXT3 (trying to install Ubuntu)
E drive 80 GIG fat 32
F Drive 125 Gigfat 32
G Drive 60 GIG Fat32 (partition 2 of drive 1)
H Drive 125 GIG Fat 32 (partition 2 of drive 2)
J Drive 80 GIG fat 32 (partition 2 of drive 3)
J Drive 125 fat 32 (partition 2 of drive 4)

All drives are PATA


**IF **I can get past the partioning screen (have to try like 10 different things before it will work EVERY TIME) Install begins and I get all teh way through to where it says RESTART.
I take the CD out and reboot only to get a differnt grub error every time.
I have tried loading grub in HD0. HD0,1 and HD1 Each one has failed.:( :( :confused: 
HHHHEEEELLLLPPPPPPP

PLEASE!

---

### Post by Jaidee on 2007-03-10
Could you post the output from GRUB?

You say your are trying to install GRUB onto HD0, HD0,1 and HD1. There is a chance you have overwritten the boot sector for the windows installation, in which case a Windows repair install may be neccessary. Need a bit more information from you first though.

---

### Post by maccawolf on 2007-03-10
HD0, hd0,1 **OR** hd1.
I have had error 15, error 17 error 21 and error 22 

don't remember what's before that. MAybe Grub 1.5 or something like that...

---

### Post by rusty4r on 2007-03-10
According to your list it would seem to me that you would be aiming for (hd1,0) or (second drive, first partition) is that right?

---

### Post by maccawolf on 2007-03-10
now that's one I haven't tried...Be back in a little while and let you know the results.....

TIA if it works!

---

### Post by maccawolf on 2007-03-10
It may be a while til I figure out if that worked. First I have to figure out how to remove Grub so I can boot normally, THEN see if HD1,0 will work.....

---

### Post by maccawolf on 2007-03-11
HD1,0 didn't work. I got a FATAL GRUB ERROR. I finally got it to work about an hour ago by manually editing Grub following the step by step instructions given for the person who asked how to boot without grub. THAT worked (although I think it's still using grub. I just think it's FIXED now.

Thanks for all the replies though!

---

