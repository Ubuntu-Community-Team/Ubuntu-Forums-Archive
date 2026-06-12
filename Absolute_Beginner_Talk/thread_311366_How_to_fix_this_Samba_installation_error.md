---
title: "How to fix this Samba installation error?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-12-02
I'm trying to install Samba server but can't get past this error:

```
samba:
  Depends: samba-common (=3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu4 is to be installed

```

Anyone have a clue? I'm semi dead in the water until I get this solved.

---

### Post by PilotJLR on 2006-12-02
How are you producing this error? What command did you enter?

All you should need to do to install samba is:
```

sudo apt-get update
sudo apt-get install samba

```

---

### Post by wrybread on 2006-12-02
Sorry I should have said, it was from Synaptic.

If I run it from terminal I get the following:

wrybread@boofus:~$ sudo apt-get update
[lots of stuff, edited out]
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

wrybread@boofus:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu4 is to be installed
E: Broken packages

---

