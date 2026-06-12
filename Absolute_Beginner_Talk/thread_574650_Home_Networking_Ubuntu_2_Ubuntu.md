---
title: "Home Networking Ubuntu 2 Ubuntu"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Blue_T0oth on 2007-10-13
just bought a new laptop vaio v350n, had no probs getting the wifi going, but went and setup filesharing on both systems using the unix 1 and put in both sys's hostnames,... but when i goto network, i can c them both in there but the folders are empty

ne suggestions??

---

### Post by shearn89 on 2007-10-13
Can you clarify your problem? You have two computers which you want to share files between, and they're both ubuntu. You can see the other computer from one of them, but there's nothing in the shared folder? Have you put something in that folder from it's respective computer?

---

### Post by andguent on 2007-10-13
You didn't mention which version of Ubuntu you are using. Can we assume Feisty?

I'm on Gutsy, so it is possible your menus are different, but try clicking the System menu -> Administration -> Shared Folders.

If it isn't there, try using Add/Remove programs to install samba, the windows file sharing mechanism. Note: I just tried following my own notes and found that Add/Remove has a program called "Samba" which really should be called "Samba Config Helper" or similar. It seems helpful nonetheless.

If you want a folder you can click on samba file sharing is probably your best route. You will definitely need to share a folder on at least one of the computers.

Other options include:
* NFS -- Linux/Unix file sharing, somewhat complicated at times
* scp -- good for copying just one file or a small group of files. 
**** EX: scp [email]myusername@192.168.1.100:/home/myusername/Swanky.mp[/email]3 /tmp (copies an mp3 file from remote computer to your local /tmp directory)
* rsync -- good for syncing entire directories for backups and such
**** EX: rsync -va myusername@192.168.1.100:/etc /opt/myBackupOfEtcFromOtherComputer

---

