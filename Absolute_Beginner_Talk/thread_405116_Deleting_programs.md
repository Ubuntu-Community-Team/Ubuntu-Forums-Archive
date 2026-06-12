---
title: "Deleting programs"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by dmsymr on 2007-04-09
Im Using ubuntu 6.06 (having difficulty upgrading to 6.10, but thats for another thread!) I have managed to download automatix for 6.10 so it wont operate. Is their any way of deleting or removing a program in Ubuntu? I didnt use add/remove in applications menu to download it so I cant remove it that way. For that matter....Is their a correct way of removing anything I download from the web?
Also, Is their a program that cleans up system junk like disk cleaner in windows? Im very new to linux so im installing a lot of programs hit and miss so my system is getting very cluttered.
Please be gentle...Im a layman so dont understand most of the linux language yet!

---

### Post by taurus on 2007-04-09
Applications -> Accessories -> Terminal
```
sudo aptitude remove automatix2
```
You also need to either remove automatix's repo in /etc/apt/sources.list or at least replace the word edgy with dapper since you are using dapper, not edgy.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Maestro23 on 2007-04-09
Here's some links to massage your brain on:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jvc26 on 2007-04-09
Depending primarily how you installed them you can just get rid of the program with the command:
```

sudo apt-get remove PACKAGENAME

```
or to remove it and the config files too:
```

sudo apt-get --purge remove PACKAGENAME

```
You can also search within Synaptic Package manager (System -> Administration -> Synaptic Package Manager) for the app you're after and select to remove or completely remove it.

Finally on the cleanup section look no further than here:
[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)
Il

---

### Post by dmsymr on 2007-04-09
Thankyou Taurus, Maestro23 and Illuvator very much, I am as we speak downloading the correct version of automatix and going through all links on the thread. Im so glad I switched to linux but its not as user friendly for someone as untechnically minded as myself! Im getting their!

---

### Post by PurplePenguin on 2007-04-09
Maestro23, that's a great list of links!  You could just go from one thread to the next posting that and everybody would be happy. :D

---

