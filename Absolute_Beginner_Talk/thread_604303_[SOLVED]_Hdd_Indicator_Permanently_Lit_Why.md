---
title: "[SOLVED] Hdd Indicator Permanently Lit? Why??"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by abishek22 on 2007-11-06
hi I use 7.10 just installed it a week ago, it seems to have installed fine

 
but I see my hard
 disk indicator lit up permanently,when ubuntu is on i'm using a dell inspirin 5100 p4 laptop  


none of the power management features work


is the hdd supposed to run like this or is there a problem which has to be fixed...

---

### Post by kaiguy57 on 2007-11-06
have you tried installing powertop? download the powertop package:
sudo apt-get install powertop
then run:
sudo powertop
and follow the recommendations. this may fix your problem.

---

### Post by abishek22 on 2007-11-06
> **kaiguy57 said:**
> have you tried installing powertop? download the powertop package:
sudo apt-get install powertop
then run:
sudo powertop
and follow the recommendations. this may fix your problem.


**will do it and get back**

---

### Post by insane_alien on 2007-11-06
do you hear the drive chrning around? if o it is probably trackerd(indexes the hell out of everything) go to system>preferences>indexing preferences (sorry if that is wrong but i have modded my menu structure to hell and back, it is totally unrecognizable now) and turn indexing off.

---

### Post by abishek22 on 2007-11-06
i hear a weird chiming sound when the gui loads in the beginning when i logon to system.almost something like a jet engine starting up but with quite less sound but audible to me


after that the HDD indicator stays lit,meaning the drive is being accessed i guess, will turning indexing off cause problems ,slow down the system? or its just to search for files?

---

### Post by abishek22 on 2007-11-22
**[SIZE="5"][COLOR="Red"]powertop solved problem< although following it caused one hdd partition which was mounted to disappear[/COLOR][/SIZE]**

---

