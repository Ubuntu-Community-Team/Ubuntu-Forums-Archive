---
title: "Install lubuntu from desktop (not alternate) cd without x?"
date: 2012-01-22
forum: Apple Hardware Users
---

### Post by conal on 2012-01-22
Hi, can anyone tell me how to install from the desktop cd without the desktop environment?

More info:

I´ve had 2 successfull installs of lubunut 12.04 now, one iMac G4, one eMac. I want to get this on my old G3 iMac as well but the alternate install disk comes up with a message about kernel mismatch, saying it is unlikely the install will be successfull.

The desktop cd boots fine, but as is always the case with these machines, it boots into text only, with no x. Can anyone tell me how to install from the desktop cd without the desktop environment? I need to be able to specify which partition to use as well!

Thanks!

---

### Post by rsavage on 2012-01-22
Can you not setup an xorg.conf and then type:
 
sudo start lxdm

---

### Post by conal on 2012-01-22
´Doh! That is so obvious, thanks rsavage!

---

### Post by rsavage on 2012-01-22
Hi conal, did this work?  I've always wondered if it would!
 
Also, did the installer freeze on each of your machines?
 
Can you check your sources.list to see if you have ports.ubuntu.com referenced please?

---

### Post by Q-collective on 2012-01-22
Not setting your xorg.conf would probably not work actually, as Xorg can these days create a configuration on the fly.

If you want a version without X, you could just remove the desktop environment and Xorg.

---

### Post by conal on 2012-01-22
Hi rsavage,

No, none of the xorg.conf files that have worked on this machine in the past are working for me with lubuntu 12.04. Never mind; I have two successfull installs, don't really need 3. 

By the way:

sudo start lxdm

...retuned a message that lxdm was not installed, but:

sudo startx 

...seemed to start the process. Each xorg.conf I tried returned a different error - if I crack it I'll post my xorg.conf here!

And no the installer did not freeze on my other machines (except temporarily on the iMac as I described to you in a previous thread)

Thanks 

Conal

---

### Post by rsavage on 2012-01-23
Yeah considering 12.04 is still in development I think you are pushing your luck!  Maybe install 11.10 instead?
 
Xorg.conf maybe needs:

     [COLOR=#222222]Option "UseFBDev" "False"[/COLOR]
     [COLOR=#222222][COLOR=#222222]O[/COLOR][/COLOR][COLOR=#000000]ption "NoInt10" "True"          [/COLOR]

or 
 
Disable "dri"
 
as per the FAQ?
 
Thanks for the feedback on the commands/installer.

---

### Post by conal on 2012-01-23
Thanks, I didn't try Option "NoInt10" "True" - but I tried Option "UseFBDev" with "False" and "True" and tried Disable "dri". One of the error messages was about No Frame Buffer device being found. Anyway, I think I'll wait until the proper release before I go back to this!

---

