---
title: "5 Questions"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by DWRZ on 2007-01-31
Well, I've made the shift and for the most part it's fantastic. I'm stuck on a few things though and any help with these would be greatly appreciated!

1. When I installed Fedora Core 6 previously, AIGLX (wobbly windows, etc.) was working. I have tried enabling AIGLX on Ubuntu with no luck (using both radeon and fglrx drivers). I installed Beryl anyway and when I try to start it all the windows flash for a while and then it reverts to standard GNOME. I've also tried installing XGL and while GNOME runs all the toolbars are gray and none of the windows can be moved around.

2. I have a HP zd8000 with a Broadcom integrated card. I'm not sure exactly which card it is and I don't know how to find out. I'd like to install and use this card, but I've read several methods and I'm not sure which one is ideal. Can anyone recommend a method or FAQ?

3. I'd like the Ubuntu system as well as Evolution to display date in a custom way. Today in my way of dating is 2007.I.31 [05:3|031], time is: 17.49.34 (-0500). In other words: year.roman-numeral-month.day [week#:day-of-week#|day-of-year#]. I understand Roman numeral is complex but I was wondering if the rest can be done as in PHP. For example, more or less: 
%Y.%m.%d [%V|%j] for date
%H.%M.%S (%Z) for time

4. E-mail. I dual boot between XP and Ubuntu. I use Outlook 2003 in XP and Evolution in Ubuntu. Is there any way for me to keep e-mails between the two synchronized? Manual methods (exporting and re-importing) are fine too.

5. Can anyone recommend any software/applications? Stuff that I really ought to have on Ubuntu? Best games, best multimedia players, best FTP tools, etc.?

---

### Post by Shatrat on 2007-01-31
1. This is a beryl-free zone but you can find how-tos for beryl all over the place, these forums, help.ubuntu.com, doc.gwos.org, wiki.beryl-project.org, etc.
2. I got my wireless card working with the Broadcom how-to posted elsewhere on this forum. You can find your exact model with "lspci|grep bcm" I believe.


5. cowsay

---

### Post by sloggerkhan on 2007-01-31
there are loads of tutorials for getting graphics and beryl/compiz working, I think Ubuntu users might tend to use Beryl over compiz.  That all depends on your graphics card.
If your card worked on Fedora, I'm sure it should work on Ubuntu. Just a matter of knowing what to do.

Broadcom cards I'd say the method depends on the card. I have an 4318 Airforce one card and I use ndiswrapper + NetworkManager Applet. 

No idea about custom date display, I'm happy so long as it has date and time displayed, not just date. I think on xfce orange clock has or something like it has a really customizable date/time display, but I really don't know much about that question.

For email, I import stuff inbetween evolutions on occasion. I don't know about inboxes, but I think you can import an outlook contacts export.

Software apps for ubuntu (i'm including obvious stuff you probably have):
Open Office (+ abiword)
SuperTux
Planet Penguin Racer 
Eclips
Geany
NVU
Inkscape/Xara
Wings
Gimp
K3b
Xine
VLC
mplayer
all codecs you can find
GNUcash
If you like TI calculators: Genius Math
Battle for Wesnoth
Scribus
Blender
Evolution
GAIM
One of: Rhythbox, Banshee, or Amarok


I tend to use the connect to server thing under places as my client for sharing over most protocols. 

I'd try out Songbird and Democracy Player (latest versions probably not in repos.)

---

### Post by inCursorated on 2007-01-31
Hi...

> 
4. E-mail. I dual boot between XP and Ubuntu. I use Outlook 2003 in XP and Evolution in Ubuntu. Is there any way for me to keep e-mails between the two synchronized? Manual methods (exporting and re-importing) are fine too.
If you're serious about sticking with linux, consider purchasing crossover office and installing Outlook/Office 2003... i guess it's called [crossover linux ]("http://www.codeweavers.com/products/")now


> 5. Can anyone recommend any software/applications? Stuff that I really ought to have on Ubuntu? Best games, best multimedia players, best FTP tools, etc.?
check out [automatix]("http://www.getautomatix.com/"). it's an easy way to install a bunch of kewl stuff

---

### Post by K.Mandla on 2007-01-31
1. Beryl questions are best fielded on the [Beryl forums]("http://forum.beryl-project.org/"); Ubuntu works with Beryl, but they can probably best answer your questions there.

2. I used to have a zd7000; those 8000s always made me jealous. ... If you enter the command *lspci* in a terminal, you should get a make and model for the wireless card.

3. & 4. I'll leave to someone with more experience with e-mail clients.

5. [This]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") is more or less the "canonical list" of Windows-Linux equivalents. It's not as outdated as it might first appear. There's another thread around here somewhere that makes some other suggestions, but it's probably not anything you won't find on that page.

---

### Post by DWRZ on 2007-01-31
Wow! Didn't expect to get so many answers so quickly...

1. I've tried [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX). After setting Composite to Enabled and I try to restart, the restart only goes to a blinking underscore. After I turn off and restart the computer, I try to load GNOME but it fails, leaving me with orange desktop + mouse but nothing else. Any ideas? Hope it helps this isn't Beryl but just AIGLX?

Am I posting in the right forums? Or should I divide the questions and post each in a specific forum?

---

