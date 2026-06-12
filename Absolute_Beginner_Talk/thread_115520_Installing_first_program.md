---
title: "Installing first program"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by naaythaay on 2006-01-10
Ok...bigtime newbie to ubuntu gnome.  Want to install my first application gnucash.  Managed to download to the desktop...now what do I do?  Tried synaptic.  Think I need to do something with the command line.  Don't have a clue how...please help and be descriptive.  Searched this site, but wasn't descriptive enuff...

Thanks.

---

### Post by aysiu on 2006-01-10
Synaptic is easier to use, but the command-line's easier to give instructions for (copy and paste).

First of all, the terminal: Applications > Accessories > Terminal.
This is where you type all the commands.

Secondly, enabling extra repositories (see the first link of my sig).

Lastly, installing Gnucash ```
sudo apt-get update
sudo apt-get install gnucash
```

System > Administration > Synaptic Package Manager is a prettier-looking graphical version of this last step.

P.S. You don't need whatever you downloaded to your desktop.

---

### Post by Sef on 2006-01-11
Easiest way to find a program in Synaptic is the click on the search button and type in the program's name.

---

### Post by blackbeastofaarrgh on 2006-01-11
If it's a .deb file you can just open a terminal, go to wherever you downloaded the file, and type:
sudo dpkg -i [insert name of your file here]

---

### Post by blackbeastofaarrgh on 2006-01-11
If it's a .deb file you can just open a terminal, go to wherever you downloaded the file, and type:
sudo dpkg -i [insert name of your file here]

(Sorry for the double post. Darn Internet)

---

### Post by aysiu on 2006-01-11
[QUOTE=blackbeastofaarrgh]If it's a .deb file you can just open a terminal, go to wherever you downloaded the file, and type:
sudo dpkg -i [insert name of your file here]

(Sorry for the double post. Darn Internet)[/QUOTE] Synaptic or apt-get is better, actually, because it resolves dependencies, and it's easier to upgrade the application when a newer version arrives.

Gnucash is in the Ubuntu repositories.

---

### Post by pieboy314 on 2006-01-11
ok...

I used System > Administration > Synaptic Package Manager

installed gnuchess, no erros but it does not appear under my Games menu, where might I find it and how do I run it?

sorry for the very newbish question

---

### Post by benplaut on 2006-01-12
[QUOTE=pieboy314]ok...

I used System > Administration > Synaptic Package Manager

installed gnuchess, no erros but it does not appear under my Games menu, where might I find it and how do I run it?

sorry for the very newbish question[/QUOTE]

(i don't use GNUchess, so this may not be correct)

Press Alt+F2, then in the box that pops up, type 'gnuchess' (without the ' '), and click 'Run'.

Good Luck!

**<EDIT>**

Read what Qrk says, below.

---

### Post by Qrk on 2006-01-12
gnuchess does not incude a GUI. It is only the chess program underneath.

To run it usably, use synaptic to get either "gnome-chess" or "knights"

Knights is a KDE program but it is very nice. You'll have to configure them to use gnuchess as the chess engine.

---

### Post by Autolycus on 2006-01-12
New Guy Here...

I downloaded, via the web, a program....BitTorrent 4.2.2

I opened Synaptic and did a search..

The program shows up in the left hand window...

Now what do I do with it?

---

### Post by Madpilot on 2006-01-12
There's a BitTorrent client included with Ubuntu already.

Applications menu --> Internet --> BitTorrent

Or just click on a .torrent link in your browser, it should launch the BT client automatically.

---

### Post by mcduck on 2006-01-12
[QUOTE=Autolycus]New Guy Here...

I downloaded, via the web, a program....BitTorrent 4.2.2

I opened Synaptic and did a search..

The program shows up in the left hand window...

Now what do I do with it?[/QUOTE]
When you use Synaptic/apt-get you don't have to download anything yourself. When you select something for install, Synaptic will download and install it for you.

If you can't find something with synaptic/apt-get, your best bet is to download a .deb file, and then install it by running 'sudo dpkg -i /path/to/program.deb' Synaptic won't help now, as it only lists things in Ubuntu's web repositories, and things already installed on your machine. It won't show any file downloaded to your desktop.

---

