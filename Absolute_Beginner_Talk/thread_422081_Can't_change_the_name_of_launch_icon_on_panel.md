---
title: "Can't change the name of launch icon on panel"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-24
I dragged a copy of the terminal icon (gnome-terminal) from the Applications menu, onto the panel at the top. I am using it to open an ssh session to another computer automatically with

gnome-terminal -e "ssh -Y etc...

and that works, but I wanted to rename it. I change it's name and comment in properties, but it just keeps reverting back to the original name and comment.  I have other launch icons on the panel, like one for Thunderbird email client, and those can be renamed.

So what's different about Terminal?

---

### Post by mac.ryan on 2007-04-24
Weird... I never noticed that, but it behaves the same on my computer! :-/

---

### Post by ubnewbie2 on 2007-04-24
> **mac.ryan said:**
> Weird... I never noticed that, but it behaves the same on my computer! :-/

I'll bet it's some obscure permissions problem :(

---

### Post by zvacet on 2007-04-25
Remove it from panel and rename it in application menu.After that put it back on the panel.

---

### Post by ubnewbie2 on 2007-04-25
> **zvacet said:**
> Remove it from panel and rename it in application menu.After that put it back on the panel.

No, can't rename it in the menu either.

I ended up creating a brand new one from scratch.  Easy enough to do, but it's odd about Terminal being fixed (everywhere it seems).

---

### Post by mac.ryan on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I filed a bug on launchpad about this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919)

you can eventually confirm it there / see if the devs will comment on it there...

---

### Post by ubnewbie2 on 2007-04-25
> **mac.ryan said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I filed a bug on launchpad about this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/109919)

you can eventually confirm it there / see if the devs will comment on it there...

Thanks for doing that.  When I get a little more than one days experience with ubuntu:) , I'll register and reports bugs too.

---

### Post by Bealer on 2007-04-26
I've got the same problem. 

I think it relates to this reported bug, but I've yet to work out a solution
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/95161](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/95161)

Edit:
Got one, just go to the
$HOME/.local/share/applications
directory and rename them from there.

---

