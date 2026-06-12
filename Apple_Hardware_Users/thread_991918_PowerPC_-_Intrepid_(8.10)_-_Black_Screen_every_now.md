---
title: "PowerPC - Intrepid (8.10) - Black Screen every now and then."
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by cygma on 2008-11-24
Hello,

Objective: 
a) To display the login screen without been having to put "Linux video=ofonly" every time.
b) To be able to display the screen after logoff or reboot.

Hardware info:
Mac mini G4/1.25 1.25 GHz PowerPC 7447a (G4)
(M9686LL/B) (No BTO option)
Only ubuntu and no other OSs on board.

Terminology:
The term "black screen" used on this thread is a "no-signal" symptom. When this occurs, the LCD notes a "no-signal" sign and stays on stanby.

Process:
1: Problem
I've installed Intrepid (8.10) Altenate via iso image distributed from the link below:
[http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

The installation was successful with respect to the tip towards the CD boot:
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

But now the login screen didn't appear after the reboot.

2: Seeking Solution

I've found this response on the following thread:
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

> **calebio said:**
> Yes, this worked for me as well. But after completing the install and rebooting, yaboot loads and boot starts and then the screen fades into white and nothing further happens. A bit scary....

I've had the same problem except my screen was black....
I've typed "Linux video=ofonly" and once in 2 tries it succeeds.
There is a 50% probability of the screen getting no signals.

> **calebio said:**
> Problem solved: at the yaboot prompt, run "Linux video=ofonly". Then once booted, edit /etc/yaboot.conf to include the following:
```
  append="video=ofonly"
```

I've tried this but it did not work for me.

3. More black screens...

After attempting to append yaboo.conf as above, I've tried to reboot through the desktop. However the screen remained blank for the next 10mins. I've held the power button for a force quit and after restarting the computer, this black screen problem still occured.

4. And more black screens.

After another force quit I've put "video=ofonly" and the login screen appeared. However after logging out from the account, the black screen appeared again and off for another force quit.

5. Black screens everywhere.

After the force quit on 4. I've tried to access the login screen again by typing "video=ofonly" but this time, the login screen didn't appear but another black screen appeared.

Please forgive my lengthy post. I've tried to be descriptive as I can. I would appreciate any help please.

---

### Post by tiresia on 2008-11-24
At the yaboot prompt try```
Linux video=ofonly nosplash
```
If it works, we'll fix it later

---

### Post by cygma on 2008-11-24
> **tiresia said:**
> At the yaboot prompt try```
Linux video=ofonly nosplash
```
If it works, we'll fix it later

Thanks. Gonna try now =D

---

### Post by cygma on 2008-11-24
> **tiresia said:**
> At the yaboot prompt try```
Linux video=ofonly nosplash
```
If it works, we'll fix it later

This seem to work fine. I can now reach the login screen 100%, but still have to input something while switching the machine on. I've tried changing yaboot.conf by changing
```
append="video=ofonly nosplash"
```
but that didn't change the situation. Plus it always blackens out into the dark when logging off/rebooting/shutting down.

---

### Post by tiresia on 2008-11-24
Before making any change to a system file, it is always safe to backup it
```
sudo cp /etc/yaboot.conf /etc/yaboot.conf.bak
```
Now you can edit that file as you like, and, if anything goes wrong, you can resume the old one just by copying it back so
```
sudo cp /etc/yaboot.conf.bak /etc/yaboot.conf
```

After editing the yaboot.conf file, adding the option 'append' as you did,  you must update the yaboot self, so that it becomes aware of the new configuration. Run```
sudo ybin -v
```

Anyway, if you have still problems with the video, which grafic card do you have?

---

### Post by cygma on 2008-11-24
Thanks again, and also thank you for the tip.
It seems as though I've forgot to update yaboot.
The updated code now properly enables the boot and object a) has been accomplished =D
Thank you very much indeed.

However, objective b) is still an issue.

Before I continue, the graphic card on this mac mini seems to be an ATI Radeon 9200 confirmed by sysinfo.

Having said that, logging off/rebooting/shutting down still results as a black screen. I've only left it on for about 5 mins so if the process takes longer than that, I appologise for my impatience (but surely that's too long isn't it?).

---

### Post by tiresia on 2008-11-24
What do you mean with 'black screen'? Is it just black, without any prompt?
Can you please post the files /etc/X11/xorg.conf and /etc/yaboot.conf?

---

