---
title: "Frostwire problem"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-10-17
Hi

I decided to try and install Frostwire this evening and downloaded the Ubuntu/Debian Package, then ran: 

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

It installs as follows:

```
Selecting previously deselected package frostwire.
(Reading database ... 72421 files and directories currently installed.)
Unpacking frostwire (from FrostWire-4.10.9-2.i586.deb) ...
Setting up frostwire (4.9.11) ...
caravel@caravel-desktop:~/Desktop$
```

I've intalled and reinstalled a few times and it makes no difference.  when I click the icon nothing happens at all, and I mean nothing.

---

### Post by igknighted on 2006-10-17
> **caravel said:**
> Hi

I decided to try and install Frostwire this evening and downloaded the Ubuntu/Debian Package, then ran: 

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

It installs as follows:

```
Selecting previously deselected package frostwire.
(Reading database ... 72421 files and directories currently installed.)
Unpacking frostwire (from FrostWire-4.10.9-2.i586.deb) ...
Setting up frostwire (4.9.11) ...
caravel@caravel-desktop:~/Desktop$
```

I've intalled and reinstalled a few times and it makes no difference.  when I click the icon nothing happens at all, and I mean nothing.

If you run it from the terminal what does it say?

EDIT:  Do you have java set up?  It appears to be java based so if you don't have it set up it wont work

---

### Post by caravel on 2006-10-17
```
./usr/bin/X11/frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
```

Oops indeed. It seems I don't have the JRE installed.  I'd better get on and install it.  Pity i didn't try it from the console first.  Thanks for putting me on the righ track. :redface:

---

### Post by caravel on 2006-10-20
Well i managed to install the J2RE and frostwire and got it all working after setting Sun Java as the default java.  The last things I've done is install the 686 kernel and firestarter, and that's working as well.  But I've seen mention of a K7 kernel but couldn't find it in synaptics.  Should I do: "sudo apt-get install linux-k7" (I'm at work, hence why I haven't tried it)?

---

