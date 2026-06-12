---
title: "installing google earth"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by robari on 2007-11-11
Has anyone had the below error after installing Google Earth on Linux? If so could you please tell me what i am doing wrong?

[B]gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/B]

---

### Post by bulldog on 2007-11-11
Try automatix,this can installed it for you and more if you want;

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by atomkarinca on 2007-11-11
after you download the .bin file, you should prompt to the directory using terminal

```
cd /path/to/the/file
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by stimpack on 2007-11-11
atomkarinca is correct.

That makes it executable. Then it knows to execute it, instead of trying to find (in this case gEdit) a program to open it.

You should be able to right click and change permissions to executable in the file GUI too, if you have a cli aversion :)

---

### Post by P4man on 2007-11-11
Do not use automatix !!


> Automatix exists to satisfy a genuine need, and further work should be
carried out to determine whether these user requirements can be
satisfied within the distribution as a whole.[B] However, in its current
form Automatix is actively dangerous to systems -[/B] ranging from damage
to small items of user configuration, through removing user-installed
packages without adequate prompting or warning and up to the (small
but existing) potential to leave a system in an unbootable state.

The current design of Automatix precludes any reasonable way to fix
some of these problems. It is attempting to fulfil the role of a
high-level package manager without actually handling any sort of
dependency resolution itself.

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by bulldog on 2007-11-11
I use automatix from starting with Dapper and never ever had any problem with it.
From the automatix FAQ:
```
 Does Automatix2 break Ubuntu upgrades?

    * The chances of Automatix being behind the breaking of a Ubuntu upgrade is as high as the packages which Ubuntu releases for that release and the subsequent one.
 Most of what Automatix installs comes directly from the Ubuntu repositories and is installed using apt-get (just like in synaptic and Add/Remove).
It is more likely that an upgrade problem lies upstream in the Ubuntu repositories. In fact Ubuntu has been notorious for breaking xserver packages several times on stable releases in the past. 
They have also been extremely notorious for passing on the blame to Automatix for their own failings (which they still haven't stopped doing). 
It is unfortunate that many people actually believe in this FUD and help spread it even further rather than trying to investigate the real cause of a breakage. 
```

[http://getautomatix.com/wiki/index.php?title=FAQ](http://getautomatix.com/wiki/index.php?title=FAQ)

And I believe there's some truth in that statement.
Ofcourse you're free in what you believe and what you want to use,but I still use automatix on Gutsy.

---

### Post by P4man on 2007-11-11
The Ubuntu Technical Board review of automatix addresses many more issues than just the breaking of distri upgrades. Having had my share of trouble with Automatix, i'd be very reluctant to recommend using it, especially for things you can do easily with apt.

---

### Post by bulldog on 2007-11-11
> **P4man said:**
> The Ubuntu Technical Board review of automatix addresses many more issues than just the breaking of distri upgrades. Having had my share of trouble with Automatix, i'd be very reluctant to recommend using it, especially for things you can do easily with apt.

read the last line in the posted FAQ,end of discussion from my part.

---

### Post by ViRMiN on 2007-11-11
Why not add the Medibuntu repo and grab it from there? [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by P4man on 2007-11-11
> **bulldog said:**
> read the last line in the posted FAQ,end of discussion from my part.

If I or you or anyone on this board would just shout "automatix sucks" it might be FUD. But if Ubuntu's Technical Board has looked in depth at the app and drawn  conclusions which it has clearly substantiated, its not FUD.  For some reason, I tend to give more weight to Ubuntu's Technical Board than the guys  that created the original ugly hack that was called Automatix (you could call it a polished hack now I guess ;) )

Of course, its a free world, so by all means use whatever works for you, but allow me to warn other newbies that using Automatix is not without risk.

---

### Post by carloslosgrande on 2007-11-11
[FONT="Comic Sans MS"]Hi Robari. After downloading, go to the .bin file and right click, then 'properties' and select 'permissions' and tick the box 'allow executing file as program'
Then when next you click on this file it will automatically install.

This is the gui method for simplicity - for dummies like me[/FONT]

---

### Post by Casual Fan on 2007-11-12
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi Robari. After downloading, go to the .bin file and right click, then 'properties' and select 'permissions' and tick the box 'allow executing file as program'
Then when next you click on this file it will automatically install.

This is the gui method for simplicity - for dummies like me[/FONT]

From one dummy to another, thanks.

---

### Post by Flying caveman on 2007-11-12
All you have to do is download GoogleEarthLinux.bin from the google site. Right click on the icon make it executable and click on it again. select run in terminal.  Done.

EDIT Ooppps!  the answer is already here. I didn't see the second page of this thread.

---

