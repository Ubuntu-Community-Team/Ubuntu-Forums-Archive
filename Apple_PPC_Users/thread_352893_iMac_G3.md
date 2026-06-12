---
title: "iMac G3"
date: 2007-02-03
forum: Apple PPC Users
---

### Post by deviantfire on 2007-02-03
Ok, so I am trying to get Breezy to work on a little iMac G3, I've managed installations before, but am still learning, once on a G3 tower and once on an old PC.

I get to Xserver and it all falls over!!! I have tried editing the xorg.conf file into the right frequency settings, with little avail.

I used the reconfigure thingy too, no joy there! It's not connected to the internet as I don't want to mess with the network administrators head yet.

After I adjust the conf file it says Fatal Error no screens found.

I have been trying to sort this for hours now and wouldn't be posting here if I could find a way that works online!

Nayway anyhelp for this little b&w imac would be greatly appreciated, Thanks!!

---

### Post by beanworks on 2007-02-03
O.K., I've got one of those B&W iMacs.   You don't say what exactly you did to edit the config file, so here's what  I found somewhere in the forums here, and it worked for me:

/*open the xorg.conf to edit it using nano*/
[FONT="Courier New"]sudo nano /etc/X11/xorg.conf[/FONT]

/*find the horizontal refresh and vertical refresh lines and change them:*/
[FONT="Courier New"]Horizontal Sync   58-62
Vertical Refresh 75-117[/FONT]

/* Disable DRI in the MODULES section by putting a # at the beginning of its line*/
[FONT="Courier New"]#       Load     DRI[/FONT]

/* save the changes*/
[FONT="Courier New"][ctrl] O [Return][/FONT]


/*  exit nano */
[FONT="Courier New"][ctrl] X[/FONT]

/* restart the gnome desktop manager */
[FONT="Courier New"]sudo killall -HUP gdm[/FONT]

The kicker for me was that last part.  Disabling DRI may help too :-)

Good Luck!

Carol

---

### Post by deviantfire on 2007-02-04
Ok thats a different refresh rate to the one I found to change it to, apparently it's something to do with the ATI drivers not being right, I'll try that and post back, thanks a million!

---

### Post by deviantfire on 2007-02-04
Right, well that didn't work!!! Ahhhhhhhhhhhhh :confused: 

Anyone else got an idea???

---

### Post by deviantfire on 2007-02-04
Did a fresh install and all seems well, I can log in and stuff, but when Gnome starts I just get a brown desktop and a mouse cursor and nothing else, no splash screen, nada!!!

Any takers??? I'm so frustrated now!

---

### Post by 3rdalbum on 2007-02-05
'Tis the season to encounter the Date Bug:

[http://www.ubuntuforums.org/showthread.php?t=352130&highlight=date+bug]("http://www.ubuntuforums.org/showthread.php?t=352130&highlight=date+bug")

---

