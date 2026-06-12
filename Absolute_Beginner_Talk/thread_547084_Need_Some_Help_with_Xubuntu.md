---
title: "Need Some Help with Xubuntu"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-09
I have an old laptop that I wanted to get up and running with Linux but couldn't find
a distro that would run on it.  A forum user suggested Xbuntu 6.06 LTS
since it was an ealier version it may just run.

This worked and the LiveCD portion Ran Flawlessly !!!!!
Great Idea.

Well, I then installed it but a few things didn't turn out correctly

1. Xubuntu for some reason doesn't see my Linksys Wireless card
any longer. it worked great on the LiveCD.  All my DNS settings
carried over as well as everything else I setup. When I go into
Network, My Card isn't in the list. 

2. My desktop doesn't have my home folder and my computer
on it.  This worked fine on the LiveCD as well.

Any ideas..... Everything else seems great.  :KS

---

### Post by overdrank on 2007-09-09
> **Orbital75 said:**
> I have an old laptop that I wanted to get up and running with Linux but couldn't find
a distro that would run on it.  A forum user suggested Xbuntu 6.06 LTS
since it was an ealier version it may just run.

This worked and the LiveCD portion Ran Flawlessly !!!!!
Great Idea.

Well, I then installed it but a few things didn't turn out correctly

1. Xubuntu for some reason doesn't see my Linksys Wireless card
any longer. it worked great on the LiveCD.  All my DNS settings
carried over as well as everything else I setup. When I go into
Network, My Card isn't in the list. 

2. My desktop doesn't have my home folder and my computer
on it.  This worked fine on the LiveCD as well.

Any ideas..... Everything else seems great.  :KS
HI and I am no networking guru but is the card listed with the command lspci in the terminal? And have you check Xubuntu comes with a graphical networking utility. Launch it with Applications->System->Networking. I believe you home folder is placed on the upper task bar by applications.

And for future reference 
[https://help.ubuntu.com/xubuntu/desktopguide/C/index.html](https://help.ubuntu.com/xubuntu/desktopguide/C/index.html)

---

### Post by Orbital75 on 2007-09-09
I ran the lspci command as you suggest and it seems the Linksys Wireless Card isn't
listed. I also looked in the Network Utility in the GUI and its not in there either.
the card is an old 802.11 B card and it worked great with the LiveCD before I installed
it to the hard drive.  

When the System boots, I see that it checks PCMIA ( ok ) 
everything is ( ok ) durning boot.  My Wireless card lights
are even on as if it's working normally. 

What could have happed ?

---

### Post by Orbital75 on 2007-09-09
I ran the LiveCD again and chose to boot the CD instead of the HardDrive.
Picks up the Wireless Card fine.  Could the installation had just gone
bad?

---

### Post by Orbital75 on 2007-09-09
I tried reinstalling and the same thing happen.  

Any ideas how to solve this?

---

### Post by gn2 on 2007-09-09
> **Orbital75 said:**
> 

Any ideas how to solve this?

Try 7.04 instead or use the Wireless Utility in my sig which can be downloaded from here: [https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

---

### Post by Orbital75 on 2007-09-09
Well, This is a 1998 400mhz  laptop with 192 megs of ram.

This is the only Linux with a GUI that I have found that will make it
through the entire installation process. 

Even when I run " lspci " in the command prompt
it doesn't show up, it's like it not there.

or use the Wireless Utility in my sig.
What does this do?

Thanks

---

### Post by gn2 on 2007-09-09
> **Orbital75 said:**
> Well, This is a 1998 400mhz  laptop with 192 megs of ram.

This is the only Linux with a GUI that I have found that will make it
through the entire installation process. 

.
Tried Sam Linux, Puppy or Zenwalk?

---

### Post by gn2 on 2007-09-09
> **Orbital75 said:**
> 
or use the Wireless Utility in my sig.
What does this do?

It is a replacement network manager.

I'm running Xubuntu 7.04 on a 500mhz P3 with 192mb RAM.

Have you tried using the "Alternate CD" ?

---

### Post by Orbital75 on 2007-09-09
Yep, tried all of those.... even the Alternitive CD.
not sure what's going on, everything works in the
LiveCD, it's just after the install that the Card Disappears.

---

### Post by brennydoogles on 2007-09-09
Who makes the chipset of your card?? If it is made by broadcomm, you should check out [this thread]("http://ubuntuforums.org/showthread.php?t=405990").

---

### Post by nonewmsgs on 2007-09-09
i have a weird wireless issue in xfce too.  the weird thing is it works fine in gnome!  
everytime i select xfce after bootup i have to manually do the whole madwifi setup in terminal.

if i pick gnome and logout and then go into xfce im ok.

---

### Post by Orbital75 on 2007-09-09
It's a** Linksys WPC11** ver. 3

I think that it would be using the Prism and Prism2 drivers
but I am unsure.

Ubuntu 5.10 will work on it  including the Wifi  but it's sooooo slow with Gnome.
I've tried every other combination of distros and versions.
but Xubuntu 6.06 LTS  is the only distro/desktop that will run smoothly.
The only issue is my Card won't work .

---

### Post by gn2 on 2007-09-10
I had a similar problem before. Wireless card worked during Live session, but not installed.

Cure was to continually attempt the network set-up phase of the install process until it worked then continue the rest of the install process.

If I selected to set it up later because it failed during install, it would not work at all no matter what I tried.

---

### Post by Orbital75 on 2007-09-10
Just want to make sure I understand you..... Your saying to set it up completely as I did before
in the LiveCD and just keep trying to install the 30 minute install over and over and over
until it shows up? Also, This install doesn't take you through a Wireless Setup Phase, you have to do it
your self in the Network Gui while in the LiveCD. There has to be a better way then to install it 24 times and hope it
works.

Isn't there a way that I can manually install the card after the installation?


Just a though, in the LiveCD the PC is named ubuntu. 
During installation, it asked you your name and what
user name you would like to log in as well as a chance
to name the computer.  Could changing this name break
the card during the install?

---

### Post by brennydoogles on 2007-09-10
> **Orbital75 said:**
> Just want to make sure I understand you..... Your saying to set it up completely as I did before
in the LiveCD and just keep trying to install the 30 minute install over and over and over
until it shows up? Also, This install doesn't take you through a Wireless Setup Phase, you have to do it
your self in the Network Gui while in the LiveCD. There has to be a better way then to install it 24 times and hope it
works.

Isn't there a way that I can manually install the card after the installation?


Just a though, in the LiveCD the PC is named ubuntu. 
During installation, it asked you your name and what
user name you would like to log in as well as a chance
to name the computer.  Could changing this name break
the card during the install?

Maybe attempt using the Alternate CD. You can choose which step you want to do next there. Hope this helps!

---

### Post by Orbital75 on 2007-09-10
I've tried the Alternative Ubuntu 6.06 CD but never the Alternative Xubuntu CD.
The Alternative Ubuntu 6.06 CD wouldn't make it past install but that was the
full Ubuntu version.

What are the differences in the discs?
How can it help?

---

### Post by overdrank on 2007-09-10
> **Orbital75 said:**
> I've tried the Alternative Ubuntu 6.06 CD but never the Alternative Xubuntu CD.
The Alternative Ubuntu 6.06 CD wouldn't make it past install but that was the
full Ubuntu version.

What are the differences in the discs?

HI the xubuntu alternate cd is designed for low memory systems
[http://xubuntu.com/get](http://xubuntu.com/get)

---

### Post by gn2 on 2007-09-10
> **Orbital75 said:**
> Just want to make sure I understand you..... Your saying to set it up completely as I did before
in the LiveCD and just keep trying to install the 30 minute install over and over and over
until it shows up? 

No, during the installation to the hard drive there is part of the set-up where you configure the network. Continue doing this part till it works, then complete the rest of the installation.

Maybe this bit only happens with the "Alternate CD" I'm not sure, I only ever use that one.

---

### Post by Orbital75 on 2007-09-10
Good call guys !!! 

The Xubuntu Alternative CD worked like a charm.
The Network Section is different from the Standard CD.

Thanks everyone for your help, she's up and running.  :KS

---

### Post by overdrank on 2007-09-10
> **Orbital75 said:**
> Good call guys !!! 

The Xubuntu Alternative CD worked like a charm.
The Network Section is different from the Standard CD.

Thanks everyone for your help, she's up and running.  :KS

WOOO HOOO good luck! :popcorn:

---

### Post by jimrz on 2007-09-10
I have ubuntu 7.04 running nicely on an old thinkpad PIII 500 + 384 ram and am using the gnome desktop. yours should be able to handle Xubuntu 7.04 ok and you should get better wifi support. give a shot...probably would use the alternate install cd for this though.

---

### Post by gn2 on 2007-09-11
> **Orbital75 said:**
> Good call guys !!! 

The Xubuntu Alternative CD worked like a charm.
The Network Section is different from the Standard CD.

Thanks everyone for your help, she's up and running.  :KS

Result! :-)

The Alternate CD is definitely a better way to go.

---

