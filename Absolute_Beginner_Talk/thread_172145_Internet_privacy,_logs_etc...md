---
title: "Internet privacy, logs etc.."
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-05-08
Hi.

I'd like some info on internet traces/logs/privacy please. Coming from XP I have a little knowledge about temp files, DAT files, traces etc. In the big move to Ubuntu which will be permanent (soon!) I need to know where any internet logs, traces, historys are kept - more in particular to other users on my PC. I have tried various google searches but with not much joy...

Any help please?

---

### Post by louis_nichols on 2006-05-08
This actually depends on the browser you are using. For example, Firefox works exactly the same both in windows and ubuntu (or any Linux distro for that matter).

It will store browsing info (html, cookies) in a folder belonging to your profile, located in /home/<user-name>/.mozilla/firefox/xxxxxxxx.default/Cache where the x's will be a random array of characters.

temporary stuff is usually just stored in /temp folder and can be configured to be deleted at shutdown.

I'd say you needn't worry: the safety Ubuntu offers compared to windows is one of the main reasons most of us use it.

EDIT: if you're worried about users on the same pc seeing each-others stuff, you needn't, either. Each file has appropriate permissions, which will prevent other users than the owner from seeing them. Well... root account can see all, but someone's gotta be able to do it.

---

### Post by Nikusan on 2006-05-08
All your browser's history/bookmarks/saved passwords will be in /home/pelham/.mozilla (or whatever your username is)
Similarly, gaim's chat logs will be in /home/pelham/.gaim
It's exactly the same for any other users on the computer, just change the folder under /home/

---

### Post by Herman on 2006-05-08
The command ```
$ last
``` shows a list of all users who logged in and out according to your /var/log/wtmp file since that file was created.

or the command ```
$ lastb
``` shows a log of any bad login attempts in /var/log/btmp

```
$ man last
``` Will give more information on these commands, there are options you can use with them to include the IP addresses and/or hostnames of those listed.

And the command ```
$ who
``` shows who is logged on at the moment (at the time you enter the command).

---

### Post by hw-tph on 2006-05-08
System logs are stored in /var/log/ but they should only be readable to root and members of the administrative "adm" group (the default user should be).


Håkan

---

### Post by sophtpaw on 2006-05-08
[QUOTE=Pelham123]Hi.

I'd like some info on internet traces/logs/privacy please. Coming from XP I have a little knowledge about temp files, DAT files, traces etc. In the big move to Ubuntu which will be permanent (soon!) I need to know where any internet logs, traces, historys are kept - more in particular to other users on my PC. I have tried various google searches but with not much joy...

Any help please?[/QUOTE]

There is a program called Tor, which also helps you keep anonymity from other computers. But maybe that is not what you meant

Welcome to Ubuntu,

--
sophtpaw

---

### Post by Pelham123 on 2006-05-09
Thank you all for the replies :KS

---

