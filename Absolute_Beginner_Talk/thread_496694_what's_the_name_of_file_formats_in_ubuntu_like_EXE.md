---
title: "what's the name of file formats in ubuntu like EXE in windows?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by 3enith on 2007-07-09
what's the name of file formats in ubuntu like EXE in windows?:confused:

---

### Post by Raineer on 2007-07-09
Typically .sh (text-readable script file) or .bin for binary.  Although you'll also run into .pl for Python among a few others.

---

### Post by EndPerform on 2007-07-09
Or, there may not be an extension.  As a rule of thumb, most executables live in /usr/bin.  Linux doesn't depend on file extensions to know how to deal with files.

---

### Post by stalker145 on 2007-07-09
There's also the .deb (Debian) files that act much like Windows installation apps.

---

### Post by UnixAnt on 2007-07-09
Linux and other Unix/Unix-like OS's do not adhere to the Microsoft introduced 8.3 notation (8 char filenames, a dot, then 3 letter extension).

In Unix/Linux, everything is a file and can be manipulated depending on what flag has been set.  So for example, if I have a file called linux and the executable bit is set (the x part of rwx) then this file may be executed with ./linux (assuming you are in the same directory).

Likewise, if you have, say, a text file - there is absolutely no reason to label it mydocument.txt.  You can call it whatever you like.

To find out information about a file you come across whilst navigating via a shell, use the 'file' command:

file /etc/hosts

hosts:      ascii text

for example.

In short - you have very little restrictions in terms of what you may/may not call something ;)

---

### Post by reset3x on 2007-07-09
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-managing-file-types.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/getting-started-guide/s1-managing-file-types.html)

---

### Post by Wiebelhaus on 2007-07-09
> **stalker145 said:**
> There's also the .deb (Debian) files that act much like Windows installation apps.


which should be accepted as THE standard IMO. (*dodges face melting flame forged daggers of doom*)

---

### Post by UnixAnt on 2007-07-09
And if you come across an extension you really don't know, have a look at the database of file extensions:

[http://filext.com/]("http://filext.com/")

---

