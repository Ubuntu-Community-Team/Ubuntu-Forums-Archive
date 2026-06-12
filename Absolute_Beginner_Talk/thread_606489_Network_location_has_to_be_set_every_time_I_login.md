---
title: "Network location has to be set every time I login"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by babik573 on 2007-11-08
Hopefully this is an easy one to answer.  Every time when I boot up and log in I have to go into the network settings and select the location "home" that I set up before I am connected to my home network.  Is there an easy way to set this as a default when logging in?  Thanks

---

### Post by SomeGuyDude on 2007-11-08
Is this on a notebook, and are you traveling with it elsewhere in between? I know it's an odd question, but from what I've seen Ubuntu tries to re-connect to wherever it was last time, the only time I have to manually re-set it is if I've gone elsewhere and was on a different network.

---

### Post by babik573 on 2007-11-08
Yes it is a laptop, and so far I have only connected when at home.  Usually I go into network settings and select the "home" location and click the checkmark icon and I am connected.  Next time I boot up I will have to do the same thing.

---

### Post by antony11 on 2007-11-08
I have same problem but mine is not a laptop its my main box. Not only that but now its started asking me to log in with my password but it wont accept my password. Still this is all moot since it wont access the network anyway.

---

### Post by parsim on 2008-02-08
I have this problem on my desktop. Every boot, I need to manually go into System -> Administration -> Network and set the location to "Home" (where I have saved the correct DNS settings).

How can I get it to load these settings automatically?

---

### Post by r4ik on 2008-02-08
@parsim

Radical but effective.
Go to synaptic and remove (not total remove) networkmanager.
Go to system - admin -network and set the dns and you're done network will keep the settings.
This works for my wired connection i don't know about wireless.

---

### Post by florian.bw on 2008-03-12
My problem is that I carry my laptop with me to work, and home again. It's quite annoying for me as I have to change the network location twice a day, and the process is quite slow.

II started a brainstorm request to add the possibility to change the network location in the login screen.

[http://brainstorm.ubuntu.com/idea/4365/](http://brainstorm.ubuntu.com/idea/4365/)
[[IMG]http://brainstorm.ubuntu.com/idea/4365/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4365/)

---

