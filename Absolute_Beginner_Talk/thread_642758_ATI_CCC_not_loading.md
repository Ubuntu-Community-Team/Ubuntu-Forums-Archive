---
title: "ATI CCC not loading"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by shegs on 2007-12-17
alright so I finally got this thing setup with my dual x1900xt's that I use for crossfire in windows.

I have tried all 3 methods that I know to install FGLRX (system->admin.Restricted drivers, ENVY, and directly from ATI) and nothing works.

the only good thing is that it can detect my cards(lspci reports that I have a primary and a secondary x1900xt) and it also properly detects my monitor as my resolutions are correct and font is more crisp than without the driver.

the bad:
framerates even in mundane desktop work and text reading is dead slow
I get no actual 3D (beryl just goes black)
ATI CCC wont load saying the drivers arent installed or I need to run aticonfig --initial (which I have)

my xorg.conf shows the fglrx drivers under device

so I am lost

any help would be greatly appreciated!
thanks

---

### Post by shegs on 2007-12-17
bump

---

### Post by shegs on 2007-12-18
no love?

---

### Post by shegs on 2007-12-19
no one has any idea how to fix this? I am the only person?

---

### Post by NateMan on 2007-12-19
ok your in luck, kinda. I have an 975x crossfire capable mobo, although I am not currently using crossfire. I have one x1900xt installed and I did have an x700 installed in my secondary slot. I attempted to get the machine to load and work properly with both cards installed, however I had similar problems. I removed the secondary x700 from my system and it worked flawlessly after I installed xgl. I would go back and remove the envy and the straight from ati installed drivers and go back to the restricted manager. Then install xgl and it should work. Are you using 7.10 or 7.04? I noticed you said that you were using beryl, do you mean compiz? if you are using 7.04 update to 7.10. if you are using beryl, uninstall it and try installing compiz fusion. There is no reason to use beryl now as it is merged with compiz to create compiz fusion. All the functionality of beryl is still there, just works better. Some more information would be helpful involving your setup if you wish to get assistence. I can't give you details due to not knowing what version of compiz and ubuntu you have installed.

---

### Post by shegs on 2007-12-19
I have 7.10 and as this is the newbie zone and I am a nixnewb all I knew about was beryl
I have since removed it since it looses it effectiveness when the entire screen goes black and I am unable to install any compiz fusion due to my wifi not working worth crap.

on a sunnier note I was able to correct some of the problem. after following the advice from the ati linux [wiki]("http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration")
I was able to partially restore some performace. the screens wiggle and move very smoothly now. buuut I am still un able to run the ati CCC. here is my info, as my wifi deosnt work in linux I am sending you this through my win boot (which is a totally different hard drive)

Mobo: Asus p5w DH deluxe
Vid: asus ati x1900xt crossfire/asus ati x1900xtx
mem: 2 gig patriot high speed
hdd: dedicated 180 gig

I am unsure if you need anything else.

I am unwilling to remove either of my cards as gaming is why I still use windows. but I will attempt to remove envy and redo the restrictred drivers as i now have some acceleration.

thank you

oh and I have also been looking for some way to make my damn realtek rtl8187 wifi card more stable sometimes it can find the network but I can almost never ping it and when I do get connection I get 3 percent connectivity (so says the router) I know it isnt the hardware or the router as when in windows everything is peachy. 
if you can point me in the right direction of a possible fix I would be greatly appreciative. I have tried building the drivers from realtek with no avail, the documentation just assumes that I am leet nixhacker or something and doesnt go into enough depth as to tell me the commands. if not that is cool i can search elsewhere
thanks

---

