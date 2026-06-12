---
title: "Screen savers fail to start"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by gitano1 on 2006-10-30
I installed 6.10 last week. It ran perfectly for a couple of days but for some reason the screen saver stopped coming on. Instead I get a blank screen. I changed screen saver options from Random to one of the other options and it worked until I left the machine on over night. In the morning the screen savers no longer came on. I tried rebooting, but without any effect. I have also tried changing the saver again. No effect. Any suggestions on how to get it going?

---

### Post by apjone on 2006-10-30
have you got xscreen-saver / gnome-screensaver service started?

---

### Post by gitano1 on 2006-10-30
I am a rank beginner. How do I find out if I do have it activated or if I have somehow disabled it? It was working for a couple of days.

---

### Post by nickburns on 2006-10-30
Go to the terminal and type in:

ps -ef

and post back if you see a gnome-screensaver running.

---

### Post by gitano1 on 2006-10-30
Thank you very much. I am at work and will try that when I get home and report back at that time. ](*,)

---

### Post by gitano1 on 2006-10-30
Gnome screensaver does show in the list.

---

### Post by nickburns on 2006-10-31
Sorry for the delay,  I wonder if you went to the Synaptic Package Manager and did a reinstall on the gnome-screensaver if that would be the ticket.


Goto

System >> Administration >> Synaptic Package Manager
Type in your root password
Do a search for 'gnome' and find the gnome-screensaver

Right click on it and do "Mark for Reinstallation"

Click on the Apply button.

let us know how it goes...

---

### Post by gitano1 on 2006-10-31
Thank you, Nick. I came up with that idea this morning just prior to reading your message. Once again, here I am at work unable to do anything until I get home. However, I will do it as soon as I get home. That seems to me the only answer. Apparently, something got corrupted because it worked fine for a couple of days. Very un-Linux like!

---

### Post by gitano1 on 2006-10-31
I have tried simply reinstalling, removing and installing and a number of other tweaks. Nothing changes. It just simply will not bring up the screensavers. I just get a blank screen. I am wondering if original downloaded version is corrupt and reinstalling it simply doesn't do any good. Is there a way to go back to the source and download that package only and try installing it?

---

### Post by g3k0 on 2006-10-31
I have this same problem, I left mine running for a while and when I came back it wasnt working anymore.  Only thing I can think of is that I installed  Atis proprietary driver ...

---

### Post by gitano1 on 2006-11-01
Essentially mine did the same thing. I left it running and after I woke it up the screensaver did not work anymore. I have not installed any proprietary software. After I downloaded Edgy there were a couple of upgrades that showed up. Best I can figure is that one of them was the monkey wrench. All attempts to reinstall the software has been to no avail. I suspect that this is a bug that will be discovered and corrected in some future update.

---

### Post by nickburns on 2006-11-13
Ironically I now have the same problem.  Any luck getting this resolved?  It looks like the daemon is running to start the screensaver, but it never gets the signal to get running....

---

### Post by shane.gardner on 2007-03-11
I also have a similar problem.  My screensaver no longer works.  When it activates, or when I try to configure it, it flashes to a black screen then I am sitting at the login screen.  Gnome-screensaver is a running process.

When I try to configure it from System, Preferences I see the dialog box for a second then right to the black screen!

I am running 64 bit ubuntu 6.06 LTS.

I am wondering if some automatic update killed it?

---

### Post by Pat.Hat on 2007-03-12
I'm definitely experiencing the same problem... upon a fresh boot, the screensaver works charmingly. Once the computer shuts off the monitor to save power, the screensaver just turns to a blank screen from then on.

---

