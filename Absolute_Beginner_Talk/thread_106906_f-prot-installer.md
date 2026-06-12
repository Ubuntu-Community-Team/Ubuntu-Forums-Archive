---
title: "f-prot-installer"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by kagoole on 2005-12-21
Any help appreciated,
I am trying to install f-prot-installer and am getting the following problem
```

Setting up f-prot-installer (0.5.19~breezy1) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from ftp://ftp.f-prot.com/pub/linux/
19:50:08 URL: ftp://ftp.f-prot.com/pub/linux//fp-linux-ws.tar.gz.md5 [53] -> "fp-linux-ws.tar.gz.md5" [1]
md5sum looks O.K.

       Old and new checksum are identical.
       You already have the latest version
       installed. Congrats!

       If you want to force a re-installation,
       please call update-f-prot with the -f option.

Checking if virus definitions need to be updated...
syntax error at /usr/lib/f-prot/tools/check-updates line 146, near "or"
Execution of /usr/lib/f-prot/tools/check-updates aborted due to compilation errors.
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I'm lost,where next ??????

---

### Post by bluefrog on 2005-12-22
nothing, as it says syntax error in the update file. so correct it by hand or install another antivirus.

james

---

### Post by bishop on 2005-12-23
[QUOTE=bluefrog]nothing, as it says syntax error in the update file. so correct it by hand or install another antivirus.[/QUOTE]And one would go about this correction ... how?

---

### Post by bscbrit on 2005-12-23
If you could post, say, 10 lines either side of the error in line 146, then perhaps some wizard on this forum could suggest the change.  Might not be enough, but it might be.  

Another couple of avenues worth exploring:

Search these threads (using the search facility - not manually!) for f-prot to see if anyone else has had the same problem and maybe even fixed it.

Find F-Prots own site and ask someone there for help.  They will probably be quite pleased have the error pointed out to them (politely). I've got no doubt that they would like the update script to work for their users.

---

### Post by Perfect Storm on 2005-12-23
Here's a howto: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by bishop on 2005-12-23
[QUOTE=Artificial Intelligence]Here's a howto: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)[/QUOTE]Excellent. I hadn't had time to do a full search on f-prot install, but only the error that came up last night before I had to run out the door. THIS is excellent helpfulness. I appreciate your time and work on the thread there.

---

