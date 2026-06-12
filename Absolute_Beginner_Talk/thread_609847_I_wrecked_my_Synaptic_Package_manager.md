---
title: "I wrecked my Synaptic Package manager"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-11
I wrecked my synaptic package manager somehow. Can I fix it without a reinstall?

---

### Post by creeco on 2007-11-11
Try opening a terminal, then write
```
sudo synaptic
```
and post the output of that command!

---

### Post by Maestro23 on 2007-11-11
> **bgast1 said:**
> I wrecked my synaptic package manager somehow. Can I fix it without a reinstall?

What were you doing when you "wrecked" it?  Any error messeages?  Thiis info will help us... help you.

---

### Post by jaybombalous on 2007-11-11
I am not sure but I think synaptic is just a front end for dpkg and aptitude. If thats the case then all u would need to do is re-install or re-configre synaptic. All the relevant information in the other apps will not be harmed.

I might be horribly wrong though.

---

### Post by creeco on 2007-11-11
> **jaybombalous said:**
> I am not sure but I think synaptic is just a front end for dpkg and aptitude. If thats the case then all u would need to do is re-install or re-configre synaptic. All the relevant information in the other apps will not be harmed.

I might be horribly wrong though.

Reinstalls doen't work in most cases, (unless he edited some files inside synaptics directory, which i REALLY doubt he did.)

---

### Post by bgast1 on 2007-11-11
Sorry it took so long to get back. What I wanted to do was get a package to unpack a .rar file  and somewhere along the line I screwed that up. Here is the error message that came up in the box when I try to go to Synaptic:

[PHP]E: Type 'N.B.' is not known on line 28 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/PHP]

Incidently this is the first time I ever tried to put something in a box, like I see you all put 'Code' in a box, how do you actually do that? I also don't know how to do what they are saying when they say to 'Go to the repository dialog to correct the problem.'

---

### Post by kwacka on 2007-11-11
check sources.list:- press ALT + F2 keys & type "gksudo gedit /etc/apt/sources.list" in the box.

You will find lines similar to "## N.B. software from this repository is ......"

ALL such lines must be preceded by a # (it stops the line being read & mis-interpreted as a reference)

Alternatively, delete all lines EXCEPT those that start with 'deb' or 'deb-src'.

---

### Post by kwacka on 2007-11-11
Second part of your question, when synaptic starts click on settings --> repositories & tick the boxes (under the various tabs) that you want synaptic/dpkg/apt to access.

---

### Post by bgast1 on 2007-11-11
> **kwacka said:**
> check sources.list:- press ALT + F2 keys & type "gksudo gedit /etc/apt/sources.list" in the box.

You will find lines similar to "## N.B. software from this repository is ......"

ALL such lines must be preceded by a # (it stops the line being read & mis-interpreted as a reference)

Alternatively, delete all lines EXCEPT those that start with 'deb' or 'deb-src'.

Then what do I do?  Nevermind. I just did what you asked me to do, went back to Synaptic, opened it up and it worked fine. Now, I need to find something to open a .rar file.

---

### Post by bgast1 on 2007-11-11
Did what I was asked to do. Solved the problem. Went to ask about how to deal with a .rar file, looked at some other threads before posting and installed rar unrar through a terminal and extracted the .rar file in question. Worked like a charm.

Thanks everyone for your help, this Ubuntu experience has been all positive. The only real bump in the road is my sound card, and there just isn't any support for it that I know of. 

Sound Blaster X-Fi Extreme Gamer.

---

