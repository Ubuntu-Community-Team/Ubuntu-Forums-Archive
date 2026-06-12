---
title: "Using Xubuntu OFFline"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Tedel on 2007-12-07
Hello, everybody,

Before installing Xubuntu, I have been trying the LiveCD for a couple of weeks. The installation did not run smoothly. I had to pause the process, use the Gnome Partition Editor to change my partitions myself, but at the end everything came out fine.

Now I have Windows XP and Xubuntu on my PC, and I am happy. For those who want to know, my computer is an IBM Pentium 3, with 256mb of RAM and a hard disk of 15gb. The partition for Xubuntu is 6gb large.

Now my situation. I use that computer offline only because it is there where I store my most important files and I will never risk it to a virus threat (while I was under Windows only, at least). **Now I need to download and install some applications to eventually replace Windows completely on that machine.** I was thinking about OpenOffice, GIMP, Inkscape, but additionally I need suggestions on which programs use to design websites (a text xHTML editor is enough) and to convert my mp3 files to OGG format.

But, besides that, I need to know which sort of programs (packages) can I download for Xubuntu. .deb? .tar.gz? .rpm? The list is huge and I am confused.

Thank you for your replies.

---

### Post by hyper_ch on 2007-12-07
Well, can't you go online for installing the stuff? It would be a lot easier that way.

Using Synaptic (Gui) or apt-get / aptitude (command line) the installation of that stuff is really simple - as you download that stuff from trusted sources, there's also no chance (well, a very slim one) that you can catch a virus.

As for HTML you can test Bluefish.

[as *buntu is Debian based you have to stick to either .deb files or source files]

---

### Post by g2g591 on 2007-12-07
.deb is best, you can go to [SIZE=-1]**packages**.**ubuntu**.com to download them (all those that are normally installable) just navigate to your windows folder where you saved them (under xubuntu) and, just double click to install (its going to be hard though, somethings depend on lots of other things to be downloaded).
[/SIZE]

---

### Post by Tedel on 2007-12-07
Will this happen again if I installed Ubuntu (Gnome), Kubuntu (KDE) or Fluxbuntu (Fluxbox)?
I'd really like to find an option to be able to use Linux Offline, so if this is not possible, then what about other distribution?

---

### Post by Bartender on 2007-12-07
Maybe someone else can help out on this - I'm thinking you could use an Ubuntu alt-install CD as a repository for OpenOffice and GIMP at least.  But I'm not sure how well this would work under Xubuntu's xfce DE.  
I think it would work, wouldn't it?  If you added the Ubuntu CD to the 3rd party source list, then asked Xubuntu to "Add" OpenOffice, wouldn't it simply grab the gnome stuff that it needed in order to add GIMP and OpenOffice?
That's assuming of course you have a way to download and burn an Ubuntu alt-install CD.  If so, you might want to download/burn a Kubuntu CD also so you could get K3B, digiKam, Amarok, etc.

There's also aptonCD, which I'm not familiar with but sounds useful.  That'd  only work if you have another Ubuntu PC that can go online.

---

### Post by maybeway36 on 2007-12-07
Yeah, using the CD as a repo should work just fine.

---

### Post by hyper_ch on 2007-12-07
I still don't see why you don't want to install it while being online? you can go offline afterwards...

---

### Post by Tedel on 2007-12-07
> **hyper_ch said:**
> I still don't see why you don't want to install it while being online? you can go offline afterwards...

Because, to do it, I would have to take my computer from my house to my office, in taxi and to move a lot of cables. =S

---

### Post by Duck2006 on 2007-12-07
In these forms i remeber seeing, a thread that had the thing your need, to do to get the repo's you need to install the things you want to a system without a internet connection but i for got what it was called. It worked out to 30Gb of stuff. Thats programs and repo's.

---

### Post by Duck2006 on 2007-12-07
This may help.

[http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line](http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line)

---

### Post by Tedel on 2007-12-07
OK, I'll take a look. :)

---

### Post by Tedel on 2007-12-24
Hello,

I think it was a better idea to "resurrect" this thread rather than start a new one.

I have been using Linux offline pretty well. I had Xubuntu installed, but it didn't came up with the software I wanted, so, I installed Ubuntu and then added XFCE desktop. I did the job.

What I wanted to ask now is this:

With Synaptic, I have the option of generating a script to download packages from another computer and that's great. But I still wanted to ask:

1. Is there any way to make that script a Windows executable file?
2. How can I update my Synaptic packages offline?

Thank you. =)

---

### Post by zvacet on 2007-12-24
You can use [this](http://www.nonetdebs.homeip.net/).For mp3 to ogg (and much more) try [this](http://viiron.googlepages.com/),because I think in Xubuntu you have Amarok and you can add that script to Amarok as plugin and you will have GUI for it.

---

### Post by cadcrazy on 2007-12-25
[This]("http://ubuntuforums.org/showthread.php?t=617049&highlight=offline") might also help you

---

### Post by ugm6hr on 2007-12-25
This is by far the best option for offline Linux updates / application installation I have seen:
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

