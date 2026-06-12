---
title: "Add/Remove NOT loading"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by panayic on 2007-03-22
Hello out there,
I'm facing the forward issue.I cant get Add/Remove Application functioning.All i see is that it's loading up to a point while checking for installed applications and it's either finishing checking and exiting the application OR exiting just like that.
Can anybody take a look at it?
Thank you

---

### Post by mahy on 2007-03-22
Weird indeed. Does Synaptic works? Can you install/uninstall anything using that?

---

### Post by Kateikyoushi on 2007-03-22
Try synaptic from System > Administration > Synaptic, if does not work try from terminal "gksudo synaptic" and let us know about the error message.

---

### Post by panayic on 2007-03-22
Well,synaptic worked fine-i uninstalled Ekiga successfully.
After that i exit Synaptic and tried to load Add/Remove once more but in vain.It just exits without any message-just like that.
i dont know if this has something to do with my issue but my last action was to follow the steps found in here : [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
.A big THANK you for your time

---

### Post by panayic on 2007-03-22
What a silly newbie am i :) 
I followed the procedure found here [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) from the beginning and the Add/Remove works fine.
The thing now is that i got the following warning from the terminal:

Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [6061B]     
Fetched 6449kB in 2m22s (45.2kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Shall i run  apt-get update  or or it's better to ignore it so not to conflict anything?

---

### Post by mcduck on 2007-03-22
> **panayic said:**
> What a silly newbie am i :) 
I followed the procedure found here [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) from the beginning and the Add/Remove works fine.
The thing now is that i got the following warning from the terminal:

Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [6061B]     
Fetched 6449kB in 2m22s (45.2kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Shall i run  apt-get update  or or it's better to ignore it so not to conflict anything?

It's telling you that you have some line twice in your sources.list. Just remove the other one and your problem is fixed.

---

