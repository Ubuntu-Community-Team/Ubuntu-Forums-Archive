---
title: "Fspot can't find eog"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by maljaros on 2007-12-08
I have been running Gutsy and Fspot for two weeks and they both do good things for me, but I can only see the thumbnails in Fspot.  Try to "open with" and get "no applications available".  Reloaded Fspot - didn't help.  Reloaded eog - didn't help.
Although Synaptic says that eog loaded successfully I cannot find it on the menu.
I also have gThumb up, but Fspot doesn't find that either.
Any ideas guys?

---

### Post by ptn107 on 2007-12-08
```
sudo apt-get remove --purge eog -y && sudo apt-get install eog -y
```

---

### Post by maljaros on 2007-12-09
Thank you ptn107 for your helpful response.  The command > **ptn107 said:**
> ```
sudo apt-get remove --purge eog -y && sudo apt-get install eog -y
``` seems to have reloaded eog (where do I find out how to do this stuff?) but has not solved the problem.
If I right-click a .jpg file in File Browser it offers me Open With:
Firefox Web Browser
F-Spot Photo Viewer
GIMP Image Editor
gThumb Image Viewer
Mozilla/Thunderbird Mail News
so it seems that any or all of these are mounted and available.
But if I right-click an image in F-Spot Photo Manager I still get No Applications Are Available.
Should I try
sudo apt-get remove --purge f-spot -y && sudo apt-get install f-spot -y:
confused:

---

### Post by PsychoAlienDog on 2007-12-09
I'm having the same problem with f-spot.  It started when I installed Ubuntu Studio.
It appears as though f-spot uses gnome vfs to populate the open with menu (see [http://www.mail-archive.com/f-spot-list@gnome.org/msg02683.html](http://www.mail-archive.com/f-spot-list@gnome.org/msg02683.html)).

---

### Post by ptn107 on 2007-12-09
```
sudo apt-get remove --purge f-spot -y && sudo apt-get install f-spot -y
```

Give it a try.

---

### Post by PsychoAlienDog on 2007-12-09
that didn't worrk for me.

---

### Post by jordanmthomas on 2007-12-09
Try creating a new user and see if it works from a fresh account.
Odds are, a setting is just screwer up somewhere.  This will confirm if it's a configuration problem or a problem with the program itself.

The reason eog might not show up in your menus is that it's called "Image Viewer" and not Eye of Gnome.

---

### Post by PsychoAlienDog on 2007-12-09
creating a new user did not fix it, **however** I did find the solution though.
there seems to a conflict between f-spot and gnome-raw-thumbnailer.
maljaros, try uninstalling gnome-raw-thumbnailer, that worked for me.

---

### Post by ptn107 on 2007-12-10
If a solution or workaround is found, please mark the thread as **[Solved]** which will help out others seeking a solution.

---

### Post by maljaros on 2007-12-11
Nope, in my case gnome-raw-thumbnailer was not installed - so I did install it and then removed it .  No change.

---

### Post by wickerman1413 on 2008-04-26
I have the same problem (F-Spot -> Open With -> No applications available) though via a different route.

I was running Ubuntu 7.10, with GIMP and F-Spot happily working, moved my home folder to a seperate partition and then did a fresh install of Ubuntu 8.04. This gave me GIMP 2.4 and F-Spot 4.2 - same versions I had previously had. What was missing was the ufraw gimp plugin. I tried Applications -> Add/Remove and added Ufraw, but this didnt give me a GIMP plugin. I then did a "sudo apt-get install gimp-ufraw" which now allows me to right click on files in Nautilus, open with GIMP and have Ufraw intercept it, deal with any RAW specific settings, and finally open the image directly into GIMP.

No joy with f-spot though. 

A download and quick grep of the F-Spot source code shows src\Extensions\OpenWithMenu.cs is the class that creates this menu and appears to create the Open With menu by polling for suitable registered MIME applications. I havent got any further than this, so if someone could point me in the right direction it would be much appreciated.

---

### Post by the_nz_monkey on 2008-05-03
Hi wickerman, I've been fighting with the same problem here - I've managed to get something that works, though..

Oddly enough, with Hardy, installing gnome-raw-thumbnailer seems to allow F-spot to open my raw images using UFRaw.  In Gutsy, the raw thumbnailer stopped the F-spot Open With menu working on Raw images; now the opposite seems to be the case.

this is with F-Spot 0.4.3.1, so I'm not sure it'll be the same for 4.2.

Cheers
NZMonkey

---

