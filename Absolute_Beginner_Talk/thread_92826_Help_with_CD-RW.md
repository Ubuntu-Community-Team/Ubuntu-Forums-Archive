---
title: "Help with CD-RW"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by SumoJim on 2005-11-20
I am having trouble with writing CD's. When I insert a blank CD an empty window pops up. I click and drag a file into that window and select "_W_rite to Disc...".
It then gives me the message:
"Please put a blank disc, with at least 1 MiB free, into the drive."

I double checked the disc was blank and grabben a fresh one from the stack, tried again and got the same message. The discs should hold 700 MB of data.

It works fine to read discs however. I was able to copy files from other discs that had information on them with no problem and my Operating system (Hoary Hedgehog) Seems to recognise that the drive is indeed a CD-RW drive.

Can anyone help me to get my CD-RW to work properly?

---

### Post by nevelis on 2005-11-20
Hey dude

The best program I've used is K3B, it's KDE but it works.  An alternative is nerolinux, do a search for it.

To install K3B:
```
apt-get install k3b
```

Might take a while if you dont have qt and kde libs installed, hope you've got a fast connection!

Cheers,
Aaron

---

### Post by SumoJim on 2005-11-21
Ok, I typed that into my command line and I saw all kinds of neat lines saying it was installing stuff. Now what? Is there another program on my computer somewhere? I am a complete newbie to Linux and I don't even know what apt-get is exactly.

---

### Post by LHZ on 2005-11-22
Type 
> k3b
into a terminal to start the program.

If you're lucky, it'll also show up somewhere in the menus, but since K3b is a KDE application Gnome may not be able to find it. Otherwise, you'll have to edit your menu with SMEG (search the site, there's plenty of tutorials), or just run it from the command line.

*edit:* apt-get is like a universal installer: it grabs the software you want, checks whether it's complete and then installs it. There's a graphical frontend to it called Synaptic, which has beautiful search functions and stuff, under System->Administration->Synaptic.

---

### Post by SumoJim on 2005-11-24
Does anyone have a solution for the CD-copier that comes with Ubuntu? Or if not the standard one at then mabey least a good GNOME compadable solution?

---

### Post by sjh on 2005-11-24
[QUOTE=SumoJim]Does anyone have a solution for the CD-copier that comes with Ubuntu? Or if not the standard one at then mabey least a good GNOME compadable solution?[/QUOTE]

Nautilus uses cdrecord as it's burn engine.  By default only root can access it.
You can edit the file /etc/default/rscsi to allow your user to access the burner.

```
sudo cp /etc/default/rscsi /etc/default/rscsi.bak
sudo gedit /etc/default/rscsi
```

The file is all commented out and explains the problem.  Just add the line

   USER=YourUserName

to the file and the burner should start to work, at least it did for me.

Also Gnome-Baker is a good Gnome based application.

SJH

---

### Post by SumoJim on 2005-11-29
Ok, I typed:
"sudo cp /etc/default/rscsi /etc/default/rscsi.bak
sudo gedit /etc/default/rscsi"

into the command line and entered:
USER=sumojim
At the bottom of the file but still same result.

I've devided to attempt to use Gnome-Baker but don't know how to get it. I've figured out that apt-get is pretty much required and cant be installed just anywhere easily like in Windows.

Where can I find a list of things that I can use "apt-get" for anyway?
And how do I delete them if I later decide I don't want them?
And lastly what exactly do I type in the command line for gnome-baker?

"sudo apt-get gnome-baker" ???

---

### Post by SickTwist on 2005-11-29
Instead of using apt-get, you may wish to try Synaptic to install or remove programs. It has a graphical interface that allows you to browse all of the programs that are available to install. It also makes it easy to see what is currently installed.

System --> Administration --> Synaptic Package Manager


As for your original question, it sounds like GNOME is having trouble recognizing that the discs are rewriteable. Unfortunately, I am not sure what the solution is. I tried using CD-RW discs in the past but I had a lot of trouble with them (they quit working right after only a few burns and some Linux distros would not boot correctly from them).

---

