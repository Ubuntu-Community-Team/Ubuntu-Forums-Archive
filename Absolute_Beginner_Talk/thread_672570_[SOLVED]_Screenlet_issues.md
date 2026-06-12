---
title: "[SOLVED] Screenlet issues"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by A4006 on 2008-01-19
I have finally managed to complete my "perfect" desktop using screenlets, only to have this annoying error message pop up when I star the Screenlet Manager- "Unable to connect or launch daemon. Some values may be displayed incorrectly". Then, I discovered that when I log back in, the screenlets disappear and I have to reload them.  I thought it was because I didn't check the "Automatically start at login" box, but it just un-checks itself :-x. Then I noticed that a few screenlets wouldn't load when I clicked or otherwise tried to load them, and I thought "so what, I don't like them anyways", but now none of them work :(.  I'm using Ubuntu 7.10 with (I'm not sure if this matters) Compiz-Fusion and Emerald Themer.

---

### Post by spiderbatdad on 2008-01-19
i don't think screenlets for composite environments are stable yet, so you have to expect problems. There seems to be a shortage of documentation. If you get the ones you want working, you might be able to remember currently running applications under preferences>>sessions>>session options

---

### Post by A4006 on 2008-01-19
Well, I just rebooted into Ubuntu (I dual boot with Vista) and found that the screenlets have started working again.  I'll see if it will remember my settings when I log out this time...

---

### Post by A4006 on 2008-01-19
Nope.  Still "forgot" them, and I tried telling it to remember currently running applications under preferences>>sessions>>session options but all that did was screw up my Vista Menu utility.

---

### Post by eapache on 2008-01-19
As far as I know, screenlets requires a composite environment, so I doubt that's the problem. How did you install them? Through the repo on the screenlets site?

---

### Post by A4006 on 2008-01-19
I used the instructions here <http://hendrik.kaju.pri.ee/screenlets/?q=node/5>, downloaded the tarball, unpacked it and used "sudo make install" in terminal, following the Readme instructions packaged with it.  I was wondering if it could be a problem with either permissions or Emerald, as I am using Compiz-Fusion with Emerald instead of Beryl.

---

### Post by trash on 2008-01-19
I get the 'unable to connect' message everytime i open screenlets too, and ya it's still flaky. On boot up they always start however it's not uncommon that only 4 out 5 start. I seem to remember it took me a while to get them all working it was a mystery and I almost got rid of them till one boot they all appeared... just keep enabling them and selecting on startup and eventualy it'll stick, did for me.

---

### Post by A4006 on 2008-01-20
Kind of like how in Windows things randomly start and stop working for no reason at all?

---

### Post by trash on 2008-01-20
> **A4006 said:**
> Kind of like how in Windows things randomly start and stop working for no reason at all?

Yes, but it takes way longer in Vista:lolflag:

---

### Post by SunnyRabbiera on 2008-01-20
uh huh, please keep in mind stuff like this is still under development so its no wonder why you have issues...
but by far i feel the screenlets in ubuntu is far more stable then anything in vista, if they crash the system it usually easy to resolve in linux unlike vista where a full restart is needed.

---

### Post by A4006 on 2008-01-20
I'm beginning to think that the root of all my problems might be in the permissions. I think that it might be trying to save the "Automatically start at login" command but doesn't have the permissions to.  This wouldn't be the first time that has happened....

---

### Post by Thund3rstruck on 2008-01-20
Yup, toss screenlets out the window. They have never worked correctly without crashing and contributing to overall poor system performance. 

They're cool to showoff but that's all

---

### Post by eapache on 2008-01-20
Try installing the latest version from here:

[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_users_.28Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon.29)

---

### Post by A4006 on 2008-01-20
So should I get rid of the version I downloaded from here <http://hendrik.kaju.pri.ee/screenlets/?q=node/5>before installing the ones from Screenlets.org, or will it just overwrite those?  Also, could my problem be coming from not having this stuff-

"First of all you need python (tested with 2.4 and 2.5). Further you need pygtk (at least version 2.10), pycairo, python-xdg and the package python-gnome2-desktop."?

---

### Post by eapache on 2008-01-20
If you are using the repos, then you don't need to do anything. If you downloaded it and then make installed it, use the link I gave you. You shouldn't need to remove anything first.

---

### Post by A4006 on 2008-01-20
Unfortunately, I have read your last post too late, because I went ahead and removed the old version, and then reinstalled it using the link you gave.  I still have the same problems, only now it can't find some of the screenlets.

---

### Post by A4006 on 2008-01-22
I just tried out gDesklets, and they do work, too, although I must assume that the "g" stands for "gay".   I hate them.  Besides looking like they came from the late '90's, they give me more error messages than I had with the Screenlets.  I am wondering weather Emerald themer may be a problem?

---

### Post by spiderbatdad on 2008-01-22
Emerald has no effect on the weather. Whether it would effect gdesklets is highly doubtful. It is a windows theme manager. Trying to run desklets or screenlets in a gl environment is the problem. Screenlets are definitely not supported. Don't drag homophobia into your posts.

---

### Post by A4006 on 2008-01-22
Whether the weather is affected by Emerald is debatable...  Anyways, sorry for the derogatory comment about gDesklets.  I just made a script to run the screenlets on startup using this post I found  [http://ubuntuforums.org/showthread.php?t=555795]("http://ubuntuforums.org/showthread.php?t=555795") but I have no idea how to go about executing it on startup.  I've also done a test run of it and it only loads the first screenlet:(.  Here is the script.. keep in mind that I have almost no experience with programming...

python /home/a4006/.screenlets/Sidebar/SidebarScreenlet.py
python /usr/local/share/screenlets/Calendar/CalendarScreenlet.py
python /home/a4006/.screenlets/ClearWeather/ClearWeatherScreenlet.py
python /home/a4006/.screenlets/CPU_Meter/CPU_MeterScreenlet.py
python /home/a4006/.screenlets/NowPlaying/NowPlayingScreenlet.py
python /home/a4006/.screenlets/WaterMark/WaterMarkScreenlet.py

What have I done wrong?

---

### Post by spiderbatdad on 2008-01-22
you'll need to make the script executable```
sudo chmod a+x /path/to/script
```

then you can add it to startup programs...System>>Preferences>>Startup Programs>>Add...then navigate to it using browse. After adding go to the sessions options tab and select remember current session. Sometimes adding startup programs is quirky and takes a few attempts. There are other ways also, like adding the script to init.d, but I haven't tried that. Haven't looked into py really, though I would think you need a ";" possibly after each line??

---

### Post by A4006 on 2008-01-23
I tried adding a ";" after each line and it did nothing, still just loads the first screenlet.  What is interesting is that after I quit the first screenlet, the next one I put in the script pops up, and so on.

---

### Post by eapache on 2008-01-24
Put an ampersand (&) at the end of each line. This will tell it to run the next line even though the last line isn't finished yet. The last line normally doesn't finish until the program closes.

---

### Post by A4006 on 2008-01-24
Thanks, all of you.  Finally, they all load at startup, with no problems (yet, at least).  I'm very grateful for your help.

---

### Post by trash on 2008-01-24
> **A4006 said:**
> Thanks, all of you.  Finally, they all load at startup, with no problems (yet, at least).  I'm very grateful for your help.

Thank you for a workable solution;). After upgrading only half of mt screenlets would load, but all is well now:)

---

