---
title: "having trouble installing games for windows on ubunu"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by stevebuntu on 2008-01-07
i currently installed ubuntu to my computer as i have been getting inceasingly upset with windows and i have found ubuntu so far much better and i was wondering if anyone can help me with a little problem i am having i want to install tiger woods 2004 on my comp but i am having some troubles       any help would be awesome......thanks

---

### Post by tech9 on 2008-01-07
you need a program called wine to install windows executables (games)

```
sudo apt-get install wine
```

configure/create c_drive in wine configuration manager

then 

```
wine /media/cdrom0/"name of exe install"
```

---

### Post by (((X))) on 2008-01-07
is that game made to play on linux?

---

### Post by ubername on 2008-01-07
Have you tried installing wine (Its a tool which allows windows applications to run in ubuntu)

Go to Synaptic Package manager (from your 'System' menu) and search for wine.

Also search for 'ubuntu wine' in a search engine of your choice.

Good luck.

---

### Post by aktiwers on 2008-01-07
You are aware that Windows games normally wont run very well on Linux?

Its a little like trying to play Playstation games on a Xbox.

But it is somehow possible with some games with the use of Wine or Cedega.

But as stated, not all games work sadly, as they are all written for Windows.

---

### Post by Perpetual on 2008-01-07
As said above, Wine is your only option.  [Here]("http://appdb.winehq.org/appbrowse.php?catId=0") is a good place to start to see what others were or were not able to run under Wine.  Otherwise, Google search may help you find something.

---

### Post by billgoldberg on 2008-01-07
> **tech9 said:**
> you need a program called wine to install windows executables (games)

```
sudo apt-get install wine
```

configure/create c_drive in wine configuration manager

then 

```
wine /media/cdrom0/"name of exe install"
```

This type of information is good but it's just scary for beginners.

---

### Post by lvleph on 2008-01-07
Might want to check the [url=http://wine-forum.org/]wine forums[/url for any help.

---

### Post by tech9 on 2008-01-07
> **billgoldberg said:**
> This type of information is good but it's just scary for beginners.

very true... sometimes I forget that I need to be specific about everything...

I guess launching terminal to put these commands in aren't a given then ;)

---

### Post by sub2007 on 2008-01-07
You wouldn't expect to be able to run Mac software on Windows and likewise you shouldn't expect to be able to run Windows software on Ubuntu. Wine is definitely a fantastic project and it is getting better and better with every release but it's far from perfect, in my opinion if you can get a Windows program running via Wine then it's a bonus rather than an expectation. If you want to play games then a dual boot is probably your best solution, for the only games that have run via Wine for me (and I only play a couple of games and don't play graphically any intensive games) they definitely don't run at native speed.

Maybe you could look at some of the native Linux games, you might find something you like: [http://ubuntuforums.org/showthread.php?t=653049](http://ubuntuforums.org/showthread.php?t=653049)

---

