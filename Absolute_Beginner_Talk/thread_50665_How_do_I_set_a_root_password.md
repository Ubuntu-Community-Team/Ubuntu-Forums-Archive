---
title: "How do I set a root password?"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by arcanistherogue on 2005-07-21
Hey.  I reformatted an old Gateway computer I found lying around today, and I installed Ubuntu to fool around with.  I use linux on my main computer along with windows, and I added linux in May.  

I remember my friend told me I had to set a root password (am I remembering wrong?) and he showed me how too.  That same friend is on vacation now though, so I can't contact him for help.  I wanted to install some things but I can't use synaptic if I can't log in as root. 

How would I go about doing this?

Thanks in advance

---

### Post by bored2k on 2005-07-21
You do _not_ need to set a new password. Like Mac OS, Ubuntu uses sudo.
> 
Ubuntu uses sudo to allow a normal user administrative privileges. Thus the traditional UNIX 'root' account is disabled (i.e. it is not possible to log in as root). All the graphical configuration utilities use sudo by default. Thus when Synaptic or something similar asks you for a password, it is asking for your password.

[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

---

### Post by arcanistherogue on 2005-07-21
Thanks alot!

---

