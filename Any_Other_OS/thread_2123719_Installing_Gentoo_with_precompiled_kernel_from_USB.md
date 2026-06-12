---
title: "Installing Gentoo with precompiled kernel from USB disk"
date: 2013-03-08
forum: Any Other OS
---

### Post by janck on 2013-03-08
[COLOR=#000000][FONT=Verdana]Hello! [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I'm new with Gentoo and I got a pretty interesting task to do. Before I start with question, I must tell you that I installed Gentoo once for now, and this installation was successfull - without any problems [/FONT][/COLOR][IMG]http://forums.gentoo.org/images/smiles/icon_smile.gif[/IMG][COLOR=#000000][FONT=Verdana] I'm using Linux a few years, but I didn't meet rolling releases before, so that's my first rolling release distribution. I have also some experience with basic Linux commands, so there isn't problems with this because I understand mostly all of them. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]**What's my job that I have to do?**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]First of all I need to install Gentoo on some computer with LiveCD - partitioning, chrooting and other stuff. But during the install instead of compiling the kernel, I need to use kernel which I will get on USB disk and I need to import it into the system. I actually don't know how to do that and what this depends on - modules and what else? Also I don't know how to mount USB disk and what do I have to do after I finish this job - do I need to unmount it and when? [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]**How to export already compiled kernel?**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]As I mentioned, I already installed Gentoo with compiling kernel, so I would like to copy files which are connected with importing the kernel, to USB disk. Why I need them on USB disk? Because I have to practice importing of kernel on my system so after all I could do that without mistakes. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]That's it for now [/FONT][/COLOR][IMG]http://forums.gentoo.org/images/smiles/icon_wink.gif[/IMG][COLOR=#000000][FONT=Verdana] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thanks to all of you![/FONT][/COLOR]

---

### Post by prodigy_ on 2013-03-08
Using something "precompiled" with Gentoo is so wrong it makes Tux cry. :)

Seriously though, what you need to do is mount the USB stick, copy the kernel to /boot, install (emerge) bootloader and try to boot.

[http://wiki.gentoo.org/wiki/GRUB2](http://wiki.gentoo.org/wiki/GRUB2)
[http://wiki.gentoo.org/wiki/GRUB2_Quick_Start](http://wiki.gentoo.org/wiki/GRUB2_Quick_Start)

---

### Post by MadmanRB on 2013-03-09
If new to Gentoo you may want to try Sabayon.
Its a good way to learn its layout and quirks (and overall I like sabayon, I almost used it full time if it not for me needing more space because of all the packages I needed to compile with it using portage)

---

### Post by janck on 2013-03-09
> **MadmanRB said:**
> If new to Gentoo you may want to try Sabayon.
Its a good way to learn its layout and quirks (and overall I like sabayon, I almost used it full time if it not for me needing more space because of all the packages I needed to compile with it using portage)
[COLOR=#000000][FONT=Verdana]
Actually I got this task for homework because sometime in the future we will have examination about Linux, but computers in school are not fast enough. So instead of compiling we'll get precompiled kernel made for these computers and there will be also limited time to finish all tasks. I have no choice of which distribution I'll take, because we can only work with Gentoo. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]In which folder(s) next to /boot do I need to copy kernel files and how to "register" them to the system that it will recognize it? [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Because I need to practice this - which files do I need to copy on USB disk, so that they I can use next time? [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]What about mounting and unmounting USB disk - how can I check if the disk is plugged in and how to mount and unmount it during installation?[/FONT][/COLOR]

---

### Post by oldos2er on 2013-03-09
Gentoo forums are here: [http://forums.gentoo.org/](http://forums.gentoo.org/)

From the Code of Conduct: While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.

Closed.

---

