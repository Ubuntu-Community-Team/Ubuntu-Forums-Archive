---
title: "How to exactly use Synaptic for Complete Idiots like me"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by newbie8 on 2006-09-29
It seems I am having problems "installing" various programs that I found in synaptic.

I have tried to install ClamAV and checked the appropriate boxes, then pressed "apply" but nothing seems to happen after the process. No ClamAv icon appears.

I have also tried these steps with other programs but nothing seems to happen.

Am I supposed to "restart" my computer? 

Am I missing a step somewhere?

I tried reading other posts but there does not seem to be any clear guidelines for complete idiots.

Thanks.

---

### Post by Iarwain ben-adar on 2006-09-29
Try this :D
```
sudo apt-get install clamav   
```
That should do the trick for you..

If you don't get it in you menu afterwards, try starting it manually,
probabely by typing 'clamav' (i'm not sure about the command, but if you type 'cla' and then TAB twice, you should see what commands start with "cla"


Iarwain

---

### Post by po0f on 2006-09-29
newbie8,

ClamAV is a command-line tool to scan files for virii.  You'll need to install a GUI frontend if you want it.  I know of KlamAV, which is Qt/KDE based.  I can't recall any of the names of GTK-based ones, hopefully someone else can make a recommendation.  Hope this helps.

---

### Post by newbie8 on 2006-09-29
Where am I supposed to type or cut/paste that code/command to?

Please be specific for complete idiots (absolute beginners seem to know more than complete idiots).

Thanks!:D

---

### Post by hyper7 on 2006-09-29
> **Iarwain ben-adar said:**
> Try this :D
```
sudo apt-get install clamav   
```
That should do the trick for you..

If you don't get it in you menu afterwards, try starting it manually,
probabely by typing 'clamav' (i'm not sure about the command, but if you type 'cla' and then TAB twice, you should see what commands start with "cla"


Iarwain

The problem with that is people who are new to *nix don't see an AV running, so they think it isn't.  I think it's best to go with automatix installation.

[Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")

---

### Post by orb9220 on 2006-09-29
nevermind

---

### Post by Boatswain on 2006-09-29
For ClamAV in particular, you may want to pick up avscan, which is a GUI for clamAV.  After that, if you just type avscan at the terminal, the avscan windows will pop up.

---

### Post by newbie8 on 2006-09-29
Thanks to all the replies. I do not see ClamAV or any other thing which I "applied" from the synaptic.

I do not see it in the alacarte menu either.

I am just used to seeing an avg, avast or clam icon to have the peace of mind that an anti-virus is installed.

---

### Post by newbie8 on 2006-09-29
> **Boatswain said:**
> For ClamAV in particular, you may want to pick up avscan, which is a GUI for clamAV.  After that, if you just type avscan at the terminal, the avscan windows will pop up.

This worked "typed avscan in the terminal" and a window opened.

Should I type clamav too?

---

### Post by spockrock on 2006-09-29
no I avscan is all you need to do.

---

