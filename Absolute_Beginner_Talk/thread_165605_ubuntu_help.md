---
title: "ubuntu help"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by yugiohmaster on 2006-04-24
hello im new to this linux/linux stuff cause i spend most of my time with windows. but i recently installed ubuntu(hoary hedgehog) and it installed it .i think? but when i turn on my pc is in command prompt and it says you got new maill and asks for my pass and user then i put it the it says user@ubuntu:"$ like is waiting for some command but what should i do next?.:-k [-(

---

### Post by ncappel1 on 2006-04-24
Hoary is very much an old version of Ubuntu, the next step up is Breezy Badger, and now in May or June The next version will be released, Dapper Drake. I would simply suggest getting a breezy cd and reinstalling, you'll be saving yurself time and a headache. You also have nothing to lose, do you?

---

### Post by Nano Geek on 2006-04-24
That's odd that Ubuntu act that way. By the way, there is a newer version of Ubuntu: Ubuntu 5.10 Breezy Badger, and in June they will release 6.06 Dapper Drake. So I would suggest downloading the newer version, you can find it [here]("http://www.ubuntu.com/download").

---

### Post by Sutekh on 2006-04-24
Did you chose to do a normal installation, by pressing Enter at the main screen?  Or did you choose to do a 'server' or 'expert' installation?

---

### Post by KLineD on 2006-04-24
normally Ubuntu installations give you a graphical screen where you can put your username and password and then use a graphical system. My guess is that your system is not configured for graphical desktop but just to be sure type the following after you login:

```

sudo gdm

```

It will ask for your password, type it again and then you should be presented with a graphical desktop where it asks for your username and password. If it doesn't, make a note of the error and post it here so we can try to help.

---

### Post by yugiohmaster on 2006-04-24
thats the prob it said type server for basic install because i only got 1.5gigs  so i did the basic i didn't know it would be such a pain

---

### Post by Sutekh on 2006-04-24
That's cool, but at least we know that the installation was successful.

Now the trick will be installing a GUI that you can fit on 1.5GB.  I wouldn't recommend the more popular GNOME/KDE desktop environments.

You may want to check out these links for some options for low memory systems.

[Ubuntu Wiki - Low Memory System](https://wiki.ubuntu.com/Installation/LowMemorySystems)

[Ubuntu Wiki - OpenBox](https://wiki.ubuntu.com/Openbox)

They could be a little harsh for someone new to Linux, but you will find the community here very supportive.

Here are some links for these smaller GUIs, so you can see what they look like

[http://xwinman.org/](http://xwinman.org/)

[XFCE](http://www.xfce.org/) - I think you would probably find this easiest, plus a fair number of people on the forums use Xubuntu (Ubuntu + XFCE)

[IceWM](http://www.icewm.org/)

[FluxBox](http://fluxbox.sourceforge.net/)

[OpenBox](http://www.icculus.org/openbox/) - I use OpenBox, but you may find it hard to configure

---

### Post by yugiohmaster on 2006-04-24
another thing since you seem to know a lot about this stuff when i tried the live cd the os loaded up completly but the screen was like mirrored or like dual just weird wonder if will be the same with the whole installation

---

### Post by Sutekh on 2006-04-24
What sort of video hardware do you have?

Onboard? NVIDIA? ATI?

Some types of video hardware are not as well supported as others, since the card manufacturers are reluctant to release their specs. 

NVIDIA/ATI have their own drivers for Linux, but don't release them in an open way, so Ubuntu doesn't ship with those drivers.  You can install these drivers afterwards to fix any issues.

This is something that is improved with newer releases of Ubuntu too.

---

### Post by yugiohmaster on 2006-04-25
no i got a 3d phantom from pine inc. and another thing i keep getting  id 1 responding too fast disable for 5 minutes and kernel panic and ext3 virtual sector something i have tried it with 2 different hard drives but i don't know whats the problem hope you can help .and whats  the difference between the new one and mine which is 5.04?.

---

### Post by yugiohmaster on 2006-04-25
i really hope somebody can help me with this

---

### Post by pbaehr on 2006-04-25
Don't spend too much time worrying about how well that version works with your computer. A lot of improvements have been made since it was released. I'd advise you to download 5.10 (Breezy Badger) and give that a spin. You may find a lot of the issues vanish.

6.06 (Dapper Drake) is even more refined, however, it's still in beta so it's stability is questionable. I use it without any real issues, but it can't be expected to perform perfectly yet. It will be released from beta in June.

---

### Post by yugiohmaster on 2006-04-25
i really hope somebody can help me with this

---

### Post by ubuntu27 on 2006-04-25
yugiohmaster: SInce you have a low asp. System. Maybe it is betetr to use Xubuntu (ubuntu + Xfce)

Folow this guide: [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by yugiohmaster on 2006-04-28
whats that supossed to mean?

---

