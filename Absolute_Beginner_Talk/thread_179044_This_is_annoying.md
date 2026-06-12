---
title: "This is annoying"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-18
Ok I have been working with samba.  I am able to connect from my windows machine to my linux machine and vice versa.  I have Private and Public shares, and am using Security = share.  

Problem is that before I can access the linux box from the windows machine, I have to disable the network card, then reenable it.  Otherwise when I try to access the linux box it says that the computer may not have the correct permissions.  I would like to be able to connect to the linux box automatically since I have mapped the public drive as H.

Has anyone had this happen, and found a way to fix it...Ive been trying for 5 days.  I have tried to update the drivers, change smb.conf, basically anything I could think of on both machines.  I am out of ideas.  Anyone out there have any idea how to fix the Windoze ... Windows box.

---

### Post by joshrobinson on 2006-05-18
does it pop up and ask for a username and password? or does it go right to the permissions problem

---

### Post by JNowka on 2006-05-18
it goes directly to permission problems, I can't even get into it to see the shares.  When I disable reenable the card I am able to look at the shares avalible on the Linux box and put in passwords to the approriate folders.  I am able to access the public drive without passwords and write to it without hassle.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=JNowka]it goes directly to permission problems, I can't even get into it to see the shares.  When I disable reenable the card I am able to look at the shares avalible on the Linux box and put in passwords to the approriate folders.  I am able to access the public drive without passwords and write to it without hassle.[/QUOTE]

wow.. thats weird.. mines always worked fine i just had to add smbusers on my linux box so the windows machine could login

do you have any other windows machines to try it on? to see if its a problem with the windows computer? thats weird that after you re-enable it that it works

it cant be an fstab problem either, since it works at sometimes then others.. sorry i cant help, maybe someone else can point you in the right direction
it wasnt the problem i thought it was

---

### Post by JNowka on 2006-05-18
I know, i set up smbusers, i set up permissions, i have done everything I can.  
Thanks for the help anyways.

---

### Post by JNowka on 2006-05-18
Ok, Im gonna uninstall and reinstall File sharing on windows and reboot.  see if it works. brb


This seems to have worked.  I rebooted for the first time with the ability to access everything without disabling, reenableing the network card.  Apparently Windoze had a corrupt File Sharing install.

---

### Post by joshrobinson on 2006-05-19
[QUOTE=JNowka]Ok, Im gonna uninstall and reinstall File sharing on windows and reboot.  see if it works. brb


This seems to have worked.  I rebooted for the first time with the ability to access everything without disabling, reenableing the network card.  Apparently Windoze had a corrupt File Sharing install.[/QUOTE]

good idea reinstalling it.. it seemed like it had to be a problem on the windows end of things since you had everything configured correctly on ubuntu

---

### Post by ProjectGod on 2006-05-19
what sort of a network setup do you have? are you using DHCP?

are both machines on the same workgroup?

when windows asks you for "permissions" again try pinging the ubuntu machine. after a successful ping try connecting again to the shares.

---

