---
title: "vmware wont connect to internet"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by doodger on 2007-07-29
ok so this is the problem: vmware wont connect to internet. 
Ive tried all Windows XP connection stuff and it still dont connect




Im using vmware player
my version is feisty

Any help would be very appreciated:-D

---

### Post by doodger on 2007-07-29
bump








Does anybody have a hint? :(

---

### Post by anewguy on 2007-07-29
Are you trying to connect with a hard wired connection or a wireless connection?

---

### Post by oilchangeguy on 2007-07-29
use the NAT connection. that way the guest os, uses the host os connection.

---

### Post by doodger on 2007-07-29
> **oilchangeguy said:**
> use the NAT connection. that way the guest os, uses the host os connection.

What is NAT? I use wireless

---

### Post by oilchangeguy on 2007-07-29
> **doodger said:**
> What is NAT? I use wireless

locate the connection set-up in your vmware software, and select NAT for the connection.

---

### Post by doodger on 2007-07-29
there seems to be no connection setup i can find in vmware player. Ive tried install vmware server but it wont work.

---

### Post by anewguy on 2007-07-29
Ahhh..... if you were using VMPlayer you had no way to configure your VM except by editing the .vmx file.  Going to VMWare Server is the best idea, but there is one slight "gotcha" - you have to completely remove VMWare Player before you can install VMWare Server.  Sometimes the uninstall script works, other times not.  If you installed VMWare player from the synaptics package manager and took the default answers, try using the information I posted in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=507421&page=2") in response to a similar problem.  Let me know how that goes, as we may need to have you delete other things as well.:)

---

### Post by anewguy on 2007-07-29
Forgot to mention, if you know where your .vmx file is (try "locate *.vmx" in a terminal window), you can edit it and replace "bridged" with "nat" on the network interface and save the file, then try player again.  I would really recommend VMWare Server to anyone wishing to try virtualization - it's the easiest place to start and get running.:)

---

### Post by doodger on 2007-07-29
tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in
the "/tmp/vmware-config7" directory.


it say that when i configure the server

---

### Post by upthelum on 2007-07-29
Try the server or workstation versions and set it to use NAT.

---

### Post by doodger on 2007-07-29
i tried to install the server but this error still appear:

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in
the "/tmp/vmware-config7" directory.

---

### Post by doodger on 2007-07-29
bump

---

### Post by Nussbaum on 2007-07-29
Is that what synaptic says or what are you doing that gives you that error message?

In any event free bump

---

### Post by anewguy on 2007-07-29
Did you follow my previous post and the link to how to delete enough of VMWare Player so that you can install VMWare Server?  If so, what were the results?  If you did it all, and are trying to install VMWare Server in Ubuntu 7.04 Feisty Fawn, you need to follow special instructions:

[[COLOR="Red"]Vmware Server - Ubuntu 7.04[/COLOR]]("https://help.ubuntu.com/community/VMware/Server")

Please post back.......:)

---

### Post by anewguy on 2007-07-30
Did you follow my other link and remove vmware-player first?

---

### Post by ksskruthic on 2007-10-25
> **anewguy said:**
> Did you follow my other link and remove vmware-player first?

Hi Anewguy,
Your instructions really helped.  I followed the same by removing vmplayer. Uninstall was a snap on my gutsy. I installed vmserver. pretty much same steps as vmplayer. I am able to ping the host OS (Gutsy) from my guest (RHEL 4) and vice-versa since they are NAT'ted. That really helped me a lot and made things simple. VM Server is really awesome.

I was wondering if you can help me with another problem related. Considering the above scenario, Unfortunately I am unable to ping the guest OS from another computer on the same network. I believe it has something to do with my guest OS taking a private IP address(172.*.*.*) that is not in the  usual private IP range(192.*.*.*) that my router gives every computer that is trying to connect. I am unable to ping this 172.*.*.* network from my other computer (running windows XP). I some how need to be able to access this 172.*.*.* from a webpage from every computer on my network. I am able to achieve this from my host OS (Gutsy) via webpage as the guest OS is running a webserver but not from any other computer.

BTW, I am using a wireless connection via TrendNet Wireless Router. Any suggestions greatly appreciated.

Thanks again,

-Sonu

---

