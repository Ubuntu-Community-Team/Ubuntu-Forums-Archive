---
title: "[SOLVED] A Crash"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by NikS on 2008-04-14
Hi every1,

I was installing dependencies for mplayer (since i dnt have net i was doing it from a usb drive), n the package installer gave me an error message..

Now when i try installing any package, it says: "U have broken dependencies go to Synaaptic to fix it first"..

When i opened Synaptic & used filter: Broken to look for the dependensies I found 2 Broken libs,
When i tried to remove (As i couldnt figure out any other meaning for "FIXING" this ) them its warning me that: This action will remove 1057 packages!!!!!!!! Proceed only if you know what u r doing!!!!

Those include almost Everything i know is installed on the comp!!! Even OO.o!!

M planning a Complete format and reinstall..

Any other openinons??

---

### Post by forrestcupp on 2008-04-14
Try opening a terminal and typing
```
sudo apt-get -f install
```

---

### Post by kelnage on 2008-04-14
Have you tried "Reinstalling" the broken packages (right click on each package and choose "Mark for reinstallation", then click "Apply")? It might help, let us know.

---

### Post by phidia on 2008-04-14
Without an internet connection you are going to have problems using the package manager-I think.
However you can give [this]("http://ubuntuforums.org/showthread.php?t=753449&highlight=broken+dependencies") a look. Hope that helps.

---

### Post by NikS on 2008-04-14
Thanks every1 for your time..

> **forrestcupp said:**
> Try opening a terminal and typing
```
sudo apt-get -f install
```

Gave me Same output as synaptic: Says it will remov e 1057 packages!!!
I did try reinstalling but by doubleclicking the .deb packages, i dint find the option "Mark for reinstallation " in the context menue... Most probably it was disabled, i dont remember, will boot in ubuntu n try again...

---

### Post by forrestcupp on 2008-04-14
It sounds like you downloaded dependencies that don't work right with your system.  If you can remember all of the 'dependencies' that you installed, you probably need to uninstall each of them.  Then you can download the correct dependency versions for Gutsy at [the correct place](http://packages.ubuntu.com/gutsy/).

---

### Post by NikS on 2008-04-14
Thanks pal,
But everything i downloaded was what i was given links to from : nonetdebs.homeip.net!!!

Its the Best place as i have known!!! All the links are from archive.ubuntu.com!!!

---

### Post by prshah on 2008-04-14
> **forrestcupp said:**
> Try opening a terminal and typing
```
sudo apt-get -f install
```

Try these, one after another, in turn:
```
sudo apt-get -f check
sudo apt-get -f -m check
```

---

### Post by NikS on 2008-04-15
Thanks every1 and prshah..

But i was too frustrated yesterday night n the 1st thing in the morning after getting up i did,is to remove n reistall ubuntu!!!!!!
M sorry...

Thanks always for ur time and effort...!!!

---

### Post by forrestcupp on 2008-04-15
Sorry you had to do that.

I was thinking about it, and I wonder if the problem was that you didn't have an internet connection to update your entire system.  So you were using some older versions of things that you had no way of updating.  The things you downloaded were the new versions of things from the repos which are meant to be used with an updated system.

It's hard to get the full potential out of Ubuntu without an internet connection.

---

