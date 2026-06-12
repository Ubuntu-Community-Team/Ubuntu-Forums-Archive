---
title: "Ubuntu files from Winxp Over network"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-11-02
Hey

I have two networked computers. 1 Ubuntu and 1 WinXp computer.

What i want to do is to be able to share files between them

When i turn my windows firewall of (zonealarm) i can see all the shared files on it from my ubuntu computer, But how do i see the Ubuntu files from the WinXP computer?

I have heared something about something called Samba? but have no idea what it is or how to use it.

Please help! thanks :)

---

### Post by tribaal on 2006-11-02
Samba is server software that lets you use a windows network as if you were running windows (to keep it simple: lets you share folders and/or printers).

Ubuntu comes with a samba client by default, but no server. This means you should be able to browse network shares on a windows network, but cannot yourself share folders and/or printers.
It's a very simple task to install a samba server: just open a terminal and type in "sudo apt-get install samba" (without the quotation marks of course). This will download and install the samba server, and make it run in the background.
Then to select and create shares, ubuntu comes with a handy little GUI utility that pretty much does all the gruntwork for you: Go to System > Administration > Shared folders.
The rest of it is pretty self-explainatory.

Edgy's version of this program actually checks that you have samba installed and if not will install it for you, but you can't be wrong if you install samba yourself first.

Hope this helps...

- trib'

---

### Post by Tobywuk on 2006-11-02
Thanks, that was very very helpfull and worked first time withought any cufuffle which makes a change :D 

one thing though,on my winxp comp, i see the samba server but when i try and access it, its asking for uname and pword to connect to localhost.localdomain.  Tried my ubuntu Uname and Pword, and my windows one but i cant get in

---

### Post by mattskr on 2006-11-02
Change your username and password on your XP box to match your Ubuntu login and it should work.

---

