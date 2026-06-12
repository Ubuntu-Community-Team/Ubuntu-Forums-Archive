---
title: "Convert me to ubuntu!!!"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by mrvanx on 2006-04-27
Hey people, currently i have a server set-up in my house to provide:
http (with php and mysql)
printer sharing
file shares
pop3/smtp services

Now this is running on winXP but am finding it a serious resource hog (its a P3 500Mhz with 96 MB Ram)

Am i able to perform these tasks and more using ubuntu instead??

---

### Post by khightower on 2006-04-27
[QUOTE=mrvanx]Hey people, currently i have a server set-up in my house to provide:
http (with php and mysql)
printer sharing
file shares
pop3/smtp services

Now this is running on winXP but am finding it a serious resource hog (its a P3 500Mhz with 96 MB Ram)

Am i able to perform these tasks and more using ubuntu instead??[/QUOTE]

Big time. Look up LAMP (Linux, Apache, MySQL, PHP). Since Ubuntu is a version of Linux you will be on your way to turning on the light:D

---

### Post by mjm115 on 2006-04-27
Check out [http://www.howtoforge.com/taxonomy_menu/1](http://www.howtoforge.com/taxonomy_menu/1)

This site will show you how to set your servers up on linux.  You will see your options on the left.  If you go up to the search bar on the site and type in Ubuntu, it will bring up all tutorials specifically designed for ubuntu.

Hope this helps.

---

### Post by mrvanx on 2006-04-27
Phew hopefully it should do the stuff for me :D. One more thing i use RealVNC to connect to it because i have the server in a cupboard (ventilation is fine) would there be a VNC equivalent on ubuntu???

---

### Post by Wide on 2006-04-27
[QUOTE=mrvanx]

Am i able to perform these tasks and more using ubuntu instead??[/QUOTE]


Not only will it do that but will give you forever happiness;)

---

### Post by mrvanx on 2006-04-27
:D :D :D

Cool!

Ok these apps ive got a feeling is what il need to use:

Web server (php/mysql) : Apache, php, mysql
Email server : DONT KNOW
Printer server : cups???
File sharing : samba???
vnc : realvnc (unix version)

think these sound ok, what does everybody think?

---

### Post by khightower on 2006-04-27
[QUOTE=mrvanx]:D :D :D

Cool!

Ok these apps ive got a feeling is what il need to use:

Web server (php/mysql) : Apache, php, mysql
Email server : DONT KNOW
Printer server : cups???
File sharing : samba???
vnc : realvnc (unix version)

think these sound ok, what does everybody think?[/QUOTE]

The good thing you can try all this for free.

---

### Post by manicka on 2006-04-27
[QUOTE=mrvanx](ventilation is fine) would there be a VNC equivalent on ubuntu???[/QUOTE]

yes VNC is available for linux

---

### Post by 3rdalbum on 2006-04-28
If you're used to using the GUI in Windows XP, then you'll almost certainly want to upgrade the RAM in your computer before switching to Ubuntu. 96 megs isn't officially enough to run Gnome or KDE in Linux, although the Xfce desktop environment (xubuntu) will work.

If you don't mind using the command line to set up your server, then what you've got will work nicely. I've also heard that you can start up Gnome with only 96 megs, but I can't confirm it. Try installing Ubuntu, and if you can't get the GUI then type:

```
sudo apt-get install xubuntu-desktop
```

Downloading will ensue, then when it's finished type "startx" and you'll be in business.

---

### Post by mrvanx on 2006-04-28
Im tempted to shell out for some more RAM for it, would 512MB be worth going for?

---

### Post by khightower on 2006-04-28
[QUOTE=mrvanx]Im tempted to shell out for some more RAM for it, would 512MB be worth going for?[/QUOTE]

512 is a sweet spot for price and performace with most OS's

---

### Post by Rinzwind on 2006-04-28
[QUOTE=mrvanx]Im tempted to shell out for some more RAM for it, would 512MB be worth going for?[/QUOTE]
Yes, absolutely. And 512 isn't going to be very expensive aswell. 

If you can afford it you should.

---

### Post by pshnfry on 2006-04-28
With a P3 500 I'll assume your board is PC100/PC133?  Where I am this is now quite expensive new.  I'm running Breezy 5.1/Gnome on Celeron 733, 4gb hdd, 448mb PC100 ram (leftover 256+128+64) and an old Rage 128 ATI card.  Multiple browser windows, downloads, terminal sessions etc and while it maxes every thing out it's still stable and reasonably responsive compared to our "real" pc's in the house.  To continue with the P3 box in its current role try your nearest pc upgrade shop for s/hand ram or leftovers from friends/colleagues/family pc upgrades.  Should almost be able to get this ram for next to nothing s/hand.

---

### Post by mrvanx on 2006-04-28
currently bidding for 512MB PC133 ram, £30 should cover it. theres an 80GB hard drive enroute for it to use aswell, thinking of dual booting it with the current XP OS on it to start with to rule out annoying the mrs when im fiddling with ubuntu :):)

I ran the live version of 5.10 last night on my 'real' PC (Athlon XP 2200 overclocked to 2177MHz with 1gb ram) and it seems REAL user friendly compared to other distros ive tried.

---

### Post by Rinzwind on 2006-04-28
[QUOTE=mrvanx]currently bidding for 512MB PC133 ram, £30 should cover it. theres an 80GB hard drive enroute for it to use aswell, thinking of dual booting it with the current XP OS on it to start with to rule out annoying the mrs when im fiddling with ubuntu :):)

I ran the live version of 5.10 last night on my 'real' PC (Athlon XP 2200 overclocked to 2177MHz with 1gb ram) and it seems REAL user friendly compared to other distros ive tried.[/QUOTE]
Do you need more converting? :D
Did you ShipIt your free cd's yet? :D

---

### Post by az on 2006-04-28
Dapper's server install disk will have a turn-key LAMP installation.  You boot, pick LAMP and you reboot into your LAMP box.

---

### Post by Sef on 2006-04-28
> Dapper's server install disk will have a turn-key LAMP installation. You boot, pick LAMP and you reboot into your LAMP box.

That will be nice.  I am planning to set up a server.  Maybe if can get hold of an old computer that I know of, I will make it a server.

---

### Post by mrvanx on 2006-04-28
[QUOTE=azz]Dapper's server install disk will have a turn-key LAMP installation.  You boot, pick LAMP and you reboot into your LAMP box.[/QUOTE]

Please explain more, cant tell you how much that would help me out.

Just had a think and dont really need a webserver now, just installed the 80gb hard drive in it (copied partitions across from 8gb) thats gone ok, the bidding for the RAM won so that should be with me soon too!!

---

### Post by mrvanx on 2006-05-02
Quick update (bump hehe) 

My stick of 512MB ram will be heading here this week, just picked up a pc mag which has a version of dapper drake on it. Is it worth goin with this one?? or shall i stick with 10.5 i have on DVD?

---

