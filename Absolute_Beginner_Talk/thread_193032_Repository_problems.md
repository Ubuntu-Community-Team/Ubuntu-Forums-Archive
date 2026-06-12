---
title: "Repository problems"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by sweeney on 2006-06-09
Synaptic package manager is giving me a message stating it cannot start various source packages (see below)

Any idea what the problem might be here?

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breez........

etc etc

---

### Post by briguy on 2006-06-09
The servers might be down.  You could edit the file to remove the gb part of it (so it comes from the main ubuntu repos and not the Great Britain ones), so the line would look like so:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

instead of 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy universe

This worked for me when I was having troubles with my regional repos

---

### Post by sweeney on 2006-06-09
that initially seemed to work but now i get the following message:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists

etc etc

does any one have any idea what may have happened?

---

### Post by dralaroc on 2006-06-09
You need to delete one of the entries you are showing two ;).  Then give it a whirl.

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bi nary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/list

You could remove via sudo gedit /etc/apt/sources.list or in the synaptic manager.

---

### Post by Brunellus on 2006-06-09
deleting's not recommended unless you happen to know what you're doing.  If you want to "ignore" any line in a configuration file, put a hash mark (#) in front of it:

# this line would be ignored; it's a comment

THIS LINE WOULD BE EXECUTED

# THIS LINE WOULD BE EXECUTED; but I put a hash mark in front, so it's not.

The advantage here is that if you mess up any of your configuration files, you can uncomment/comment out individual lines to isolate problems.  It also saves you the trouble of remembering what the config file looked like before.

---

### Post by sweeney on 2006-06-11
thanks for that-im on a steep learning curve

---

### Post by sweeney on 2006-06-12
My repository problem above seems to have been solved. However, how did the problem arise in the first place?

Specifically how does a duplicate source list appear and why, when it does so, is it not possible to ignore one when it does occur?

thanks in advance.

---

