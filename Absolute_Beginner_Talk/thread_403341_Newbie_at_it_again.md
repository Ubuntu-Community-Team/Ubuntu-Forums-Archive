---
title: "Newbie at it again"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Swimerdude on 2007-04-06
Ok so i was trying to install the latest drivers onto my machine(mainly to get beryl working but also just to have the latest drivers.)  the past 2 times i've crashed the system and had to reinstall.  this time i tried out envy.  which seemed to wor untill i reinstalled.  Now at that point it asked to change an x(filename) or something simliar, i said auto configure, and it seemed to work, i restarted and boom:( terminal.  now i'm your newbie and cna't really work around in just the terminal yet.  but how should i stop this from happening so much?

---

### Post by yabbadabbadont on 2007-04-06
Quit playing with experimental beta software...  ;)

Try:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Maestro23 on 2007-04-06
> **yabbadabbadont said:**
> Quit playing with experimental beta software...  ;)

Try:```
sudo dpkg-reconfigure xserver-xorg
```

Yeah. I'm seeing a pattern in all posts with a join date in March/April:  "My computer blew up."  "Can't login anymore".  "I was trying to install Beryl and...":) 

To the OP:  Hope you get you system back up.:guitar:

Some links to introduce the OP to Ubuntu:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29%7C%28driver%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29%7C%28driver%29)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Swimerdude on 2007-04-07
I didn't know putting the newest drivers on a computer was installing beta software:) I totally understand that using beta software has big chances of having issues:)   I was just wondering because I've tried dling the packet form nvidia, that didn't work.  I've tried using the sudo get things and that never seems to work(the guide on the beryl page) and envy didn't work for me:) so i was seeing if there was another way that i haven't tried that might be better:)

---

### Post by yabbadabbadont on 2007-04-07
Beryl is the experimental beta software to which I was referring.  :)

Try getting the latest nvidia drivers using the "envy" utility and get them working before you try messing with Beryl.  Once they are working, then tackle the Beryl part.  Baby steps.  :D

See the following for getting the latest video drivers with envy:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

By the way, you didn't say which version of Ubuntu you are using.  Dapper, Edgy, Feisty  (if you are using Feisty, you deserve all the trouble you get ;))

---

### Post by Swimerdude on 2007-04-07
opps. Well i am using edgy.  And i did use envy and it didn't work for me:)   But thanks for the help i really appreciate it.

---

### Post by Maestro23 on 2007-04-07
> **Swimerdude said:**
> opps. Well i am using edgy.  And i did use envy and it didn't work for me:)

Glad to hear. Read over those links I provided, will help you alot.

---

### Post by Swimerdude on 2007-04-07
So guys i'm at it again. well io got my video drivers to work but somehow i got rid of my wireless drives.  where should i go to replace the ones that have disappeared?

---

