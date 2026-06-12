---
title: "Updating firefox"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by hawksigns on 2006-03-12
I seem to be running an old version of firefox and I can't seem to update the version.  It's supposed to do it itself and while I tried to install a newer version, it said I "already had the latest version".  If I check the "About Firefox"  thing, it says I'm running version 1.0.7 instead of the latest 1.5

Any ideas?

BTW, bitdefender seems to be installed, but I still can't figure out how to find it and get it to do anything.

---

### Post by 5-HT on 2006-03-12
To upgrade to FireFox 1.5, there is a great, step by step guide here:
[https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion").

HTH

---

### Post by hawksigns on 2006-03-12
Whoa... huge problem and I'll bet it has something to do with the list thing that I was supposed to copy and paste over this morning...

Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

followed by a page and a half of error messages after typing in  sudo apt-get install libstdc++5 as instructed at that site.

Then when I tried to apt-get update: 

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by hawksigns on 2006-03-12
Somebody told me to do this to "update my repositories" or something...

Follow the instructions here to get up-to-date and non-conflicting repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Which I did and I don't know if that's where this weird error message is coming from but I remember it had something to do with copy and pasting over something about "lists"....

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=hawksigns]
Then when I tried to apt-get update: 

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/QUOTE]


That's the message you will get if you try to type apt-get update.... You have to use sudo in front of that command, then give your password...

```
sudo apt-get update
```

same with installing...

```
sudo apt-get install libstdc++5
```

---

