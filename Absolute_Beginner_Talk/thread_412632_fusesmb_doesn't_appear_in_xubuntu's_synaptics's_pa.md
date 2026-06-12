---
title: "fusesmb doesn't appear in xubuntu's synaptics's package list"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by notroot on 2007-04-18
Hi everyone,

I have Xubuntu Edgy installed on my good old HP nx9000 laptop. I'm totally new to both xubuntu and linux, so please bear with me. I have tried to get my laptop integrated into a corporate network and one of the things I need most is sharing files.
Now, from what I have read on this forum, a simple way to do that is to install fusesmb, use it to mount network to a folder (say, /media/network) and then browse that folder using Thunar. However, the fusesmb does not appear in synaptic's package list even though I have downloaded the most recent package list (or whatever is the proper terminology).

So, my question is:
[LIST]
[*]what do I do to install fusesmb
[*]is this the right thing for me? Is there a simpler way to do this?
[/LIST]

Also, if you feel like answering them, there's whole bunch of other question. In essence, they're off-topic, but who's there to stop me from posting them here? (yeah, I know - the admins)
[LIST=1]
[*]I have used the following howto to configure my samba server (or daemon, if you wish):
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
But - do I really have to use WINS and do I have to add my ip to every XP box that I want to see me? Can't I use Active Directory or something?
[*]I have tried to install another language version of xubuntu, but somehow openoffice.org wound up to be on the dependencies list. Do I really have install open office to have bilingual xubuntu?
[*]Also, I would like to run some windows applications on Xubuntu (notable notepad++ - vim and emacs may be really great, extensible and what not, but they're _NOT_ intuitive and easy to use code editors). As I understand it, I need wine for that. Once again, though, it doesn't appear in the package list. Is it even in ubuntu's package repository? Are there alternatives?
[*]Where's something like Firefox's "Application Data"? Is there a way for multiple users to share the same bookmarks?
[*]Also, would someone explain me why the authors of xubuntu denied users root access and offered them sudo? Don't get me wrong - I am not questioning the logic behind it, I am merely trying to understand it.
[/LIST]

---

### Post by notroot on 2007-04-18
just bumping the thread to the top of the list.

---

### Post by Compyx on 2007-04-18
Fusesmb appears to be in the universe repository (for Edgy and Feisty), so you'll have to enable the 'universe' repository in Synaptic. Same goes for wine.

Here's how to enable extra repositories in Edgy:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

Hope this helps.

---

### Post by notroot on 2007-04-18
Thanks, that worked. Trivial. One has to love this package system after all that hassle with registry and DLL hell in Windows.

---

