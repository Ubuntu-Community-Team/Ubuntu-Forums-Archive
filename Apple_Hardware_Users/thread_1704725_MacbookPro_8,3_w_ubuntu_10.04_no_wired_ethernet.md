---
title: "MacbookPro 8,3 w/ ubuntu 10.04 no wired ethernet"
date: 2011-03-11
forum: Apple Hardware Users
---

### Post by itsmrjon on 2011-03-11
Let me begin by saying, thank you all for taking a look at this issue of mine!

Details are as follows:
New Macbook pro 17" (version 8,3)
Installed an ubuntu 10.04 variant (CAELinux to be exact)
Neither the wireless nor wired ethernet is working.

I'm aware based on my scavenging of these forums that users on the newer macbook pro models have not been able to get wireless to work sucessfully (with the exception of a few) however I have not seen anyone have a problem with wired as well.

I honestly do not even know where to begin probing the problem. I have attempted to follow the instructions of people who have managed to get the wifi to work in 11.04, but I didn't expect that to work in my case considering I'm not running the same build.

Does anyone have any recommendations of where to begin trouble shooting or a method to fix this issue?

---

### Post by itsmrjon on 2011-03-11
So I managed to partially solve the problem!!!

My wireless is now WORKING!

Here is what I did...

Burned a copy of 11.04
Booted into 10.04
Inserted the live CD
Ubuntu informed me there were repositories available on the disk
I upgraded all possible repositories (some required additional download, and since I didnt have internet available I wasnt able to do those)
I then proceeded to this page [https://help.ubuntu.com/community/MacBookPro8-1/Natty#preview](https://help.ubuntu.com/community/MacBookPro8-1/Natty#preview)
I followed the directions VERBATIM
voila! wifi works

still no wired ethernet working however

There may have been intermediary steps that I was messing around with that may have contributed to the success of this method, considering I've been working on this non-stop for the past 2 days, i would say its possible something else I may have done may have contributed to success.

Additional things I did include using the mactel repositories as well as install and try many of the wireless drivers from here [http://linuxwireless.org/](http://linuxwireless.org/)

Looks like I may keep my mac for work after all! well i still have 12 days to make up my mind

---

### Post by binary10 on 2011-03-12
I'm using a MacBookPro8,2 i7-2820QM 2.3, hires

No problems on wired using natty dev build (12-Mar)
Wireless still requires manual work.

A few other issues though, but time will get them resolved.

---

### Post by artistadelamultitud on 2011-07-05
Does anybody has a solution for the wireless?

I'm needed of the comand to add ndiswrapper to "autostart", becasuse I don't know exactly wich one is...

I have a MacBook Pro 8.2 with Ubuntu 11.04

---

