---
title: "what is ufw and how do you"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by threegremlins on 2008-04-08
set it up? At least with firestarter you could tell something was going on even if you diidn't know what you were looking at, like the icon going red. "Oh My God I'm Under Attack!"
What the hell do you do with ufw? Leave it alone and wonder if your safe, praying to the coders to whom you've  place your world in their keystrokes?
Comparing this with firestarter cause I know about 25% of it, you can set up a deny list and an accept list.
How does a person without command line knowledge do that with ufw?

---

### Post by mikeyphi on 2008-04-08
It's only just being coded!!

Read about the plan here: [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by threegremlins on 2008-04-09
ufw  is being implemented into the hh system already, so I can assume it is functional. 

On the link this is an example of the command line you would use to set rules to ACCEPT or DENY.
# ufw allow|deny [proto <protocol>] [from <address> [port <port>]] [to <address> [port <port>]]
However, I'm not clear as to how you can tell whether you need to close a port or restrict an address. Do you need to call another program manually to see if something is trying to access an open port? Is it done automatically and you get a popup window? I read, by default all ports are closed, yet when I fire up a browser or email I've changed nothing and these programs access my providers and the web.

---

### Post by threegremlins on 2008-05-03
Hey threegremlins, I just installed Xubuntu because Ubuntu was acting buggy. Anyway I checked ufw out right away and it said it wasn't loaded. So I  ran sudo ufw enable and everytime now when I fire up Xubuntu it says it's loaded. I uninstalled usplash(I like to watch the process) and it says it's loading as the sytem starts. As to how you can find out whether someone's trying to hack in to your box I don't know but I'll let you know when I find out.

---

