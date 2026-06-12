---
title: "command meaning ?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-11
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

^ what does this means ?

---

### Post by taurus on 2007-03-11
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by HunkieChan on 2007-03-11
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

thanks bro.. is there anyway i can have your im id ?.. i am new in this world.. i constantly need help;.. you seem like a pro.. is it possible.. ?

---

### Post by taurus on 2007-03-11
Sorry but don't have IM.

---

### Post by HunkieChan on 2007-03-11
sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree


^ it gives me this error .. what should i do ?

---

### Post by HunkieChan on 2007-03-11
> **taurus said:**
> Sorry but don't have IM.

its okay, just try to be here for awhile.. i installed ubuntu yesterday.. everything is messed up..

---

### Post by HunkieChan on 2007-03-11
taurus.. you there ?

---

### Post by taurus on 2007-03-11
Try 

```
sudo aptitude clean
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by HunkieChan on 2007-03-11
> **taurus said:**
> Try 

```
sudo aptitude clean
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

dude you gave me a heart attack.. i need your help. how do i install java.. i want install limewire.. is there a better one by the way ?

---

### Post by taurus on 2007-03-11
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by HunkieChan on 2007-03-11
> **taurus said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

of those 4 code.. only 1st and last two worked.. what do ido now ?

---

