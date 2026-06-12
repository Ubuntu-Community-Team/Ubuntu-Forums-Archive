---
title: "Can´t move anything in ¨file system¨"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by flippykid on 2007-11-27
I don´t know why but I can´t move anything in the folder called file system, the place with all the stuff like /usr/ and stuff, I want to move something there but I can´t seem to move anything around in there. The main reason why I want to do this is because someone said that if you move a few files to the firefox/plugins location the flash player will work, but I can´t move anything yet, and this command line stuff is super confusing. I don´t get a second of it.

---

### Post by Dr Small on 2007-11-27
You either have to use [Sudo]("https://help.ubuntu.com/community/RootSudo") or login to nautilus as root.

---

### Post by flippykid on 2007-11-27
alright, i like the gksudo nautilus way, but is there any way to make it permenent? so that every time i open this window i can always move stuff.

---

### Post by PeterJS on 2007-11-27
There is, but you really don't want to do that. The changes that would allow a user account unlimited access to the file system would also completely undermine the security of the system. Check out the Ubuntu Security guide over in Servers and Security for more info:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by oldos2er on 2007-11-27
I don't recall having to move any files around to get Flash working in Firefox. I'd be very careful moving files in /usr/* .
 Make sure you've got libflash-mozplugin installed.

---

