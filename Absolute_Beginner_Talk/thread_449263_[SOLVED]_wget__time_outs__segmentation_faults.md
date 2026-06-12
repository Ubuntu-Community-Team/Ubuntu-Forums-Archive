---
title: "[SOLVED] wget | time outs | segmentation faults |"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Lutherian on 2007-05-19
Hi all.

I suspect that like most people I use wget for my downloads.
typically I'd use a commandline such as

[COLOR="Red"]wget -t0 -c --retry-connrefused -P/My-Downloads -i /my-download-url-list.txt
[/COLOR]
For the most part it works fine.
The idea is that wget will retry connections if they drop, and failing that, will just go on to the next url if it can't
Strangely though I get an error like this:

[COLOR="Red"]Data Connection: Connection Timed out;
Segmentation fault[/COLOR]


I accept that sometimes the Server itself will terminate a connection, but I'm worried about the "Segmentation fault" (Sounds Scary!)
i.e. My Question - why doesn't wget just proceed to the next url in my list - is there a command option I can use. (There are plenty of *--timeout *type command lines in the man pages but I'm not sure if they'll help with this)

Thanks in advance for the help - I'm very grateful. (^_^)

---

### Post by Lutherian on 2007-05-20
Hi all.[ Apologies to Sys Admins for reposting, but I realised that my original post didn't quite belong in it's previous category (networking) so I reposted here - won't do it again (^_^) ...]

I suspect that like most people I use wget for my downloads.
typically I'd use a commandline such as

wget -t0 -c --retry-connrefused -P/My-Downloads -i /my-download-url-list.txt

For the most part it works fine.
The idea is that wget will retry connections if they drop, and failing that, will just go on to the next url if it can't
Strangely though I get an error like this:

Data Connection: Connection Timed out;
Segmentation fault


I accept that sometimes the Server itself will terminate a connection, but I'm worried about the "Segmentation fault" (Sounds Scary!)
i.e. My Question - why doesn't wget just proceed to the next url in my list - is there a command option I can use. (There are plenty of --timeout type command lines in the man pages but I'm not sure if they'll help with this)

Thanks in advance for the help - I'm very grateful. (^_^)

---

### Post by ajmorris on 2007-05-20
> **Lutherian said:**
> Hi all.[ Apologies to Sys Admins for reposting, but I realised that my original post didn't quite belong in it's previous category (networking) so I reposted here - won't do it again (^_^) ...]

I suspect that like most people I use wget for my downloads.
typically I'd use a commandline such as

wget -t0 -c --retry-connrefused -P/My-Downloads -i /my-download-url-list.txt

For the most part it works fine.
The idea is that wget will retry connections if they drop, and failing that, will just go on to the next url if it can't
Strangely though I get an error like this:

Data Connection: Connection Timed out;
Segmentation fault


I accept that sometimes the Server itself will terminate a connection, but I'm worried about the "Segmentation fault" (Sounds Scary!)
i.e. My Question - why doesn't wget just proceed to the next url in my list - is there a command option I can use. (There are plenty of --timeout type command lines in the man pages but I'm not sure if they'll help with this)

Thanks in advance for the help - I'm very grateful. (^_^)



Which version  of wget?, i know there was an error like this in version 1.10

---

### Post by bapoumba on 2007-05-20
@ Lutherian: merged your other thread in this one.

---

### Post by Lutherian on 2007-05-21
Unfortunately I'm not at my machine right now - It's the default version that came with Ubuntu 6.10 LTS
I checked the repos for a new version / update - but there wasn't one. If you know of a place where I could get a newer version to download I'd be grateful (preferably a .deb versiion ... still a bit of a noob and tend to screw up complining these things)

---

### Post by ruy_lopez on 2007-05-21
a segmentation fault is a serious error. Something is being referenced which doesn't have a valid memory address (inside the program). Is it only happening for a specific URL?

---

### Post by ruy_lopez on 2007-05-21
If you are concerned about it, there's a python script you can use in place of wget:

```
#!/usr/bin/python

import sys, urllib, os

def hook(*a):
     print '%s: %s' % (fn, a)
for url in sys.argv[1:]:
     fn = os.path.basename(url)
     print url, "->", fn
     urllib.urlretrieve(url, fn, hook)
```

just copy the code above into a file, rename it wget.py, then "chmod +x wget.py". To use it, type "./wget.py <url>"

---

