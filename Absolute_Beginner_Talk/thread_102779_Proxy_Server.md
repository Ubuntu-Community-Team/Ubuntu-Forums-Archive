---
title: "Proxy Server"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by georgeca on 2005-12-12
I want to share my dialup connection with another computer I have in my house. When I had Windows, I had CCProxy installed, and everything went well. How would I set up my Ubuntu computer as a proxy? Is there a program I should download, or is it built it? Thanks in advance.

---

### Post by sjh on 2005-12-12
I did it a while back before I got broadband by using Iptables.    Looks like Firestarter (front end for Iptables) should be able to set it up.

Good Luck
SJH

---

### Post by georgeca on 2005-12-12
So I would have to install Firestarter to do so?

---

### Post by sjh on 2005-12-12
Yes, it is not installed by default.  I do not use it but the website:

[http://www.fs-security.com/](http://www.fs-security.com/)

says that it can set this for you.  I would assume it is much easier that writing .conf file.

Synaptics or 
```
sudo apt-get install firestarter

```

(in terminal) should download and install it.  Then just type 'firestarter' (less quotes) in terminal should start the set-up pgm.

SJH

---

### Post by georgeca on 2005-12-13
To keep the firewall on, must I keep Terminal open? Because each time I close terminal, the firewall shuts off from the tray icon.

---

### Post by sjh on 2005-12-13
Again, I don't use this package (yet), I have been researching it.  From this post:

[http://ubuntuforums.org/showthread.php?t=102645&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=102645&highlight=firestarter)

I assume the firewall is still working, just the gui has shut down.

One of the comments in this post is that a firewall is not required for linux.  I agree somewhat, but when you share the internet to a windows box from a ununtu box, Iptables is a much better firewall (disclaimer here:  a properly configured Iptables) than anything windows can offer.

---

