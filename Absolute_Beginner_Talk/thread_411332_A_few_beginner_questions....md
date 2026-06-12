---
title: "A few beginner questions..."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by scottdizzle on 2007-04-16
Okay.. well I've just started using Ubuntu from a long lapse of linux. I used to use Redhat 7.2 and 7.3 and I was getting pretty good but now I feel like an idiot all over again..

First, I accidentally took my Recycle Bin off my taskbar thing. How can I put it back? Where does the Recycle Bin really exist? Like it's actual path?

Second, when I install programs.. where do they go? Like windows = c:\program files.. where are they on Linux?

I use XMMS and I don't know how to find it to add skins to my 'skins' directory.

Other than that it's been pretty smooth sailing.. although.. I wonder why 'Envy' isn't included in the Ubuntu installation considering it was the only thing that has made my graphics card drivers work properly thus far?

---

### Post by jfinkels on 2007-04-16
> **scottdizzle said:**
> Okay.. well I've just started using Ubuntu from a long lapse of linux. I used to use Redhat 7.2 and 7.3 and I was getting pretty good but now I feel like an idiot all over again..

First, I accidentally took my Recycle Bin off my taskbar thing. How can I put it back? Where does the Recycle Bin really exist? Like it's actual path?

right click on the panel, select "add to panel..."

I think the trash is on "/home/*yourusername*/.Trash"
> 
Second, when I install programs.. where do they go? Like windows = c:\program files.. where are they on Linux?


most of the time "/usr/bin/"

> 
I use XMMS and I don't know how to find it to add skins to my 'skins' directory.


Will get back to you.

> 
Other than that it's been pretty smooth sailing.. although.. I wonder why 'Envy' isn't included in the Ubuntu installation considering it was the only thing that has made my graphics card drivers work properly thus far?
I'm not sure. Maybe a restricted-drivers thing?

---

### Post by NeoLithium on 2007-04-16
Your xmms skins are in 

/home/USERNAME/.xmms/Skins

It's a hidden directory, so if you're using nautilus, type CTRL+H, which will show the hidden files, open it up and you can work normally, or just extract by command line into there with less trouble. :)

---

### Post by jfinkels on 2007-04-16
> **jfinkels said:**
> 
Will get back to you.


I think you have to put the skins in ```
/home/*yourusername*/.xmms/Skins/
```Note the dot! that's a hidden file so it has a period as its first character.

---

### Post by jfinkels on 2007-04-16
> **NeoLithium said:**
> Your xmms skins are in 

/home/USERNAME/.xmms/Skins

It's a hidden directory, so if you're using nautilus, type CTRL+H, which will show the hidden files, open it up and you can work normally, or just extract by command line into there with less trouble. :)

Darn you Neolithium! Darn you to heck!

Foiled again...

:D

---

### Post by gringogrande on 2007-04-16
Incase you install a package and you want to know what files it installed, you can check it with
```
dpkg -L <package>
```

---

### Post by scottdizzle on 2007-04-16
Wow! Blown away by the great response and response time here! You guys are great. Everything you said was exactly correct and I'm now feeling ten times more comfortable on Ubuntu.

Thanks much.

---

### Post by NeoLithium on 2007-04-16
No problemo :) Glad it's all working out.
EDIT:
Sorry jfinkels, maybe next time ;)

---

### Post by Maestro23 on 2007-04-16
More logs on the fire:

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

Welcome and Good luck with Ubuntu.:D

---

