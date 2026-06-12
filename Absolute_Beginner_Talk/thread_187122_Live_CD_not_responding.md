---
title: "Live CD not responding"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by tcturner2002 on 2006-06-02
Hi all,
Seems like an absolute beginner question.  I ran the 5.10 Live CD on my Thinkpad 600E, and decided that I want to put in the install CD and install it.  Only problem is, the Live CD is extremely slow, it's been "loading" help for a couple of hours, and it's not responding well to anything I do.  So, first of all, how do I shut down?  Is there some sort of shortcut I can use to make it stop what it's doing and shut down/restart?  Do I need to go back to Windows before I can install it, or can I just put that CD in and restart?  But I can't open the tray when the comp is off, and I probably can't take out the Live CD while it's running????  :confused:  Does this make any sense?  Thanks for trying to understand!  -ct

---

### Post by blackjack6.21.91 on 2006-06-02
Just shut down (manually hold down the shut down button), and then turn it on again, and before the Live CD boots, you can take it out.  Also you might want to check the live CD for errors, because unless you downloaded the wrong CD, it shouldn't ever take that long.  Don't give up though, man.  It's pretty hard to set up, but if it wasn't any good, none of us would be here.  Were not all crazy, right?

---

### Post by mscman on 2006-06-02
[QUOTE=tcturner2002] I ran the 5.10 Live CD on my Thinkpad 600E, and decided that I want to put in the install CD and install it.  [/QUOTE] Just curious, but is there any reason why you are choosing to run the Breezy Live CD instead of the Dapper CD (6.06)  I would recommend trying the Dapper Live CD, which includes a nice graphical installer as well.

If you need to use 5.10 for some strange reason, I agree with the above post in that you should check your cd for errors.

---

### Post by tcturner2002 on 2006-06-02
OK, so I should turn off the computer, take out the live cd when i turn it back on, then put in the install cd, and it will boot from that without having to go back to windows?
A friend had the cds, i have dialup and can't really download anything.

---

### Post by blackjack6.21.91 on 2006-06-02
Right, but it's just a live CD.  It won't delete your windows partition.  To do that put in the install CD.  If windows automatically starts up, you may have to enter the boot menu whe your PC starts up.  Usually do that by pressing F12 or something.

---

### Post by tcturner2002 on 2006-06-03
OK, that's what I did.  Now I have a new problem.  I finished stage 1 of installation, rebooted, started stage 2, then got about 65% through "installing packages" (or something like that), and it crashed.  A bunch of I/O device errors, journal aborted, etc. and it was locked up.  So I cut the power, booted Ubuntu again, it said it couldn't install some packages; that I could do it later, and I got to a command line.  So I have two questions:

1. How do I get into Gnome?  I guess it doesn't do that by default.
2. What about the rest of the installation?  If I start over, is it likely it would crash again?  Maybe I should get a 6.06 cd instead?

Ok, thanks again for all the help. C

---

### Post by confused57 on 2006-06-03
Type "startx"(without the quotes) at the command prompt, then press "enter", if gnome was installed, you'll start the GUI.

Ctrl+Alt+Del will reboot your computer if it locks up

Ctrl+Alt+F1 will bring you back to a command prompt, if the GUI doesn't display properly.  You may have to press Ctrl+Alt+Backspace to exit the GUI before pressing Ctrl+Alt+F1.

---

### Post by CybaCowboy on 2006-06-03
[QUOTE=mscman]Just curious, but is there any reason why you are choosing to run the Breezy Live CD instead of the Dapper CD (6.06)[/QUOTE]

That would probably be because *it's not available yet!*

Just head on over to [http://shipit.ubuntu.com](http://shipit.ubuntu.com) - it states that the Ubuntu 6.06 ("Dapper Drake") CD won't be available until until "early June", and it will take up to about six weeks to arrive!


I'm sure [tcturner2002]("http://www.ubuntuforums.org/member.php?u=117744") doesn't want to wait six weeks or more just to try out Ubuntu...

---

### Post by mscman on 2006-06-03
[QUOTE=CybaCowboy]That would probably be because *it's not available yet!*
[/QUOTE]
Actually, *IT IS AVAILABLE!!!*, follow [THIS LINK]("http://www.ubuntuforums.org/showthread.php?t=185721") to read about the release and [THIS LINK]("http://us.releases.ubuntu.com/releases/6.06/") will take you to the download site.  It's actually been available for two days now, along with the Xubuntu version.  I'm not sure about ShipIt because I never use it, so it MAY be displaying the same message still, but I would hope they would update it soon.  At any rate, of course ShipIt will take a long time, it's MAIL!!!

---

### Post by CybaCowboy on 2006-06-03
[QUOTE=mscman]Actually, *IT IS AVAILABLE!!!*, follow [THIS LINK]("http://www.ubuntuforums.org/showthread.php?t=185721") to read about the release and [THIS LINK]("http://us.releases.ubuntu.com/releases/6.06/") will take you to the download site.  It's actually been available for two days now, along with the Xubuntu version.[/QUOTE]

Yes, but that's to *download* it, not the CD version...

Sure, there is the option to burn an "ISO image" to CD, but believe it or not, not everyone has a broadband connection or the patience to download a few hundred megs over dial-up!

Oh yeah, that page also provides a link to ShipIt, which does not yet have the Ubuntu 6.06 CDs...


[QUOTE=mscman]At any rate, of course ShipIt will take a long time, it's MAIL!!![/QUOTE]

I'm not debating the time that Snail Mail takes, I'm making a point - if he wants Ubuntu 6.06 on *CD*, it could take six weeks or more!

---

### Post by painterboy on 2006-06-03
[QUOTE=tcturner2002]OK, that's what I did.  Now I have a new problem.  I finished stage 1 of installation, rebooted, started stage 2, then got about 65% through "installing packages" (or something like that), and it crashed.  A bunch of I/O device errors, journal aborted, etc. and it was locked up.  So I cut the power, booted Ubuntu again, it said it couldn't install some packages; that I could do it later, and I got to a command line.  So I have two questions:

1. How do I get into Gnome?  I guess it doesn't do that by default.
2. What about the rest of the installation?  If I start over, is it likely it would crash again?  Maybe I should get a 6.06 cd instead?

Ok, thanks again for all the help. C[/QUOTE]
i would just try to reinstall from scratch then see if it hangs in the same spot and what error messages are returned if any.  If it does hang again have you tried just wiping the disc maybe it is a little dirty or scratched.  Im new to linux myself   so if this seems a little basic its i apologize but its the best i can offer right now

---

### Post by gigi1234 on 2006-06-03
Not enough RAM maybe? 

With Dapper they are recommending 192 MB RAM for the live cd.

---

### Post by tcturner2002 on 2006-06-03
Gnome won't start, I get a message about server error, so I guess I'll do that.  Just put in the CD and see where to go from there...  Thanks. CT

---

### Post by painterboy on 2006-06-03
[QUOTE=tcturner2002]Gnome won't start, I get a message about server error, so I guess I'll do that.  Just put in the CD and see where to go from there...  Thanks. CT[/QUOTE]
do you get a command line?  It kinda sounds like you are doing a server install instead of a desktop install.  The difference between the two is that the server install doesnt come with the gnome desktop at least thats what I understand.  If you get a command line type startx.  If this doesnt work type sudo apt-get install ubuntu-desktop.  Im just kinda pitching ideas at you.  hope it works.

---

### Post by tcturner2002 on 2006-06-03
I just erased the partitions and reinstalled like you suggested.  It worked great!  Thanks to everyone for your help!

---

