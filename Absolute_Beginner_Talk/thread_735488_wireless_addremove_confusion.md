---
title: "wireless add/remove confusion"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-25
Just instaled ubuntu- small wireless problem but it seems to work fine now.

BUT when trying to use add/remove, it says: "the list of applications is not availabe-to reload the list you need an active working internet connection"

i click reload, and it simply says the same thing, AFTER reloading the list successfully.
 Anyone know how to ge tout of this incessant loop?

:(

---

### Post by jan quark on 2008-03-25
when you run

```
sudo apt-get update 
```

in terminal, do you get any error messages?

---

### Post by hungryOrb on 2008-03-25
Nah, successful:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Reading package lists... Done

---

### Post by hungryOrb on 2008-03-26
It doesn't seem to save the results from its reloading of the list of available applications.. Or could it be related to the wireless settings??
Thanks for any helps!

---

### Post by hungryOrb on 2008-03-26
Thought I would add that the wireless does SEEM to work fine, have downloaded and installed stuff, and while browsing (including posting) I haven't run into a single hitch so far :)

---

### Post by JohnnyDiamond on 2008-03-27
I have the same problem, but I find it strange. I am using 7.10 as well. I had installed in OEM configuration, and the update worked fine. Then I installed mono trying to get .net to work... that turned out to be a BAD thing and broke my system in half. 

SO I reinstalled everything, but did a normal install (via live CD), and the add/remove program did not work this time. Wireless works fine, and I have the same result from apt-get as above. Anyone else have this problem?

I will continue to research...

JRY

---

### Post by JohnnyDiamond on 2008-03-27
Fixed it:

I went to System > Admin > Software Sources

I noticed that all the sources were UNCHECKED. I assume this is due to poor wireless performance during install. I checked all the ones I thought normal, ran the update (sudo apt-get update) and it found like 176 packages or so... 

Anyone having this same problem may want to check that. I also UNCHEKCED the "use CDROM update" box... since I noticed every time someone ran apt-get all it was checking was the CD... 

Hope this helps! :guitar:

---

