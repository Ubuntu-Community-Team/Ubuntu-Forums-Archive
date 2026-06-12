---
title: "An OSX like dock?"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Animus on 2005-10-30
I've seen screenshots of people using Ubuntu, with an OSX style dock at the bottom of the desktop, and I was wondering if anyone knew where I could find a guide for doing this, as I've been unable to find one myself.

---

### Post by aysiu on 2005-10-30
I think it's a gDesklet. You can install gdesklets through apt-get (you may need to enable Universe, I think). For more info on how to do this: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Animus on 2005-10-30
I have those repositories enabled I believe, but I tried sudo apt-get gdesklets, and got nothing.

I know how to install software, but I need to know what particular software to install in this instance...

I checked gdesklets site, and didn't see anything like the OSX dock however...


EDIT: Found The following

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=245](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=245)

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=127](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=127)

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)

Now, how would I go about apt-getting these?

---

### Post by aysiu on 2005-10-30
What do you mean by "got nothing"? Can you show me the exact output of the command ```
sudo apt-get install gdesklets
```? If it says the package can't be found, you don't have the right repositories enabled. Follow these directions, then: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

To install a gDesklet, you just download the file and drag it to the gDesklets manager.

---

### Post by raggamuffin on 2005-10-30
for people using Kubuntu...apt-get install **superkaramba**....and head over to kde-look.org to find a good theme...(i prefer Kroller)...

---

### Post by Animus on 2005-10-30
Okay, I forgot the install part of the command lol.  Ran the command, everything seems to have gone fine.  Where is the gdesklets manager located by default in the system?  I'm having a hard time tracking down where it is...


EDIT-Found it, trying to see how everything works now, thanks for your help so far man.

---

### Post by raublekick on 2005-10-30
should be under Applications->Accesories->gDesklets

---

### Post by jasay on 2005-10-31
This is probably the launcher your looking for
[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210")

Look around the rest of the site for other desklets you like and download them.  As mentioned you can get to the gDesklets shell to manage your desklets from Applications > Accessories > gDesklets.  Install desklets by dragging the tar file(s) into the gDesklets Shell or choosing File>Install package and navigating to the tar file--no need to unpack them. To put a desklet on the desktop, double click on the desklet in the shell and click where you want to place it.  You can then move it by dragging with the middle button.  Most desklets need a right-click > "configure desklet" to set them up how you want them.

For the starterbar (OSX dock thing) you can add new launchers by dragging them from a panel or right clicking and choosing "new starter".  After dragging a firefox launcher to starterbar, some people have had it open to random pages instead of the home page.  If that happens, right-click > "edit  starter" and remove the %u from the command line.  

Also if your desklets show up in a big black box instead of being transparent, try right clicking on the gdesklets icon in the notification area (originally in the top right of the screen) and choosing Configuration.  Then *un*click translucency.

That's about all I know about gdesklets.  Hope it helps.:D

---

### Post by jonah1980 on 2007-05-04
hey guys also got gdesklets, don't like to use compiz/beryl at the moment and on gnome so gdesklets seems most stable and best for dock. but all i've found is starterbar, which won't auto hide or come over top of open windows, does anyone know of any others in dev. and how come gdesklets is moving so slow and doesnt have much dev going on. it's totally awesome, there should be loads of desklets for it....

---

