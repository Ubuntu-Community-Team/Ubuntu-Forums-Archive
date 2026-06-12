---
title: "dpkg: parse error Update Manager stalls"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by thedarky on 2007-05-29
Howdy,
New to both linux and ubuntu today.

Using a live feisty cd as pointed to in the sticky thread- md5sum checked - I successfully resized my OS X 10.3.9 partition to allow a ubuntu install, after running the system live to check it out on my eMac 1.25 (USB 2.0).

All went very smoothly, except the install reported that it couldn't finalize packages at the end .
Whatever the error, it wasn't fatal and I am now dual booting smoothly and system and user utilites and the network are all fine.

But when I  ran the Update Manager when notified that there were updates to download and install, the utility is returning an error message:
"Update is complete."
"Not all changes and updates succeeded."

 with a terminal narration highlighted
"extracting templates from packages: 100%
Preconfiguring packages . . .
dpkg: parse error,  in file `/var/lib/dpkg/available' near line 1:
   newline in field name `'"

At this point, there remain all 48 packages yet to install and Update Manager will just repeat to the error message at each attempt to update.

Since two of the packages are updates to the Update Manager, this could give me some endless fun unless I get it straight.

It seems that the dpkg application is possibly corrupt.

Can any user point me along a line of  troubleshooting the package handler or is it the Update Manager that's faulting?

thanks in advance for any help.

---

### Post by thedarky on 2007-05-29
There's more here that makes it look like bug #64012
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/64012)

It would make sense that the /available file could have got corrupted during installation - it's seeming that the installation on PPCs is getting done more by good luck than by guided planning.  The complexities of apple's hardware variations don't help here.  For a good example, the live cd is reporting difficulties with a powerbook pmu button - on an eMac.  
I may just try a new installation to see whether that manages to miss the corruption - not being able to get a download of emacs that I can sudo edit the corrupted file with, and also having no clue about what an /available file is supposed to look like anyway, it'd be getting surreal if I went down that path.

Although no participants have responded here, I'll report the outcome for the archives.

---

### Post by thedarky on 2007-05-29
Reinstall got lucky and the introductory updates have been installed without stalling.

It occurs to me that I'm in a rural area and a power fluctuation enough to affect the hardware but not enough to cause an outage isn't out of the question during the first install.

---

### Post by stmiller on 2007-05-29
Yeah sounds like a corrupted package in there somewhere. Probably dpkg. Glad the reinstall worked.

FYI a possible alternative fix would be:

sudo apt-get autoclean

and

sudo apt-get autoremove

to clean things up.

And you can reinstall dpkg with:

sudo apt-get --reinstall install dpkg

---

### Post by tamas4president on 2007-06-03
sudo nano /var/lib/dpkg/available

then delete the text until the first instance of 

Package:

Save and Update manager will work

---

