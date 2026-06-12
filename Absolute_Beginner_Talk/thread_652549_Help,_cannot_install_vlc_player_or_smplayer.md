---
title: "Help, cannot install vlc player or smplayer"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by silent1977 on 2007-12-28
I try to install vlc player and smplayer in the ADD/REMOVE PROGRAM section but it's pop up said "CANNOT INSTALL "VLC"/CANNOT INSTALL SMPLAYER" BECAUSE THIS APPLICATION CONFLICTS WITH OTHER INSTALLED PROGRAM. TO INSTALL VLC THE CONFLICTING SOFTWARE MUST BE REMOVED FIRST. 

What I have to do? What kind of applcation i should remove? Sorry, I'm new with ubuntu. Kindly advice me. Thanks :):)

---

### Post by taurus on 2007-12-28
Close the Add/Remove window.  Then, open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```
Also, post your /etc/apt/sources.list too.

```
cat /etc/apt/sources.list
```

---

### Post by silent1977 on 2007-12-29
hey , thanks for your help.

I try to follow what you teach me. 

sudo apt-get update -- done!

but sudo apt-get install vlc -- shown BROKEN PACKAGES. :(:(

for cat /etc/apt/sources.list -- can't work

Pls Help. Thanks

---

### Post by CypherHackz on 2007-12-29
i install vlc from add/remove. go to applications > add/remove. make sure you select all applications. then filter vlc, check it, and install.

edit: why cat /etc/apt/sources.list? perhaps you put the wrong command. just open that file with text editor.

-cypher.

---

### Post by shshgn83 on 2008-01-07
Hi while installing vlc player I face below error

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
E: Broken packages


If I try to install packages mentioned in mailthread..I go into recursive loop to install dependent packages but end result doesnt insall VLC player.....

Can I get help on this...
I am not able to install any of the media packages to read CDs...

---

### Post by Tekno_Cowboy on 2008-01-07
Edit: This reply removed due to the temporary stupidity of the poster when posting it. lol.

---

