---
title: "can't see server from windows machine"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Shadow Skippie on 2008-03-05
I am using a an Ubuntu server machine at home. I'm having problems seeing the machine, it was working okay the other day but now all of a sudden i can no longer see it. I can see out from the server, hell it can connect to the internet but i can't see into it from my windows machines. 

It has 4 network cards in it, all static, 3 are add ons one is built in. the addons are gigabit while the on board is 100 speed. (at the moment only one is in use but when i figure out how to do internet routing in linux this machine is going to bond my internet connections together, hence the need for mutiple network connections). currently the server is only being used as a file server, the shared folders that i use are not password protected. 

those are the details of the machine, if you need need anymore info please ask, i'd really like to know why it keeps disapearing and i seem to be having the same problem with a fedora machine at work (this one is pass protected) so i'd really appreciate if someone could help me with this

:confused:  Help

---

### Post by dstew on 2008-03-05
What protocol are you using to share the Ubuntu folder? Samba or NFS?

---

### Post by Shadow Skippie on 2008-03-05
i didn't setup a protocol but i believe the default is Samba and i think that's the one i've been seeing as i work on it.

---

### Post by dstew on 2008-03-06
Yes, when you use the Shared Folders item in the System --> Administration menu, you can chose Windows networking or NFS. Samba is the Linux software that does the Windows networking.

Post the output of the command```
cat /etc/samba/smb.conf
```and we can see how your samba server is set up. [Here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html") is some documentation on configuring samba.

However, it is not at all clear from your description of your problem that the samba configuration is to blame. It might be your networking setup, or even a hardware problem.

---

### Post by Shadow Skippie on 2008-03-06
it's not the hardware, that was the first thing i checked. I have an ethernet tester, the line is fine and i've tested the card in another machine, it works, which means the only other thing is linux. it's more then likely that i havn't set it up properly. i'll take a look at those docs this weekend, it's basically the only time i can sit down to look at it

thanks for the help

---

