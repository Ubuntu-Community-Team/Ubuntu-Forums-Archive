---
title: "Mapping Directories"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by Norrad on 2005-07-28
Hi everyone,

I need help with mapping directories. I have a second hard-drive which I have mounted as /storage
Now everytime I want to get files from there I have to browse the filesystem and scroll down till I find it. Is there anyway to map this directory to my Home folder, or create a shortcut in my Home directory to take me to it?

Oh yes, I also want to serve a website from my home directory. I have apache/mysql/php installed and working. How do I create a folder in my home directory that can contain my website?

Kind regards,
Norrad

---

### Post by heimo on 2005-07-28
[QUOTE=Norrad]Now everytime I want to get files from there I have to browse the filesystem and scroll down till I find it. Is there anyway to map this directory to my Home folder, or create a shortcut in my Home directory to take me to it?
[/QUOTE]

Symbolic link should do it. I don't know how it's done in GUI, but in terminal you use ln.

 ```
ln -s [source] [destination]
``` 
(see *man ln* for exact syntax)

Your other question: You need apache installed and configured. I don't remember if some specific directory under user home dirs are automaticly published, if it is, the directory is probably something like ~/public_html

Oh, see this:
[http://ubuntuforums.org/showthread.php?t=17453](http://ubuntuforums.org/showthread.php?t=17453)

---

