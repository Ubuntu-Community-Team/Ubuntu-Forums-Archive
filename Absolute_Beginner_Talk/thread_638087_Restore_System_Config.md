---
title: "Restore System Config"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by gsub on 2007-12-11
Hi: 

I managed to get my system to just the way I like it - in terms of appearance and functionality, and then had to reinstall gutsy.

Is there any way I could have backed up the following for restoration:

1. default font size/effects/etc.
2. keyboard shortcuts - changed using gconf-editor

Many thanks.

---

### Post by taurus on 2007-12-11
You could backup your $HOME directory.

---

### Post by PeterJS on 2007-12-11
The easiest way would be to back up you're home directory, especially the hidden directories, to another disk. And then copy everything back after you've got the new install done. Most of those settings are stored in the hidden directories and files in your home directory.

---

### Post by Dr Small on 2007-12-11
Greetings,
Here is a script that I wrote that was created for this purpose:
[http://php.8ez.com/drsmall/blog/?p=166](http://php.8ez.com/drsmall/blog/?p=166)

Dr Small

---

### Post by syxbit on 2007-12-27
i'd like to know the actual locations for some of these things, as often the reason i'm reinstalling is cause i've messed something up :)
restoring the messup wouldn't help

---

### Post by taurus on 2007-12-27
Most if not all of them are in /etc.

---

### Post by dcstar on 2007-12-27
> **gsub said:**
> Hi: 

I managed to get my system to just the way I like it - in terms of appearance and functionality, and then had to reinstall gutsy.

Is there any way I could have backed up the following for restoration:

1. default font size/effects/etc.
2. keyboard shortcuts - changed using gconf-editor

Many thanks.

I find having a separate /home partition keeps a lot of customisation intact when I reinstall/install new versions.

Basically doing this keep all you user data isolated from the various versions of Linux that you can have on your system (a forum search should provided detailed info on how to set up a separate /home partition).

---

### Post by syxbit on 2007-12-27
> **taurus said:**
> Most if not all of them are in /etc.

surely they're part of your profile in /home/username/

---

### Post by maybeway36 on 2007-12-27
Anything specific to your user is ~/.something
System-wide settigns are /etc/something

---

### Post by taurus on 2007-12-27
> **syxbit said:**
> surely they're part of your profile in /home/username/

Personal settings are in $HOME and system settings are in /etc.

---

