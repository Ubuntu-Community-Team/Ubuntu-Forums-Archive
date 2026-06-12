---
title: "Old mac-mini won't boot to linux install disks"
date: 2009-12-01
forum: Apple Hardware Users
---

### Post by jeff_p on 2009-12-01
Hello,

I have recently retired an old workhorse... my mac mini1,1. Its got a 1.66Ghz Intel Core duo, and a 60gb hard drive.

I am trying to install linux on it... Unfortunately, I have been unable to boot to an install CD. I do not get any error... just a nice black screen.

During boot, I hold down "option" to see all available boot disks, and select the CD from there. The screen goes blank, and then.... nothing.

I have tried several install disks... ubuntu, ubuntu alternate install, arch core, arch ISO linux.. nothing seems to work. The machine WILL boot to the OS X install disk, however.

Does anyone know what is wrong? What are my options? Is there some linux distro that people have used successfully with beloved old minis like mine?

Thanks,

---

### Post by linuxopjemac on 2009-12-02
What if you first install rEFIt? Will it then boot ?

Download and install [rEFIt]("http://refit.sourceforge.net/"), an EFI boot manager. rEFIt will allow you to choose between MacOS X and Ubuntu when you power on. Follow their instructions to install it on your MacOS X volume.

---

### Post by linuxopjemac on 2009-12-02
Feisty seems to work ootb:
[http://thedarkmaster.wordpress.com/2007/04/06/ubuntu-feisty-beta-on-intel-mac-mini/](http://thedarkmaster.wordpress.com/2007/04/06/ubuntu-feisty-beta-on-intel-mac-mini/)

---

### Post by jeff_p on 2009-12-02
@linuxopjemac: I have refit on it now... it will recognize both USB and CD boot images, but once I boot to them I have the same issue...  blank screen, nothing else.  

I will try Feisty tonight, with refit.  I'll report back!

---

### Post by linuxopjemac on 2009-12-02
The problem with Feisty is that it is an end of life version. You might try 7.10 and update that to 8.04.

[https://help.ubuntu.com/community/UpgradeNotes#Unsupported%20(Obsolete)%20Versions](https://help.ubuntu.com/community/UpgradeNotes#Unsupported%20(Obsolete)%20Versions)

---

### Post by linuxopjemac on 2009-12-02
I found something else which might be interesting for your Apple Mac Mini:

[http://support.apple.com/downloads/Mac_mini__early_2006__SMC_Firmware_Update](http://support.apple.com/downloads/Mac_mini__early_2006__SMC_Firmware_Update)

and this one:
[http://ubuntuforums.org/archive/index.php/t-467958.html](http://ubuntuforums.org/archive/index.php/t-467958.html)

the last one ;)
[https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini)

---

