---
title: "Where is the konqueror located?"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Ruso on 2005-11-23
A bit nooby question, but I can't find where the konqueror is located.
I installed it using synaptic because the FireFox is pritty slow in my machine. And when I am trying to install Flash plugin it askes me to write the location of my web Browser, and I dont know where it is.

The command "sudo find / -name *konqueror*" did not helpe me :(

Can u say me the default location of it?

Thank you.

---

### Post by xelink on 2005-11-23
use kubuntu insteed of ubuntu, konqueror is KDE based if I am nto mistaken... as I have said ebfore, i could be wrong I am still new to the entire linux deal but...

---

### Post by mcmillan on 2005-11-23
My guess would be that it would end up in /usr/bin/konqueror, for the actual command to run it. Stuff about plugins may need to go in the library folders, which would probably be a folder in /usr/lib. To make sure though you can try typing
whereis konqueror
It should tell you where anything with the name konqueror is.

---

### Post by Ruso on 2005-11-23
Still can not install the flash plugin :(

I dont have any directory under /usr/lib that relies to konqueror. I tried to install the plugin to the /usr/lib/kde3, but obviusly it did not work.

The /usr/bin/konqueror is not a directory and the "stupid" instalation programs wants the direcory. :(

Any1 knows??

---

### Post by malegria on 2005-11-23
1. Please check for typos & grammatical errors  before you post, it makes your problem much easier to decifer.

2. You have to install Konqueror. Open a terminal and type this:

sudo apt-get install konqueror libflash-mozplugin

PROBLEM SO EASILY SOLVED!!!

---

### Post by Ruso on 2005-11-23
> 
1. Please check for typos & grammatical errors before you post, it makes your problem much easier to decifer.

Easy to say, difficult to do assuming that english is my 3rd language.

> 
sudo apt-get install konqueror libflash-mozplugin

PROBLEM SO EASILY SOLVED!!!

I installed this library, but I still have the same error while trying to access some sites.

"No plugin found for Shockwave Flash Media"
:(

---

