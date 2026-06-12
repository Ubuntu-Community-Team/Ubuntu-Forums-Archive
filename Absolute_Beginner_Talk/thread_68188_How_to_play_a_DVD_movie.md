---
title: "How to play a DVD movie?"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by sneax on 2005-09-22
Hello, I want to play a DVD movie. I installed mplayers, xine, videolan and whatnot from synaptic but in all those applications I can not play a DVD movie. I can play all movie formats but a DVD movie from a DVD disc doesn't work. I also installed libdvdcss2 as instructed by the ubuntu wiki. I have also tryed regionset but the region is correct (region 2 for europe, the dvd is region 2).

Basicaly, on my DVD there's a file named 'VIDEO_TS" those media players can't handle 'the format'.

What do I have to do to play DVD's in this format? I have no clue at what to try. All media players tell me the same problem. Just simple movie files like .avi (divx or xvid), mpeg, wmv etc... they all work.

---

### Post by aysiu on 2005-09-22
[QUOTE=sneax]All media players tell me the same problem.[/QUOTE] What problem do they all tell you? Is there an error message?

---

### Post by gez on 2005-09-22
try [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 
although I can't seem to get the link to work at the moment which is probably the horrid connection in my office.

But if it works this page can answer all sorts of questions like that.

---

### Post by sneax on 2005-09-22
[QUOTE=aysiu]What problem do they all tell you? Is there an error message?[/QUOTE]
 After a quick check, this is basicaly the error that all media players give:
"There is no plugin to handle this movie."

In Totem I select 'play disc' and then the only thing I can select is the VIDEO_TS file which gives me this error. So sure I have to get the right plugin, but which one? win32codecs is installed, together with libdvdcss2 and some others ... maybe it's not finding the plugin? How would I go about checking that?

---

### Post by sneax on 2005-09-22
[QUOTE=gez]try [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 
although I can't seem to get the link to work at the moment which is probably the horrid connection in my office.

But if it works this page can answer all sorts of questions like that.[/QUOTE]
 It's down for me too :(

---

### Post by krylla on 2005-09-22
Try to reinstall xine after you installed the codecs

ps found a alternetive adress to ubuntuguide  [http://koti.mbnet.fi/mikko75/ohjeet/ubuntuguide/en_index.html](http://koti.mbnet.fi/mikko75/ohjeet/ubuntuguide/en_index.html)

---

### Post by sneax on 2005-09-22
Xine is installed ...

---

### Post by Kapre on 2005-09-22
[QUOTE=sneax]Xine is installed ...[/QUOTE]

sneax - seems like you did not install all the codecs. Try following the guide on this shortcut [guide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html). This is just the mirror because the ubuntu guide is down.

K

---

### Post by sneax on 2005-09-22
I checked the error logs and I saw a 'Permission denied' somewhere so I stopped looking altogether and just logged in as root in a console window and ran the command
xine
I just pressed the button 'DVD' and BANG my dvd menu appears.

So i guess these plugins are only accessible as root? Should I install them as a user to make them work? I don't realy understand! So it's clearly a permission problem.

EDIT: When starting totem as root it works flawlessly too!

---

