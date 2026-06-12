---
title: "Extremely slow and no internet after upgrade to Fiesty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by noob12345 on 2007-05-31
I recently upgraded to Fiesty, and it sucks

first of all, my Netgear MA111 wireless usb adapter, which uses linux-wlan-ng, now doesn't work
in Edgy, it would load up automaticly, and even under Dapper, I could activate using a few commands in terminal
but in Fiesty, I get no internet, the ping doesn't work, and all the forms (dns, host, etc.) are empty (although it was able to detect a wifi signal when selecting essid)

second of all, it is so slow
I have computer with hyperthreading, so I had installed 686-smp kernal
in the GRUB menu, there was nothing with smp in it, so I selected one with just 686
I see 2 cpu's in system monitor, but at least 1 is at above 90% usage just monitoring it 
I tried the command  (still without internet) sudo apt-get install linux-686-smp  (or something like that I found on this website), and it said I already had the newest version
Network configuration takes almost a minute to open, and visual effects have this annoying lag
it is slower than a 386 kernal in Edgy and almost as slow as 386 in Dapper

and can anyone tell me why Ubuntu now needs to use a "restricted driver" for my modem (which I don't use)
also, why was mozilla removed? it had half the start-up time as firefox for me

I read on the web somewhere that Fiesty was acually much faster than Edgy

does anyone have the slightest clue what is going on?

---

### Post by northicert on 2007-05-31
I'm very new on the block.  I had problems setting up a wireless also.  I think there are to many differences in wireless cards to know where to begin.  I found my answer when I double clicked on the little monitor icon in the upper bar. it showed me all my wireless routers and their signal strength.  I seledted one and entered the wep key and was soon on the web.  However my netgear router wouldn't connect to web even after I entered the wep key.

---

### Post by RaZoR-x11 on 2007-06-09
Hey,  Firstly, I would advise sticking to a version that has no problem's or works for you, For instance Dapper Drake 6.06, or Edgy Elf 6.10, as  most off the bug's and kninks have bin fixxed. Secondly i would say, if you are going to use 7.10, Beware that it is still in a very much better stage, and alot off bug's have not bin fixxed yet, so if you want it to work, i would go use edgy or dapper.   raz.

---

