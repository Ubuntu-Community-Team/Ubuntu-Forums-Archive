---
title: "Can ndiswrapper work with a Live CD?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Hacked.Alias on 2006-12-15
Hey, I've used Ubuntu a couple of times via a live CD, but I haven't been able to browse the web. My friend told me about ndiswrapper but I'm not sure how to use it and if it would work when I am using a live CD.


Thanks,

-ha

---

### Post by macogw on 2006-12-15
It should work, but you'd have to reconfigure every time you booted from the cd.

---

### Post by Hacked.Alias on 2006-12-15
How would I configure it? I'm sorry, but I'm completely lost at this subject.

---

### Post by aysiu on 2006-12-15
*ndiswrapper-utils* is on both the Desktop ("live") and Alternate CDs. Paste these commands into the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by Hacked.Alias on 2006-12-15
> **aysiu said:**
> *ndiswrapper-utils* is on both the Desktop ("live") and Alternate CDs. Paste these commands into the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

Whoa, so just to be sure, Save the file onto my thumbdrive, load LIVE paste ndiswrapper onto my desktop. Open up terminal and run the command? 

Im sorry, but I'm a total thickhead and I have to be sure to get every last detail to a tee.

---

### Post by macogw on 2006-12-15
while you're in the live cd, type "sudo apt-cdrom add" into the terminal and hit "enter".  then type the second line and hit enter. then type the third line and hit enter. then do all the "here's the windows driver, moosh with ndiswrapper, ta-da! stuff--and you have to do this each time you boot up the live cd because the cd doesnt know to save the info

---

### Post by Hacked.Alias on 2006-12-15
Allright, I know I'm being a pest, but so I just paste the Icon on the desktop and type that stuff in the terminal and I should be fine?

---

### Post by aysiu on 2006-12-15
To be honest, I'm not sure how using the CD as a repository works while you're actually using the CD to run the live session, too. I know that once you install Ubuntu you can use the CD as a repository. You're welcome to try it, though--worst that could happen is you get an error telling you you can't add the CD as repository.

The first command says, "Hey, Ubuntu, I want to get some software off the CD. Is that cool?"

The second command says, "Okay. Now that you've approved the CD as a software source, what the hell's on that CD anyway?"

The third command says, "Now that you know what's on there, can you install *ndiswrapper* from the CD for me? Thanks."

---

### Post by aysiu on 2006-12-15
> **Hacked.Alias said:**
> Allright, I know I'm being a pest, but so I just paste the Icon on the desktop and type that stuff in the terminal and I should be fine? I'm not sure I know what you mean about the icon on the desktop, but you should paste into the terminal the commands I gave you--retyping will take too long and leave more room for error.

That just gets *ndiswrapper* installed. I have no idea how to use it (I don't have wireless).

---

### Post by macogw on 2006-12-15
> **aysiu said:**
> I'm not sure I know what you mean about the icon on the desktop, but you should paste into the terminal the commands I gave you--retyping will take too long and leave more room for error.

That just gets *ndiswrapper* installed. I have no idea how to use it (I don't have wireless).

He/she can't paste.  They're using two different computers.  One has internet access.  One has Ubuntu on a live cd.

---

### Post by Hacked.Alias on 2006-12-15
I understand what you're saying, but you see, I dont want to install Ubuntu. 

So instead of installing it, loading a CD and typing the script; is there a way where I load the live cd but have ndiswrapper on my thumbdrive?

EDIT
And actually, Im using one computer. My main OS is XP (yes I know) and I'm just stepping into the linux waters, so I dont want to install anything yet, thats why I use the live cd.

---

### Post by macogw on 2006-12-15
> **Hacked.Alias said:**
> I understand what you're saying, but you see, I dont want to install Ubuntu. 

So instead of installing it, loading a CD and typing the script; is there a way where I load the live cd but have ndiswrapper on my thumbdrive?
You can install ndiswrapper without installing Ubuntu. It'll just be a virtual install.  The installation of ndiswrapper will go away when you unload the Ubuntu cd.  It's only sort of pretending Ubuntu and ndiswrapper are even there.

I can't help on the thumbdrive thing, sorry.

---

### Post by aysiu on 2006-12-15
> **macogw said:**
> He/she can't paste.  They're using two different computers.  One has internet access.  One has Ubuntu on a live cd.
Doh! You're right. I'm a dunce.

Yes, retyping is necessary in this case.

---

### Post by aysiu on 2006-12-15
> **macogw said:**
> You can install ndiswrapper without installing Ubuntu. It'll just be a virtual install.  The installation of ndiswrapper will go away when you unload the Ubuntu cd.  It's only sort of pretending Ubuntu and ndiswrapper are even there.

I can't help on the thumbdrive thing, sorry.
To be more precise, the program gets "installed" to your RAM. Once you reboot, your RAM is, for all practical purposes, cleared.

---

### Post by Hacked.Alias on 2006-12-15
> **macogw said:**
> You can install ndiswrapper without installing Ubuntu. It'll just be a virtual install.  The installation of ndiswrapper will go away when you unload the Ubuntu cd.  It's only sort of pretending Ubuntu and ndiswrapper are even there.

I can't help on the thumbdrive thing, sorry.


Ah well, I guess I'll be without internet :-| 

thanks for the help anyway.

---

### Post by macogw on 2006-12-15
Oh you can get internet just fine, just have to get used to a little routine that you do on each boot

---

### Post by aysiu on 2006-12-15
> **macogw said:**
> Oh you can get internet just fine, just have to get used to a little routine that you do on each boot
Or create a script that you can run after you boot the live CD session.

---

### Post by macogw on 2006-12-15
oh yeah that would work....it just requires knowing how to do shell scripting...yeah, no clue

---

### Post by Hacked.Alias on 2006-12-16
If I were to reconfigure that code you gave me aysui 

> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils

if I were to make it 

> sudo apt-e-drive add
sudo aptitude update
sudo aptitude install ndiswrapper-utils

or something like that, do you think it would work? (I'm trying to install ndiswrapper from a thumbdrive to a live cd)

---

### Post by aysiu on 2006-12-16
What's *apt-e-drive*?

By the way, I don't know why you need *ndiswrapper* on a thumb drive. It's already **on** the live CD, which is why we gave the command *sudo apt-cdrom add*--to add the live CD as a repository source.

---

