---
title: "Amarok Install prob / sources list"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-04-19
Hello 

I am having problems installing Amarok. I am of course a newbie, this is what I have done.

I have Enabled universe and multiverse and I also ran gst-register0.8. I have followed the install instructions on the Amarok site, but when I get the apt-get update, or apt-get install amarok I get "cannot lock some file error".

I have found some info that indicates I need to edit my sources.list file. I can only find a sources.list.save file. I cannot edit the file in the GUI mode, its read only. I can edit the file in using the terminal but I dont know how to save it properly an keep getting errors that there are 2 files something to do with swap files.](*,) 

Please help

---

### Post by uantuzri on 2006-04-19
Here you have information:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

It is always useful looking for information at [https://wiki.ubuntu.com](https://wiki.ubuntu.com) using the search box. Once you've done it, tell us if it worked.

---

### Post by rubrboots on 2006-04-19
I have already enabled universe and multiverse, using that exact guide. There is more to the guide about adding "outside" and "non Ubuntu" repositories. Do I need to add these as well?

Thanx

---

### Post by uantuzri on 2006-04-19
No, you don't need them.

I'm not sure how to solve the problem, but try installing amarok via synaptic instead of via terminal. To do this, Sistem>Administration>Synaptic package manager. Click on search, write in amarok, and when the list appears, right click on amarok and amarok-engines and check to install. It will ask you if you want to install the needed dependencies, OK.

How newbie are you? I don't want to offend but remember writing sudo before the apt-get command to get root permissions.

---

### Post by aysiu on 2006-04-19
[QUOTE=rubrboots]There is more to the guide about adding "outside" and "non Ubuntu" repositories. Do I need to add these as well?[/QUOTE] I would never add non-Ubuntu repositories. It's a bad idea and can easily lead to system breakage.

---

### Post by rubrboots on 2006-04-19
Well it looks like I screwed up the sources list when I was trying to change it, because when I opened synaptic to try and install Amarok that way I got this message

> E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


How can I replace the original Sources list?

---

### Post by aysiu on 2006-04-19
[QUOTE=rubrboots]
How can I replace the original Sources list?[/QUOTE] Just follow these instructions: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by rubrboots on 2006-04-19
Sweeet! I finally have Amarok

Thanks uantuzri and aysiu. I got the sources list back, which allowed me to update. Then installed Amarok via Synaptic:p 

So am I right to say, that I can only edit textfiles by starting in the terminal and typing "sudo gedit directory/filename"

---

### Post by aysiu on 2006-04-19
[QUOTE=rubrboots]
So am I right to say, that I can only edit textfiles by starting in the terminal and typing "sudo gedit directory/filename"[/QUOTE] If it's not in /home/rubrboots, probably.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

