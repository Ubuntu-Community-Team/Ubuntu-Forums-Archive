---
title: "Ubuntu network"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-06-03
I want to network the two computers running Ubuntu 7.04 on my home network.  Both are communicating with the router wirelessly at the moment, but I could hook mine up via wire if I wanted.

It doesn't seem to matter.  I cannot find computer 2 from computer 1 when both are running Ubuntu.  If I boot computer 2 into XP, then, Ubuntu compute 1 can find and explore computer 2.

What am I missing?

Thanks in advance for any suggestions.

Caruso

---

### Post by wpshooter on 2007-06-03
Probably need to install **SAMBA** under SHARED  FOLDERS which is under System/Administration.

Good luck.

---

### Post by drs305 on 2007-06-03
Here is a good source for how to do almost all the basic things in ubuntu. Take a look at the networking section. We are here to help if you run into problems.

General Index:
[http://ubuntuguide.org/wiki/Main_Page]("http://ubuntuguide.org/wiki/Main_Page")

Samba is section 1.21.6
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server")

SSH is section 1.21.8
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server)

---

### Post by mlentink on 2007-06-03
System>Administration>Shared Folders

Under the tab Shared folders click "Add" and specify a folder you wish to share
Under the tab General specify a windows domain workgroup name (should preferably be the same for all the computers in your network. You may want to look at the windows settings for this)

Hope this helps.

---

### Post by carusoswi on 2007-06-03
> **mlentink said:**
> System>Administration>Shared Folders

Under the tab Shared folders click "Add" and specify a folder you wish to share
Under the tab General specify a windows domain workgroup name (should preferably be the same for all the computers in your network. You may want to look at the windows settings for this)

Hope this helps.

Thanks for all the replies.
With respect to workgroup names, would that be specific to sharing windows computers or is it necessary for Ubuntu sharing as well?

I have Samba - It worked ok when all the computers in the house ran XP except mine - but, now that we have loaded Ubuntu on all machines, it no longer seems to work.  I must be missing something.  Will have a look at all the links/guides provided.

Thanks again.

Caruso

---

### Post by gwm on 2007-06-04
Hi,
I have a similar setup and experienced half of your problem. This is what fixed my problem.

Both the PCs in question were running Ubuntu Feisty Fawn 7.04 in a dual boot setup.
I installed SSH, which automatically also installed openssh-server and openssh-client.
Using the GUI menus I went to **Networking** and setup host references to the static IP addresses that I use. I think my problem arose because I didn't do this all nice and tidily and tried to use SSH before I'd completely set things up. A shared printer came into the picture here somewhere and messed things up.

Using the GUI menus I could connect-to-server from computer1 and could browse computer2 fine. When computer 2 was  running Ubuntu I connected using SSH. when computer2 was running windows I connected using Samba. It showed me all the public shares etc. and I could access them correctly.

Now we go to computer2 which misbehaved. With it I could make the windows connection alright but the Ubuntu one refused. After reading the forums and many attempts I found that one could connect to computer1, using the command line on computer2 as follows (when the command works you are asked for a login password and all):

**ssh user1@computer1**

This gave me an error message that the GUI didn't. It taught me that there is a file in a hidden directory called ~/.ssh/known_hosts and that something was wrong with it. The file is encrypted and I couldn't work out how to go about fixing it, so I did the following on computer2 (The computer from which that I couldn't see the other. The one where I got the error message). The idea was to uninstall SSH, delete the offending file and start all over again.

1. Using Synaptic Package Manager completely **uninstall SSH, openssh_server, openssh_client**
2. Remove that known_hosts file using **rm -r ~/.ssh**
3. Using Synaptic Package Manager **reinstall SSH** (openssh_server and _client are automatically installed along with ssh)
4. Using the GUI menu **Places->Connect to Server** connect to computer1 using ssh

The ~/.ssh/known_hosts file was recreated and my problem was fixed. Now both boxes can see each other very nicely thank you. I have yet to check whether the shared printer is still working.

:popcorn:

---

### Post by drs305 on 2007-06-04
> **gwm said:**
> 
This gave me an error message that the GUI didn't. It taught me that there is a file in a hidden directory called ~/.ssh/known_hosts and that something was wrong with it. The file is encrypted and I couldn't work out how to go about fixing it, so I did the following on computer2 (The computer from which that I couldn't see the other. The one where I got the error message). 
:popcorn:

Sometimes the file gets corrupted or changes with computer changes. If you remove the known_hosts file it will simply recreate it when you run SSH the next time and ask you for the passwords. So you can just delete the file and it might fix everything without removing/reinstalling SSH.
```
rm ~/.ssh/known_hosts
```

---

### Post by lazyart on 2007-06-04
Lazyart's guide to simple Lin-Win networking.

1- locate the folder you wish to share in Ubuntu.
2- right click on it, set it to shared, Samba (or SMB).
3- at the command line type```
sudo smbpasswd *username* -a
sudo smbpasswd *username* -e
```

Now Ubuntu user *username* has the same permissions to that folder across the network as it would if sitting in front of the machine.

---

### Post by ttr738 on 2007-09-20
cheers for that fix. spent ages trying to figure out why ssh wasn't working in gnome any more!
much appreciated

---

