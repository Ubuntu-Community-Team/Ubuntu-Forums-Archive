---
title: "*Warning* Absolute beginner"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Siffan on 2006-08-01
So finally I decided to go with a "real" Linux server. I went for Ubuntu and installed the LAMP part following [this guide]("http://www.howtoforge.com/lamp_installation_ubuntu6.06").

It all went well. I needed to set up the route manually, but that shold be okay. Now being a total noob and never tried this before I figured I needed a GUI and typed in the command "sudo apt-get update" followed by "sudo apt-get install ubuntu-desktop"

Both commands gave me errors like: Couldn't find any name or package whose name or description matched "Ubuntu-desktop"

And error followed by some Danish words and some url's. I must admit I'm totally lost, but I really mean it this time I want to try this out ](*,)

---

### Post by reacocard on 2006-08-01
Did you type it in all lower-case? Linux is case sensitive. Package names are always lower-case.

---

### Post by T700 on 2006-08-01
1.  Welcome to the forum!

2.  Using clear, descriptive, titles will always get more eyeballs on your problem and get you better answers.

Paul

---

### Post by Ozitraveller on 2006-08-01
Can you be more specific about the errors?

Maybe the repos are down?

---

### Post by wildseven on 2006-08-02
did you un-comment your repositories?
try 
```
gksudo gedit /etc/apt/sources.list
```
take out the '#' infront of the lines that start with 'deb'
save and close it.

then do
```
sudo aptitude update
```
```
sudo aptitude upgrade
```
```
sudp aptitude install ubuntu-desktop
```

hope this helps.

---

### Post by Arisna on 2006-08-02
You'll have to use

```
sudo nano /etc/apt/sources.list
```

to edit that file because you currently have no graphical environment.  Navigate with arrow keys, save with Ctrl-O.

---

### Post by Arisna on 2006-08-02
You'll have to use

```
sudo nano /etc/apt/sources.list
```

to edit that file because you currently have no graphical environment.  Navigate with arrow keys, save with Ctrl-O.

---

### Post by wildseven on 2006-08-02
> **Arisna said:**
> You'll have to use

```
sudo nano /etc/apt/sources.list
```

to edit that file because you currently have no graphical environment.  Navigate with arrow keys, save with Ctrl-O.


wo0ps, he is correct lol. i forgot you have no GUI. sorry heh~

---

### Post by Siffan on 2006-08-02
> **wildseven said:**
> did you un-comment your repositories?
try 
```
gksudo gedit /etc/apt/sources.list
```
take out the '#' infront of the lines that start with 'deb'
save and close it.

then do
```
sudo aptitude update
```
```
sudo aptitude upgrade
```
```
sudp aptitude install ubuntu-desktop
```

hope this helps.

First of all thank you very much for all your help and this goes out to everybody.

I tried the above using this
```
sudo nano /etc/apt/sources.list
```

But still no go. I will try to translate the errors I get using
```
sudo aptitude update
```
The errors I get is in Danish, but here's my attemt to translate them:
Error hhtp://security.ubuntu.com dapper-security Release.gpg
Temporary error ot translating the name 'security.ubuntu.com'
Couldn't get [http://dk.archive.ubuntu.com/ubuntu/dists/dapper/release.gpg](http://dk.archive.ubuntu.com/ubuntu/dists/dapper/release.gpg)

There's a lot of there with different urls and ind the end it writes "some index files could not be downloaded they are ignored or the old ones is used instead.


Still I'm lost :roll:

---

### Post by wildseven on 2006-08-02
hey, the inxex problem i kinda had similar when i first installed ubuntu. when u nano sources.list do u see something that says cd? if u do put a '#' infront of it because it might be using the repositories from the cd only and not allowing you to update the new online repositories. I'm not a pro but give it a shot. Hopefully someone more experienced will read this.

hope this helps.

---

### Post by Siffan on 2006-08-02
> **wildseven said:**
> hey, the inxex problem i kinda had similar when i first installed ubuntu. when u nano sources.list do u see something that says cd? if u do put a '#' infront of it because it might be using the repositories from the cd only and not allowing you to update the new online repositories. I'm not a pro but give it a shot. Hopefully someone more experienced will read this.

hope this helps.

2 lines said cd I put a # in front of them but still a no go ](*,) 
But still.... thank you very much for trying to help a real noob

---

