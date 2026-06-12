---
title: "Installing Drivers for Brodcom STA wireless"
date: 2010-11-10
forum: Apple Hardware Users
---

### Post by kjiang on 2010-11-10
Hey guys, this is my first post on here and I'm not really familiar with Ubuntu, but here it goes.

I just installed Ubuntu on my Macbook Pro today, and I'm trying to install the drivers. 
I ran the command "sudo dmidecode -s system-product-name" and I got "Macbook 6,2"

On [[COLOR="SlateGray"]https://help.ubuntu.com/community/MacBook[/COLOR]]("https://help.ubuntu.com/community/MacBook") it only lists up to Macbook 6,1 so I just went with that.

I'm trying to install the "Brodcom STA wireless driver" However, when I authenticate it and begin the installation, it says: "Sorry, the installation of this driver failed. Please have a look at the log file for details: /var/log/jokey.log"

Can anyone tell me what's wrong?
Thanks!

---

### Post by Whiteice on 2010-11-10
A long time ago I came across some issues with broadcom drivers. The best fix I found was to find the driver .ini file somewhere on the internet for your card and then use the program ndiswrapper which i believe can still be found on the repositories. what this will do is attempt to use in my case the windows driver for linux. you should be able to do the same thing if your running a macbook with intel specs.

---

### Post by alexmurray on 2010-11-11
> **Whiteice said:**
> A long time ago I came across some issues with broadcom drivers. The best fix I found was to find the driver .ini file somewhere on the internet for your card and then use the program ndiswrapper which i believe can still be found on the repositories. what this will do is attempt to use in my case the windows driver for linux. you should be able to do the same thing if your running a macbook with intel specs.
No - don't do this.

Instead try running the following from a terminal and see what the output is:

```
sudo apt-get install dkms bcmwl-kernel-source
```

---

### Post by kjiang on 2010-11-11
Well I ran the command, and it upgraded the "dkms" package.
I tried to install the driver again but I got the same message: 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

---

### Post by alexmurray on 2010-11-11
Well what does the file /var/log/jockey.log contain??

---

### Post by kjiang on 2010-11-11
> **alexmurray said:**
> Well what does the file /var/log/jockey.log contain??
Its just a really long log with a ton of entries like this:

2010-11-10 19:56:28,791 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl

---

