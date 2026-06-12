---
title: "Mac thin client"
date: 2005-06-07
forum: Apple PPC Users
---

### Post by Kurbycar32 on 2005-06-07
ok so i work at a school district and we have a few thousand macs that we cant afford to replace.  we have thin client servers and using a live ubuntu cd i was able to boot the OS open a shell and connect to my server using the rdesktop command.  i have shown that it will work now heres what i want to do.

1. strip down the OS to the bare minimum so it boots quickly
2. automaticly configure the network (runs DHCP should be no big deal)
3. auto-connect to a term server that i select prior to burning the cd  
4. be able to change what server the cd  connects to easily before i burn it (think modifiable .INF file but whatever linux uses)

basicly i want this to do one thing and be idiot proof.  i am a linux novice and am more then happy and able to read whatever guide i need to go do.  i would preferr to develop this on my windows PC since i am so familiar with it.  can anyone point me in the right direction?  if i get it working it would save the schools between 2-3 million dollars they could spend on other stuff, like books :smile:

---

### Post by gil-galad on 2005-06-07
Whats the terminal server hosting?  Windows runnning remote desktop?  Would you be better off installing linux on each mac instead of burning a whole bunch of cds?

---

### Post by Kurbycar32 on 2005-06-08
[QUOTE=gil-galad]Whats the terminal server hosting?  Windows runnning remote desktop?  Would you be better off installing linux on each mac instead of burning a whole bunch of cds?[/QUOTE]
 yea i could but were talking about 3500-4000 macs.  it would take forever to install on all of them.  if i developed a live cd we could have some intern burn cd's for a week and get it done instead of occupying a technician for several months
the servers are running windows term services and like i said i tested it working on ubuntu, i just want to make the process automated

---

### Post by FLeiXiuS on 2005-06-08
You may also want to take a look at:
[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by mips on 2005-06-08
Cant you prep one or two machines. Create Images of the HD. Store the image on the server and install over the network ??

Can you actually make an image of a Linux HD ?


Cheers
mips

---

### Post by Kurbycar32 on 2005-06-09
[QUOTE=FLeiXiuS]You may also want to take a look at:
[http://www.ltsp.org/](http://www.ltsp.org/)[/QUOTE]

Itsp is cool but it doesnt connect to a windows server.  the idea is to attach it to our existing infrastructure by connecting to a windows terminal server

---

### Post by cvr20 on 2005-06-19
sounds like a job for network booting alright. 

I finally managed to setup a linux server as osx netboot server (10.3.9 dmg as shared root filesystem, nfs mounted home directory) and while I can easily load the yaboot\ and yaboot.conf, with the vmunix and initrd from the livecd over tftp, the kernel on the livecd doesnt seem to grasp the concept of nfs mounting a root filesystem. 

This is usually trivial to fix by compiling a kernel with the nfsroot option.. unfortunatly I dont currently have access to a mac that is able to boot off cd/dvd so for now, im stuck. 

That should do the trick, though. no need to bother with inf files or burning the server ip and/or settings to the cd either, the dhcp server should provide that information.

Case

---

