---
title: "Network"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-02-13
How the hell do i make a network in linux that has to be able to deal with both linux and windows pc's? like for instance if i want to make on for a place where a lot of students are together and want to share music and movies? named kot for example. didn't get a clue from google how it's explaind. and how do i modify the windows networking than?

cheerz

---

### Post by mips on 2006-02-13
Do a search here for SAMBA & NFS. Samba allows windows PC's access and NFS is for linux PC's.

---

### Post by ignorance on 2006-02-13
that's i figured out after some clicking and such but i just don't know how to set it up

---

### Post by Chappy on 2006-02-13
Question: how/where is the search/find tool on Ubuntu? I didn't notice it  when I was trying to get online today. I wanted to serach for "modem" and GnomePPP. Can someone tell me real quick where to find this utility? 

Thanx, and btw, see my other thread,  please!!  (Chappy grabs hair and pulls out another handfull).

---

### Post by ignorance on 2006-02-13
think you mean System > Preferences > Network proxy not sure thou.

---

### Post by AndyCooll on 2006-02-13
[QUOTE=Chappy]Question: how/where is the search/find tool on Ubuntu? I didn't notice it  when I was trying to get online today. I wanted to serach for "modem" and GnomePPP. Can someone tell me real quick where to find this utility? 

Thanx, and btw, see my other thread,  please!!  (Chappy grabs hair and pulls out another handfull).[/QUOTE]

Are you talking about on these forums or actually on your Linux box?

On these forums it's there towards the top on the dark brown strap

On the Linux box it's under Places->Search for files

The help tool is on the taskbar

:cool:

---

### Post by AndyCooll on 2006-02-13
[QUOTE=ignorance]that's i figured out after some clicking and such but i just don't know how to set it up[/QUOTE]

Easiest way is for you to use the search function on these forums with the terms "NFS" and "HOWTO". Then "Samba" and "HOWTO". There are quite a few threads which will take you through the setup process.

Here are a couple to start you off:
[NFS]("https://wiki.ubuntu.com//SettingUpNFSHowTo")
[Samba]("http://www.ubuntuforums.org/showthread.php?t=76647")

:cool:

---

### Post by ignorance on 2006-02-14
thank you much

---

### Post by ignorance on 2006-02-14
well i think i completely fucked it up, followed the howto's step by step and still i don't get it running when i try to mount i get this error

> Could not resolve mount point /home/christophe/Network

can someone help me i really wants this get up and running.

---

### Post by mips on 2006-02-14
[QUOTE=ignorance]well i think i completely fucked it up, followed the howto's step by step and still i don't get it running when i try to mount i get this error
[/QUOTE]

What howto's did you follow, links please as we have no idea what you did ?

---

### Post by ignorance on 2006-02-14
[http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

i followed this one, and i don't have the option to use nfs since i'm located in a totaly hostile windows environment

---

### Post by mips on 2006-02-14
At what point in the guide did the error occur ?

---

### Post by ignorance on 2006-02-14
when i tried to acces it true

Code:

sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000 //[whatever you named the Samba server]/[network user] /home/`whoami`/Network

i got the error

 Could not resolve mount point /home/christophe/Network

---

### Post by mips on 2006-02-14
If you used the version of Samba found in the repos via synaptic then I suggest you uninstall all of it (samba & samba-common)

Download the new version from the Samba site according to that guide and reinstall. People seem to be having problems with the version in the repos.

Look at post #2 here, [http://ubuntuforums.org/showthread.php?t=124449](http://ubuntuforums.org/showthread.php?t=124449)

---

### Post by mips on 2006-02-14
[QUOTE=ignorance]when i tried to acces it true

Code:

sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000 //[whatever you named the Samba server]/[network user] /home/`whoami`/Network

i got the error

 Could not resolve mount point /home/christophe/Network[/QUOTE]

Are all the details correct, no typos, upper/lower case issues etc ? (Sorry, I know I'm asking the obvious)

---

### Post by ignorance on 2006-02-14
as far as i know yes.

and also i really fucked it up, even with the howto's so can someone explain me how to set up an entire network with the name kot for excample, and also how the hell i get connected to the windows pc's? really i tried and failed.

---

### Post by ignorance on 2006-02-15
after a lot of typing, reading, searching and reading i came up with this

[muziekdeelII]
        path = /home/christophe/muziek
        guest ok = Yes
        browseable = No

so now how can i change browseable to yes?

---

