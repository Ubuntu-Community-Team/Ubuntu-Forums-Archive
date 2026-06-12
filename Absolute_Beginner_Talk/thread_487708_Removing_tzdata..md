---
title: "Removing tzdata."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-29
I am having a problem while installing libc6. It is having problems with tzdata. I ve heard that removing it would do no harm. Could someone post how to remove tzdata. I am not an expert in the terminal and give me the code I have to type in the terminal. I use kubuntu 7.04 and it doesnt allow me to install  libc6. Please help me.

---

### Post by limbourg31 on 2007-06-29
I'm in ubuntu but i guess that the command is still sudo apt-get remove tzdata, if that doesn't work you can always try to remove it in the kubuntu equivalent of synaptic (adept isn't it?) could you post the output when you try to install libc6 and remove tzdata?

---

### Post by Rabindranath on 2007-06-30
I tried updating tzdata with the new one and then installed libc6. It worked fine then. Thank You.

---

### Post by W8eR_CZech on 2007-10-17
Could you please write a command for updating program. Also a version please, because i'm offline. Finally, how can I find out which package is the newest? Thanx

---

### Post by Rabindranath on 2007-10-18
I am not good in the terminal. I downloaded it in windows and installed just by right clicking it and opened with the debian package installer. 
[http://packages.debian.org/etch/tzdata/all/download](http://packages.debian.org/etch/tzdata/all/download)                   ( This is the latest stable version, I think. The one I used is tzdata_2007f-9_all )
       Try the above link or just Google it. 
Sorry for the late reply...

---

### Post by W8eR_CZech on 2007-10-18
thx for the reply, problem solved. More problems coming with ubuntu 7.10

---

### Post by freed0m on 2007-10-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/125349](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/125349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This can help too.

Go to -> System -> Administration -> Time and Date -> and change the time zone to America/Phoenix.
Then reinstall tzdata from Synaptic. Or apt-get -f install and so on.

Cheers

---

