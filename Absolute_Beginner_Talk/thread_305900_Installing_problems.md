---
title: "Installing problems"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by xonuxus on 2006-11-24
I've been trying to install Ubuntu on my computer and it seems it's a little hard for me... I have 2 HDDs, master and slave... On slave hdd I've created 2 partitions, 6GB and 1GB for Ubuntu... the problem is that when I try to select these partitions to install Ubuntu the setup says something about choosing another partition... 

Could you please tell me what can I do to install on these partitions because I don't want to mess with Windows' partition... I am sick of installing windows!!! :confused:

---

### Post by Bachstelze on 2006-11-24
Hi and welcome to Ubuntu :)

Whenever you are reporting error messages, please be more precise and tell us **exactly** what the message says.

---

### Post by xonuxus on 2006-11-24
> **HymnToLife said:**
> Hi and welcome to Ubuntu :)

Whenever you are reporting error messages, please be more precise and tell us **exactly** what the message says.

It says something about choosing a "root" partition... Excuse-me if I dont't remember precisely... I know very little about Ubuntu...

---

### Post by Bachstelze on 2006-11-24
I take it you are using the "Desktop" CD then... I never use it so I can't really tell you but I guess at some point you will have the possibilit to define "mount points" for your partitions. You must have at least one partition with the "/" mount point, that will be the root of the filesystem, whare all the files will go. 

Typically, people also define another partition with the mount point "/home", where all the users' personal files will be stored and a third one for "swap", which is the equivalent of Windows' "Virtual memory".

---

### Post by xonuxus on 2006-11-24
> **HymnToLife said:**
> I take it you are using the "Desktop" CD then... I never use it so I can't really tell you but I guess at some point you will have the possibilit to define "mount points" for your partitions. You must have at least one partition with the "/" mount point, that will be the root of the filesystem, whare all the files will go. 

Typically, people also define another partition with the mount point "/home", where all the users' personal files will be stored and a third one for "swap", which is the equivalent of Windows' "Virtual memory".

I tried to select a "/" partition and swap partition but it won't work... I had a similar problem with windows when I had to make a very small partition for its .ini... I want to keep windows on my primary and ubuntu on my slave...

---

### Post by Bachstelze on 2006-11-24
Then the only thing I can tell you is "use the Alternate CD" !

---

### Post by Doug11 on 2006-11-24
It took me some time to figure this out as well. I had hd1, which is my windows partition. I ignored this one, then created a small one for my swap, then another for whatever size I wanted to actually use for Ubuntu. I used 60GB,(not that it matters). If you already had this partition formatted by another OS like I did, I had to delete it cause I kept getting the same messages you are, then I went "add new" chose the unformatted partition and then it worked. It took some time for me to figure this out but it finally worked in the end. Just don't give up. Hope this helps.

---

### Post by louieb on 2006-11-24
Why don't you just unplug your windows drive.  
Thats what I did when I did my first Linux install.
I was paranoid about messing up windows.
It's a little bit bigger hassle  to set up dual boot that way but at least you know your window install is safe

---

