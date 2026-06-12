---
title: "Quicklauncher in Xubuntu"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-01-09
Hi all... Newbie alert :-)

I'm using the xfce desktop in Xubuntu Edgy

I have a quicklauncher set up for the terminal. It's simply the word "terminal" which, I assume, links to the executable file called "terminal" in /usr/bin. 

But now I would like to have a quicklauncher which will pass a command to the terminal command line, specifically the command "vnstat -h" (no quotes)

Typing "terminal vnstat -h" (no quotes) in the quicklauncher does nothing. 

Can someone point me in the right direction please. 

Many thanks
Miguel

---

### Post by kerry_s on 2007-01-10
Try this-> xterm -T "vnstat" -e vnstat -h
or if you want it pretty->
xfce4-terminal -T "vnstat" -e vnstat -h

---

### Post by Miguellint on 2007-01-10
Hi Kerry......Very cool. Did just what I asked for. 

And I could even understand what you'd done once I'd read "man xterm".

I even added a -hold option to keep the terminal window visible. 

xterm -T "vnstat" -hold -e vnstat -h

Many thanks
Miguel.

---

