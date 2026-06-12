---
title: "TV Capture Card Drivers (ATI &amp; aVermedia)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by MayaLynnRin on 2006-11-16
Two days ago all I knew about Linux was that it was an OS, last night I installed Ubuntu 6.06.1. I've done some homework reading but for the most part I'm figuring everything out as I go. Problem: I need to install a tv capture card but I don't have the neccesary drivers. I have tried google and the forums, what information I found I could not understand. Either it was not the information I needed or I need it broken down more. I have two capture cards, an ATI and an avermedia, anyone who could point me in the right direction to finding drivers for these would be greatly appreciatted. Thank you.

---

### Post by maybeme on 2006-11-16
Maybe you could do something with this:
[http://linux.bytesex.org/v4l2/drivers.html](http://linux.bytesex.org/v4l2/drivers.html)

---

### Post by MayaLynnRin on 2006-11-16
Fantastic! It's a springboard if nothing else, and further than I've managed on my own. Thank you very much.

---

### Post by anaconda on 2006-11-16
[www.linuxtv.org](www.linuxtv.org)
could be of help.

And if you find the right driver you propably need to copy the file to 
/lib/firmware -directory. Atleast That was all I needed to do with my card (which is of different brand than yours,)
Then just install a program that you can use to watch TV .. eg kaffeine is good.

---

### Post by MayaLynnRin on 2006-11-16
Thank you, unfortunately My Ubuntu machine is at home so I won't know what works till tonight. Is kaffeine very user friendly?

---

### Post by Tim Prosser on 2006-11-16
Kaffeine is fine with TV, once you get the cards working (this is the hardest bit). 

I have a couple of Twinhan digital (DVB-T) cards and once I'd got the drivers working Kaffeine allowed a full scan of the frequencies to grab a channel list.  It allows you to stream it to another PC or record manually.

Once you get comfortable with Ubuntu, and get the cards working (whether analogue or digital), you might want to have a look at MythTV.  [http://www.mythtv.org](http://www.mythtv.org)

It isn't the easiest of paths to follow, and can be frustrating, but its well worth it once you get it working.  Edgy is easier as the latest version is available from one of the repositories, but it is possible on Dapper as well (not sure if anyone has done a backport from Edgy)
See

[http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source#Installing_the_pre-compiled_MythTV_0.20_packages_from_the_official_repositories_Ubuntu_Edgy_6.10](http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source#Installing_the_pre-compiled_MythTV_0.20_packages_from_the_official_repositories_Ubuntu_Edgy_6.10)

and

[http://parker1.co.uk/mythtv_0.20.php](http://parker1.co.uk/mythtv_0.20.php)

---

### Post by MayaLynnRin on 2006-11-16
I'm not a big "tv person" (but I will check out myth tv, I've heard a bit about it before). I'm mostly just installing the capture card for my PS2, will Kaffeine run PS2?

---

### Post by Naegling23 on 2006-11-16
check out tvtime, its in the repositories.  Easy to set up, and works great.  The only downside is that it doesnt record, but if your just looking to play playstation games, it wont matter.

tvtime is in the standard repositories.

---

