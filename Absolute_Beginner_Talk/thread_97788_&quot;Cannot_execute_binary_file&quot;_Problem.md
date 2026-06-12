---
title: "&quot;Cannot execute binary file&quot; Problem"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by yeti on 2005-12-01
Ok, so I installed Breezy last week on my iBook and thus far its been great-- loved the easy install.  This problem stumps me however.  It started yesterday when I tried to install Realplayer.  I chmodd'ed the file and tried to execute the binary, but it give me this error message: 

```
bash: ./RealPlayer10GOLD.bin: cannot execute binary file
```

I didnt think much of it, but today when I tried to install firefox 1.5 according to the howto on the wiki i got the same message: 

```
/opt/firefox/run-mozilla.sh: line 166: /opt/firefox/firefox-bin: cannot execute binary file
```

This one stumps me.  Any ideas?

---

### Post by teaker1s on 2005-12-01
try running with either gksudo or sudo in terminal as there is a permissions bug

---

### Post by yeti on 2005-12-01
That didnt solve it -- I ran it as sudo, but it just returned the same reply.  ls -l returned the following:

```
-rwxr-xr-x  1 yeti yeti 5789348 2005-12-01 12:50 ./RealPlayer10GOLD.bin

```

Any more ideas?

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=yeti]That didnt solve it -- I ran it as sudo, but it just returned the same reply.  ls -l returned the following:

```
-rwxr-xr-x  1 yeti yeti 5789348 2005-12-01 12:50 ./RealPlayer10GOLD.bin

```

Any more ideas?[/QUOTE]
Can you execute any binary files?  What about executable shell scripts?

---

### Post by yeti on 2005-12-02
I can activate many of the things in /usr/bin, however, of the two binaries that were put on my machine by neither synaptic or installation (firefox 1.5 and realplayer), I can run neither.  Im afraid that I am too much of a n00b :) to know how to check weather I can run executable shell scripts.

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=yeti]I can activate many of the things in /usr/bin, however, of the two binaries that were put on my machine by neither synaptic or installation (firefox 1.5 and realplayer), I can run neither.  Im afraid that I am too much of a n00b :) to know how to check weather I can run executable shell scripts.[/QUOTE]
Lots of the programs you run actually are shell scripts.  It may be that the binaries you have are corrupt in some way so they can't be loaded.

---

### Post by yeti on 2005-12-03
Ok, Im dumb.  I think my problem was that both the realplayer binary and the firefox binary are both meant fo x86 arch's and Im running a ppc arch.  I found a compiled version of the firefox arch over in the ubuntu:ppc formus and now it is running.

---

