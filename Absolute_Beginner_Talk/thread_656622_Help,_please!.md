---
title: "Help, please!"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by wiredheat on 2008-01-02
World of Warcraft using wine. I've copied all of the files to a new directory, and this is the tutorial I'm using:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I'm at the part where I'm supposed to do this:

Start the installation by opening a terminal and running these commands:

cd /<path-to-directory>/
wine Installer.exe

This is where the location of the folder I copied the files to is:

/home/user/Desktop/WoW Install


This is what I've entered into the terminal so far, but it doesn't work:

:~$ cd /</home/user/Desktop/WoW Install>/
bash: /home/user/Desktop/WoW: No such file or directory
:~$ cd /<home/user/Desktop/WoW Install>/
bash: home/user/Desktop/WoW: No such file or directory
:~$ cd /home/user/Desktop/WoW Install/
bash: cd: /home/user/Desktop/WoW: No such file or directory
:~$ cd /home/user/Desktop/WoW Install
bash: cd: /home/user/Desktop/WoW: No such file or directory
:~$


What am I supposed to be typing? Help please! I'm fairly new to linux.

---

### Post by jken146 on 2008-01-02
You are meant to substitute the word "user" with your username.  You also don't need the <>.

You also need to escape the space in the path name.  Put a \ in front of the space or put the whole path in single quotes.

```
cd ~/Desktop/WoW\ Install
``` is what you want.  ~ means "my home directory".

---

