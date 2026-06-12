---
title: "How do I install Steam + Wine?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Johnson on 2007-08-09
I wonder how can I install Wine and Steam?

Do I do this? sudo apt-get install wine?
Or, and? :( :( :(

---

### Post by wormser on 2007-08-09
> **Johnson said:**
> I wonder how can I install Wine and Steam?

Do I do this? sudo apt-get install wine?
Or, and? :( :( :(

Yes

```
sudo apt-get install wine steam
```

---

### Post by Rocket2DMn on 2007-08-09
I suggest getting wine from the repositories, then following this guide:
[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)
You can ignore the first parts about getting/installing wine, but start at section 2.3 which is about getting the tahoma font.  Part 3 can also be skipped.

---

### Post by jake16424 on 2007-08-09
> **wormser said:**
> Yes

```
sudo apt-get install wine steam
```

where do you people get those command lines? ive been a windows user, and i just started seriously hating it, with all possible fibers of my being, now i am trying to become a full ubuntu\linux user, as my windows, hell, ive formatted so many times cause it gets bloated and laggy,, ubuntu, is retard fast,, i love it.. but i need to know where you guys get those command lines>??

i mean, if i say, sudo apt-get turkey sandwich, will one come out of my disk drive? ,, ok so not that but,, still where do you get your knowledge from?? O_O :confused:

---

### Post by jake16424 on 2007-08-09
ok, assuming that command works, it installs, now, wil you be able to play half life 2? and counter strike? or am i better to leave my windows hard drive for windows, and use ubuntu, for every day stuff, and hit windows when i want to download media?

---

### Post by Rocket2DMn on 2007-08-09
I don't think you can install steam in that command, just wine.  Run
```
sudo apt-get install wine
``` and it will install wine on your computer.  Then follow the guide I gave above as I suggested.
FYI: "sudo" gives you root privileges so you can change the system - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
apt-get is a command line install program - [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)
More info on installing: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020) (very detailed)

---

### Post by Johnson on 2007-08-09
Installed Steam, problem when I'm at the Steam login part screen, cannot see nothing.

No writng, just colour of the program.:confused::(

---

### Post by MenZa on 2007-08-09
This is because you're missing the Tahoma font. Since it's copyrighted (to my knowledge), I won't like it from here, but find the Tahoma font in the file type TTF, and copy it to /usr/share/fonts/truetype, then restart X. (CTRL+ALT+Backspace). And yes, you will be able to play Half-Life 2 and Counter-Strike, and Counter-Strike: Source and Day of Defeat: Source. I've run all these games with decent results, but I have felt quite a drop in FPS from Windows (Windows = 100-120fps, Wine = 60-80fps).

---

### Post by jake16424 on 2007-08-09
> **wormser said:**
> Yes

```
sudo apt-get install wine steam
```

Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
jacob@jacob-desktop:~$

---

### Post by Rocket2DMn on 2007-08-09
Wait, what was that I mentioned earlier?  Oh yeah!
> **Rocket2DMn said:**
> You can ignore the first parts about getting/installing wine, but start at section 2.3 which is about getting the tahoma font.
:)
I'm just playing with you, but FYI: linux doesn't come with a lot of windows fonts installed, so you need to add it manually (since steam relies on it).  That guide I gave above tells you how to do it correctly.
Good luck.

---

### Post by jake16424 on 2007-08-09
> **MenZa said:**
> This is because you're missing the Tahoma font. Since it's copyrighted (to my knowledge), I won't like it from here, but find the Tahoma font in the file type TTF, and copy it to /usr/share/fonts/truetype, then restart X. (CTRL+ALT+Backspace). And yes, you will be able to play Half-Life 2 and Counter-Strike, and Counter-Strike: Source and Day of Defeat: Source. I've run all these games with decent results, but I have felt quite a drop in FPS from Windows (Windows = 100-120fps, Wine = 60-80fps).

ok, now how do i get wine to install>? this is what i got after a bunch of stuff came up 
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
jacob@jacob-desktop:~$


after i get all that good stuff in there. how do i use it? where did it run away to?

do i then after all this is done with,, install hl2 from my disk?

---

### Post by Rocket2DMn on 2007-08-09
> **jake16424 said:**
> Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
jacob@jacob-desktop:~$

OK, that's a simple fix, you just need to enable the Universe repository.  Have a look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
and here: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by MenZa on 2007-08-09
> **Rocket2DMn said:**
> OK, that's a simple fix, you just need to enable the Universe repository.  Have a look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
and here: [https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Actually, adding the [Wine repository](http://www.winehq.org/site/download-deb) might be better; I know some of the releases have been a bit... screwy with Steam:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update && sudo apt-get install wine

```

Et vóila!

---

### Post by Rocket2DMn on 2007-08-09
> **MenZa said:**
> Actually, adding the [Wine repository](http://www.winehq.org/site/download-deb) might be better; I know some of the releases have been a bit... screwy with Steam:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update && sudo apt-get install wine

```

Et vóila!

That is explained in the first link 
:lolflag:

---

### Post by MenZa on 2007-08-09
Meh. Well, it's here now ;)

---

### Post by jake16424 on 2007-08-09
> **Rocket2DMn said:**
> That is explained in the first link 
:lolflag:



god help me,, im lost,, idk what the hell todo,, how do i activate repositories? and,, O_O wow...

---

### Post by MenZa on 2007-08-09
> **jake16424 said:**
> god help me,, im lost,, idk what the hell todo,, how do i activate repositories? and,, O_O wow...

Just look at my post above, and enter the commands in the box one by one. (one line at a time).

---

### Post by jake16424 on 2007-08-09
> **jake16424 said:**
> god help me,, im lost,, idk what the hell todo,, how do i activate repositories? and,, O_O wow...



never mind, im running 64bit, so it wont work no matter what, grrrrr

---

### Post by MenZa on 2007-08-09
> **jake16424 said:**
> never mind, im running 64bit, so it wont work no matter what, grrrrr

Well, you could build Wine yourself, but I'm not sure if Steam would run. Sorry. :/

---

### Post by Johnson on 2007-08-09
Man there is so much stuff here, I'm confused. What am I suppose to do again?

I did everything, it worked. I can't see any Wine programs or NOTHING!

---

### Post by MenZa on 2007-08-09
> **Johnson said:**
> Man there is so much stuff here, I'm confused. What am I suppose to do again?

I did everything, it worked. I can't see any Wine programs or NOTHING!

Err, it appears there we two people posting in here all along. Very confusing. What version of Ubuntu are you running? 32- or 64 bit?

---

### Post by jake16424 on 2007-08-09
> **MenZa said:**
> Well, you could build Wine yourself, but I'm not sure if Steam would run. Sorry. :/

I GOT SOMETHING TO INSTALL O_O OMG,, and, no i couldnt build wine myself as im not a programmer, but after i go to colllege i probably will be, for firewalls, and antiviruses, so more than likely, ill make some kicking stuff if ubuntu is stil around.

---

### Post by Johnson on 2007-08-09
I got Ubuntu 7.04 (32bit) normal version.

I was looking for a clean looking program that help me play Steam games, like Counter-Strike Source.

And also maybe launch up Windows XP wanna-be thing too, where I can use Adobe programs?

---

### Post by MenZa on 2007-08-09
> **jake16424 said:**
> I GOT SOMETHING TO INSTALL O_O OMG,, and, no i couldnt build wine myself as im not a programmer, but after i go to colllege i probably will be, for firewalls, and antiviruses, so more than likely, ill make some kicking stuff if ubuntu is stil around.

Hah; you don't have to be a programmer to compile an application from source: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware).

> **Johnson said:**
> I got Ubuntu 7.04 (32bit) normal version.

I was looking for a clean looking program that help me play Steam games, like Counter-Strike Source.

And also maybe launch up Windows XP wanna-be thing too, where I can use Adobe programs?

You can install Steam by reading through this thread and doing the necessary steps.

In regards to the Adobe thing.... it's possible, but it is a slightly tricky process: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization).

---

### Post by mitchellthegreat on 2007-12-21
I installed steam only cuz i wanted it to play gmod and i didn't know that they had it so i got excited and ran the command in Konsole (I'm in kubuntu). I installed and it told me that i needed mysql-server. so i ran this to get rid of steam.

```
sudo apt-get remove steam
```then i ran this to get rid of the rest of it

```
sudo apt-get autoremove steam
```

now i'm installing mysql-server like it told me too and i'm going to reinstall steam.

```
sudo apt-get install mysql-server
```

[CENTER]*         *          *          *
[/CENTER]


now what should i do to get to steam?

---

