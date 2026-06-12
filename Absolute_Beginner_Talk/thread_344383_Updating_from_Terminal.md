---
title: "Updating from Terminal"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by teejay17 on 2007-01-22
I'm just wondering how to update Ubuntu from the terminal, rather than using Synaptic or Update Manager. 
What would I type in the terminal to fetch and install all the updates currently available?

---

### Post by tbroderick on 2007-01-22
sudo apt-get update
sudo apt-get upgrade

---

### Post by crispy_420 on 2007-01-22
sudo apt-get update

sudo apt-get upgrade

---

### Post by teejay17 on 2007-01-22
> **crispy_420 said:**
> sudo apt-get update

sudo apt-get upgrade
Cool. Thanks.

---

### Post by aysiu on 2007-01-22
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Shatrat on 2007-01-22
```
echo 'sudo apt-get update' | /bin/bash
echo 'sudo apt-get upgrade' | /bin/bash
```

Remember, in order to impress non-linux users you must obfuscate your commands as much as possible.
The minute everyone understands how to do this is the minute my false sense of superiority dies!

---

### Post by teejay17 on 2007-01-22
Okay, thanks guys. You both answered my question promptly, and I appreciate that. 
But your help also prompted another question. It seems that the server that's hosting the updates is down (or something) and the really important updates (i686, etc.) cannot be downloaded at this time (404 error). 
My question is this: is it possible to switch the download site, where the updates come from? So, for example, instead of the ca.ubuntu.com mirror from which I currently download, perhaps I can get these updates from somwhere else? 
All this from the terminal, of course.

---

### Post by Shatrat on 2007-01-22
It is certainly possible, although I am not sure where to find the list of repository domains.
Mine ceme from us.archive.ubuntu.com/ubuntu  so maybe you could try inserting that instead of ca.ubuntu.com, assuming that is your main repository.

---

### Post by tbroderick on 2007-01-22
The file to edit is /etc/apt/sources.list. You can change to any mirror you want. 

```
sudo nano -w /etc/apt/sources.list
```

---

### Post by Shatrat on 2007-01-22
I just found this, pretty nifty:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Sef on 2007-01-22
> sudo nano -w /etc/apt/sources.list

You should use gksudo when opening a graphical program, otherwise you may not be able to login.  Check out [Root/Sud]("https://help.ubuntu.com/community/RootSudo")o for more information.

```
gksudo nano -w /etc/apt/sources.list
```

---

### Post by tbroderick on 2007-01-22
> **Sef said:**
> You should use gksudo when opening a graphical program, otherwise you may not be able to login.  Check out 

Thanks, but nano is is a console/terminal editor. You don't need X.

---

### Post by crispy_420 on 2007-01-23
I would suggest backing up your sources list if you decide to screw around with it.

---

### Post by davidvasta on 2007-01-23
You guys all beat me to it. Nice thread. This would be one of those handy threads when I forget how. I just did all this so it's still fresh.

---

### Post by teejay17 on 2007-01-23
> **Shatrat said:**
> I just found this, pretty nifty:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
This is a great link, and a great service. Thanks for posting it! And thanks for making it, whoever you are!

---

