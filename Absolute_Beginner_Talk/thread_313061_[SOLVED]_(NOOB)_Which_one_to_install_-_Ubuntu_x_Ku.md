---
title: "[SOLVED] (NOOB) Which one to install - Ubuntu x Kubuntu x Xubuntu"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2006-12-05
Hi all,

  I'm an average Windows user, have used it my whole life. I'm not an expert but I'm pursuing a career into the area (currently working on my MCSA). 

  Anyways, I've always been extremely curious about Linux. I had installed RedHat 9 on an old PC but never got around on using. I also have another 2 Linux/freeBSD devices (Smoothwall & FreeNAS) that run on my network.

  I got a CD from a friend of mine at work with Ubuntu which drove me into wanting to install it on my Laptop. I need to keep my XP on it for my studying thou.

  My laptop is a dell with Pentium M (1.08 MHz), 1GB RAM and has a 60GB HD. I'd like to use 10GB out of it for Linux (which I read is the minimum recommended). 

  My question is, which of these 3 would you recommend me to install:
-Ubuntu 
-Kubuntu
-Xubuntu

  I'm totally noob to Linux, but not dumb (at least is what my mother says :) ). I catch up fast but have limited time due to my studies and my daughter.


Thanks a lot for any input!!!!


Vic

---

### Post by Thav on 2006-12-05
Your laptop should be able to handle any of the three. I can't speak for big differences between Ubuntu/Kubuntu, but Xubuntu is very resource light, so is definitely the choice if you want something fast and low on frills.

---

### Post by d3v1ant_0n3 on 2006-12-05
I would personally recommend installing Ubuntu. And then, once everything is setup and lovely, install the xubuntu-desktop and kubuntu-desktop packages with Synaptic. That way you can try all 3 environments without having 3 seperate installs. They should all run pretty nice and smooth for you, but you might find Xubuntu is that bit faster.

---

### Post by Mimsy on 2006-12-05
I would recommend you install Ubuntu for the same reason I did: It's what the majority of forum users have installed, so you get more help, and quicker. Having limited time on my hands myself, due to studies, every little bit helps.

Other than thatit all comes down to personal preferences.I tried all three but kept Ubuntu because I like Gnome better than the other two desktop environments.

/Mimsy

---

### Post by equal on 2006-12-05
Well, personally, I find Ubuntu less confusing, and there are more people using it, which means that the support base is bigger on these forums. However, if you're looking for something familiar, Kubuntu (which is KDE based) looks and feels a bit more like Windows.

Xubuntu is very different from Windows, and is more suited for people used to Linux, who want a basic striped down GUI.

I'd say download the Ubuntu cd, install it, and then install the Kubuntu desktop by typing the following into your terminal prompt.

```

sudo apt-get install kubuntu-desktop
```

This way you'll be able to alternate between both, and decide which you prefer. Good luck, and be sure to come back with any questions you have once it's installed!

---

### Post by stalker145 on 2006-12-05
> **victorbrca said:**
> My question is, which of these 3 would you recommend me to install:

Vic, Welcome to the family. 

To answer your question without really answering it I would say that it all comes down to preference. As previously mentioned, your computer is surely able to handle any of the environments, it just all depends on what you want.
I always like to send people over to the [Psychocats page]("http://www.psychocats.net/ubuntu/kdegnome") to get information. It's a great resource for the newbie as well as the old fart.

Personally, I use Ubuntu, though I've tried XUbuntu. Mostly it comes down to me having gotten comfortable enough to not desire trying something new... yet;)

---

### Post by Josh1 on 2006-12-05
Ubuntu, Kubuntu (KDE Ubuntu) will eat the laptops resources. I installed KDE on a 1ghz 512 RAM pc and it went slow as hell, Ubuntu ran fine! :).
Depends on preference really, I have a good computer and run Ubuntu with some tweaks but still the default theme + wallpaper.

---

### Post by gn2 on 2006-12-05
I would suggest PCLinuxOS which IMO is a more advanced distro, and more user-friendly.

---

### Post by victorbrca on 2006-12-05
Wow... I never seen so many replies in so little time....

  And thanks a lot for the welcoming messages!!! :)

  I think after all these inputs, I'll install Ubuntu and try out the different desktops for the other version, keeping my eyes open for different versions of Linux like PCLinuxOS once I'm more familiar.

  I will for sure become a member of the forum, and hopefully contribute in the near future.

  Thanks a lot guys!!!  :)


Vic

---

### Post by Mimsy on 2006-12-05
> **victorbrca said:**
>   I will for sure become a member of the forum, and hopefully contribute in the near future.

Welcome to Ubuntu! And to the forums. :)

You will be assimilated. :twisted: 

/Mimsy

---

### Post by IYY on 2006-12-05
Here's my answer to the same question, from a different thread: [http://ubuntuforums.org/showpost.php?p=1848279&postcount=5](http://ubuntuforums.org/showpost.php?p=1848279&postcount=5)

---

### Post by xpod on 2006-12-05
Welcome to THE machine

Given just half a chance and a little patience Ubuntu can become very very additctive...as can the forums.
Enjoy the ride

---

### Post by finferflu on 2006-12-05
Actually, to install the other Ubuntu flavours, I would recommend to use aptitude instead of apt-get, so:

```
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
```

In this way you can easily remove them, if you wish so, by simply issuing:

```
sudo aptitude remove kubuntu-desktop
sudo aptitude remove xubuntu-desktop
```

Have fun! ;)

---

### Post by Circus-Killer on 2006-12-05
> **xpod said:**
> Welcome to THE machine

Given just half a chance and a little patience Ubuntu can become very very additctive...as can the forums.
Enjoy the ride

*scratchy itchy look*

<scratchy-voice>
hey man, you got some beans for me man? c'mon man, dont hold out man, i know you em good beans? some roasted beans. i need the beans!
</scratchy-voice>

---

### Post by victorbrca on 2006-12-06
I guess I'm gonna need to keep a notepad with all these commands until I learn to understand the code... :)

  Installed Ubuntu on my laptop yesterday.. lol.. was up till midnight doing this!!! :)  It took me a while due to the 2x stupid partitions on my dell laptop.

  Gonna spend the day at work playing around and trying to figure couple of little things like enabling WPA, installing video driver and upgrading my firefox to 2.0.

  Thanks a lot for the welcoming. I was always a little skeptic of joining Linux cz some ppl are not so understanding with noobs... But this is good...


Vic..

---

### Post by Bartender on 2006-12-06
victor -
Maybe you can help me help someone else.  I've been posting back and forth with a guy who's got a Dell.  His Dell has some weird partitions, and I'm guessing they're similar to yours.
Here's what the output of ```
sudo fdisk -l
``` looks like on his PC.

Device Boot Start End Blocks ID System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 6689 53689230 7 HPFS/NTFS
/dev/sda3 6690 7112 3397747 db CP/M /CTOS/ ...

Is yours similar?  Just open a terminal and paste in the above command, hit Enter.

I'll PM you.

---

### Post by Sef on 2006-12-06
> Maybe you can help me help someone else. I've been posting back and forth with a guy who's got a Dell. His Dell has some weird partitions, and I'm guessing they're similar to yours.
Here's what the output of
Code:

sudo fdisk -l

looks like.

Device Boot Start End Blocks ID System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 6689 53689230 7 HPFS/NTFS
/dev/sda3 6690 7112 3397747 db CP/M /CTOS/ ...

Is yours similar? Just open a terminal and paste in the above command, hit Enter.

I'll PM you.

If you do resolve anything be sure to post it, so that others may benefit from your knowledge.

---

### Post by Chinkostu on 2006-12-06
> **xpod said:**
> Welcome to THE machine

Given just half a chance and a little patience Ubuntu can become very very additctive...as can the forums.
Enjoy the ride


Very true. sometimes i don't know why i spend the effort of doing things with a working windows partition. i started using it as just a side project to have something to do, and i'm steadily spending more time on it

heck, i've got it installed on a virtual machine in college now!

---

### Post by Bartender on 2006-12-06
Hi, Sef -
I didn't want to prattle on on the main forum, so that's why I PM'ed victor, but will certainly post back if resolved.
Stephen47 started out on a different forum, I suggested he post here and he did
[http://www.ubuntuforums.org/showthread.php?t=312036](http://www.ubuntuforums.org/showthread.php?t=312036)
but didn't hit paydirt.  I know a lot of people have installed Ubuntu on Dells so was hoping for some specific guidance but that didn't happen.
Here's Stephen47's other thread
[http://forums.techguy.org/unix-linux/519487-ubuntu-install.html](http://forums.techguy.org/unix-linux/519487-ubuntu-install.html)
The Dell partitioning discussion starts on the bottom of Page 2.  That'd be great if you had a few minutes to help us!!

---

### Post by victorbrca on 2006-12-06
> **Bartender said:**
> victor -
Maybe you can help me help someone else.  I've been posting back and forth with a guy who's got a Dell.  His Dell has some weird partitions, and I'm guessing they're similar to yours.
Here's what the output of ```
sudo fdisk -l
``` looks like on his PC.

Device Boot Start End Blocks ID System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 6689 53689230 7 HPFS/NTFS
/dev/sda3 6690 7112 3397747 db CP/M /CTOS/ ...

Is yours similar?  Just open a terminal and paste in the above command, hit Enter.

I'll PM you.


Wow, I'm honored to just become part of the forum and be able to help!!!

PM on it's way. Not sure if I should post it here too???

Vic

---

