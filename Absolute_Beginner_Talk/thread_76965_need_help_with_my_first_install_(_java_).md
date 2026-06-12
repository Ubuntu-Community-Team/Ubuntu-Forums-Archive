---
title: "need help with my first install ( java )"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-10-16
ok I am going to install sun java and then azureus. 

I know I have to install sun java first right?

so I am trying to follow this link
[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=uncomment+universe+repositories](http://www.ubuntuforums.org/showthread.php?t=76702&highlight=uncomment+universe+repositories)

and the first thing I need to do is add the extra repositories. so I go to the guide 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

and I think that all went ok.

but then when I go to the next step I downloaded the right sun java package. then I saved it in a folder I made in my home folder. is that ok or should it go somewhere else? 

Whe I try to go the step sudo apt-get install fakeroot java-package java-common

I get all this error stuff

Setting up java-package (0.23) ...
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fileor directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fileor directory)
W: You may want to run apt-get update to correct these problems
peter@desktopUbuntu:~$ fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
Error: The file "jre-1_5_0_05-linux-i586.bin" does not exist.
peter@desktopUbuntu:~$

the name of the file I downloaded is j2sdk-1_4_2_09-linux-i586.bin

what have I done wrong?

---

### Post by davmac on 2005-10-16
There is discussion about this at [http://www.ubuntuforums.org/showthread.php?t=76702](http://www.ubuntuforums.org/showthread.php?t=76702)

Looking at what is said here I would guess it is the backports that are causing your problem. Try commenting these out in the repositories. First "sudo gedit /etc/apt/sources.list" and then put an # at the start of each line that mentions the backports. Then run "sudo apt-get update" and have another go.

The person who wrote the HOWTO shows the sources.list used. You could even, temporarily copy exactly this into your sources list.

HTH,

Dave Mac

---

