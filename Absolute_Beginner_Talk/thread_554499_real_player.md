---
title: "real player"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by haZZe08 on 2007-09-19
i downloaded automatix so i can install real player easily but unfortuantely ubuntu gutsy 7.10 doesnt support it. So i need some help to get real player to work. I dowloaded it to my desk top and don't know how to install in terminal. any suggestions, i'm new to comps and new to ubuntu. Just installed yesterday

---

### Post by Perfect Storm on 2007-09-19
Keep away from automatux/easyubuntu etc. if you want to avoid playinh hazard with your system.

Have you enable mediabuntu/universe/multiverse in your sourcelist?

(note: if you're a beginner, you should wait playing with a development release)

---

### Post by haZZe08 on 2007-09-19
how can i check if they've been enabled? i honestly don't know, jus downloaded the software updates it tells me to. Downloaded real player so i can watch the matrix. It says that it cant play in totem since it needs real video 4.0 codec plugin. It looks for the codec but says there are no matches found

---

### Post by Perfect Storm on 2007-09-19
Actually it would be better if you try mplayer+mplayerplugin+codec than totem, but the totem plugin you're looking for is poroperly in the source you havn't enable.

Any reason you are using a development release of ubuntu. You know it can break from one day to another.

check;
```
cat /etc/apt/sources.list
```

---

### Post by haZZe08 on 2007-09-19
i'm new to the comp world. i jus pieced together my comp and was looking for an OS instead of windows. Saw an ubuntu dowload option foooo freeeee! and here i am. I ran that code but i dont think it did anything. Tried viewing the matrix again but no dice.

---

### Post by Perfect Storm on 2007-09-19
I suggest you'll go back to 7.04 

and read this, before advancing into something more difficult; 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and

some helpful stuff; [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by misfitpierce on 2007-09-19
Automatix is risky.... Easy Ubuntu is perfectly safe. "
**Is it safe?**

 Yes, EasyUbuntu, unlike its predecessors is now capable of doing its job without even touching your system setup (such as your sources.list). It does not force install packages. Any modifications made are backed up."

---

### Post by Jeroen Vernooij on 2007-09-19
Hi,
the command that Artificial Intelligence let you run, only views your current repositories (these are databases with packages in it which you can install)
If you just installed 7.10, you obviously won't have the medibuntu repository enabled because it doesn't come pre-installed.

However, you don't gain anything with medibuntu repositories, because Realplayer isn't in them:
[http://www.medibuntu.org/packages.php](http://www.medibuntu.org/packages.php)

So I would recommend Easyubuntu.

---

### Post by Perfect Storm on 2007-09-19
Yeah, but again, it's not recommendable for a very new beginner to fiddle with a development version. To get the most pleasent linux experience it's better with something stable and throughout tested ;)
When he/she good the basic knowledge about linux, some basic commands etc. he/she could go for an upgrade.


misfitpierce;

Point taken.

---

### Post by Jeroen Vernooij on 2007-09-19
An even easier way it to download and run this file:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)

Got it from [http://ubuntuguide.org/](http://ubuntuguide.org/) : lots of useful information.

---

### Post by haZZe08 on 2007-09-19
> **Jeroen Vernooij said:**
> An even easier way it to download and run this file:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)

Got it from [http://ubuntuguide.org/](http://ubuntuguide.org/) : lots of useful information.

noice!... that worked... another question tho, think easy ubuntu didn't download correctly since i cant open it. When I try and open it, it asks me for my password and then does nothing.

---

### Post by Jeroen Vernooij on 2007-09-19
I have the same problem on my 7.10 installation. Can't help you with that one.
Happens more with alpha software, that's why they say to use stable software.

---

### Post by haZZe08 on 2007-09-19
another question i have is...
1.can beryl run on 7.10?

2. where and how can i download?

3. would it normally be installed off of easyubuntu?

---

### Post by haZZe08 on 2007-09-19
now i have a problem with real player.

when i watch a movie on real player and rotate the cube, it terminates all apps i have running and takes me to the login window...lol

---

### Post by Jeroen Vernooij on 2007-09-19
beryl is replaced by Compiz Fusion.
Compiz fusion is newer and better.

Compiz fusion is installed and enabled by default in 7.10
You can turn it on or off in the Appearance applet: system->prefs-> appearance -->tab: desktop effects

What you can do is install compizconfig-settings-manager and compiz-fusion-plugins-extra

---

### Post by haZZe08 on 2007-09-19
how do i install those  extra features?

---

### Post by haZZe08 on 2007-09-19
nevermind, got'm coach

---

### Post by hagarid on 2007-10-02
Thank you Jeroen Vernooij that was much easier than I had thought.

---

### Post by odzk on 2007-10-02
> **Jeroen Vernooij said:**
> An even easier way it to download and run this file:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)

Got it from [http://ubuntuguide.org/](http://ubuntuguide.org/) : lots of useful information.

i dont know if the problem is on my comp or what but everytime i clicked on the link above it keeps on going to imageshack.us is there a problem on the link.. thanks i also need this

---

