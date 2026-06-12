---
title: "wireless networks"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by mulleta on 2006-12-25
hi, i am trying to pick up a wireless network. what application do you suggest?
the wireless works well in windows, but i dont know where to begin when it comes to wireless  management in ubuntu. any help is apreciated.

thanks. oh i have searched for wifi radar and the command 

sudo apt-get install wifiradar 

says the package isnt availabel. any suggestions?

thank you

---

### Post by dbbolton on 2006-12-25
just go to applications > add/remove

and wifiradar is there.

---

### Post by Mazen on 2006-12-25
```
sudo apt-get install wifi-radar
``` this should work!! i suggest you search for the package before entering the name
```
sudo apt-cache search wifi radar
``` will give you a result of wifi-radar....+ description that way you know what the package is called
when using the apt you should be connected to the internet!

---

### Post by mulleta on 2006-12-25
well i didnt want to start this thread as there are so many posts concerning wireless connections but wifiradar doesnt seem to be part of the applications available to add or remove?

i am running ubuntu dapper 6.06 and i know it should be there, shouldnt it?

---

### Post by mulleta on 2006-12-25
thanks but the cache-search command doesnt produce any results. and the install command still says i cannot find the package?

---

### Post by Mazen on 2006-12-25
yes again are you connected to the internet? get yourself a wired connection for the time being that should help you solve a lot of problems

---

### Post by mulleta on 2006-12-25
thanks, i am connected at the moment :) what package should i download?

---

### Post by mulleta on 2006-12-25
ok, when i select system->administration->networking

it only picks up the current eth0 connection which is active and a modem connection ppp0 which is not configured. does this mean that ubuntu doesnt pick up my wireless card? or that the correct drivers are not installed?

---

### Post by Mazen on 2006-12-25
mmm..ok first ```
sudo apt-get install wifi-radar
``` this will give you the wireless utility to view netwroks in range and so on, if this works and you see netwroks then ur wireless card is working...i'm sorry i don't know the command to check that in the terminal](*,)

---

### Post by mulleta on 2006-12-25
thanks.

this is the reply that i have been geeting from your suggested command.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wifi-radar

doesnt find the package and i dont know why?

---

### Post by Mazen on 2006-12-25
mm ok...well i've never had a problem with that actually so i don't really know how to "force" it or something....u might want to wait for another person to reply mate...i'm sorry ...i'll look it up for you and try to find something

---

