---
title: "Cire installation problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by dcbergen on 2008-04-16
Hi all,

I'm trying to install Cire (diary/journal software) onto my computer and am getting the following message during the installation process:

checking for gtk+-2.0 >= 2.0.2... configure: WARNING: Couldn't find GTK, building without it.


When I try to open Cire I get the this message:

Hrmm, you don't seem to have included any user interfaces in this build.


I can't find   gtk+-2.0 in the Synaptic Package Manager. I assume that if I could find this and install it on my computer I'd be able to properly install and use Cire. I could be completely wrong... Any help will be appreciated. :confused:

David

---

### Post by dcbergen on 2008-04-16
I found gtk+-2.0 here: [http://gtk.org/](http://gtk.org/)     This requires other old packages such as glib-2.0, 2.0.1 atk, and 1.0.1 pango. Perhaps this will be more trouble than it's worth...

---

### Post by unutbu on 2008-04-16
I believe the package you need is called libgtk2.0-dev.
Try 
```
sudo apt-get install libgtk2.0-dev
```

If that succeeds with no errors, great. If not, make sure your /etc/apt/sources.list contain

## Updates.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

Then do:
```
sudo apt-get update
```

and try installing libgtk2.0-dev again.

---

### Post by dcbergen on 2008-04-16
Oh yes, this works perfectly. Thank you!

---

