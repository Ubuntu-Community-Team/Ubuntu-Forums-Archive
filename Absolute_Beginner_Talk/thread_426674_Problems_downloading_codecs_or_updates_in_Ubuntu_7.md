---
title: "Problems downloading codecs or updates in Ubuntu 7.04"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by darrellfjohnson on 2007-04-28
I've tried to download them both from inside MPlayer, and in the Add/Remove menu and I get the same error message which says:


```
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

I also get the same message when I check for updates, and even after I overwrote my sources file with the default one for 7.04 using the source-o-matic website.

Are the servers down, or is there something wrong with my system?

Thanks in advance for any help.

---

### Post by taurus on 2007-04-28
I recommend you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by [S|G] on 2007-04-28
You could try this:
```
sudo apt-get update && sudo apt-get install -f
```
And see if you can install things normally afterwards

---

### Post by darrellfjohnson on 2007-04-28
Thank you Taurus, that worked perfectly.  This Ubuntu installation just got a lot more usuable.

I have a question though, why did that work?  Is it just that the US servers were down, or was the URL wrong or what?

---

### Post by taurus on 2007-04-28
I think the US server (mirror) is either down or dead!

---

