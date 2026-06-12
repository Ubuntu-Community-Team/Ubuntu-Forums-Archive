---
title: "Synaptic Manager: &quot;Couldn't stat source package list&quot;?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by MadL on 2006-02-19
Opened the Synaptic Package Manager tonight and was greeted with this message:

> W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

What does this mean? I don't remember deleting files or directories with these names.

---

### Post by BitTorrentBuddha on 2006-02-19
that repository is down, if it really bugs you you can go into /etc/apt/sources.list and comment it out by preceding it's line with ##
```
sudo gedit /etc/apt/sources.list
```
and then find the line that says [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages and put ## infront of it

(btw, in the future use the search feature)

---

### Post by AndyCooll on 2006-02-19
Ignore it and simply continue with whatever you are doing.

Sometimes you get a message like this if a repository is temporarily unavailable (as mentioned in the post above). In most cases the following day it's back up and working again!

:cool:

---

### Post by MadL on 2006-02-19
Good to know. Thanks! :)

(P.S. For some odd reason, my searches beforehand didn't turn up the earlier threads on this. Sorry about that. :( )

---

### Post by Cesium on 2006-02-19
If it doesn't update in the next week,  you can change your source.list as noted above.  I was getting the same error as you. I'm impatient and changed my sources.list based off this:

[http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")

I am not sure what impact it has for me to use that instead, but now synaptic works fine. I did back-up and save my old sources.list in case I run into problems.

---

