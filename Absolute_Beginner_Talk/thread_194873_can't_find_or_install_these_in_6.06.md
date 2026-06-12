---
title: "can't find or install these in 6.06"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-06-12
Hello all,

I have been trying to install or find certain things since upgrading, but have been rather unsuccessful.

Nautilus.  it is not in my system tools and can't seem to find it anywhere.  Need to access it.

MPlayer.  Was my DVD player of choice but when I go to add applications it tells me it is not available in any software channel, possibly due to my PC's architecture.  What?  It worked perfect before on 5.10.  I am no big fan of totem, so any help on this would be great.

Adobe Reader.  gives me the same problem as MPlayer.

---

### Post by Sef on 2006-06-12
> but when I go to add applications it tells me it is not available in any software channel, possibly due to my PC's architecture.

What architecture do you have?  (Likely it is not a problem since breezy worked on yours system.)

Have you changed any hardware lately?

---

### Post by Madpilot on 2006-06-12
[QUOTE=KarmaKing]Hello all,

I have been trying to install or find certain things since upgrading, but have been rather unsuccessful.

Nautilus.  it is not in my system tools and can't seem to find it anywhere.  Need to access it.
[/quote]

**Places->Home Folder** doesn't work?

> 
MPlayer.  Was my DVD player of choice but when I go to add applications it tells me it is not available in any software channel, possibly due to my PC's architecture.  What?  It worked perfect before on 5.10.  I am no big fan of totem, so any help on this would be great.

Adobe Reader.  gives me the same problem as MPlayer.

Mplayer is still in Multiverse, same as it was for 5.10, as is acroread - check your sources.list to make sure you've still got Multiverse enabled.

Which reminds me, I need to reinstall acroread myself...

---

### Post by KarmaKing on 2006-06-12
[QUOTE=Sef]What architecture do you have?  (Likely it is not a problem since breezy worked on yours system.)

Have you changed any hardware lately?[/QUOTE]

Hello Sef, MadPilot

No I haven't changed anything.  This install was flawless.

> Places->Home Folder doesn't work?
There is nothing there except the (hidden) naut folder containing the metta files.  I need the application launcher. I just don't see it.
I am fairly certain I have all the repositories checked, but I will check it again.

---

### Post by blackjack6.21.91 on 2006-06-12
Right click a panel, press add to panel, and find Main Menu.  Select it and click "Add to panel"

---

### Post by KarmaKing on 2006-06-12
[QUOTE=blackjack6.21.91]Right click a panel, press add to panel, and find Main Menu.  Select it and click "Add to panel"[/QUOTE]
I alread have the main menu, so I tried what you said but it is still not listed under Apps--system tools.

I checked the repositories and I seem to have all of them checked...am I missing something here.
The programs that I listed are not in synaptic.

---

### Post by Perfect Storm on 2006-06-12
Try setup your soucelist with this: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by richbarna on 2006-06-12
[QUOTE=KarmaKing]Hello all,

Nautilus.  it is not in my system tools and can't seem to find it anywhere.  Need to access it.

[/QUOTE]

In the Terminal type :-
> gksudo nautilus

Be careful if you change or delete anything as this is ROOT access.
If Nautilus doesn't appear, you have a wee problem.

---

### Post by KarmaKing on 2006-06-12
> karma@karma-desktop:~$ gksudo nautilus
(nautilus:14288): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


maybe a wee problem then.  This is what I got in terminal.

---

### Post by richbarna on 2006-06-12
[QUOTE=KarmaKing]maybe a wee problem then.  This is what I got in terminal.[/QUOTE]

I get this as well:- 
> XXXXX@XXXXXX:~$ gksudo nautilus
(nautilus:14412): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

But Nautilus still opens.
This is a silly question, but, you have got the GNOME desktop ? not KDE ?
Also maybe you can reinstall ubuntu-desktop.

---

### Post by brentroos on 2006-06-12
*

---

### Post by KarmaKing on 2006-06-13
thanks for all the replies, certainly my newbie karma is good.

I reinstalled with the alternate cd and everything is perfect now. Found all the programs I need and all are installed.

---

