---
title: "how to erase harddrive for clean install"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by willray on 2007-05-08
Hello. I am running an older Dell Inspiron 8000 pentium iii machine. I have been attempting to move to linux but running into bumps along the way. One of which is a problem with this  model's screen resolution which interferes with the installation process.

I did successfully install old 5.10 version but having learned more think it best for me to use Xubunu.

Bearing the screen resolution issue and with time and efficiency in mind:  Is there anyway to easily erase my harddrive clean and do a completely new install?

THANKS! Will

---

### Post by klayn on 2007-05-08
Boot from the install CD, and when you get to the step where you have to partition your drives, delete all your partitions. Or, alternatively, use the automatic partitioner and tell it to erase your entire disk.

---

### Post by aeiah on 2007-05-08
> **willray said:**
> Hello. I am running an older Dell Inspiron 8000 pentium iii machine. I have been attempting to move to linux but running into bumps along the way. One of which is a problem with this  model's screen resolution which interferes with the installation process.


how does it interfere? is the screen resolution too small (ie, everything looks massive and you cant see enough of the screen) or does your screen show a mangled mess?

all the installation cds have options for a non-graphical install mode, which should get rid of that problem. you'll then be able to set your graphics issue straight once you've installed. the text-only installation procedure is pretty simple. the only thing that can be confusing is the partitioning, but since you just want one partition with the entire drive formatted, that shouldnt be an issue.

---

### Post by starcraft.man on 2007-05-08
You can do the above quite easily, just a note but if you want privacy in mind and have sensitive things you never want to be recovered. [DBAN]("http://dban.sourceforge.net/") is your friend :)

Otherwise, do use the paritioner. I just put it out for the privacy paranoid. Great tool for nuking drives :p

As for the installer problem, try the text install from the Alternate CD [here]("http://releases.ubuntu.com/") if the live cd won't work at all...

---

### Post by willray on 2007-05-08
Having looked around a bit (found this in another ubuntuforum post) it appears that autoclave seems to be an easy way to start over with a freshly erased hd so as to allow a clean install after running it.


you can find autoclave here:
[http://staff.washington.edu/jdlarios/autoclave-discontinued/](http://staff.washington.edu/jdlarios/autoclave-discontinued/)

---

### Post by willray on 2007-05-08
> **aeiah said:**
> how does it interfere? is the screen resolution too small (ie, everything looks massive and you cant see enough of the screen) or does your screen show a mangled mess?

all the installation cds have options for a non-graphical install mode, which should get rid of that problem. you'll then be able to set your graphics issue straight once you've installed. the text-only installation procedure is pretty simple. the only thing that can be confusing is the partitioning, but since you just want one partition with the entire drive formatted, that shouldnt be an issue.


screen shows a mangled mess and is in HUGE resolution so while using the graphical interface I can't read or access all of the needed information in order to move through the install steps.

didn't know i could use a text-only installation, is this what is referred to as alternate boot cd ?

---

### Post by moredhel on 2007-05-08
putting a very strong magnet near the harddrive has always worked for me ;D

---

### Post by starcraft.man on 2007-05-08
> **willray said:**
> screen shows a mangled mess and is in HUGE resolution so while using the graphical interface I can't read or access all of the needed information in order to move through the install steps.

didn't know i could use a text-only installation, is this what is referred to as alternate boot cd ?

Yes, for the text installer you need the alternate CD, I put a link in my first post. Just select your version, and then scroll down to alternate CD.

As for autoclave, if you want a sterile drive I recommend DBAN over autoclave, DBAN has been proven time and time again, I love it and so do any friends of mine who need to nuke a drive.

---

### Post by willray on 2007-05-08
main problem i've run into is that i ended up installing 5.1 because it was text only install, but... as it turns out (at least as i understand it)  iin order to install most recent versions of ubuntu i have to install each successive version -- ie, breezy to dapperdrake, dapperdrake to fiesty.


so, i thought going from clean hd to fresh install would be easiest/simplest route.

just curious -- can one go from one version of OS to another? For example, can I go from using  Ubuntu to xubunu easilyi?

---

### Post by willray on 2007-05-08
> **starcraft.man said:**
> Yes, for the text installer you need the alternate CD, I put a link in my first post. Just select your version, and then scroll down to alternate CD.

As for autoclave, if you want a sterile drive I recommend DBAN over autoclave, DBAN has been proven time and time again, I love it and so do any friends of mine who need to nuke a drive.



what does "sterile drive" mean? thanks.

---

### Post by starcraft.man on 2007-05-08
> **willray said:**
> main problem i've run into is that i ended up installing 5.1 because it was text only install, but... as it turns out (at least as i understand it)  iin order to install most recent versions of ubuntu i have to install each successive version -- ie, breezy to dapperdrake, dapperdrake to fiesty.


so, i thought going from clean hd to fresh install would be easiest/simplest route.

just curious -- can one go from one version of OS to another? For example, can I go from using  Ubuntu to xubunu easilyi?

You don't need to upgrade to Feisty. The Alternate Install Disk is right [here.]("http://releases.ubuntu.com/7.04/")

Yes, you can easily install any other desktop environment like KDE Xubuntu or even enlightenment if you like after you install, via the command line. I'd focus on installing Ubuntu first if thats what you want. If you do want KDE by default then install Kubuntu... its your choice :)

---

### Post by willray on 2007-05-08
THANKS everyone!

---

### Post by moredhel on 2007-05-08
To be honest, I would try out each seperately to stop the need for uneccesary bloat.

So perhaps trying both livecds would be best, or text installing both by splitting the harddrive, then deleting the one you don't want to use.

I don't mean to mass generalize, but imo this is what the 3 biggest guis (gnome,kde,xfce) aim for:

Gnome: Very consistent, complete easy usability.

Kde: Pack in loads good features and eye candy (though gnome and xfce can both look very awesome as well!)

XFCE: Gnome, but a little more limiting, but less resource demanding, so more ideal for older pcs or pcs that need the extra because of what you do on it (like rendering stuff in blender ;P - infact while I do that, I use blackbox ;)

---

### Post by willray on 2007-05-08
> **moredhel said:**
> To be honest, I would try out each seperately to stop the need for uneccesary bloat.

So perhaps trying both livecds would be best, or text installing both by splitting the harddrive, then deleting the one you don't want to use.

I don't mean to mass generalize, but imo this is what the 3 biggest guis (gnome,kde,xfce) aim for:

Gnome: Very consistent, complete easy usability.

Kde: Pack in loads good features and eye candy (though gnome and xfce can both look very awesome as well!)

XFCE: Gnome, but a little more limiting, but less resource demanding, so more ideal for older pcs or pcs that need the extra because of what you do on it (like rendering stuff in blender ;P - infact while I do that, I use blackbox ;)

OK. I'll give them all a drive and see what works best.

---

