---
title: "Need Kino"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by deville75 on 2006-05-25
I hear Kino is Linux's replacement for Adobe Premiere (video editing software).. Where can i get this program? it's not in the add applications option either.

---

### Post by meng on 2006-05-25
I'm sure it's in the repositories and can be installed by Synaptic, that's how I did it. What's your source list?

---

### Post by bruce89 on 2006-05-25
You will have to add the universe reposistory.

---

### Post by fyo on 2006-05-25
Unfortunately, the version from the universe repository is over a year old. It freezes when trying to open the DV files I have encoded with MainConcept's DV Codec. Reportedly, freeze/crash-on-open issues have been long since fixed, but that does me little good.

I'm not quite ready to compile it myself, sadly. (Basically the reason I got away from my previous distribution, tired of compiling things myself and all the associated head-aches).

---

### Post by Perfect Storm on 2006-05-25
You could also try Cinerella - [http://doc.gwos.org/index.php/Cinerella](http://doc.gwos.org/index.php/Cinerella)

---

### Post by meng on 2006-05-25
Thanks for the info. I have been burned several times by the poor stability. (Save early and often!) However, for my purposes - editing home video - it is great.

---

### Post by fyo on 2006-05-25
[QUOTE=deville75]I hear Kino is Linux's replacement for Adobe Premiere (video editing software).. Where can i get this program? it's not in the add applications option either.[/QUOTE]

Oh, and let's not get ahead of ourselves. Comparing Kino to an $800 fully fledged video-suite is perhaps... no, strike that... definately unreasonable. It's more of a "Pinnacle Studio" or "Ulead Media Studio" than an "Adobe Premier".

For added functionality, you might want to consider using VirtualDub as well (i.e. in addition to Kino). The filters available for VirtualDub and its AviSynth plugin are unparalleled, even by Premier. VirtualDub is a windows-only app, but running it under WINE has worked just fine for me (although installing CODECs was a bit of a hassle).

---

### Post by deville75 on 2006-05-25
[QUOTE=meng]I'm sure it's in the repositories and can be installed by Synaptic, that's how I did it. What's your source list?[/QUOTE]


Repositories? Wheres that? I'm a noob to ubuntu still, so sry for the noob question. 

And Artificial intelligence: is Cinerella another Video editor? guess i'll give both a try and see which one fits me better.

---

### Post by meng on 2006-05-25
Here's a guide on installing software on Ubuntu: [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

For the GUI way, use Synaptic Package Manager, you'll find it under System > Administration. However, you may need to update/expand the repositories that Synaptic/apt-get looks for software in.

I find that Add Applications is limited in software choice and also doesn't work consistently. Hence I always use Synaptic, apt-get or dpkg.

---

### Post by fyo on 2006-05-25
[QUOTE=deville75]Repositories? Wheres that? I'm a noob to ubuntu still, so sry for the noob question. 

And Artificial intelligence: is Cinerella another Video editor? guess i'll give both a try and see which one fits me better.[/QUOTE]

Last question first. Yes, Cinerella is another video editor. You can read about it here:

[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

As for "repositories", these are the "archives" that Ubuntu checks for programs and other packages. There are a number of official repositories, some semi-official and some completely unofficial. 

There's a very nice overview (including why there are more than 1 in the first place) of the official and semi-official repositories here:

[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

There's one more semi-official repository that I just found out about. It's called the "back-ports" repository. Apparantly, Ubuntu policy is to release a new version of Ubuntu exactly every 6 months and to freeze all packages until the next version of Ubuntu is ready. This means that you only get security updates to your installed packages, you don't get "normal" updates. As I mentioned (complained, is perhaps more accurate) before, the version of Kino provided in the official repositories is rather old and contains a bug that prevents me from using it. The "back-ports" repository contains, well, back ports of new versions of packages to the old Ubuntu version(s). In my case, I can actually get a much newer version of Kino from the "back-ports" repository (I haven't tried it yet, so I don't know if my particular issue is fixed).

You can read all about the back-ports project here:

[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---

### Post by deville75 on 2006-05-25
ok well i got cinerella cuz it sounds pretty awesome.. problem is, after following the instructions given at [http://doc.gwos.org/index.php/Cinerella](http://doc.gwos.org/index.php/Cinerella) i cant find the program... where did it install?

---

### Post by meng on 2006-05-25
I'm gonna ask a silly question: did you try alt-f2 then "cinelerra", or alternatively, "cinelerra" from the command line?

---

### Post by deville75 on 2006-05-26
ur silly question worked!  ya i'm that much of a noob..  thx
is there anyway to make a shortcut in applications menu for the program?

---

### Post by ozPATT on 2006-05-26
i think you go to preferences, then shortcuts, then type in what you would type from the command line, and assign a key. :)

---

### Post by meng on 2006-05-26
[QUOTE=ozPATT]i think you go to preferences, then shortcuts, then type in what you would type from the command line, and assign a key. :)[/QUOTE]
In addition to this, you can edit the menu - the way I do it is by installing and using smeg (GNOME menu editor). However, the gurus' method is to write your own .desktop file - which is not difficult - and thereby bypass the need for a GUI frontend.

Some examples of menu entries are included here: [http://ubuntuguide.org/](http://ubuntuguide.org/) Yes it's for Ubuntu 5.04 but the basic principle is the same.

---

### Post by Perfect Storm on 2006-05-26
Just don't use the sourcelist from there, then you should be fine.

---

