---
title: "Synaptic problems"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2005-10-17
I just installed breezy and I have just uncommented the source.list file to gain access to the repositories. When I try to run synaptic, a pop-up error message appears:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

I am not sure what it means.
Any help is appreciated.

---

### Post by Murgle on 2005-10-17
The first thing to check is if you are on the internet,

EDIT:
I don't know if the breezy-backports are existant yet... they are they packages that are made backwarsd compatable from the next release and I don't know if work on  Dapper Drake has started yet and it looks like that the backports are what you are missing

---

### Post by blueoyster on 2005-10-17
Yes I am connected, I am currently posting and surfing ON ubuntu using firefox.

---

### Post by Murgle on 2005-10-17
If you go into synaptic and got to settings -> Repositories then tell me what you see.

---

### Post by blueoyster on 2005-10-17
I see:
Ubuntu 5.10 "Breezy Badger" (Binary)

Ubuntu 5.10 "Breezy Badger" (Source)

Ubunt 5.10 Upades (Binary)

            "           "       (Source)


Then:

Ubuntu 5.10 "Breezy Badger" (Binary)

Ubuntu 5.10 "Breezy Badger" (Source)

but these two say ""Community mantained" 

Then 4 repositories that say 
Ubuntu 5.10 Security Updates with both source and binary files

Then finally the last slot says
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports (Binary)

---

### Post by Murgle on 2005-10-17
try removing the last one, with the backports in it.  You might want to write it down somewhere as it will be good to have later when work starts on Dapper Drake and they port programs back so you can use them.

---

### Post by teaker1s on 2005-10-17
had the exact same problem the solution is to manually set the name server in your router to your isp dns.
 set up static ip on router and set (system networking) to your static ip and dns 

 your dns ip   [http://www.portforward.com/networking/dns.htm](http://www.portforward.com/networking/dns.htm)

---

### Post by blueoyster on 2005-10-17
I commented the last repository from the sources.list file and everything work just fine.

Thank you very much for your help.

edit: teaker1s thnx for you input also

---

### Post by andrewsawyer on 2005-10-18
Heya,

Just so you know, the backports haven't yet been released for Breezy.  They should be opened up at the same time (or just after) the repos for Dapper are opened.

Cheers,

Andy

---

