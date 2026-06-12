---
title: "Need Help Bad Please"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Jason_howard on 2007-07-24
I lost my home folder and my Computer and I cant access my windows side

Couldn't execute command: nautilus
Verify that this command exists.   thats what it says when I try to launch my home folder its also missing from the places


I cant Even right click on the desktop to create folders or anything  did my Nautilus some how get messed up?

---

### Post by lsutiger on 2007-07-24
Check your trashcan.

---

### Post by Jason_howard on 2007-07-24
I cant even access the Trash can?

---

### Post by Al3xK3aton on 2007-07-24
This is some serious problems, man. I'd reinstall Linux altogether if I was you.

---

### Post by lsutiger on 2007-07-24
Before doing that, try reposting in one of the other threads. I would recommend either the Installation and Upgrades link.

---

### Post by HermanAB on 2007-07-24
Hmm, if your desktop system screws up, create a new user account, then log in and copy your data over from the old account.

So, take a deep breath and do something like this (sorry I'm not on an Ubuntu machine now!):
Open a terminal - ctrl-alt-f2 I guess.
Then do something like:
Login: oldusername
Password: oldpassword
$ sudo groupadd newusername
$ sudo useradd -g newusername -s /bin/bash -d /home/newusername newusername

Then log out and log back in as the new user - ctrl-backspace may also do it for you.

If that works, then you can hunt down your data and copy it over to the new home directory and eventually delete the old user account.

'Hope that helps!

Herman

---

### Post by Jason_howard on 2007-07-24
I Did some searching and seemed to have fixed the Problem.

Thanks to all that helped

---

### Post by lsutiger on 2007-07-25
Could you post what you did to resolve the problem for the future persons that come into the same problem?

---

### Post by Jason_howard on 2007-07-25
I some how deleted natuilis so I went into synaptic package manger and reinstalled what I thought went with it.

to be honest it was pure luck comming from this Linux Newbee

---

