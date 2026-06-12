---
title: "sound card problems HELP"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by BananaCakes471 on 2006-07-31
i can't get music to play! i don't know why i think its my soundcard though...something might be wrong with it or maybe linux can't recognize it i'm not sure but i need help please#-o

---

### Post by croak77 on 2006-07-31
What soundcard do you have?

---

### Post by BananaCakes471 on 2006-07-31
i don't know how to check which soundcard i have...i have install the proper codecs so  it has to be a soundcard problem

---

### Post by SpawnSC on 2006-07-31
mp3 files? :confused:

---

### Post by BananaCakes471 on 2006-07-31
yea i have mp3 files i can play them but no sound comes out...same with the xubuntu example files

---

### Post by BananaCakes471 on 2006-07-31
ahhh help to much silence!!!

---

### Post by croak77 on 2006-07-31
Open a terminal and paste the output of :

lspci | grep audio

---

### Post by BananaCakes471 on 2006-07-31
i tried that and it ended up jst bringing me back to the main command line without anything after it

this...


bananacakes471@Marklar:/$ lspci | grep audio
bananacakes471@Marklar:/$

---

### Post by croak77 on 2006-07-31
Do you have Windows installed? Do you know if you are using a PCI soundcard or your motherboard's onboard sound?

---

### Post by BananaCakes471 on 2006-07-31
well i have xubuntu installed...its an old computer ..dell polaris 61734..so i think the sound card might be onboard... i google the computer to see if i could find out what sound card it had but i had no results for "dell polaris 61734" OH also my speakers are built into the monitor but with sepereate speakers it still doesn't work

---

### Post by croak77 on 2006-07-31
Try going to Dell and enter your service tag.

[http://support.dell.com/support/topics/global.aspx/support/my_systems_info/en/details?c=us&l=en&s=gen&~tab=2]("http://support.dell.com/support/topics/global.aspx/support/my_systems_info/en/details?c=us&l=en&s=gen&~tab=2")

---

### Post by BananaCakes471 on 2006-07-31
ehhh!

---

### Post by croak77 on 2006-07-31
> **BananaCakes471 said:**
> ehhh!

What does that mean?

---

### Post by BananaCakes471 on 2006-07-31
EVERYBODY!!! lol i have sound thanks for all the help in the end i used this guide [http://ubuntuforums.org/showthread.php?t=23369&page=3&highlight=CS4236](http://ubuntuforums.org/showthread.php?t=23369&page=3&highlight=CS4236)
and now i have sound...i love XUBUNTU!!!

---

