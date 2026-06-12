---
title: "Installations and file endings"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by alan_uk on 2007-04-07
I have installed Ubuntu 6.04.  I have become familiar with installing applications using Synaptic and tarballs using the terminal.  I am a bit confused over some of the file endings.  Do different distros have their own file endings?  For instance I attempted to install ati-driver from my home folder: ati-driver-installer-8.34.8-x86.x86_64.run. I used the terminal typing - 'sudo sh ati-driver-installer-8.34.8-x86.x86_64.run'  - and got the response 'No such file or directory'

---

### Post by Maestro23 on 2007-04-07
To exucute that file, navigate to the directory it is in. Then:

> chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run

sudo ./ati-driver-installer-8.34.8-x86.x86_64.run



ATI How-To: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

Can also try the Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good luck.

---

### Post by alan_uk on 2007-04-07
Thank you for your reply.  I followed your instructions but on typing 'chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run' in the terminal I got

alan@alan-desktop:~$ chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run
chmod: cannot access `ati-driver-installer-8.34.8-x86.x86_64.run': No such file or directory

The application is definitely in my Home Folder (SH shell file)

---

### Post by Maestro23 on 2007-04-07
> **alan_uk said:**
> Thank you for your reply.  I followed your instructions but on typing 'chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run' in the terminal I got

alan@alan-desktop:~$ chmod 755 ati-driver-installer-8.34.8-x86.x86_64.run
chmod: cannot access `ati-driver-installer-8.34.8-x86.x86_64.run': No such file or directory

The application is definitely in my Home Folder (SH shell file)

Are you in the /home folder when you try an run the command?

cd /home

ls (shows contents of /home)

---

### Post by alan_uk on 2007-04-07
Thanks successful! There was an mismatch in the file string so obviously the command could not succeed.  Just one small point - will this application resolve any graphic card issues between Linux and my ATI graphic card?

---

### Post by Maestro23 on 2007-04-07
> **alan_uk said:**
> Thanks successful! There was an mismatch in the file string so obviously the command could not succeed.  Just one small point - will this application resolve any graphic card issues between Linux and my ATI graphic card?

If you install it correctly, it should. Earlier, I linked you to an Nvidia wiki. sorry.  I went and changed the link to the ATI wiki that I used to install my X1600.  Sorry about that and good luck.

Some more useful Ubunutu links:

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
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

