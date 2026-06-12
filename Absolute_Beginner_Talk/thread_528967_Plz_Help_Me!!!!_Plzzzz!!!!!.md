---
title: "Plz Help Me!!!! Plzzzz!!!!!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Franscartoons on 2007-08-18
I installed BackTrack and it wouldn't let me boot ubuntu (or get to grub), so I re-installed ubuntu, hoping that it would fix the boot and still keep the old ubuntu (files, apps, settings..just how it was before).
It boots up ubuntu, but theres none of the old versions in grub, just the new one.

Now I looked carefully when it was installing to make sure it never said "format" or "delete" or anything like that.

Plz help me get my old ubuntu, just like it was before.

PLEASE HELP!

Thanks.

:confused::(:confused::(:confused:

---

### Post by Drakkor on 2007-08-18
Sorry,but it seems to me, the only way you'll get everything like it was before, would be to make a backup image of the whole OS,before you installed something to restore it back....before the catastrophe. I use Acronis from my windows partition to backup all of Ubuntu

---

### Post by Chris S. on 2007-08-18
I don't know how you did it, but when I reinstalled Ubuntu from the Live CD it forced me to format the root partition where Ubuntu installs.  If you did the same and missed this message, then you may have formatted the root partition during reinstall.

---

### Post by GuitarRocker2562 on 2007-08-18
well, i cant help you finding it, but it may be there, anyway, to keep this form hapening, once you found your files and backed them up, or came to the conclusion you can't get them, re-install ubuntu but make a seperate /home partition!

---

### Post by Franscartoons on 2007-08-18
Damn.
I never backed it up, I have installed it before and it just added it to the boot list.

if theres anything i can do to just get the files back aleast..PLEASEEEEE LET ME KNOW!

PPLLLLEEEAAASSSSEEEEEEEEEEEEEE!!!!11!11!!!!!!111!!:(

---

### Post by schorsch on 2007-08-18
If your home directory was not on a separate partition but in the / filesystem lying on the same partition .. sorry, without a backup you will have no chance to get it restored ... :-(

---

### Post by Franscartoons on 2007-08-18
But i have installed a few ubuntus before and they didn't wipe the old ones, and iam sure it never said anything about formatting.

:(:(:(:(:(

---

### Post by schorsch on 2007-08-18
> **Franscartoons said:**
> But i have installed a few ubuntus before and they didn't wipe the old ones, and iam sure it never said anything about formatting.

:(:(:(:(:(
On the same hardware? Install or upgrade? Well, perhaps the BackTrack installation could have messed something up. But perhaps you had separate partition for your $HOME. 

Please post the output of 
```
sudo fdisk -l
```

---

### Post by Franscartoons on 2007-08-18
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4783    38419416   83  Linux
/dev/hda2            4784        4864      650632+   5  Extended
/dev/hda5            4784        4864      650601   82  Linux swap / Solaris

---

### Post by schorsch on 2007-08-18
Uhm, sorry to tell you that but as far as I can see you are not able to restore the old settings as everything regarding your $HOME is on one partition and this seems to to be formatted after the last install of ubuntu .... sorry ...

---

### Post by Drakkor on 2007-08-18
I'm not backing up no more, just waiting tor the 7/10/07 release of Gutsy,lol.
I only clean install everthing,lol :)  It's a new day !!!, lol

---

### Post by Franscartoons on 2007-08-18
Well, is there anyway just to undelete the files? (like my documents)

---

