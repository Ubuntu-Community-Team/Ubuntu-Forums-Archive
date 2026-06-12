---
title: "[SOLVED] Installing cairo-dock - dependency is not satisfiable"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by apcfreak on 2008-02-01
I am installing cairo-dock on dapper using a deb from their website. When I try to run it, I get "Error: Dependency is not satisfiable: libgtk2.0-0" when I already have that package installed. Could anyone shed some light on the problem here?

---

### Post by Crumpets and Jam on 2008-02-01
> **apcfreak said:**
> I am installing cairo-dock on dapper using a deb from their website. When I try to run it, I get "Error: Dependency is not satisfiable: libgtk2.0-0" when I already have that package installed. Could anyone shed some light on the problem here?

Sorry, I don't have a solution, but I have a suggestion.

I would try [AWN]("http://en.wikipedia.org/wiki/Avant_Window_Navigator") (Avant Window Manager). It works much better in Ubuntu and is always being updated. Here is how to install AWN.

Open the Terminal and type

```
gksudo gedit /etc/apt/sources.list
```

At the very bottom of all these lines, press Enter/Return to make a new line and add these on individual lines.

```
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

```
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

Now open the terminal again. Type these followed by return after each line.

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc -O- | sudo apt-key add -
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get install avant-window-navigator-bzr
```

```
sudo apt-get install awn-core-applets-bzr
```

Installation of AWN is finished you can Customize AWN from AWM Manager which you can Access from System -> Preferences -> AWN Manager.

---

### Post by apcfreak on 2008-02-01
> **Crumpets and Jam said:**
> Sorry, I don't have a solution, but I have a suggestion.

I would try [AWN]("http://en.wikipedia.org/wiki/Avant_Window_Navigator") (Avant Window Manager). 

Thank you for your suggestion, but my current video card can't run compiz, which is required for it. :\

EDIT: Also, those instructions aren't for Dapper ;) thanks for the reply though.

---

### Post by Crumpets and Jam on 2008-02-01
> **apcfreak said:**
> Thank you for your suggestion, but my current video card can't run compiz, which is required for it. :\

EDIT: Also, those instructions aren't for Dapper ;) thanks for the reply though.

Oh dear, my mistake. Sorry.

---

### Post by apcfreak on 2008-02-02
Doing the daily bump.

---

