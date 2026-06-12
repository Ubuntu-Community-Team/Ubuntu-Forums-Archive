---
title: "Ubuntu Instalation Issues"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by PsYcO~KJ on 2008-04-15
Well I'm new to Linux, and Ubuntu. My problem is that is seems as if the installation is freezing, it has been sitting at "detecting file system" n 15% for 2 hours now.

Should I just try to reboot, and then try to install again, or just let it go for another hour and see if it moves?

---

### Post by swimm3r137@gmail.com on 2008-04-15
are u installing with the live cd or alternate

---

### Post by PsYcO~KJ on 2008-04-16
It would be LiveCD, but its not in drive, does it need to be when installing wine?

---

### Post by Paqman on 2008-04-16
> **PsYcO~KJ said:**
> It would be LiveCD, but its not in drive, does it need to be when installing wine?

Are you trying to install Ubuntu, or Wine? No, the LiveCD does not need to be in the drive to install packages (although you can use it as a repo if you want)

---

### Post by PsYcO~KJ on 2008-04-16
Oh, nvm, got it working now, but when i did load it, it said something about the cdrom, i made it in another post, now to find it >.<

---

### Post by 19bab79 on 2008-04-16
if you are installing ubuntu just start over again. if you are installing wine then do it from command line with sudo apt-get install wine. you don't necessarily need the cd. Go to 
system ==> administration ==> software sources and see if you have the cd selected as one of your repo sources. deselect it if you do.

---

### Post by PsYcO~KJ on 2008-04-16
yes, i got ubuntu n wine working, but when i go install a game through the cd, if ti takes multiple cds, it wont elt me eject the cd, to put in the next cd, i get a message saying "An application is preventing the volume "CD-Name" from ejecting" and a couple times i got this "An application is preventing volume "cd-name" form unmounting" then id get the ejecting error.

---

### Post by PsYcO~KJ on 2008-04-16
> **19bab79 said:**
> if you are installing Ubuntu just start over again. if you are installing wine then do it from command line with sudo apt-get install wine. you don't necessarily need the cd. Go to 
system ==> administration ==> software sources and see if you have the cd selected as one of your repo sources. deselect it if you do.

OK well under the first tab, all is checked, and i changed the download from--main server to the usf location.

what your saying is to deselect the bottom where it says 'Installable from CD-ROM/DVD" correct? and what others should i deselect?

---

### Post by bumanie on 2008-04-16
Deselect cdrom and from source, the fifth box, (sorry at work on windoze machine so can't check exact wording). Then go to third party sources and select whatever may be there (probably something mentioing canonical).

---

### Post by PsYcO~KJ on 2008-04-16
ok thank you bumanie

---

