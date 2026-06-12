---
title: "Need to speed up boot to login"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2008-02-09
[**solved]**New install from CD. First removed windows, then wiped with Norton's, then used
CD to install. The Gutsy Gibbon runs well, never halts, is quick, does all I want it to.
It just takes about 2 minutes 40 seconds to get from pushing power on to log in
screen. After that, it is great.  Have read many entries in the forums, they seem to
be more concerned with video or after log in. Any ideas what would make it slow
to get to the log in screen?

tried the Weird solution.  It worked!.  Thanks for the help.

---

### Post by pieisgood4589 on 2008-02-09
More swap space helps... Or more RAM.:lolflag:

---

### Post by y-lee on 2008-02-09
About the only way other than upgrading machine is cut back on start up services not needed. Lots of tips on that and you better know what you are doing. 

see [Speed up ubuntu boot process - the way you can feel it.]("http://ubuntuforums.org/showthread.php?t=89491")

I for one don't bother but be careful if you do :)

---

### Post by asmoore82 on 2008-02-09
[QUOTE=ME]A lot of non-essential services are enabled on all "Easy to Install/Use" "Desktop" Linux
systems, Open "System->Administration->Services" and turn off what you don't need.
I noticed also that a lot of new user-space startup stuff was added in 7.10. Open
"System->Preferences->Sessions" and turn off what you don't need.[/QUOTE]
[http://ubuntuforums.org/showthread.php?p=4194761#post4194761](http://ubuntuforums.org/showthread.php?p=4194761#post4194761)

---

### Post by rtrdom on 2008-02-09
Thanks all. I have 10GB swap space, 2 GB ram so hardware should not be a problem.
I will look into the system services though. Thanks.

---

### Post by Shazaam on 2008-02-09
A 10gig swap is overkill. You will never use it unless you have a VERY small amount of physical ram. 2gigs max (and thats pushing it) is a good rule of thumb.

---

### Post by rtrdom on 2008-02-09
Thank you shazaam for the info.  I'll use gparted to reduce that partition and add it
to the others. I looked at system/preferences/session and shut down tracker and
bluethooth and evolution alarm notifier.  The rest (only 8 in startup) appear to be important. They are:Network, Power, and Restricted Drivers Manager, - Printer Que Applet, Update Notifier, User Folders Update, Visual and Volume Manager. If any of 
these can be shut down with out affecting operation of computer, I will.
Thanks again for the information.

---

### Post by spiderbatdad on 2008-02-09
you might look at /etc/usplash.conf or post the settings here. set to your supported screen res.

---

### Post by thechilipepper0 on 2008-02-19
believe it or not, i followed this advice and cut my bootup time from 3:30 to 1:30
[http://ubuntuforums.org/showthread.php?t=580903&highlight=long+startup]("http://ubuntuforums.org/showthread.php?t=580903&highlight=long+startup")

all it tells you to do is to tell ubuntu to "unquiet" the splash at bootup, meaning you get all the text and stuff as the system starts up. i have no idea why that speeds things up. maybe this will help.

---

