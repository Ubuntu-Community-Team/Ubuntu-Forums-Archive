---
title: "Ubuntu and kubuntu"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by pbplaya87 on 2006-11-17
I currently have Windows XP and Ubuntu installed on my pc, and I also want to install kubuntu as well.  Do i need the regular install version or the alternate version since I already have grub installed on my computer to handle the boot selection? Or is there an easier way to have both desktops.

---

### Post by Henry Rayker on 2006-11-17
I believe you could always install the KDE and the Kapps separately and select KDE or GNOME at the login screen. The sessions option in the options on the bottom left allow you to choose.

I have Enlightenment, GNOME, Fluxbox and XCFE all on one Ubuntu installation. (I'm trying to find out exactly what I like).

---

### Post by petit.padavoine on 2006-11-17
To install the Kubuntu Desktop,
```
sudo apt-get install kubuntu-desktop
```.

Then when logging in, choose it in sessions.

---

### Post by That_Geek on 2006-11-17
i would suggest sudo aptitude update

sudo aptitude kubuntu-desktop

(aptitude makes for an easier uninstall, while a more painful install, its your choice)

---

### Post by infoseeker on 2006-11-17
I installed Kubuntu and Ubuntu (from the alternate CD's) each into its own partition, with a symlink in Ubuntu pointing to the Kubuntu 'menu.lst' (for kernels,grub, etc).  I thought I would do it this way to test the merits of each independently, whether this reason is at all valid, I still don't know. I do all the updates and downloads using Kubuntu and then copy these downloaded files (debs) into the Ubuntu's '/var/cache/apt/archives/partial' directory and when I do the Ubuntu updating/software installing it finds most of the required files there.  Seems to work fine (for me) :).

---

### Post by mep on 2006-11-17
Use: 

sudo aptitude install kubuntu-desktop

-mep

---

### Post by Get_Ya_Wicked_On on 2006-11-17
The following packages will be REMOVED:
  libgl1-mesa 
0 packages upgraded, 217 newly installed, 1 to remove and 0 not upgraded.
Need to get 186MB/187MB of archives. After unpacking 520MB will be used.
The following packages have unmet dependencies:
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.5.1+cvs20060824) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]

Downgrade the following packages:
libgl1-mesa-dri [6.5.1+cvs20060824 (now) -> 6.5.1~20060817-0ubuntu3 (edgy,
edgy)]

Leave the following dependencies unresolved:
libxine1 recommends libxine-extracodecs
Score is -266


I have beryl with XGL and the ATI fglrx drivers installed.

What is this saying in layman's?

---

### Post by Zeerak on 2006-11-17
did you apt-get it or aptitude it? while there is virtually no difference but  there is a bit of a difference according to what i've read and when i've used it.

---

### Post by Get_Ya_Wicked_On on 2006-11-17
aptitude'd it...

I'm thinking it's just going to downgrade my mesa library...

(which I thought I had removed since I'm using fglrx)

But I am not going to do anything without some type of assurance.

---

### Post by Get_Ya_Wicked_On on 2006-11-18
Anyone?

---

### Post by lumpki on 2006-11-18
It's suggesting a fix. First downgrade the libgl1-mesa-dri package to the version it wants:
```
sudo apt-get install libgl1-mesa-dri=6.5.1~20060817-0ubuntu3
```
Then try 'sudo apt-get install kubuntu-desktop' again.

---

### Post by pastorjay on 2006-11-18
Henry, can you explain how you installed the enlightenment desktop?  I would love to do that myself...

Jason


> **Henry Rayker said:**
> I believe you could always install the KDE and the Kapps separately and select KDE or GNOME at the login screen. The sessions option in the options on the bottom left allow you to choose.

I have Enlightenment, GNOME, Fluxbox and XCFE all on one Ubuntu installation. (I'm trying to find out exactly what I like).

---

