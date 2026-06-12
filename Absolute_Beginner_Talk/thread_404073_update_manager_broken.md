---
title: "update manager broken"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rhardie on 2007-04-07
Since I'm new and busy shooting myself in the foot on occassion (don't need a conceled carry permit to shoot myself in the foot) I suspect I broke my software.

6.10 version

Attempt to update software

Error Message:

E: dpkg was inturrupted.  You must manually run 'dpkg -- configure -a' to correct the problem.

I guess this means I'm supposed to run a scrip but I don't know how at this point.

How can I repair this?

Rhardie
Austin, TX

---

### Post by ComplexNumber on 2007-04-07
its not broken.
fire up the terminal (you will find it in main menu -> accessories -> terminal). then then type in the following:
**dpkg -- configure -a** (i think you may have to precede this by sudo, but can't remember)

when its finished, you can then try again :)

---

### Post by rhardie on 2007-04-07
SUDO was required.  That did the trick.  Thanks!

RockyH
Austin, TX

---

### Post by rhardie on 2007-04-07
Another question, if you don't mind.

I am new to LINUX and Ubuntu and don't normally work with operating systems - and this is quite fun; however, I need to learn some of the basic functions with the command lines.

I have the book Ubuntu Unleashed as a reference.  Any suggestions on a sequential process of learning how to operate/manipulate within the operating system?

Example:  I am attempting to get the media player to play a DVD and the totem is broken and I have no clue what to do.

I may download an application or printer driver onto the desktop and not know how to get it loaded for use.  Kinda like having "windows withdrawal" or something.

Thanks in advance,

Rocky H
Austin, TX

---

### Post by rhardie on 2007-04-07
Was updating software and received this error.

E: /var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb: subprocess pre-installation script returned error exit status 10

Would I be lucky enough to be able to do a simple command line entry? :-)

Thanks,

Rocky H
Austin, TX

---

### Post by Maestro23 on 2007-04-07
> **rhardie said:**
> Another question, if you don't mind.

I am new to LINUX and Ubuntu and don't normally work with operating systems - and this is quite fun; however, I need to learn some of the basic functions with the command lines.

I have the book Ubuntu Unleashed as a reference.  Any suggestions on a sequential process of learning how to operate/manipulate within the operating system?

Example:  I am attempting to get the media player to play a DVD and the totem is broken and I have no clue what to do.

I may download an application or printer driver onto the desktop and not know how to get it loaded for use.  Kinda like having "windows withdrawal" or something.

Thanks in advance,

Rocky H
Austin, TX

I see I was beaten in telling you to run the command. :)   Perhaps I can provide you with some links that will help you learn the Ubuntu way:

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


Welcome and Good luck.:guitar:

---

### Post by rhardie on 2007-04-07
Thanks for the links.

Reading a reference manual and attempting to learn something is like having my face 6 inches off the ground and crawling through a forrest when I need to be on a hill top to survey the general landscape (big picture) before decending into the trees.

Thanks again,

Rocky H
Austin, TX

---

### Post by ComplexNumber on 2007-04-07
**rhardie**
you will learn as you go along ;). just have fun.

---

