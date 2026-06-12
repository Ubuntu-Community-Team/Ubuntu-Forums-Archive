---
title: "Wine Audio Configuration"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-25
I am currently running Kubuntu 7.10 (Gutsy) with Wine wine0.9.57.  For some reason when I click on the Wine configuration and then click on the Audio tab, Wine freezes up and crashes every single time. 

I have a program for my music class that I was able to get running, except no audio (kinda defeats the purpose), and another program from [www.musicnotes.com](www.musicnotes.com) that I was able to get working AFTER I installed firefox through Wine and installed the firefox plugin through Wine (they only had the program for Windows and Mac, not Linux). I got that program to work too, but again, no audio. Does anyone know how to troubleshoot this to a) get Wine configuration to load the audio tab so I might be able to figure out why Wine isn't passing control of the audio from Kubuntu to Wine when audio is needed.

Thanks.

---

### Post by mikeyphi on 2008-03-25
Sorry - can't answer that! I know it takes a little time for the audio tab to sort things out but don't know about 'freezing'.
Try asking for advice on the wine forum:  [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by erginemr on 2008-03-25
Did you try any other version, say the newest 0.9.58 or older versions 0.9.55 or 56 from Wine home page:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Maybe, the problem will not reproduce in a different version...

---

### Post by Stealth on 2008-03-25
Do you get any output when you run WINE from a terminal? I remember getting this once, Googling I foudn this possible solution:

mkdir -p $HOME/.kde/socket-`hostname` 

I can't remember what it does, I think it had something to do with JACK too, so you might want to install some of those libraries as well.

---

### Post by spacefreak86 on 2008-03-25
Okay, I tried running firefox through Wine from command line and still no audio output. Is there a way to configure Wine audio from the command line, and if so, how? (Please note I know how to change directories in command line, that's about all)

---

