---
title: "server or desktop?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by SyCo123 on 2008-01-16
I have Ubuntu already installed on my laptop and it's working great. The issue is with the LAMP install which is totally screwed. I cant re install or remove anything apache related. I remove, purge and everything else but still screwed.

I thought I'd start again and reinstall Gutsy as it went hassle free the first time. I installed the server edition on another box then the XFCE desktop and I have a nice easy LAMP based file server.

So if I install the server edition on my laptop, then install the Gnome desktop will I have the same system as if i installed the desktop edition and them LAMP? If not what would the differences be?

---

### Post by ckennow on 2008-01-16
Well as far as what i've done in the past when getting used to linux I would do the perfect server settup and then run 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install ubuntu-desktop

```

---

### Post by SyCo123 on 2008-01-17
OK thanks I'll give that a go and see how it works out.

---

### Post by dcstar on 2008-01-17
> **SyCo123 said:**
> 
........
So if I install the server edition on my laptop, then install the Gnome desktop will I have the same system as if i installed the desktop edition and them LAMP? If not what would the differences be?

The server install will install the server kernel - one that is optimised for server use and not desktop use (as the "generic" one is).

---

### Post by SyCo123 on 2008-01-24
thanks for the extra indo DCstar.

I decided to try it both ways and there was little difference to a lay person like me. I ended up using the proper desktop version and installing LAMP first and it all went fine. I have my laptop set up just how I want it now and am a very happy camper!

---

