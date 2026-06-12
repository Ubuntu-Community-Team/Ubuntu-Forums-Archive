---
title: "Apache in Ubuntu"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-01-14
I have Apache installed, it is running on port 80.
I am a complete noob to apache, I didn't even know I had it installed.
I'm wanting to change the default local server location so that it hosts something other than the default apache html file. I looked on Apache's site, and saw mention of the command httpd, but Ubuntu is not recognizing such a command.

Any suggestions?

---

### Post by jonny on 2007-01-14
The default web server root on ubuntu is /var/www and Apache's configuration files are in /etc/apache2.  Note that Ubuntu splits the configuration files into a number of smaller parts, so you might need to adapt instructions written for Windows, OSX or other Linux / Unix flavours.

---

### Post by SavageFreedom on 2007-01-14
> **jonny said:**
> The default web server root on ubuntu is /var/www and Apache's configuration files are in /etc/apache2.  Note that Ubuntu splits the configuration files into a number of smaller parts, so you might need to adapt instructions written for Windows, OSX or other Linux / Unix flavours.

Thanks. That was actually my first guess, but I wasn't sure. I'll test it out. :)

---

### Post by rabid9797 on 2007-01-14
if you already have a folder architecture setup with the files where you need them and such and don't want to move everything, you should consider doing this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)

---

