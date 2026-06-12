---
title: "I cant install newest frostwire deb file"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-26
I keep getting this lou@c-67-163-247-106:~$ sudo apt-get install FrostWire-4.10.9-1.i586.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package FrostWire-4.10.9-1.i586.deb
Why? I even tried it in root is it because i have i386 kernal? and not i586?

---

### Post by taurus on 2006-03-26
Did you download the .deb package?  If you did, you have to use dpkg to install it...
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```

---

### Post by jwsawyer on 2006-03-27
[QUOTE=taurus]Did you download the .deb package?  If you did, you have to use dpkg to install it...
```

sudo dpkg -i FrostWire-4.10.9-1.i586.deb

```[/QUOTE]
I downloaded FrostWire, Installed it exactly as you said.  I find the Icon in Applications - Internet.  when I click on it nothing happens.  I checked all the files and it loaded okay, everything seems to be in the correct place.  I'm using Dapper upgraded to the latest build.

---

### Post by LanceM on 2006-03-27
I get the same thing. Install runs, icon shows up, click on the icon and nothing happens. Running from a terminal it looks like there is something wrong with the config:
```
lance@home:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
lance@home:~$

```

---

### Post by jrib on 2006-03-27
[QUOTE=LanceM]I get the same thing. Install runs, icon shows up, click on the icon and nothing happens. Running from a terminal it looks like there is something wrong with the config:
```
lance@home:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
lance@home:~$

```[/QUOTE]


please visit [https://wiki.ubuntu.com/FrostWireHowTo](https://wiki.ubuntu.com/FrostWireHowTo) and see the note concerning your error

---

### Post by LanceM on 2006-03-27
Found the problem. runFrost.sh is in the wrong format, known issue. Here is the fix:

[http://www.gnutellaforums.com/showthread.php?threadid=54814](http://www.gnutellaforums.com/showthread.php?threadid=54814)

---

