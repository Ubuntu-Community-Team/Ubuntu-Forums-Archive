---
title: "Two problems (New to Ubuntu)"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by anathema on 2006-12-18
I find myself with two, no doubt easily answered, problems.

First: After installing Ubuntu 6.06 off the alternate disk on my Powermac G4, I decided to boot back up in OS X, so I held down the "X" key while booting the computer, which worked fine. My problem: How do I get back to Ubuntu?

Second: I have been attempting to install Wine onto Ubuntu, but everytime I refresh the Synaptic Manager, it just gives me an error 404 saying the Wine file could not be found. How do install Wine?

Sorry if these questions sound stupid >.<

---

### Post by handylinux on 2006-12-18
> **anathema said:**
> First: After installing Ubuntu 6.06 off the alternate disk on my Powermac G4, I decided to boot back up in OS X, so I held down the "X" key while booting the computer, which worked fine. My problem: How do I get back to Ubuntu?

Actually, from my experimenting it doesn't seem that holding down **X** while booting will switch from Ubuntu to OS X. My guess is that your Mac still has OS X set as startup in the Startup Disk System Preference pane, in which case it will start up from OS X even after you've installed Ubuntu.

Where did you install Ubuntu -- i.e. on what partition? If Ubuntu is installed on the **first** partition, you can boot into Ubuntu by pressing **D** during startup. If Mac OS X is installed on the first partition, the only way to get to Ubuntu is by pressing **option** during startup, which should give you a screen showing both OS X and Ubuntu, where you can choose which you want to use -- for that startup only.

So far as I know, there's no way to set Ubuntu as the startup System in the Mac's firmware, since Startup Disk doesn't recognize the Linux partition as bootable. Thus it is best, if you want to set up your Mac for dual booting, to install Linux on the first partition, so you can get to it easily.

See "[How to switch OS on dual-boot Mac?]("http://www.ubuntuforums.org/showthread.php?t=318682")" for more discussion.

BTW, I'm curious: Why did you choose Ubuntu 6.06 instead of 6.10?

As for WINE, sorry, I can't help. Maybe best to start another thread for an unrelated question.

---

### Post by anathema on 2006-12-18
I installed 6.06 as my computer seemed unable to burn the 6.10 version (it would crash in the middle of burning the disc, even when using alternate methods).

Also, whenever I start up my computer in OS X, it tells me that there is an unreadable disc in the computer (the Ubuntu drive) and asks me to initialize it. Will holding Option really read through this error?

---

### Post by linear on 2006-12-18
> **anathema said:**
> Second: I have been attempting to install Wine onto Ubuntu, but everytime I refresh the Synaptic Manager, it just gives me an error 404 saying the Wine file could not be found. How do install Wine?

On a PowerPC, you don't. :( It's Intel-only.

---

### Post by stream303 on 2006-12-19
Don't let OSX initialize your Ubuntu disk! OSX just doesn't recognize the ext3 filesystem and wants to help you out. :)

Holding down the option key during boot should allow you to choose between either drive - just wait for the watch icon to turn into a cursor, highlight the drive you want to boot, and click the arrow.

---

### Post by Geodesic17 on 2006-12-31
> **linear said:**
> On a PowerPC, you don't. :( It's Intel-only.

Is this still the case?  I've been stuck trying to compile source code so that I can run WINE on a Ubuntu/MacG3 system.

---

### Post by handylinux on 2006-12-31
> **Geodesic17 said:**
> Is this still the case?  I've been stuck trying to compile source code so that I can run WINE on a Ubuntu/MacG3 system.
Yes. Wine will never run on PPC. Wine basically duplicates the minimum necessary functions of Windows to allow a Windows app to run in another OS **on an x86 processor** without having to run the whole Windows OS. It's never run on any PPC processor, and couldn't. The entirely unrelated Virtual PC for Mac, and similar efforts, were required to run Windows (within pre-Intel versions of Mac OS) on a PPC, and did so even at best rather poorly, since Windows is of course entirely designed to run on x86. See the [Wikipedia article]("http://en.wikipedia.org/wiki/Wine_software") for more on Wine.

---

