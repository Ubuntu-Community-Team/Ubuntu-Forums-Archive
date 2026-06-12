---
title: "Back to Basics"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Spook27 on 2007-08-25
After a couple months of being utterly unable to use my old laptop, I finally managed to replace the power cable and boot her back up again.  It's a pretty clunky beast nowdays (a Gateway Solo 1150) but it happens to be the first machine I actually installed Ubuntu (dapper) on and the one that dispelled the myths and FUD about doing so.  Apart from the usefulness of having a laptop on campus, there's a bit of nostalgia when it comes to keeping it running.

My intent was to do a nice clean reinstall of either Dapper or Feisty, since I managed to junk up my hard drive pretty badly.  Sadly, the CD-ROM drive seems utterly borked and won't read a disc let alone use it as a bootable medium.  What I would like to do is strip my desktop enviroments from the system and settle down with just Fluxbox.  Given that removing the existing DEs will probably take my login manager with them, I'm wondering if that means I'll be stuck with a command-line system where I'll have to invoke "startx" to get into flux.

Also of concern is the wireless situation.  My card (an Orinoco gold, hooray!) works flawlessly with dapper, so that's not a problem.  However, I have no clue how to connect to a WAP without the handy graphical tools provided in KDE and GNOME.  

So, to summarize...

[LIST]
[*]What's the best way to cleanly remove GNOME and KDE, and what will I be left with?
[*]How do I connect to wireless LANs from a bash prompt?
[*]Will I be able to go from my prompt to Fluxbox easily?
[/LIST]

Thanks for your time,
-Spook27

---

### Post by aysiu on 2007-08-25
I think your best bet is to remove a little a time.

Keep Gnome installed. Then install Fluxbox and use it instead of Gnome. Then, use Synaptic to one by one remove what you think might be extraneous packages. Every time you mark one to be removed, Synaptic will warn you about what *other* packages will also be removed so keep an eye out for things you think you might need (*network-manager* and *gdm* are essentials).

---

