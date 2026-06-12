---
title: "A few tweaks and questions"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Solenoid on 2007-11-13
Hi, I'm a brand new egg in the Linux world... finally had some time to plan the partitions and actually do it. But there are some things I would like to change. To rename a file I have to right-click and select rename, in XP I was able to just click a second time on the file and voilà... how come I can't in Ubuntu?

I also have XP on another partition (for games), and I can see the ext3 partition of my stuff with some driver I downloaded. From Ubuntu /home seems clean, but in XP it's full of crap. I made an NFTS partition for XP (15GB), an ext3 for Ubuntu (8GB), another ext for my stuff (the biggest) and the 2GB swap partition... I thought my /home was ONLY for my stuff... but it's cluttered with all kinds of useless junk, like .config, .gnome... and my music, video and picture folders amongst these. I know it has something to do with settings, but can't they be in ONE folder, in the corner and not all over the place?

---

### Post by Inxsible on 2007-11-13
[COLOR=Red]DO NOT DO THAT !![/COLOR]

that will remove everything in your home folder !!

---

### Post by taurus on 2007-11-13
> **noodleremainsftw said:**
> ```
*********
```

type that in console

that should help unclutter your /home

What's the matter with you, dude?

---

### Post by Inxsible on 2007-11-13
> **noodleremainsftw said:**
> ```
sudo rm -rf ~/*
```type that in console

that should help unclutter your /homeWhy the hell are you giving wrong instructions, you miscreant !!! This is the third time today that I have seen this.

[COLOR=Red]Please anyone seeing instructions like this one, do not follow them.[/COLOR]

---

### Post by CatKiller on 2007-11-13
It's not really "useless junk" - those are all your settings. If you look at a Windows drive from Ubuntu, it's similarly full of "useless junk", but both operating systems are clever enough that they recognise their own settings, and don't show them to you unless you ask.

They **are** all in one folder, and not all over the place. It's called your Home folder. And it means that all of your settings don't need to affect other users, since they can't even see inside your Home folder.

---

### Post by Perpetual on 2007-11-13
Try pressing ctrl + h to disable showing hidden files.

---

### Post by CatKiller on 2007-11-13
> **Perpetual said:**
> Try pressing ctrl + h to disable showing hidden files.

It's not in Ubuntu that he's seeing the files (although he could toggle hidden files with Ctrl-H, as you say) but in Windows XP.

I must admit, I got similarly annoyed by the Recycler and System Volume Information directories that Windows insisted on plastering over my drives. I knew how to stop them showing up in Ubuntu though. But then Windows died, and I never quite got round to re-installing it. I never missed it.

---

### Post by Perpetual on 2007-11-13
> **CatKiller said:**
> It's not in Ubuntu that he's seeing the files (although he could toggle hidden files with Ctrl-H, as you say) but in Windows XP.

I must admit, I got similarly annoyed by the Recycler and System Volume Information directories that Windows insisted on plastering over my drives. I knew how to stop them showing up in Ubuntu though. But then Windows died, and I never quite got round to re-installing it. I never missed it.

Sorry, misread the OP's post.

---

### Post by oldos2er on 2007-11-13
Your .gnome, .config, etc. files aren't junk, they're your user configuration settings. In Linux, a dot preceding a file name indicates a hidden file; obviously Windows doesn't respect that. If you have a .config file for a program you no longer use, it would be safe to delete it. Other than that, I'd leave them alone.

---

### Post by Solenoid on 2007-11-13
Well the ~/* was kind of suspicious... so I didn't do it (wildcards are dangerous). I understand that the OS has to keep its settings, but why in my folder. Every OS does it, the most annoying is the OSX's .Trashes files it leaves EVERYWHERE. Anyway I'll go around and make the video, pictures and music folders in the document folder, replace them on the right and redirect XP's My Documents to the Ubuntu documents.

Thanks for the warning.

---

### Post by oldos2er on 2007-11-13
They're not the OS's settings, they're your user settings, that's why they're in your /home folder.

---

