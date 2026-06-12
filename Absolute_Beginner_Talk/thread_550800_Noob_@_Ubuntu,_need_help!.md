---
title: "Noob @ Ubuntu, need help!"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by mdhus on 2007-09-14
Hello.

Just installed Ubuntu 7.04 on new desktop i just built.  After toying around with it for a while i have found that i do not have permission to the file system or "root" system.  I found this while trying to install Lucent Modem drivers(yep, here in the sticks, dialup is the ONLY thing available).  I downloaded what i believe to be the current driver for Linux and copied them to the File System from one of my windows FAT32 Harddrives(i have dual-boot windows xp pro also) then copied them over to the file system.  However, when i go to access the the drivers via the terminal:

```
siko@sikos-desktop:~$ /ltinst
```

or any other type of command such as that
all i get is "Permission Denied"

I was wondering, how do i get permission?

since i cannot get permission, i cannot tell if it is the right driver for ubuntu(any sites with modem drivers help will be well appreciated, or any tips)

and for my last question, once i get the drivers installed, how do i tell ubuntu to "dailup"(gags and chokes)?...

thanks much
mdhus

---

### Post by LowSky on 2007-09-14
type 

```
 sudo -i
```
then enter your password

you should be fine then

---

### Post by PmDematagoda on 2007-09-14
Use the sudo command in front of ```
/ltinst
```, this'll ask for your password, you cannot see the password as you enter it by the way, but its there. 

You can use gnome PPP as a dial-up though I haven't used it.

Edit:- Darn you LowSky, you beat me to it. Though your way's better.:)

---

### Post by mdhus on 2007-09-14
Cool....ill check that out later and see if it works(hopefully it doe:))...do you guys know the best driver to use for a Lucent Modem?

---

### Post by LowSky on 2007-09-14
PmDematagoda  I figured ```
sudo -i
``` would be better command for him because it can be used at other moments too. While ```
 sudo /ltinst
``` would only run that program.. I was hoping mdhus might pick up on that.

---

### Post by Maestro23 on 2007-09-14
> **mdhus said:**
> Cool....ill check that out later and see if it works(hopefully it doe:))...do you guys know the best driver to use for a Lucent Modem?

Might help: Lucent Modem HOW-TO: [https://help.ubuntu.com/community/DialupModemHowto/Lucent?highlight=%28Lucent%29%7C%28modem%29](https://help.ubuntu.com/community/DialupModemHowto/Lucent?highlight=%28Lucent%29%7C%28modem%29)

---

