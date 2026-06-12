---
title: "Can't get into ubuntu desktop"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by The Pathologist on 2007-06-10
I have been eager to try the LINUX OS and heard alot about the ubuntu.. So I did downloaded ubuntu server edition from:
```
 http://www.ubuntu.com/getubuntu/download
```

I installed it on my PC (with windows XP professional edition) and I THINK I had no installing problems>> rebooted and then this appeared:
[IMG]http://i12.tinypic.com/5ytxanl.jpg[/IMG]


After supplying the user name and password (the cursor blinks butdoesnt move with the  password), I see this:

mada@ubuntomada:~$: 


and whatever I make, I can't go into the desktop :???:

my desktop spec. :
CPU: P4, 2.4
RAM: 512 MB
VGA; Geforce FX 5200 (128MB)
HDD: WD (80GB)

btw, the XP works like charm after ubuntu installation

---

### Post by mudguts on 2007-06-10
I think that the command is:
'xstart' then enter

---

### Post by The Pathologist on 2007-06-10
NOPE
```
-bash : xstart: command not found
```

---

### Post by Outrunner on 2007-06-10
> **mudguts said:**
> I think that the command is:
'xstart' then enter

That would be
```

startx
```

and it won't work because the server edition doesn't have(and isn't supposed to have) a GUI.

If you want gnome
```

sudo aptitude install ubuntu-desktop
```

for kde

```
sudo aptitude install kubuntu-desktop
```

and finally for xfce

```
sudo aptitude install xubuntu-desktop
```

---

### Post by The Pathologist on 2007-06-10
```
bla, bla, bla
couldn't find any package whose name or description matched "ubuntu-desktop"
No packages will be installed, upgraded or removed
bla, bla,  bla
mada@ubuntomada:~$:
```

**Did I downloaded a WRONG version??**

---

### Post by Outrunner on 2007-06-10
> **The Pathologist said:**
> ```
bla, bla, bla
couldn't find any package whose name or description matched "ubuntu-desktop"
No packages will be installed, upgraded or removed
bla, bla,  bla
mada@ubuntomada:~$:
```

**Did I downloaded a WRONG version??**

Umm, are you connected to the internet?

```
ping -c 3 bbc.co.uk
```

to see if you can ping bbc.co.uk 3 times.

EDIT: And unless you want to run a server, then yes, I would say you downloaded the wrong version(unless you have a special reason to use a barebones install?)

---

### Post by The Pathologist on 2007-06-10
I am connected to the internet through my Laptop (ubuntu is on desktop)

OK I may download the desktop version but how can I:

1) remove the server version installation?
2) guarantee that it will work?

Thanks for help :)

---

### Post by Outrunner on 2007-06-10
> **The Pathologist said:**
> I am connected to the internet through my Laptop (ubuntu is on desktop)

OK I may download the desktop version but how can I:

1) remove the server version installation?
2) guarantee that it will work?

Thanks for help :)

It doesn't matter if your laptop is connected, it matters if your ubuntu computer is... Anyway, you can install over your current Ubuntu installation, it will be reformatted automatically. And I can't guarantee that it will work, just browse around when you boot the LiveCD to see if it works/

---

### Post by The Pathologist on 2007-06-10
So I have no hope to pass into the desktop currently ?

---

### Post by Outrunner on 2007-06-10
> **The Pathologist said:**
> So I have no hope to pass into the desktop currently ?

Did you check if you're connected?

---

### Post by The Pathologist on 2007-06-10
I am not connected through the desktop

---

### Post by Outrunner on 2007-06-10
I really think the easiest thing to do is download and burn a LiveCD and go on from there...

---

### Post by The Pathologist on 2007-06-10
> **Outrunner said:**
> I really think the easiest thing to do is download and burn a LiveCD and go on from there...

Can you supply me a link?

---

### Post by Zootropo on 2007-06-10
For example
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fcarroll.cac.psu.edu%2Fpub%2Flinux%2Fdistributions%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fcarroll.cac.psu.edu%2Fpub%2Flinux%2Fdistributions%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=)

---

### Post by The Pathologist on 2007-06-10
> **Zootropo said:**
> For example
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fcarroll.cac.psu.edu%2Fpub%2Flinux%2Fdistributions%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fcarroll.cac.psu.edu%2Fpub%2Flinux%2Fdistributions%2Fubuntu-releases%2F&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=)

Thanks for this :)

---

### Post by The Pathologist on 2007-06-10
Sorry for this guys, but how can you say that Ubuntu is easy to use :???:


I wanted nothing but getting into the desktop screenie and 3 respected members tried to help but Nothing

---

### Post by Outrunner on 2007-06-10
> **The Pathologist said:**
> Sorry for this guys, but how can you say that Ubuntu is easy to use :???:


I wanted nothing but getting into the desktop screenie and 3 respected members tried to help but Nothing

Well considering the fact that you installed the Server Edition, it would have been pretty hard to start up the GUI without one installed.

---

### Post by The Pathologist on 2007-06-10
> **Outrunner said:**
> Well considering the fact that you installed the Server Edition, it would have been pretty hard to start up the GUI without one installed.

as this is my first time to think about trying linux OS, I couldn't know this and I think a remark beside the "download" button may be useful :-k
The download page offered very ittle info IMO

---

### Post by Outrunner on 2007-06-10
If you look at [this]("http://www.ubuntu.com/getubuntu/download") page you will see that it is detailed enough.

---

### Post by The Pathologist on 2007-06-10
> **Outrunner said:**
> If you look at [this]("http://www.ubuntu.com/getubuntu/download") page you will see that it is detailed enough.

this is the page I downloaded from, sorry mate can't find anything about my problem or a pre-installed GUI :confused:

---

### Post by martinrandau on 2007-06-10
Should you just have downloaded the ubuntu desktop version instead of the server you would have GUI right now. This have nothing to do with ubuntu not being easy to use, it's just about not knowing what you are downloading! :p

---

### Post by Outrunner on 2007-06-10
> **The Pathologist said:**
> this is the page I downloaded from, sorry mate can't find anything about my problem or a pre-installed GUI :confused:

Is it supposed to? Why did you download the Server Edition anyway, did you want to run a server? If not, wouldn't the Desktop Edition(LiveCD) have been the obvious choice.You can't have everything handed to you on a silver platter, you have to think for yourself as well.

---

### Post by The Pathologist on 2007-06-10
O Rly?!!

---

### Post by The Pathologist on 2007-06-10
I gonna buld my server soon.. It was my fault I shouldn't jump to this Thanks guys

---

### Post by Outrunner on 2007-06-10
Well, good luck to you... I have to be honest, I think you'll need it.

---

### Post by The Pathologist on 2007-06-10
SO can anyone tell me how to get rid of the dual boot menu and the installed ubuntu .. I just want my system back till theubuntu live cd download is complete

---

### Post by deeteesbeard on 2007-06-10
I wouldn't try and get rid of the dual boot menu, just select windows from the list when you boot up. That should boot you into windows (I can see from your first post that windows still works).

I would make sure you have backups of everything on your windows system that you want to keep. I don't mean to sound patronising, and I'm by no means an expert myself, but you do seem to be rushing headlong into this without having done much research first - and in my experience that often has disastrous consequences.

---

### Post by The Pathologist on 2007-06-10
every single important data on my desktop is backed up into DVDs.. I just dont want to install the desktop version over the previous server edition :|

---

### Post by Lakefall on 2007-06-10
> **The Pathologist said:**
> I just dont want to install the desktop version over the previous server edition :|
I don't think thats going to be a problem. The installation probably wipes the partition clean and the desktop and the server are fundamentally the same thing anyhow. The server just doesn't have a graphical user interface on the installation CD and probably has some other things not on the desktop installation CD. However, if the computer you installed on had an Internet access, the both versions would by default share the same software repository on the internet. As somebody already tried to point out, if you had the internet access, you could download and install the graphical desktop into the server simply by typing: ```
sudo aptitude install ubuntu-desktop
```

Unlike the desktop version (at least tries to be), the server version is not designed to be easy to learn for new users. As far as I know it's designed for experienced system adminstrators, who already know Linux well and know what and how they are going to do with the server.

It's true this isn't explained on this page:
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)
Maybe it should be.

However you should have also seen a page like this:
[http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/7.04/](http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/7.04/)
It at least clearly says about the server: "It will not install a graphical user interface." It also says about the desktop: "This type of CD is what most people will want to use."

It's silly to say Ubuntu is hard to use, because you accidentally downloaded a wrong version. You may whine that the Ubuntu web pages are misleading, but that has nothing to do with the usability of the operating system.

---

### Post by hasubu on 2007-06-10
> **Outrunner said:**
> That would be
```

startx
```

and it won't work because the server edition doesn't have(and isn't supposed to have) a GUI.

If you want gnome
```

sudo aptitude install ubuntu-desktop
```

for kde

```
sudo aptitude install kubuntu-desktop
```

and finally for xfce

```
sudo aptitude install xubuntu-desktop
```
So.....  what can I do with the Server if it does not have a GUI....?  I am not not a guru at CLI!!  the desktop version if fine, but you mean I cannot use the Server like the Desktop version, in a GUI mode?
that would be disappointing..

---

### Post by hasubu on 2007-06-10
Ok, i installed the Server version on a PC and the desktop version on my laptop.  both networked DHCP.  How can I benefit from this? 

thanks,

hasubu

---

### Post by Lakefall on 2007-06-10
> **hasubu said:**
> So.....  what can I do with the Server if it does not have a GUI....?  I am not not a guru at CLI!!  the desktop version if fine, but you mean I cannot use the Server like the Desktop version, in a GUI mode?
that would be disappointing..
If you have Internet access, both the desktop and the server share the same package repositories (AFAIK). That means you can install all the software that is installed by the server CD into a desktop install and also can install all the software that is installed by the desktop CD into a server install. Basically you can turn a desktop install into a server install or a server install into a desktop install by adding and removing packages. Just use synaptic or aptitude.

Basically the CD:s are just different starting points.

If you do not have Internet access, the situation is worse. In my opinion Ubuntu pretty much requires access to the Internet.

> **hasubu said:**
> Ok, i installed the Server version on a PC and the desktop version on my laptop.  both networked DHCP.  How can I benefit from this?
I don't know. What do you want to do?

---

### Post by The Pathologist on 2007-06-11
Thanks for the explanation Lakefall.. Hope the desktop edition will be more joyfull experience :)

---

### Post by fasty on 2007-06-11
> **Outrunner said:**
> If you want gnome
```

sudo aptitude install ubuntu-desktop
```

for kde

```
sudo aptitude install kubuntu-desktop
```

and finally for xfce

```
sudo aptitude install xubuntu-desktop
```

Thank you, Outrunner. Found this response in a search of the forums, and it's exactly what I needed.

---

