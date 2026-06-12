---
title: "help with printer install"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2006-11-21
I am new to Kubuntu and linux in general and I am trying to install my printer. I have a hp psc 1210 and i found what I think should work for the drivers here ([http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)) but i have no idea how to do this part that comes up when I get the auto installation going it says to:

Before proceeding please enable the universe/multiverse repositories in Synaptic or Apt.  In addition disable the Ubuntu CD source

Would someone please walk me through this so I can get my printer installed. Keep in mind I am brand new to linux so I need baby steps.
Thanks in advance

---

### Post by turbojugend_gr on 2006-11-21
No need to install software m8, just go to wherever it says sth like "printers" in KDE, there add new printer nad choose psc1210 from the list, I have a PSC 1510 adn it works like a charm in Ubuntu.

Cheers, TJ.

---

### Post by ReaderRat on 2006-11-21
If you want to know about repositories,
[**[COLOR="RoyalBlue"]Add Extra Repositories[/COLOR]**](http://www.psychocats.net/ubuntu/sources)

---

### Post by rev_b on 2006-11-21
> **richiewrt said:**
> I am new to Kubuntu and linux in general and I am trying to install my printer. I have a hp psc 1210 and i found what I think should work for the drivers here ([http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)) but i have no idea how to do this part that comes up when I get the auto installation going it says to:

Before proceeding please enable the universe/multiverse repositories in Synaptic or Apt.  In addition disable the Ubuntu CD source

Would someone please walk me through this so I can get my printer installed. Keep in mind I am brand new to linux so I need baby steps.
Thanks in advance

Yes, no drivers download needed. I have a psc 1215, using 1210 drivers and the install was simple. Ubuntu was already using my scanner without a problem.

Go to System Settings -> Printers -> Add -> Add Printer/Class

The Add printer wizzard will start, select Local printer, next, it should have already detected your printer (it must be on, not like installing windows drivers that you only turn on the printer after installing the software), select HP psc 1200 series USB, and them select the driver: Manufacturer HP, Model PSC 1210. Just keep going accepting the default settings, and you will have your printer installed.

---

### Post by Ajd on 2006-11-21
As an aside, if you have problems with the gnome printer manager (I did which is why i'm mentioning it) you can go to [http://localhost:631/](http://localhost:631/) to work directly with the cups interface.

---

### Post by ramjet_1953 on 2006-11-22
HP does a pretty good job of making its printers work with Linux.
If you want to use the extra facilites of HPLIB, you will probably have to set up a ROOT password. I couldn't get to access any of the extra facilities without it. ie SUDO didn't work.
If someone knows of a workaround without a ROOT password, I'd appreciate it.

Roger 8)

---

### Post by richiewrt on 2006-11-22
Thanks for all the replies, but my problem was in kubuntu, there wasn't a driver listed for the psc 1210. i finnally got it downloaded and installed though by repeated trial and error after i figured out how to enable the repositories.

---

### Post by rev_b on 2006-11-22
> **richiewrt said:**
> Thanks for all the replies, but my problem was in kubuntu, there wasn't a driver listed for the psc 1210. i finnally got it downloaded and installed though by repeated trial and error after i figured out how to enable the repositories.

I was telling you how to install the PSC 1210 in Kubuntu... I installed from the Kubuntu CD but I ended up installing ubuntu-dektop packages and I like gnome more.

Again, you don't need to download any drivers or to add any repositories to get your PSC working. Kunbuntu has the drivers by default. Glad you fixed the problem, anyway.

---

