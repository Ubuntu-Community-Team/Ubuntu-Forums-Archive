---
title: "Running CDROMs in Ubuntu?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by SPWaltz on 2008-01-01
I'm pretty happy with Ubuntu thus far, all things considered, but now I've hit a small snag that's driving me crazy. I'm sure this is basic stuff and I did check the forums, but everything I saw related to this seemed tangential to my much more basic concern. 

So anyway, here's my stupid question: I have this CDROM I need to run as part of a class I'm taking. The disk of course lists system requirements for Mac and Windows only, mentions running on Quicktime, etc. But can I run this thing in Ubuntu? 

When I put the CD into my drive, Nautilus opens a folder with all the CD's files listed in it (including icons for "start.exe" and "autorun.inf"), but double-clicking on the .exe file simply gets me this warning from the system:  "File Cannot Be Opened: No application suitable for automatic installation is available for handling this type of file". 

Total n00b here.... Help?

---

### Post by bwtranch on 2008-01-01
Might have to use a helper called Wine. It translates Windows type apps into Linux code. Go to add/remove to install (should be on your system already, actually). Go to the Wine website for more info. Gotta tell you, though, it's not perfect.

---

### Post by bump_ on 2008-01-01
Wine can be used to try and run Windows programs in Ubuntu. It's gotten pretty good at the stuff it now runs flawlessly, so its worth a try.

From the Wine website
[http://www.winehq.org/site/download-deb:](http://www.winehq.org/site/download-deb:)

```
Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Feisty (7.04):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/etch.list -O /etc/apt/sources.list.d/winehq.list
```

When that is done, type in the terminal:
```
sudo apt-get update

sudo apt-get wine
```

Then you can right click on .exe's and select "Open with WIne"

Hope it helps

Edit: Or you could do as mentioned above, but I think one's in the default repo's are a few versions old and alot of bugs get fixed with each version

---

