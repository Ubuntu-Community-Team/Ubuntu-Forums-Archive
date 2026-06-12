---
title: "Bonobo / GNOME startup errors = dead PRAM battery?"
date: 2006-10-07
forum: Apple PPC Users
---

### Post by Aspirin on 2006-10-07
So I've been getting those obnoxious bonobo-activation-server / gnome errors when I start up dapper, and after a lot of searching, seem to have traced the problem back to my 6-year-old iMac G3's PRAM battery. 

This battery, from what I understand, controls the system clock settings and all that, and if it's dead, the system clock will be wrong, right? So if I replace this battery (which I've heard usually lasts only about 5 years), then these annoying startup errors should go away...in theory.

Has anyone else had to do something similar to this? Or does anyone know if this will work?


Better yet, if anyone has it handy, wanna give me info on where to find a new PRAM battery? :-D

---

### Post by mickjapan on 2006-10-25
I get exactly the same problem, go through the log on, then come the error messages. I 'OK' or 'cancel' them as appropriate and I'm then left with a blank screen. 

Since mine is a fossil of a G3 machine, I can live with a few annoying error messages, but how can I get passed the blank screen? 

Any ideas gratefully received

---

### Post by fxftech on 2006-11-07
I am getting the same error. Did you find a new PRAM battery? If so, did it solve the problem and where did you find the battery?
Thanks

---

### Post by hulleye on 2006-11-08
A quick fix that worked for me was to simply boot the machine (a white G3 dual USB iBook) while it's connected to the internet. This way the system clock is synchronised with a network time server. As long as the laptop's own battery charge does not drain out, i'm fine. But since the PRAM battery is dead, any time the battery does drain, i have to go through this process again.

Btw, even though you get a blank screen after logging in, you can still access the command line terminal. I think it's ctrl+alt+F1, though not sure... don't have access to my machine right now.

---

### Post by HandyMac on 2006-11-08
[I've been a Mac user for 18 years, Mac consultant for a dozen +, never used any other OS; tried installing Ubunto 6.10 on my iBook today, but not using it yet. On my PowerBook in OS X now, saw this thread where I can help with answers.]

Yes, the PRAM battery keeps System settings like time & date, startup volume, etc.; most Macs will start okay with a dead PRAM battery, but with incorrect time, revert to other default settings, but some models won't startup, won't display video, or other problems. Though I don't know if it will cause the problems with Linux you describe.

Most Macs (including the iMac) use a 3.6V 1/2AA battery for this purpose; a few models use a cube-shaped 4.5V battery. Both can be found in [Radio Shack]("http://www.radioshack.com/family/index.jsp?categoryId=2032141&cp=2032056") stores (at high prices for those in a hurry), or for considerably less (if you can wait) from [Operator Headgap Systems]("http://stn2.headgap.com/resale/FMPro?-token=13148159&-db=ProductsC.fp3&-lay=WEB&-format=items.htm&-sortfield=SortID&-Max=40&category=batteries&-find") in Tennessee (the cheapest source I've found) or all-round top-quality Mac accessories dealer [OWC]("http://eshop.macsales.com/Specials/DealMac.cfm") (scroll down for batteries).

The PRAM battery is mounted on the iMac's motherboard, which is a bit of a bear to get to; instructions can be found [here]("http://home.earthlink.net/~strahm_s/manuals.html#imcs").

hulleye, the iBook (all models) *does not have a PRAM battery*; see "[Portable Computers: Models Which Do Not Have a Backup Battery]("http://docs.info.apple.com/article.html?artnum=58445")". If you leave the iBook asleep on battery until the battery expires, it will forget the time & date and other custom settings; so it's best not to run the battery all the way down.

---

### Post by hulleye on 2006-11-10
> **HandyMac said:**
> [hulleye, the iBook (all models) *does not have a PRAM battery*; see "[Portable Computers: Models Which Do Not Have a Backup Battery]("http://docs.info.apple.com/article.html?artnum=58445")". If you leave the iBook asleep on battery until the battery expires, it will forget the time & date and other custom settings; so it's best not to run the battery all the way down.


Thank you for the correction. I had inherited this iBook from my sister, and i just assumed it lost its date and time settings as a result of having a dead backup battery. Didn't know that it simply didn't have one.

---

### Post by Pza3.14159 on 2007-01-08
I've been casting about trying to fix this problem on an inherited imac, 256M RAM, 500mhz. Someone else apparently tried to put linux on it but gave up. I've managed to get Dapper PPC on it, but get the "bonobo activation server" error--which makes gnome and nautilus unusable--until I do:

ctrl-alt-f1
[login as me]
sudo date --set 01/08/2007
sudo killall gdm
sudo /etc/init.d/gdm start

I noticed that if I killed gdm first, I would get the "timestamp too far in the future" error, and sudo was thereafter useless. But, if I used sudo to set the date (as above) first, then I could continue to use sudo to kill and restart gdm just fine. Hopefully this will be a useful addition to this thread.

BUT:
I am still seeking help from all you Intarweb folks since I can't seem to permanently adjust the hardware clock, even after I get into gnome. I thought hwclock might work, but it results in "Cannot access the hardware Clock via any known method". 

I've also tried sudo -k (to clear the timestamp, apparently)
I've also replaced the PRAM battery
And, of course, I've tried adjusting the date and time once I get to Gnome, but it always reverts to 1903 upon the next boot (and gives me the bonobo errors above, requiring the same steps to get to the gnome desktop). 
Does anyone have any ideas about how I can adjust the hardware clock to actual time, or at least make gnome not care?

thanks,
bruce

---

### Post by dpny on 2007-01-08
> **Pza3.14159 said:**
> I've been casting about trying to fix this problem on an inherited imac, 256M RAM, 500mhz. Someone else apparently tried to put linux on it but gave up. I've managed to get Dapper PPC on it, but get the "bonobo activation server" error--which makes gnome and nautilus unusable--until I do:

ctrl-alt-f1
[login as me]
sudo date --set 01/08/2007
sudo killall gdm
sudo /etc/init.d/gdm start

I noticed that if I killed gdm first, I would get the "timestamp too far in the future" error, and sudo was thereafter useless. But, if I used sudo to set the date (as above) first, then I could continue to use sudo to kill and restart gdm just fine. Hopefully this will be a useful addition to this thread.

BUT:
I am still seeking help from all you Intarweb folks since I can't seem to permanently adjust the hardware clock, even after I get into gnome. I thought hwclock might work, but it results in "Cannot access the hardware Clock via any known method". 

I've also tried sudo -k (to clear the timestamp, apparently)
I've also replaced the PRAM battery
And, of course, I've tried adjusting the date and time once I get to Gnome, but it always reverts to 1903 upon the next boot (and gives me the bonobo errors above, requiring the same steps to get to the gnome desktop). 
Does anyone have any ideas about how I can adjust the hardware clock to actual time, or at least make gnome not care?

thanks,
bruce

Have you tried resetting [NVRAM or PRAM](http://docs.info.apple.com/article.html?artnum=2238)?

---

### Post by Pza3.14159 on 2007-01-09
No I haven't tried the command option P-R. 
I kind of figured it would have been reset by the removal of the (old presumably dead) PRAM battery for several hours this morning. This would seem to be confirmed by the 1904 date as well (I misspoke myself above).
Also, I don't have the original imac keyboard and am using a run of the mill usb keyboard. 
I'm not sure what the command and option keys map to on a generic keyboard (ctrl and alt?), but I might try a few combos and see what happens.

thanks,
bruce

Afternote: I just tried it (apparently it's windows-alt P-R) and I have the same pattern of behavior as before (though it's definitely resetting the PRAM with that key combo).

---

### Post by dysdera on 2007-01-16
Hello, 
I have finally solved this problem. I restarted the PMU and now all is fine:

 Resetting Power Management Unit (PMU)".
[http://docs.info.apple.com/article.html?artnum=14449](http://docs.info.apple.com/article.html?artnum=14449)

but reseting the PRAM also reset the PMU so this should also work.

My problem was that
I was unable to bring the clock to date even starting connecting to internet.

But after reseting the PMU all is ok.

I have had this problem from a long time ago,  and it started in my ibook g3 after upgrading to 6-10. It started with the sudo, timestamp too far in the future issue. Probably it was a coincidence and the real problem was that the battery drained out witout my knoledge. 

But  two day ago I left  my ibook/ubutnu making an upgrade only with the battery and I forgot it. When I came back several hours latter the mac was sleeping (amizing how long the mac can sleep!) and I was unable to shutdown so I take out the battery. 

After that I was unable to use the desktop due to the nautilis/bonobo server error.

I was suspecting about the clock battery and wondering where to buy one but after reading this page I found that ibooks does not have clock battery and the PMU reset should work and it has worked  indeed

thanks

---

### Post by jpcrow on 2007-01-17
OK, this makes sense. I need to buy a new battery (I only use AC power right now, old battery = kaput)

I am posting to say thank you for solving my question AND to ask:

I have a 700 mhz g3 dual USB ibook with 384 megs of ram. 

What ubuntu release would function fastest on my machine?

Thanks a million,

Josh

---

