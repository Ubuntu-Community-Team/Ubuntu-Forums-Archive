---
title: "Macromedia Flash"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by infernon on 2007-01-06
I have attempted to install Macromedia Flash on my machine, but something appears to have gone wrong.  I am running Ubuntu 6.10.

I ran the script after being directed to the Adobe Acrobat site, but at the end of the installation, I receive the following message:

----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/infernon/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

I am unable to find the components directory and the directory that is indicated as the Mozilla installation directory isn't there (or at least I can't see it, even though I've selected the option to show hidden files and folders in Nautilus).  I have also attempted to search the entire drive for the file indicated, but I'm not able to find it.

The problem that I'm having now is that Firefox crashes any time that I attempt to view a page with Flash stuff embedded into it.  Can someone point me in the correct direction?

---

### Post by Paul41 on 2007-01-06
There is a package available for the flash player that will install it for you

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by moma on 2007-01-06
You may install Flash-plugin (Flash 9 beta) for Firefox via Automatix2 tool.
See step 5) [here...]("http://www.futuredesktop.org")

---

### Post by infernon on 2007-01-06
Thanks for posting guys.  I'll try this at the first chance I have.

---

### Post by g1gabyt3 on 2007-01-07
> **Paul41 said:**
> There is a package available for the flash player that will install it for you

```
sudo aptitude install flashplugin-nonfree
```

I have both Firefox and Opera and wish to install flash so it works with both.  I tried the sudo command from above and this is the message I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

so I'm guessing that I need to do something else?

---

### Post by Gremlinzzz on 2007-01-07
Install flashplayer9 from here just paste commands in terminal                                                               [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by g1gabyt3 on 2007-01-07
Thanks allot, it works great for Firefox, now if I can get it to work with Opera I'll be set.

---

