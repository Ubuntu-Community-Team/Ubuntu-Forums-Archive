---
title: "How do I Install Windows?"
date: 2011-10-06
forum: Any Other OS
---

### Post by AnaMarie on 2011-10-06
Well, I have a problem. I've been using Linux for about a year now, but I have to revert back to windows, because it can't open certain files I need (even *with* Wine). So, heres the situation:
I inserted my (legal) windows disk, and opened up the file.
I double clicked on the *setup.exe* file, thinking I could open it using Wine.
And I get this error:
[COLOR=Red][I]
"The file '/media/CD_ROM/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."[/I][/COLOR]

So I right clicked, and tried to change the permissions to execute the file, but I got,
[COLOR=Red][I]
"Sorry, could not change the permissions of "setup.exe": Error setting permissions: Read-only file system"[/I][/COLOR]
[COLOR=Black]
Is there any solution for this? I don't want to have both Windows and Linux on my computer, I need to get rid of Linux completely and only have Windows. Please help me! [/COLOR]:(

---

### Post by vandorjw on 2011-10-06
With the CD in the cd-drive, restart your computer. When it says something like;
> 
Press any key to boot from cd ... 3 ..2...1 


Hit "enter"

Follow on screen instructions.
PS: I hope you still have your activation key that comes with the CD.

---

### Post by MG&amp;TL on 2011-10-06
Two options. 

1. Run it in virtualbox. Install virtualbox, setup a new machine, insert the windows cd, select your real cd drive in the Settings dialog, boot it, away you go.

2. Boot, change BIOS to boot from CD. This may be DEL, F2, F12, SHIFT, ESC, TAB, it will probably say very quickly. Once in BIOS, go to boot sequence and select CD to be first. Then reboot, insert the CD, reboot, and follow the windows installer prompts. You CANNOT run it from you linux desktop. Not that simple.

---

### Post by haqking on 2011-10-06
> **AnaMarie said:**
> Well, I have a problem. I've been using Linux for about a year now, but I have to revert back to windows, because it can't open certain files I need (even *with* Wine). So, heres the situation:
I inserted my (legal) windows disk, and open up the file.
I double clicked on the *setup.exe* file, thinking I could open it with Wine.
And I get this error:
[COLOR=Red][I]
"The file '/media/CD_ROM/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."[/I][/COLOR]

So I right clicked, and tried to change the permissions to execute the file, but I got,
[COLOR=Red][I]
"Sorry, could not change the permissions of "setup.exe": Error setting permissions: Read-only file system"[/I][/COLOR]
[COLOR=Black]
Is there any solution for this? I don't want to have both Windows and Linux on my computer, I need to get rid of Linux completely and only have Windows. Please help me! [/COLOR]:(
 you dont use wine to install windows.

Boot your computer to the disk and the install should run.

make sure your personal data is backed up first so you can still access it after getting back to windows

---

### Post by AnaMarie on 2011-10-06
Seriously. I don't know what it was, but all of your posts just made something "click" in my head. I've read God knows how many posts on this stuff, and all of a sudden I'm understanding now! Thank you so much! I'm installing it now, (hopefully it works out right)!

---

### Post by haqking on 2011-10-06
> **AnaMarie said:**
> Seriously. I don't know what it was, but all of your posts just made something "click" in my head. I've read God knows how many posts on this stuff, and all of a sudden I'm understanding now! Thank you so much! I'm installing it now, (hopefully it works out right)!

no worries.

If all goes to plan please come back and mark the thread as solved using thread tools.

Ubuntu will miss you and holds no grudges so come back to it at anytime ;-)

cheers

---

### Post by AnaMarie on 2011-10-06
I do plan to come back to Ubuntu! It was really nice, easy, and started up fast!
And its working just fine, thanks! ;)

---

### Post by Gs Dewd on 2011-10-16
Also make sure you have all the drivers for your hardware handy.

---

### Post by drawkcab on 2011-10-16
dual boot

---

### Post by MonolithImmortal on 2011-10-18
You could run windows in a virtual machine.

---

### Post by SharkMonster on 2011-10-18
> **Gs Dewd said:**
> Also make sure you have all the drivers for your hardware handy.

True, but Windows Update should get most of them.

---

