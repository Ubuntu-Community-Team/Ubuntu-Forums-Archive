---
title: "Fresh install of Ubuntu 7.0.4"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by milkolate on 2007-06-29
I saw some guides in the internet but I want to know stuff directly from you.

1. What should I install so that I can play any media file? Is VLC enough?
2. Is there a need to install Automatix2? There's already an Add/Remove Program function native to Feisty Fawn.
3. How to uninstall Evolution? I can't remove it since there are other dependencies (according to Ubuntu).
4. I'm using WLAN, Should I get WiFi radar or is the Network manager enough?
5. What are the other essential programs?
6. I'm using a laptop, are there special programs for laptop-users?

Thanks a lot! Please do help me so I won't switch back to XP :p

---

### Post by starcraft.man on 2007-06-29
> **milkolate said:**
> I saw some guides in the internet but I want to know stuff directly from you.

1. What should I install so that I can play any media file? Is VLC enough? [COLOR="Blue"]Yes. The only thing VLC doesn't play is the stupid Real format. I _despise_ them, I do.[/COLOR]
2. Is there a need to install Automatix2? There's already an Add/Remove Program function native to Feisty Fawn.[COLOR="Blue"] No. There is no "need". Between Add/Remove Synaptic and the Terminal there is nothing that cannot be done with a bit of patience, net information and forum help.[/COLOR]
3. How to uninstall Evolution? I can't remove it since there are other dependencies (according to Ubuntu).[COLOR="Blue"] Why? I don't think you can just yank it out, I mean the calender function depends on it for one, as do a few other things I believe.[/COLOR]
4. I'm using WLAN, Should I get WiFi radar or is the Network manager enough? [COLOR="Blue"]Network manager usually works for most wifi I think. WPA supplicant or a few other tweaks might be needed for some cards. I can't help beyond that, I'm an ethernet guy on Linux.[/COLOR]
5. What are the other essential programs? [COLOR="Blue"]Take your pick. [Browse the selection here.]("http://linuxappfinder.com/") [Or view by alternatives to windows applications you know.]("http://linuxappfinder.com/windows")[/COLOR]
6. I'm using a laptop, are there special programs for laptop-users? [COLOR="Blue"]You need to configure the synaptic program to get the function of your touch pad if you got one/want it, it usually is automatic I think. Other than that no, I don't think so. I can't help on that either, all my linux fun is on a desktop to date.
[/COLOR]
Thanks a lot! Please do help me so I won't switch back to XP :p

Oh and if you want to install the codecs to play files natively,[ read this. ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")Take special note of the blue header for adding extra repos.

[COLOR="Blue"]Wish granted! Any other question?[/COLOR] :D

Edit: LOL! I forgot my blue on 5 and 6 :p.

---

### Post by Seisen on 2007-06-29
1. You need to install the multimedia codecs
2. no
3. Leave it alone its part of Ubuntu Desktop, I know it sucks
4.Network manager is enough
5.It depends on what you like to do on your computer
6.That I don't know.

---

### Post by p_quarles on 2007-06-29
First of all, don't "threaten" to go back to Windows. You're likely to get a lot fewer responses that way.

1. VLC is not enough. Look in the user documentation Wiki for help with getting the packages necessary for playing restricted formats.

2. No, there's no need and it's buggy.

3. Don't uninstall it. It won't prevent you from using another e-mail client, and other things depend on it.

4. Network manager is enough. If that doesn't work, you probably need to install a proprietary wireless driver with NDISwrapper.

5. Depends on what you want to do. The basics all ship with the Ubuntu installation CD.

6. Again, the installation CD is pretty good about detecting and setting up a laptop installation. You might want to add a temperature monitor applet and CPU scaling controls, but they're not necessary. 

Hope this helps.

---

### Post by bradmayne on 2007-06-29
1.Q:   What should I install so that I can play any media file? Is VLC enough?  A:  VLC will work although rhythmbox works is just as good for music.  Totem is good for for video.  

2. Q: Is there a need to install Automatix2? There's already an Add/Remove Program function native to Feisty Fawn.  A: That's simple! no! you will be fine without it!

3.Q:  How to uninstall Evolution? I can't remove it since there are other dependencies (according to Ubuntu).  A: Why do you want to uninstall it? Just leave it be

4.  Q: I'm using WLAN, Should I get WiFi radar or is the Network manager enough?  A:Network manager is enough

5.Q:  What are the other essential programs?  A: That depends on what your needs are!

6.Q: I'm using a laptop, are there special programs for laptop-users?  A:  Possibly.  That depends on several factors: the brand, the hardware, what your needs are once again.  

7.  Q: Am I insane for answering these questions.  A:  Yes ;)  Please post more specifics here and maybe i can be of more help.

---

### Post by milkolate on 2007-06-30
What is the best alternative to Yahoo Messenger? My problem with GAIM is that it doesnt coppy the  aliases of my contacts. So I don't know their identitites.

What is the best anti-virus for linux?

---

### Post by avik on 2007-06-30
> **milkolate said:**
> What is the best anti-virus for linux?

No need :p  Just don't do anything stupid like let a program from a source you don't know run as root, and you'll be fine.

---

### Post by sloggerkhan on 2007-06-30
With GAIM, you can create your own permanant aliases.
(Just in case you didn't know.) You can also use a GAIM plugin to sync it to your evolution address book.

---

### Post by coolen on 2007-06-30
1. You can use VLC, or get the multimedia codecs. I personally prefer to use native apps whenever possible, but VLC will play pretty much anything you throw at it.
2. No need. Automatix (and EasyUbuntu, which I used previously in favour of Automatix) was most useful for installing said codecs, which can now be installed throw Add/Remove and a few lines at the terminal. Automatix does give you a lot of other applications, too, but you can easily install these on your own. It doesn't stick to the repositories, which I definitely don't like, and it killed my Edgy install a while back.
3. The calendar function is provided by Evolution, so it's kind of needed. You could probably remove it and reconstruct your system, but I'd have no idea where to start. My advice is to just ignore it.
4. Network Manager works for me, and Wifi Radar doesn't. Go figure. Network Manager should do pretty much anything for you. Top stuff.
5. k9copy, for DVD shrinking. Works beautifully. Trevino's repository ([http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)) has a lot of good ones. aMSN + tcl8.5 + tk8.5 + tile from there will give you a very good MSN client. It also has the standalone flash player (official one. Proprietary, but Gnash is still rather beta). He also has some good eye-candy: kiba-dock, avant, beryl, etc. Wine will be helpful if you're a gamer, or hanging on to a few Windows applications that are known to work. Of course, then there are native games: the repositories contain some real gems.
6. Programs for IR/bluetooth, perhaps? If you're having troubles with suspend/hibernate, I found a nice howto ([http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)) I'm going to try out now.

That's all my advice. Hope it was useful.

---

