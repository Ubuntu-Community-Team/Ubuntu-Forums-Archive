---
title: "Ultra Noob"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by HalOfBorg on 2007-04-16
I have been using Ubuntu for about.....(checks watch) 3 hours now.

I am trying to ignore all I know about Windows, and I am comfortable in the Terminal. 

BUT - there is a couple things I'd like to know.

1) How the EXPLETIVE DELETED do I type that vertical line??
example: glxinfo | grep

The line between the words.


2) I tried to install video drivers, and Ubuntu told me I need to be the "super user" to do this. I can't find it in the HELP anywhere. I am the ONLY user on the PC.

---

### Post by overdrank on 2007-04-16
> **HalOfBorg said:**
> I have been using Ubuntu for about.....(checks watch) 3 hours now.

I am trying to ignore all I know about Windows, and I am comfortable in the Terminal. 

BUT - there is a couple things I'd like to know.

1) How the EXPLETIVE DELETED do I type that vertical line??
example: glxinfo | grep

The line between the words.


2) I tried to install video drivers, and Ubuntu told me I need to be the "super user" to do this. I can't find it in the HELP anywhere. I am the ONLY user on the PC.

Hi it is the key at the top of the backslash on the top row next to the backspace. And what type of video card do you have?  Hope that helps and welcome.

---

### Post by theonlyrealperson on 2007-04-16
Congrats!

On my keyboard, the pipe is on the same key as the "\" Look for a seperated straight line that goes down.

As for super-user, you can do one of two things:

sudo <argument>

Or, log in as a super-user (something I wouldn't do, just in case):

sudo su

to get out of it and back into regular user mode, type "exit"

Good luck!

---

### Post by finer recliner on 2007-04-16
use the word "sudo" (without quotes) before any command that requires super user priveledges. make sure you know what you're doing before you do this. this is a security from others and security from yourself accidentally screwing stuff up

the pipe character | is shift+foward slash (usually above the enter key)

---

### Post by SOULRiDER on 2007-04-16
Its important that you check out the guide on how to install Video drivers and not rusha nd try to do it yourself. 

Also, this guide: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) can help you udnerstand how installing/uninstalling software works in Linux as is it different than in windows (and certanly much easier)

---

### Post by Maestro23 on 2007-04-16
Some links to help:

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

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

How to Change Default OS: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Welcome to Ubuntu and Good luck.:D

---

### Post by HalOfBorg on 2007-04-16
OK, thanks for all the help.  I just could NOT find the damn button......

I am reading all the beginners stuff I can here, all looks helpful. And the nice thing is if I mess up the system....nobody but me cares. 20 minutes away from a fresh install.

The vid card is an ATI Radeon 9800 Pro

The PC is a Shuttle SB75G2 with FB75 mobo. P4, 1Gig RAM.

---

### Post by Nythain on 2007-04-16
> **Maestro23 said:**
> Some links to help:

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

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

How to Change Default OS: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Welcome to Ubuntu and Good luck.:D

Not sure if it is already or not but that comprehensive of a list, with the explanations beside them all in one location should definately be stickied in beginner talk... i've been runnin linux for a wee bit now and still found some of that information usefull, and to have it all in one spot so i dont have to weed through a near infinite amount of posts is wonderfull... i think im gonna email it to myself actually

---

