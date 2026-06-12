---
title: "Advice setting up Linux server and router"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by emes on 2008-04-17
I am VERY new to Linux. I have been reading a few books on Linux but they were geared to Desktop and not server version.

I have 2 projects that I want to do. The problem I have is that I haven't found 1 book with all the answers to my questions. I do networking but I use Server 2003 and XP.  So far I have come across 9 versions of Linux and their variations, so that is confusing. Commands are different in some of the versions, more confusion.

Here are the projects:

1. Setup a server that allows remote users to view the files on the server. One user will have the rights to download the files and the other user only to view the files. This will be a standalone network, different IP address than the company network. (So if the server gets hacked hopefully they won't get to the other network. The firewall has 2 ports for 2 networks.) I installed a Ubuntu ISO but I couldn't find commands as to how to administer the box.

The remote users will connect with Windows XP.

2. Setup a Linux router and add software that monitors / give reports where the user visited on the Web. I would love a suggestion for software for router and monitoring software.

These are the two projects. I would need an explanation as to what Linux software to use and installation instructions, and setup instructions for user rights, creating the directories, and how to copy the files onto the Linux server.

Thank you very much. If anyone lives in the States I would like to call them and talk them on the phone if possible. It would be much faster than emailing back and forth.

Thank you very much,

Emes

---

### Post by herbster on 2008-04-17
For the server, let's clarify. You want for example to be able to see a Videos directory on the server and have one user able to download the files witih all others only able to view? This can be done using NFS I'm sure, just want to be clear on your goal.

As for a linux router, I've never done that, you should make strong usage of the search function here and google.

---

### Post by emes on 2008-04-17
The files to be viewed are jpeg files.

Emes

---

### Post by northern lights on 2008-04-17
mkey.

That does not necessarily require a "server OS" as such. As herbster pointed out, simple file sharing will do the trick.

Are the files to be viewed from other Linux machines only, or are there Windows comps on the network also? --> Choice nfs/smb

I suppose pics are to be viewed live, so ftp is out of the question, right?!

As for the router, I've only set up one and that was a good number of years back - in school, actually. While I set it up, the head of our Physics department had brought the distro, which interestingly enough had come on one 1.44MB floppy. It was very simple, but did a marvellous job. Should I find it quickly, I'll post.

Otherwise I concur - google. Ubuntu is for sure not the best choice as the OS for a router. A router does such simple work, it needs not be anywhere close to the minimum hardware required by Ubuntu. A 486 for instance will do the job just as well...

---

### Post by ScorpKing on 2008-04-17
you might find [http://m0n0.ch/wall/](http://m0n0.ch/wall/) usefull

---

### Post by boyofford on 2008-04-17
> **northern lights said:**
> mkey.
As for the router, I've only set up one and that was a good number of years back - in school, actually. While I set it up, the head of our Physics department had brought the distro, which interestingly enough had come on one 1.44MB floppy. It was very simple, but did a marvellous job. Should I find it quickly, I'll post.


Found something like that..
[http://www.enterprisenetworkingplanet.com/netos/article.php/1107911](http://www.enterprisenetworkingplanet.com/netos/article.php/1107911)

Didn't know you could do this, what are the advantages of setting up your own router? Am I being thick?

---

### Post by northern lights on 2008-04-17
> **boyofford said:**
> Found something like that..
[http://www.enterprisenetworkingplanet.com/netos/article.php/1107911](http://www.enterprisenetworkingplanet.com/netos/article.php/1107911)

Yup, that sounds pretty much like it. +1 for that one. Might as well give that "FreeSCO" a try.

As for advantages:

1. Control - you set it up, you know what's going on in there
2. Reliability - I got an MSI router and it's only got to be reset every two weeks. That's pretty decent compared to previous experience. The one before that used to f*ck out on a daily basis. Once set up, you can a run a system like that for years straight.
3. Firewall parameters, for instance - do you know exactly how your industrial router filters?
4. Last but not least - it's fun.

Feel free to add.

---

### Post by torry_loon on 2008-04-17
For your router, take a look at Smoothwall or IPCop. They are Linux distros specifically for routers.

If you need to access the file server from inside the network, you would need to set up Samba for Windows clients or NFS for Linux clients. For external access, you would need an ftp server. VSFTP and ProFTP are available for Ubuntu.

There are instructions on how to set up various servers and services in the Ubuntu wiki ([wiki.ubuntu.com]("http://wiki.ubuntu.com")).

---

### Post by herbster on 2008-04-17
> **emes said:**
> The files to be viewed are jpeg files.

Emes

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by emes on 2008-04-21
Thanks to everyone that responded.

I am on vacation for a week, but I will monitor this site daily since people are making the effort to help me. However I won't be able to do research until vacation is over. I have a wife and kids that want my full time attention.

Sincerely yours,

Emes.

---

