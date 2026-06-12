---
title: "package problems"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by natman on 2005-10-15
hi i have been using the badger vesion for a few hrs now and using in particular a program called 'kile'
anyway when i go to build it tells me i need the the following

[ViewDVI] Could not find the kviewerpart library.


Can anyone tell me how to get it 
thanks:

---

### Post by manicka on 2005-10-15
kile is available in the repos. You can add it with synaptic or with 
```

sudo apt-get install kile 
```

in a terminal

You'll also need the universe repository added to your sources.list

[http://doc.ubuntu.com/gnome/faqi386/C/ch02.html#addinguniverse](http://doc.ubuntu.com/gnome/faqi386/C/ch02.html#addinguniverse)

---

### Post by natman on 2005-10-15
yeah i have kile installed and it seems fine when i start it up, but when i go to build  get the following
'[ViewDVI] Could not find the kviewerpart library.'
 anyway i tried running the install command and got the following

'Reading package lists... Done
Building dependency tree... Done
kile is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
'
Thanks

---

### Post by natman on 2005-10-15
I just ran the system check in kile and found the following problems

'kdvi (critical failure, kile will not funcitinon)
and loads more errors'

---

