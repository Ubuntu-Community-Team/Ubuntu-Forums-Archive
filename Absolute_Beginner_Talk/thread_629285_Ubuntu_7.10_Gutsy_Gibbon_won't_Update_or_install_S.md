---
title: "Ubuntu 7.10 Gutsy Gibbon won't Update or install Software"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Stalker150 on 2007-12-02
Hi everyone!

At first I must tell you that I'm from Germany, so excuse my bad English please. I hope you can understand me anyway.

I have a problem with Ubuntu (Ubuntu 7.10 Gutsy Gibbon). The installation was no problem. Ubuntu runs perfect on my HP Compaq nx6110 Notebook. Everything is working but I can't Update Ubuntu or install any Software with the "Add/Remove Application Tool". The Update list look every time like this:

[IMG]http://img267.imageshack.us/img267/5364/updatevc3.jpg[/IMG]

Yes, up-to-date, but it was never been updated since I installed it. (because the list is always empty)

Okay, next problem is, that I can't install any Software. When I choose a software to install, the Add/Remove Application Tool tells that "The list of application is not available". Like this:

[IMG]http://img105.imageshack.us/img105/9410/apps1tu4.jpg[/IMG]

When I refresh it, it's the same again. I can't install anything, because the list is not available at any time.

Maybe someone can help me. I found nothing in the forum.

---

### Post by njparton on 2007-12-02
Is your network connection functioning?

Can you view webpages for example?

---

### Post by Daveth on 2007-12-02
or are your main Gutsy repositories" ticked" under software sources?

---

### Post by alienexplorers on 2007-12-02
Try opening firefox and see if you can access a web page such as [www.google.com](www.google.com)
If not see if you can open terminal and type in:
> ping [www.google.com](www.google.com)

---

### Post by Stalker150 on 2007-12-02
I have posted the thread with the Ubuntu! Internet is working correctly. No error, perfect ping ... never lost the connection. I have full Internet access. I thought at first that the problem is the wireless-lan connection but everything is working. I tried this with cabel and the same error came. I downloaded Unbuntu again, burned a new cd and reinstalled it but nothing changen. I installed another new Ubuntu CD on a computer from a friend but the same error came.

---

### Post by Scoobie_snack on 2007-12-02
Hey guys,

I have the exact same problem. A few days ago, I loaded Gutsy 7.10 on my laptop and got internet connection and updated everything fine. Today I installed Gutsy (from the same disc) on my desktop, got internet and firefox working but I can't update or add/remove either. I uninstalled and re-installed but I still get the same issues.  Full net access, perfect ping and all that but its like Gutsy can't see the connection to the net to update... Very odd.

---

### Post by ptn107 on 2007-12-02
check your */etc/apt/sources.list*

---

### Post by Scoobie_snack on 2007-12-02
I hope you guys don't mind me jumping into this thread :confused:

ptn107, I have the file open, what are we checking it for?

---

### Post by Stalker150 on 2007-12-02
The file is full of some link stuff. Looks like this:

[SIZE="1"]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse[/SIZE]

---

### Post by Scoobie_snack on 2007-12-02
I just found this link [http://ubuntuforums.org/showthread.php?t=629621&highlight=update+gutsy](http://ubuntuforums.org/showthread.php?t=629621&highlight=update+gutsy)
 And I followed what forestpixie said and it works!
It worked for me anyway, I hope this helps you too Stalker!

:guitar:

---

### Post by Stalker150 on 2007-12-03
> **Scoobie_snack said:**
> I just found this link [http://ubuntuforums.org/showthread.php?t=629621&highlight=update+gutsy](http://ubuntuforums.org/showthread.php?t=629621&highlight=update+gutsy)
 And I followed what forestpixie said and it works!
It worked for me anyway, I hope this helps you too Stalker!

Thanks! Everything is working correctly! Update and Software install works! Thank you very much! :)

---

### Post by Scoobie_snack on 2007-12-03
Hey, I'm glad this worked for you.
All thanks should be directed to forestpixie, I just found the link and posted it :lolflag:

Good luck and take it easy mate!

---

