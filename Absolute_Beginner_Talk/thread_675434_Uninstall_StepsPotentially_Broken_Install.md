---
title: "Uninstall Steps/Potentially Broken Install"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-22
Here's what's causing me grief, maybe uninstall isn't my best option, however I'm not sure how to proceed.

I think it was last week that I adopted the Ubuntu system into my routine, and although I am more than happy with my overall experience I think I may have "broken" the system.  

Firstly, I am using Ubuntu Gutsy (7.10) amd 64.

While trying to learn how to use the system/install version components and applications I believe I have typed in erroneous terminal commands (i know I have, in fact) and I was working as the root user of my system.  Now although I can access the net, play music, watch movies and download - certain basic functions are giving me grief.

One of my earlier posts listed problems I was having with OpenOffice crashing.  Overwhelmingly, the responses I received were that OO is very stable and no one had experienced any sort of crashing.  WHich lead me to believe that I must have made an error somewhere.  And has me thinking now that I'm SLIGHTLY more comfortable it might be a good idea to scrap everything and reinstall from scratch.

Times that OpenOffice crashes: 1. During spellcheck in Impress when I attempt to change a misspelled word (EVERYTIME), 2. Some times during spellcheck, 3. Attempting to add animations to Impress slides.

System:
(Again) Ubuntu 7.1 AMD64 dual-booting with Windows Vista Home Premium
HP Pavilion m756n MediaCentre PC
AMD Athlon 42+ 64 x 2 processor
2 gigs memory
Graphics NVIDIA GeForce 615 LE graphics card (no issues, although I have read of many concerning nvidia cards)

Any suggestions to save reinstalling?  Otherwise what is the SAFEST way to unistall/reinstall Ubuntu?

---

### Post by philinux on 2008-01-22
Suggestion.

Go to synaptic and mark open office for re-installation.

Places>Home folder   press ctrl h and delete .openoffice.org2. I'd do this first.

---

### Post by durdensbuddy on 2008-01-22
Will this allow me to retain current files?  I've already backed up, but curious.  
Thanks

---

### Post by Paul820 on 2008-01-22
Have you tried removing OOo and reinstalling it? Removing a whole ubuntu installation is a bit much just because one program is giving you grief. Try removing and reinstalling it and see what that does. Then post back.

---

### Post by philinux on 2008-01-22
> **durdensbuddy said:**
> Will this allow me to retain current files?  I've already backed up, but curious.  
Thanks

Re-install just re-installs the app.

The .openblah files are just the config files for the app not your docs or spreadsheets etc.

All files starting with a . are hidden config files. The most important are mozilla and thunderbird etc as they contain your bookmarks and emails.

---

### Post by durdensbuddy on 2008-01-22
Ok, so I've unistalled and reinstalled using synaptic.  Same result.  Attempt to add an animation and save Impress closes.  No error message, just flips almost sideways and disappears.

---

### Post by Paul820 on 2008-01-22
Can you start the program from the terminal and any error messages will be caught and printed there. Don't close the terminal until you are finished though. Just do the same steps as you did before and post the output of the terminal.

---

### Post by durdensbuddy on 2008-01-22
What's the command to do this?  I placed Impress on my top panel and this allowed me to open it in terminal, however Terminal disappears.  

Attempted to manipulate file, but still closes, and terminal displays nothing.  is there a command like "open" or "run" that will open the file from the terminal?  Sorry, still very new.

Should also be noted this is in .ppt format for windows colleagues, would that be the issue?

---

### Post by Paul820 on 2008-01-22
From the terminal
> ooffice -impress
If you need to find the command for a program in the future, just go to System->Preferences->Main Menu and right click on the program you want the command for and select **properties**, the command you need is under, well command :)

---

### Post by durdensbuddy on 2008-01-22
My command = ooffice-impress %U

As well as the following I receive the following pop-up error when attempting this "/home/
shannon/%U does not exist"  attempted same command from cd /root received same error.
shannon@shannon-desktop:~$ ooffice -impress %U

(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:8914): atk-bridge-WARNING **: failure: no device event controller found.

shannon@shannon-desktop:~$

---

### Post by durdensbuddy on 2008-01-23
bump

---

### Post by philinux on 2008-01-23
Did you try removing the open office config file.

Close any open office apps

Places>Home folder press ctrl h and delete .openoffice.org2.

When you then use open office it will regenerate this folder.

---

### Post by durdensbuddy on 2008-01-23
I receive the exact same results as before, except that the terminal error code has now changed to 

(soffice:6884): atk-bridge-WARNING **: failure: no device event controller found.


(soffice:6884): atk-bridge-WARNING **: failure: no device event controller found.


** (soffice:6884): WARNING **: Invalidate all children called

Seem to be losing the battle between learning new actions and deadline to finish the project.  I REALLY wanted to do the presentation in OO to physically SHOW that Linux is every bit as capable as MS.

---

### Post by durdensbuddy on 2008-01-24
So, I went ahead and wiped out my Ubuntu partition, resized and am back.  Now, I have the fun of reconfiguring everything, HOWEVER I find that Impress is working much more efficiently.  I was able to add custom animations to my entire slideshow, and now just need to add the audio.  

Thank you all for the help, but it appears somewhere somehow I had broken something and now have it fixed.

Any tips for making sure that audio plays throughout my slideshow?  I have been reading up and everything seems to imply that audio will end as you leave the first slide.  thanks.

Files have to be accessed by powerpoint and I am planing on recording in .wav format.

---

