---
title: "first time boot questions for nebinstein"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by danman on 2008-03-21
finally got the install down, and now I don't know what is going on.  I am on a black screen that is describing sudo. I have tried every command I can think of to get past this screen and get into the GUI with no luck. I have tried to add users here and nothing. Every time I hit enter after typing a command I get "cannot write to file xyz"   I have 7.10 server and I'm lost please help.

---

### Post by Oldsoldier2003 on 2008-03-21
> **danman said:**
> finally got the install down, and now I don't know what is going on.  I am on a black screen that is describing sudo. I have tried every command I can think of to get past this screen and get into the GUI with no luck. I have tried to add users here and nothing. Every time I hit enter after typing a command I get "cannot write to file xyz"   I have 7.10 server and I'm lost please help.

The Ubuntu server does not install with a gui by default since its a server. If you want to install the gui you can do 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by wolfen69 on 2008-03-21
the server edition does not come with a gui. you will need to install that.
first you would need xorg:
```
sudo apt-get update
```
```
sudo apt-get install xorg
```
next, what kind of desktop environment do you want? kde? gnome? xfce? or other? basic gui? with apps?

---

### Post by wolfen69 on 2008-03-21
> **Oldsoldier2003 said:**
> The Ubuntu server does not install with a gui by default since its a server. If you want to install the gui you can do 

```
sudo apt-get install ubuntu-desktop
```

doing that will give you the full suite of ubuntu apps. perhaps this is not what you want, as you are running a server edition.

---

### Post by Oldsoldier2003 on 2008-03-21
> **wolfen69 said:**
> the server edition does not come with a gui. you will need to install that.
first you would need xorg:
```
sudo apt-get update
```
```
sudo apt-get install xorg
```
next, what kind of desktop environment do you want? kde? gnome? xfce? or other? basic gui? with apps?

Whoops I forgot that xorg isnt part of the desktop meta packages. good catch.

---

### Post by danman on 2008-03-21
I'm not sure what type of environment I want to be honest. I plan on using the box for software development.  As for the code you posted. I tried it but nothing same "cannot write to" error. Do I need to have a cd in the drive with that file on it, is so where do I get it? I'm thinking that I may as well install the full monty on the apps I can always take them off if need be.

---

