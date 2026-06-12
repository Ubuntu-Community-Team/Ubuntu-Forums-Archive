---
title: "software install not on list"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by justinesalo on 2005-10-03
complete noob question: i downloaded limewire and have the installer on my desktop, only when i click it it doesn't launch the installer, just opens a folder of stuff.  i read a document on here about going to system>administration>synaptic package manager, only there's no limewire package there to easily install.  can someone tell me or point me to a page that explains how to install stuff in language a 2 year old could understand?

---

### Post by aysiu on 2005-10-03
These instructions may be outdated (we're in a bit of a transitional period, as Breezy's official release is coming up in less than two weeks), but you would follow these instructions:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

---

### Post by justinesalo on 2005-10-03
wow, thanks so much.  i feel smart now, even though i have no idea what i just did.  will i have to uncomment the stuff in the repositories section every time i want to install new software, or will it be permanently saved like that?

---

### Post by Qrk on 2005-10-03
Saved like that. Its nice, really.

---

### Post by aysiu on 2005-10-03
[QUOTE=justinesalo]wow, thanks so much.  i feel smart now, even though i have no idea what i just did.  will i have to uncomment the stuff in the repositories section every time i want to install new software, or will it be permanently saved like that?[/QUOTE] It will be permanently saved like that.

---

### Post by justinesalo on 2005-10-03
another question for anyone feeling helpful (thanks so much!)--i just tried installing adobe acrobat using the same instructions, only it didn't work.  it gave me this a bunch of times in the terminal:

Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

it's not installed.  any idea what went wrong?

---

### Post by Qrk on 2005-10-03
That site isn't used anymore. Delete the mirrormax lines from the sources list. (btw, acrobat isn't installed by default, but xpdf is) I'm not sure what repository would have  acrobat.

---

### Post by justinesalo on 2005-10-03
how do i delete the mirrormax lines from the sources list?  i'm trying to open pdf files, but there's no option to do it with xpdf--do you know how i'd do that?  sorry for all the questions.

---

### Post by aysiu on 2005-10-03
```
sudo nano /etc/apt/sources.list
``` Then put a # in front of the lines you want to delete. 

Control-X
Y
Enter

---

### Post by Qrk on 2005-10-03
go to the open with dialog... xpdf should be there.

---

### Post by justinesalo on 2005-10-03
i wouldn't be so annoying, only i actually need this tonight--for adobe, it seems to install fine in the terminal until the end, when it asks:

After unpacking 26.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

i hit yes and enter, but it aborts and when i killall gnome-panel and it's not there.  also, there's no xpdf when i go to open with.

---

