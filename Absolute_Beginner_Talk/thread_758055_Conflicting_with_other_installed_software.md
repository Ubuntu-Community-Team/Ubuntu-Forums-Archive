---
title: "Conflicting with other installed software"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by 05rutterb on 2008-04-17
ok, i went to add/remove applications, tried to install VBA Express (game boy advance emulator) and it came up with a message saying:
"This application conflicts with other installed software"
what do i need to do/delete?:confused:

---

### Post by wpshooter on 2008-04-17
I believe that I would report this as a bug !!!

---

### Post by 05rutterb on 2008-04-17
ok, are you certain its a bug?

---

### Post by 05rutterb on 2008-04-17
dont know if this helps

vbaexpress:
 Depends: libfltk1.1 (>=1.1.7-2) but it is not installable

that seems to be the problem, dont know what it means

---

### Post by wpshooter on 2008-04-18
If there is software listed in the add/remove section of Ubuntu and it won't install, IMO, that is a bug.  However, the developers of this O/S have some strange rules as far as what qualifies as a bug sometimes. 

I would post on Launchpad.  All they can say is NO it is not a bug, I don't think they can shoot us.

---

### Post by SunnyRabbiera on 2008-04-18
well you may want to try and install VBA express with synaptic, it works better anywho.

---

### Post by mc4man on 2008-04-18
If your running gutsy try running from terminal
sudo apt-get update. Then try again
You could also search libfltk in synaptic and if installed post version, if not installed search libc6 and post version 
If your running feisty post back  - your trying to install the gutsy version somehow

---

### Post by 05rutterb on 2008-04-19
> **mc4man said:**
> If your running gutsy try running from terminal
sudo apt-get update. Then try again
You could also search libfltk in synaptic and if installed post version, if not installed search libc6 and post version 
If your running feisty post back  - your trying to install the gutsy version somehow

ok, i searched libc6 and it said the version installed is "2.6.1-1 ubuntu9"

---

### Post by mc4man on 2008-04-19
just so were on same page your running _gutsy_ ?
If so go back to synaptic, search libfltk and post what it says when you mark it for install

---

### Post by jimcub71 on 2008-04-20
[SIZE="3"][FONT="Arial Black"]I am also running Gutsy ( 7.10). I can't get anything to install. I've done the add / remove thing and get the " Conflicting with other installed software" message that tells me to use Synaptic Package Manger. I try that and get a "Could not mark all packages for installation / upgrade and a box with anywhere from 2 to ?? lines of text that start "Depends: something (ver number) but is not installable." 

I am new to ubuntu and am very frustrated that I can't get software, such as GNUCash to install, even after downloading something called a package to the tmp file. There is no executable file in the download that I can find to install the program. I have been trying to install GNUCash for 2 weeks now. 

Sorry to vent. I really do like Ubuntu and it has not crashed on me once. XP crashed at least twice a week. 

Thank you in advance for any help you can give. 

Jim[/FONT][/SIZE]

---

