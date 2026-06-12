---
title: "Audio &amp; PPPOE HELP NEED (PLZ HELP ME OUT)"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by hermitology on 2006-06-01
i have installed all including win32codecs but still i cannot play music of any format  .

i have Enabled the multiverse and universe repositories .
i have go through the forum and unoffical guide nothing has helped me!
[b]
when i open Synaptic Package Manager i get following error what has gone wrong[/b]
```



W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.lowvoice.nl breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://people.ubuntu.com ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
```


[b]
conecting through PPPOE is my next task[/b]

plz help  me

hermitology

---

### Post by [S|G] on 2006-06-01
After enabling the repositories, go to a terminal and do this:
```

sudo apt-get update

```
Then try starting synaptic again :)

---

### Post by %hMa@?b&lt;C on 2006-06-01
for pppoe, try 
```
sudo pppoeconf
```

---

### Post by hermitology on 2006-06-01
when i update```

sudo apt-get update
```

i get many failure messages 

i am able to connect oto net but its toooo slow , after 5 min a web page is opened plz tell me how to improve my speed and to 

play music and audio files .

thanks

hermitology

---

### Post by [S|G] on 2006-06-01
Can you post the error messages so we can take a look?

---

### Post by hermitology on 2006-06-01
**thanks '[S|G]'**
and all of u here who have help me , iam using LINUX Ubuntu 

can u beleive that i am infact brousing from linux , its really g8 .


as audio is concern i have downloaded vlc player its working ,

---

