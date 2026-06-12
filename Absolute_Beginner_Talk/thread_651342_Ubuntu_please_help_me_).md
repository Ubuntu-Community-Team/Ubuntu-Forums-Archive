---
title: "Ubuntu please help me :)"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Alsubiheen on 2007-12-27
Hello & thanks for checking my thread :)

Well FINALY i understood how to install Ubuntu :) and to be honest it looks very nice iam so happy.

just there are some issues or lets call them points that need clearing please :)

1. after installing, i can't see any graphical effects :( when i go to "System => Prefrences => .... Nothing where i can chose the Graphical Effects =(

2. a pop up came and asked me to actually Download { 186 Updates !! } ... may i know what are they, i allready accepted and they are being downloaded as we speak. but are they new programs ? new games ? new drivers ?

3. one of the major issues iam facing is that this PC iam on right now has over 1 TB of movies and pictures and all my files. why can't i access any of that on Ubuntu ? =(

4. Anything hints pointers i should know about regarding Ubuntu as a first time user ? like downloding a Very important program or upgrade ? you know something i should know about, because this is my first time.

Well and now i would like to Thank you for reading my post, as my FIRST post on Ubuntu :)

Many thanks and appreciation in advance :)

Loyal regards,
Bassim M. Al-Subiheen

---

### Post by rickycodie on 2007-12-27
welcome to ubuntu!!

1. in system> preferences> choose appearance, then click on the effects tab. that should work.

2. the updates are newer versions of programs that you already have.

3. where are the files located?

4.check out [http://www.psychocats.com](http://www.psychocats.com)

---

### Post by jas0 on 2007-12-27
1. Right click your desktop > Change Desktop Background > Visual Effects > Normal/Extra. See what happens and whether it lets you do this. If it doesn't, there are things we can try.

2. This is normal. The reason why the download is so huge is because you're probably downloading a new kernel and a new version of OpenOffice

3. If these files are on the same computer in non-RAID drives, you will be able to access them by going to /media and exploring the drives (named something like sda1 or sdb1)

4. You're already downloading all the updates, so you're fine there. My suggestion is to just start doing what you would normally do on a computer and see what happens. When you stumble onto something you don't know how to do, you can search this forum or ask and we'll point you in the right direction.

---

### Post by rune0077 on 2007-12-27
1. Check System > Preferences > Appearance, then go to the Visual Effects tab. Under the Advanced Desktop Effects (I think its called) you can "tweak" all the effects.

2. The updates are all security updates and bugfixes to software that came with the installation. 

3. If you have a windows partition, Ubuntu should be able to read from that and access the file. If you just installed Ubuntu without partitioning you harddrive(s), the bad news is that you deleted the old partition. Let's hope that's not the case, though. Could you post some more info on where these files used to be installed.

---

### Post by nick_h on 2007-12-27
1. Look under System->Preferences->Appearance and then the Visual Effects tab.
2. These will be updates to installed programs including security updates.  It is best to let them install.
3. Are these files on a separate drive? What filesystem (FAT, NTFS)?
4. The [Ubuntu Starter Guide](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) may be of interest.

---

### Post by Alsubiheen on 2007-12-27
Ok well, when i go to System > Prefrences .... there are no Appearance there :(

and the downloading is done btw finaly :)

regarding those files, i should tell you that iam running both Windows XP & Ubuntu ... and those files are accessable through Windows XP ... however i can not find them on Ubuntu ... all my Hard disks are formatted with NTFS.

please tell me how can i solve this, or even a link that will help me get better visual effects :(

Many thanks and appreciation in advance :)

Loyal regards,
Bassim

---

### Post by rax_m on 2007-12-27
Hmm.. that's strange that you don't have an "Appearance" menu item.
As a work around you can right-click on the desktop and select "Change Desktop background". Then select the visual effects tab. 

You can also find many themes at [www.gnome-look.org](www.gnome-look.org) to change the appearance of your desktop. 

Are you XP drives not listed under your Places menu on the top panel?

Cheers

---

### Post by ChaosParser on 2007-12-27
Did you install 7.04 or 7.10? 
Fawn or Gutsy?

---

### Post by spiderbatdad on 2007-12-27
to work with the visual effects you have to have compizconfig-settings-manager from synaptic...not installed by default. Also need a windows theme manager Emerald ( in synaptic) and probably a rendering tool like xserver-xgl. 

once you install all that. launch emerald from Applications>>Preferences and work your way through the tabs to download a gpl theme...then use it.   

Reboot your computer, assuming you have gotten xserver-xgl, and it is right for your video card. Then enable "custom" effects from the visual effects tab in Appearances.

Then the learning has just begun. Probably the first step is determining your video card to ensure you get the right driver:

```
sudo lshw -C Video
```

---

### Post by rune0077 on 2007-12-27
> **spiderbatdad said:**
> 
Reboot your computer, assuming you have gotten xserver-xgl, and it is right for your video card. Then enable "custom" effects from the visual effects tab in Appearances.


Mmm, that might be hard, considering that he just pointed out there is no Appearances in his menu. But if you install CCSM (the Compiz Setting Manager thingy), then you should get an item in System > Preferences called Advanced Desktop Effects Settings that does the same thing.

---

### Post by ChaosParser on 2007-12-27
Sounds like 7.04.

---

### Post by Alsubiheen on 2007-12-27
How can i put this withought insulting my self lol

Iam a Noob, so i have no idea which Ubuntu it is, to be honest i just installed it because of the great graphics thats it lol then i discovred about all the other great functions lol

so iam not sure which version it is.

All i know is i can't find "Apperance", nether from System or from right clicking on Desktop. it just doesnt exist :(

allthough, after reading i saw that Ubuntu faces some problems with ATI cards. would that be the logical reason why its not working ? as in my card seems too bad for Ubuntu thus it is not giving me those Great Graphics Options ?

Waiting for your answers :)

Many thanks and appreciation in advance :)

Loyal regards,
Bassim.

---

### Post by LaRoza on 2007-12-27
Edited, I should read before posting

Find your version in System->About Ubuntu

---

### Post by Alsubiheen on 2007-12-27
> **LaRoza said:**
> Appearance should be under System->Preferences

Yes i know :) ... but it not there, and i can't even find it even when i right click on the Desktop and click on Change Back Ground :(

you think my ATI VGA Card has anything to do with it ?

---

### Post by Alsubiheen on 2007-12-27
it says under  System > About Ubuntu

"Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006."

---

### Post by LaRoza on 2007-12-27
> **Alsubiheen said:**
> it says under  System > About Ubuntu

"Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006."

Sorry to disappoint, but that is a really old version and doesn't have the effects and they cannot be installed.

If you can download: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The older edition is there because it is LTS. It is supported for a longer period of time and is best used by Businesses and others you don't want to upgrade every 6 months, but still need support

---

### Post by spiderbatdad on 2007-12-27
can you enter this in the terminal:  ```
sudo cat /etc/lsub-release
```

sorry to interupt...couldn't find that under system>>preferences. now i see it under system

---

### Post by Alsubiheen on 2007-12-27
> **LaRoza said:**
> Sorry to disappoint, but that is a really old version and doesn't have the effects and they cannot be installed.

If you can download: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The older edition is there because it is LTS. It is supported for a longer period of time and is best used by Businesses and others you don't want to upgrade every 6 months, but still need support

Tears are filling up my Keyboard lol :P


 Oh well, it was too good to be true any way hehe, ok last question please :)

which one should i download :)

Ubuntu 7.10 - Supported to 2009 ?

and a stupid question i know, and you may make fun of me lol ..... how can i uninstall the version of Ubuntu that i allready have lol ?


Many thanks and appreciation in advance :)

Loyal regards,
Bassim

---

### Post by LaRoza on 2007-12-27
> **Alsubiheen said:**
> Tears are filling up my Keyboard lol :P


 Oh well, it was too good to be true any way hehe, ok last question please :)

which one should i download :)

Ubuntu 7.10 - Supported to 2009 ?

and a stupid question i know, and you may make fun of me lol ..... how can i uninstall the version of Ubuntu that i allready have lol ?

Buy on of these: [http://www.cyberguys.com/templates/SearchDetail.asp?productID=11563](http://www.cyberguys.com/templates/SearchDetail.asp?productID=11563)

Yes, 7.10

If you plan on installing again (with the new version) just chose to install to the same partitions.

---

### Post by spiderbatdad on 2007-12-27
you might post the results of lspci first to get some input as to whether the special effects will work on your system, before you go through all the trouble.

---

### Post by Alsubiheen on 2007-12-27
> **LaRoza said:**
> Buy on of these: [http://www.cyberguys.com/templates/SearchDetail.asp?productID=11563](http://www.cyberguys.com/templates/SearchDetail.asp?productID=11563)


LOL ok thanks

---

### Post by Alsubiheen on 2007-12-27
Thanks alot ladies & gents for your time and effort and help.

I really do appreciate it alot :)

i shall download the new version and post again once iam live from Ubuntu :)

Loyal regards,
Bassim :)

---

