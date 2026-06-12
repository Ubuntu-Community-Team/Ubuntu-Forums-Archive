---
title: "Where and how to install DOOM"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by cmbnd10 on 2008-01-18
I was curious on where to find and how to install and play the first DOOM game on Fluxbuntu. Does anyone know?

---

### Post by Epic Plecostomus on 2008-01-18
I will second this.  I too would like to know.

---

### Post by CCNA_student on 2008-01-18
You can get LxDoom from APT. Just type that into search and it should come up. Although I was unable to get it to work properly(sound, but no video). More information can be found here at [http://www.teamtnt.com](http://www.teamtnt.com). I hope you can get it to run.

       Sin Cere,

       CCNA

---

### Post by cmbnd10 on 2008-01-18
> **CCNA_student said:**
> You can get LxDoom from APT. Just type that into search and it should come up. Although I was unable to get it to work properly(sound, but no video). More information can be found here at [http://www.teamtnt.com](http://www.teamtnt.com). I hope you can get it to run.

       Sin Cere,

       CCNA

I can't seem to get lxdoom. The website has nothing about any sort of linux/unix system, and the internet search doesnt really have anything from what i have seen.

---

### Post by CCNA_student on 2008-01-18
When I said go to APT, I meant the Add/Remove thing. Type in LxDoom into that and see what happens.

---

### Post by eolson on 2008-01-18
Just do a search on lxdoom in add/remove,  it's there.

---

### Post by cmbnd10 on 2008-01-18
Sorry I am being such a bother, I suck at this, but do you mean aptitude? That seems to be an add/remove program.

I tried to search in there, but it seems that it is only looking in my computer. I can tell I am doing something very wrong.

---

### Post by CCNA_student on 2008-01-18
Is this the thing that you are looking at? Did you select to have all applications available?

---

### Post by init1 on 2008-01-18
> **cmbnd10 said:**
> Sorry I am being such a bother, I suck at this, but do you mean aptitude? That seems to be an add/remove program.

I tried to search in there, but it seems that it is only looking in my computer. I can tell I am doing something very wrong.
```

sudo apt-get install lxdoom

```
Another option is
```

sudo apt-get install prboom

```

---

### Post by cmbnd10 on 2008-01-18
> **CCNA_student said:**
> Is this the thing that you are looking at? Did you select to have all applications available?

Okay, I opened synaptic, because mine looks like a watered down version of what you had.

I typed in "lxdoom" and it came up on the sidebar. I clicked it and pressed "reload" and this message came up.

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release: Unknown error executing gpgv

---

### Post by CCNA_student on 2008-01-18
And it would not let you do anything? Could you post a screenshot of what was happening.

---

### Post by cmbnd10 on 2008-01-18
Okay,. I just typed in that code and it looks like doom is installed.

How would I go about playing it now?

---

### Post by cmbnd10 on 2008-01-18
Bump.


It is on my menu list when you right click the screen, but when you click it, nothing happens.


HELP!

---

### Post by cmbnd10 on 2008-01-19
found out that I am missing DOOM1.WAD

Apparently it needs to go into the /usr/games folder

Where can I find that and how do I install it?

---

### Post by doorknob60 on 2008-01-19
Hmm you could google it or try reinstalling
```
sudo aptitude reinstall lxdoom
```

---

### Post by cmbnd10 on 2008-01-19
> **doorknob60 said:**
> Hmm you could google it or try reinstalling
```
sudo aptitude reinstall lxdoom
```

Now console cant find the folder

---

### Post by doorknob60 on 2008-01-19
What folder? Can you paste the error it gives?

EDIT: I'm going to bed so I can't help much more right now but the console output would be helpful to anyone trying to help you.

---

### Post by RomeReactor on 2008-01-19
> **cmbnd10 said:**
> found out that I am missing DOOM1.WAD

Apparently it needs to go into the /usr/games folder

Where can I find that and how do I install it?

Hi. To install it:
```
sudo aptitude install lxdoom-x11 lxdoom-sndserv doom-wad-shareware
```

---

