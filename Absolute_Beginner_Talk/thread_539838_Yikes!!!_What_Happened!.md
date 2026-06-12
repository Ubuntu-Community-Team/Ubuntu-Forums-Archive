---
title: "Yikes!!! What Happened?!?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-08-31
Earlier today I wanted to get rid of all the gnome/ubuntu stuff so I could just get back to "pure" kde.. as shown here --> [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde). However after doing that, and rebooting,  now I can't get to the login! I can login by ctrl+alt+f1 though.. did my video settings go screwy or something because it's acting like it did when I first installed. But I'm not even sure where to start troubleshooting?!? Is Ubuntu gone?!? Thanks so much guys!!

---

### Post by Lord Illidan on 2007-08-31
Try installing kdm.

EDIT : Or even try re-installing it : sudo apt-get install --reinstall kdm

As I recall, it will then modify a file which will make KDM your preferred login manager.

---

### Post by andyho on 2007-08-31
Just tried that.. no such luck. :(

---

### Post by Lord Illidan on 2007-08-31
What happened then? Terminal output will be appreciated.

---

### Post by alienexplorers on 2007-08-31
i tried the directions in [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) when I moved from KDE to Gnome and had no problems.  Don't know why you would have problems going from gnome to all kde.

---

### Post by Lord Illidan on 2007-08-31
Then, can you post the contents of this file, please : */etc/X11/default-display-manager*

---

### Post by andyho on 2007-08-31
Oh sorry about that!! duh.. it reinstalled, so then I rebooted. But it just went back to black screen with blinky cursor.. I did check beforehand that it was installed, but figured re-installing wouldn't hurt. :confused:

When I type in /etc/X11/default-display-manager, I get;  
-bash: /etc/X11/default-display-manager: Permission denied

---

### Post by Lord Illidan on 2007-08-31
I meant, can you open the file with gedit or nano, and copy/paste the output here?

And, if from the terminal you type in sudo  /usr/bin/kdm what is the output?

---

### Post by andyho on 2007-08-31
> **Lord Illidan said:**
> I meant, can you open the file with gedit or nano, and copy/paste the output here?

geez.. my brain is so not functioning today! LOL! with nano it pops up; /usr/bin/kdm

> **Lord Illidan said:**
> And, if from the terminal you type in sudo  /usr/bin/kdm what is the output?

absolutely nothing.. it just goes back to the command line.

---

### Post by andyho on 2007-08-31
for some reason.. I have this really bad feeling that I might have typed in sudo aptitude remove ubuntu... instead of ubuntu-desktop. that wouldn't REALLY remove ubuntu though would it?!?

---

### Post by kuja on 2007-08-31
If kdm refuses to start, then your X config is probably hosed. 
Seeing as all you've got is a shell, type "grep EE /var/log/Xorg.0.log | less"to see where it's probably dying, also (and post the results), if you can, post your Xorg.0.log file too.

---

### Post by andyho on 2007-08-31
> **kuja said:**
> If kdm refuses to start, then your X config is probably hosed. 
Seeing as all you've got is a shell, type "grep EE /var/log/Xorg.0.log | less"to see where it's probably dying, also (and post the results), if you can, post your Xorg.0.log file too.

I get, (EE) No devices detected.

As far as posting the log, it wouldn't be possible afaik.. I'm using my hubby's computer (they are networked though) to troubleshoot mine and typing out the entire log would take all night! LOL! 

One thing I see is /usr/share/fonts/X11/cyrillic does not exist.. down at the very end of the log I have..

(II) Primary Device is: PCI 02:30:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:2:3:0) found
(EE) No devices detected

Fatal server error:
no screens found

Is there anything I should possibly be looking for within the log? Thanks again!!

---

### Post by Lord Illidan on 2007-08-31
Try opening /etc/X11/xorg.conf like this :

```
sudo nano /etc/X11/xorg.conf
```

Scroll down the file until you see

Section "Device"
[INDENT]Identifier      "NVIDIA Corporation NVIDIA Default Card"
Driver           "nvidia"

[/INDENT]Or something mentioning Nvidia, but importantly in Section "Device"

and see if this line is there, if not, add it there.

  BusID           "PCI:1:0:0"

Then use CTRL+X to exit nano.

---

### Post by andyho on 2007-08-31
> **Lord Illidan said:**
> Try opening /etc/X11/xorg.conf like this :

```
sudo nano /etc/X11/xorg.conf
```

Scroll down the file until you see

Section "Device"
[INDENT]Identifier      "NVIDIA Corporation NVIDIA Default Card"
Driver           "nvidia"

[/INDENT]Or something mentioning Nvidia, but importantly in Section "Device"

and see if this line is there, if not, add it there.

  BusID           "PCI:1:0:0"

Then use CTRL+X to exit nano.

Ok.. I have it pulled up and it says BusID "PCI:0:2:0".. should I add the line beneath it or should I just change it from 0:2:0 to 1:0:0?! Thanks! :)

---

### Post by andyho on 2007-08-31
Alright, well I tried it both ways.. got enough xorg backups now.. LOL! Still nothing though..

---

### Post by Lord Illidan on 2007-08-31
Can you just reinstall ubuntu-desktop to get to a working gui at least for the time being?

---

### Post by andyho on 2007-08-31
OMG that worked!! But now what?I have all the gnome stuff back. I guess I could try it again and make sure that I didn't just type ubuntu instead of ubuntu-desktop. But at least it's working again!! THANKS SOOOOO MUCH!!

---

### Post by chamberlain2006 on 2007-08-31
Perhaps you don't have the kubuntu-desktop package installed ?  Try doing "sudo apt-get install kubuntu-desktop" to do so.

---

