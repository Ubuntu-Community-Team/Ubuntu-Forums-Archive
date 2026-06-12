---
title: "Help Not typical Windowz user!!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by hulland on 2007-03-28
Installed Ubuntu into a new volume on my P4( 2gig RAM 3 Hdrives)--am largely disappointed by the "clicking" one needs to do to get anywhere or anything to start!! ( Am spoilt!!)

--I NEVER EVER use the Windows desktop

--hate the mouse --- 

I tweaked 95/98/ME/XP--now have hot keys for 99% even DVD authoring

--( XP ProCorp boots from cold to working in 12 secs)

--My problem is--I want Ubuntu to be = fast, but I fully realize I am not a typical Windows "sheep"--but a tweaker. 

Is there any EASY way I can speed up Ubuntu to be instantly usable in the same way that I speed through operations in XP Pro ?

--OR should I forget Ubuntu as it is designed to be friendly to TYPICAL Windows users?--Is there a quick work-through or add-on pack to get rid of the more "Windows" things?
Any answer appreciated!!

---

### Post by mahy on 2007-03-28
If you're into speed and up for some serious tweaking, then you can try Gentoo or Arch Linux instead.

---

### Post by Magnes on 2007-03-28
Install xbindkeys - then you can define hot keys for everything - or just use terminal to run applications, edit configurations files instead of "clicking" in the preferences dialogs.
To speed up booting turn off not used autostarting deamons by BUM (there are several howtos on the net, also in feisty it should be easier to speed up the boot than on edgy). Learn key shortcuts in applications you use.

---

### Post by hyper_ch on 2007-03-28
or you can write shell scripts and bind them to hot keys :)

---

### Post by adriantry on 2007-03-28
> **hulland said:**
> Installed Ubuntu into a new volume on my P4( 2gig RAM 3 Hdrives)--am largely disappointed by the "clicking" one needs to do to get anywhere or anything to start!! ( Am spoilt!!)
--I NEVER EVER use the Windows desktop
--hate the mouse --- 
I tweaked 95/98/ME/XP--now have hot keys for 99% even DVD authoring
--My problem is--I want Ubuntu to be = fast, but I fully realize I am not a typical Windows "sheep"--but a tweaker. 


I think you're going to love Linux! You have a lot of options, so take you're time and get to know the broad landscape!

Unlike Windows, Linux gives you a choice of many "Window Managers", or graphical user interfaces. By default, Ubuntu uses Gnome (and Kubuntu uses KDE). You may be interested in a window manager called Fluxbox. It is very light, doesn't use the desktop, and uses keyboard shortcuts (key bindings). Check it out at
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

If you're interested in trying it, you can install it using one of Ubuntu's package managers. If you haven't learnt how to install software from the repositories yet, please ask.

You might also want to explore other window managers like XFCE, Openbox, and ICEWm. Like I said, take you're time and learn your options. You don't have to use Linux the way it comes!

Adrian

---

### Post by seshomaru samma on 2007-03-28
fluxbox is nice 
i prefer icewm 
both icewm and fluxbox do not let you create desktop icons , but of course they can be tweaked to
a nice way of doing it is running icewm with rox - see [here]("http://ubuntuforums.org/showthread.php?t=171203&highlight=icewm")

---

### Post by hulland on 2007-03-31
Thanks for all those pearls of wisdom. What I actually find a strange conflict is;- everyone here is SO helpful and leans over backwards to quote lines of code at the drop of a hat, yet ( to me an absolute mental retard!) am surprised that there is no single easy to follow "get you started guide" for Ubuntu--all the help files that come installed assume you are already a software engineer ! ( e.g I have tried 4 times to mount some of my Windows NTSF volumes in Ubuntu and have about 15 pages printed out--still no sign of them!) Sooo  where is the "10 page guide to the new user?" I think there is a need..

---

### Post by GSF1200S on 2007-03-31
> **hulland said:**
> Thanks for all those pearls of wisdom. What I actually find a strange conflict is;- everyone here is SO helpful and leans over backwards to quote lines of code at the drop of a hat, yet ( to me an absolute mental retard!) am surprised that there is no single easy to follow "get you started guide" for Ubuntu--all the help files that come installed assume you are already a software engineer ! ( e.g I have tried 4 times to mount some of my Windows NTSF volumes in Ubuntu and have about 15 pages printed out--still no sign of them!) Sooo  where is the "10 page guide to the new user?" I think there is a need..

This isnt windows. It doesnt have the COMMERCIAL SOFTWARE SUPPORT that windows does. This is why the terminal window is used so frequently...

The reason everyone is dropping code is because its the most efficient. Ubuntu gives you a GUI to let you view things graphically and gives you a shortcut straight to the kernel with the terminal window.

Think about it- who designs applications for Linux? People like you and me who happen to know enough to program and find a need for a certain application. Rather than spending countless hours or DAYS designing a graphical installers like commercial software companys do for windows, they simply write the program and give you the codes to install the program... Why waste the time required for an installer youll only see once? The program is all that anyone cares about.

Ive been using Ubuntu for a little over a week. With a little curiosity and a little patience, Ive nearly mastered the basics. I still make mistakes, and I still scratch my head (.tar.gz installs for example), but Ive basically got it.

Thats why man.. those codes believe it or not make life alot easier. The more you use them, the more you understand them- and once they fall into an organized puzzle in your mind, it becomes 10 times easier.

---

### Post by GSF1200S on 2007-03-31
> **hulland said:**
> Thanks for all those pearls of wisdom. What I actually find a strange conflict is;- everyone here is SO helpful and leans over backwards to quote lines of code at the drop of a hat, yet ( to me an absolute mental retard!) am surprised that there is no single easy to follow "get you started guide" for Ubuntu--all the help files that come installed assume you are already a software engineer ! ( e.g I have tried 4 times to mount some of my Windows NTSF volumes in Ubuntu and have about 15 pages printed out--still no sign of them!) Sooo  where is the "10 page guide to the new user?" I think there is a need..

Oh, and just post a topic on the problems youre having mounting yoour NTFS partition and I bet youll have it up in 1 day (this includes the waiting for replies).

---

### Post by Maestro23 on 2007-03-31
Some links to introduce you to Ubuntu:

How to install software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lot of other good stuff here as well)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Terminal Commands:
[https://help.ubuntu.com/community/CommandlineHowto?highlight=%28commandline%29](https://help.ubuntu.com/community/CommandlineHowto?highlight=%28commandline%29)
[https://help.ubuntu.com/community/AdvancedCommandlineHowto?highlight=%28commandline%29](https://help.ubuntu.com/community/AdvancedCommandlineHowto?highlight=%28commandline%29)

Welcome and Good luck.

---

### Post by GSF1200S on 2007-03-31
> **Maestro23 said:**
> Some links to introduce you to Ubuntu:

How to install software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lot of other good stuff here as well)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Terminal Commands:
[https://help.ubuntu.com/community/CommandlineHowto?highlight=%28commandline%29](https://help.ubuntu.com/community/CommandlineHowto?highlight=%28commandline%29)
[https://help.ubuntu.com/community/AdvancedCommandlineHowto?highlight=%28commandline%29](https://help.ubuntu.com/community/AdvancedCommandlineHowto?highlight=%28commandline%29)

Welcome and Good luck.

Holy crap dude!! Where were you when I started!?! I already know a bit about Ubuntu, and these links will help me volumes... Thanks!!

---

### Post by hyper_ch on 2007-03-31
Command line make a lot of things easier.... just about 10min ago a friend asked me what Music Files I have...

There are a couple of ways to achieve that... I could open the disk and make screenshots (that's what I used to do on windows)... I could setup a server and let them browse... I could setup vnc and give them access... or I could use the CLI...

I opened a terminal, went to the right location

```

cd ~/Music

```

Entered a command to recursively list all files and output them to a text file

```

ls -alR * > output.txt

```

Waited a few seconds for that to finish and then I sent the output.txt by aMSN to my buddy...

I think this was the quickest approach...

ls --> List file/folder
-a --> all files (also hidden ones which start with a dot)
-l --> make full listing (owner ship, permissions, size, file)
-R --> Recursive (go into subdirectories and do the same)
( -a / -l / -R are switches, you can just maked it -alR :) )
> --> save the output (that you normally would have on screen) to the file on the right of ">" in my case the output.txt

---

### Post by cowlip on 2007-03-31
[Your friendly linux command line tutorial]("http://www.linux.org/lessons/beginner/toc.html")

You're very rare in this forum indeed, you may just love the command line ;)

For bootup, Edgy includes the init replacement 'upstart' but the scripts weren't fully optimized.  Feisty Fawn's release will let you download fully optimized scripts for upstart which will make bootup really fast.

---

### Post by RedSquirrel on 2007-03-31
> **hulland said:**
> Installed Ubuntu into a new volume on my P4( 2gig RAM 3 Hdrives)--am largely disappointed by the "clicking" one needs to do to get anywhere or anything to start!! ( Am spoilt!!)

--I NEVER EVER use the Windows desktop

--hate the mouse --- 

I tweaked 95/98/ME/XP--now have hot keys for 99% even DVD authoring

--( XP ProCorp boots from cold to working in 12 secs)

--My problem is--I want Ubuntu to be = fast, but I fully realize I am not a typical Windows "sheep"--but a tweaker. 

Is there any EASY way I can speed up Ubuntu to be instantly usable in the same way that I speed through operations in XP Pro ?

--OR should I forget Ubuntu as it is designed to be friendly to TYPICAL Windows users?--Is there a quick work-through or add-on pack to get rid of the more "Windows" things?
Any answer appreciated!!

As others have suggested, you can try different window managers.

I don't use the mouse much either. Like you, I prefer to use the keyboard as much as possible. Fluxbox is great for this.

If you decide to give Fluxbox a try, some of the links in my sig might help. For shortcut keys, I have included my Fluxbox *keys* configuration file in the HOWTO (first link in sig).

Have fun! :)

---

### Post by jvc26 on 2007-03-31
On mounting your ntfs drives I'd check out the ntfs-3g stuff:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto)
Il

---

### Post by Maestro23 on 2007-03-31
> **GSF1200S said:**
> Holy crap dude!! Where were you when I started!?! I already know a bit about Ubuntu, and these links will help me volumes... Thanks!!

ROFL.. Better late than never.  Glad to help man.  Good luck.:guitar:

---

