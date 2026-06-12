---
title: "Ubuntu Server (music/home directory/printer sharing)"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-21
Hey, guys just a few questions which I would like to try to get answers to before i start work on my server.

1.) I want to share all my music from one computer ( i have around 60gb all in folders by name and then artist) i want ot be able to access it quickly and play the music i want over the network quickly. Any particular way to share this media?NFS the best?(i play the music with XMMS)

2.) I would like to share my printer from the same ubuntu server and i would like to know how to set up the printer sharing through command line as i dont want to have to install X server at all on the machine.

3.) I would like to put by home folders on the server so no matter what computer I go on my home folder is the same. I know how to share the home folder with NFS but how do i make it so that my home folder on each computer is linked to a remote location?

Thanks in advance
Saj

---

### Post by saj0577 on 2008-03-21
I know  #3 is possible throught NFS "There is no need for users to have separate home directories on every network machine. Home directories could be set up on the NFS server and made available throughout the network." from the ubuntu docs.

Saj

---

### Post by saj0577 on 2008-03-22
Can someone move this too the server forum please see if i get a response there.


Saj

---

### Post by banewman on 2008-03-22
Alot of peolple frown on nfs because it can be less than secure.
But being behind a router I use it on my lan to mount my music directory and it works ok with rhythmbox.

:)

---

### Post by Jose Catre-Vandis on 2008-03-22
I use NFS to share music, video and documents around the house to good effect. You can even set up Windows machines (XP/Vista) to have access. on Ubuntu once set up it becomes speedy and transparent
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

Setting up your printer depends on what it is. Suggest you search the forums for your type ( I have a network printer so can't help), but I guess Samba/CUPS is your answer.

NFS Home Folders - have a good read here:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by saj0577 on 2008-03-22
Then how do i mount the shared foldrr as my home folder on client?


Saj

---

### Post by saj0577 on 2008-03-22
Any tips on sharing my printer through CUPS in terminal (no x server to be used)

Saj

---

