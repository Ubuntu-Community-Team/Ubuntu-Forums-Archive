---
title: "Breezy LiveCD - Kernel Panic"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by QuartersMostly on 2006-03-30
Hi everybody,

I'm basically completely new to Linux, though I did previously do a stage 3 Gentoo install, which I gave up on when I realized how much nonsense you have to go through to do pretty much anything. So I found Ubuntu while looking for a relatively simple Linux distro.

Anyway, I downloaded the LiveCD iso, did an md5checksum (it was fine) and burned it, and tried to boot. I barely got anywhere before (maybe 30 seconds after hitting enter when prompted) I received a message saying something along the lines of "ext2-fs error (device ram0): ext2_check_page: bad entry in directory #209: rec_len is smaller than minimal." I searched the forums pretty thoroughly and basically the only recommendation I found was re-burn the CD at a slower speed. I re-burned, this time at 4x, received the same error. Is it worth burning another CD? Or could there be something else going on?

I'm running XP on a 1.26 ghz Athlon, 512 MB of RAM. I also tried on my work PC, which is a P3 also with 512 MB of RAM and received the same error again. Any ideas? I'd love to be able to try Ubuntu out a bit without having to do a full install. Thanks!

---

### Post by gord on 2006-03-30
the fact that you got the same error on two diffirent machines suggests to me that your cd-burining drive is corrupting the cd somehow, if you have some other way of burning the disk (on a friends pc maybe?) i would recomend that, otherwise you might want to try ordering some free cd's from [shipit](https://shipit.ubuntu.com/), they are compleatly 100% free but they will take a while to get to you (anything upto 2 months really). but you will get a few live cd/install cd combo's so if you end up liking ubuntu you can share them with your friends and family :)

---

### Post by Mustard on 2006-03-30
I'd have to agree that the error occuring on two different PC's points the finger at the CD being the problem.  Somewhere along the line something is beening corrupted on the CD.

---

### Post by QuartersMostly on 2006-03-30
Well, that's an easy enough recommendation. Shame it's incompatible with my impatience. I'll order a couple CDs and report back in a month or so... Thanks!

---

### Post by QuartersMostly on 2006-03-30
In case anyone has a similar problem, I decided to try burning the CD just one more time, but this time using [CDBurnerXP]("http://www.cdburnerxp.se/") instead of Nero. And this time it worked. Sort of.

Now I just have to figure out why directly after the Ubuntu splash screen goes away, a plain brown screen comes up accompanied by a repetitive "XP alert"-type sound. I'm guessing Ubuntu isn't fond of my integrated sound card. But that's a matter that requires some forum searching and maybe another thread...

---

### Post by Mustard on 2006-03-31
[QUOTE=QuartersMostly]In case anyone has a similar problem, I decided to try burning the CD just one more time, but this time using [CDBurnerXP]("http://www.cdburnerxp.se/") instead of Nero. And this time it worked. Sort of.

Now I just have to figure out why directly after the Ubuntu splash screen goes away, a plain brown screen comes up accompanied by a repetitive "XP alert"-type sound. I'm guessing Ubuntu isn't fond of my integrated sound card. But that's a matter that requires some forum searching and maybe another thread...[/QUOTE]

If the 'XP Alert' sound is like some quick drum beats, then that is normal.  It sounds like your graphics card is the trouble actually.  Try hitting ctrl + alt + f1 to get to a terminal, login with your username and password.

From there you can try reconfiguring the xorg.conf file to use 'vesa' drivers.  Use this command to reconfigure xorg.conf...

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the default answers for everything usually, but when you get to the graphics driver section, choose 'vesa' drivers.

To startx try

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

---

### Post by QuartersMostly on 2006-04-02
Well, thank you again for replying. I tried this yesterday, but I got hung up again at the same place with the same drum beat sound (you're right, that's probably a better description). I recall reading that ATI cards tend to give a bit more trouble than nVidias, and I have a ATI Radeon 9800 Pro. I'll search a bit about that.

I tried installing as usual and then going to a terminal and making the changes, as well as using the live-expert mode and specifying the vesa drivers there. Same result either way. When I specify vesa rather than xorg, though, I can't get back to a terminal after I get hung.

---

