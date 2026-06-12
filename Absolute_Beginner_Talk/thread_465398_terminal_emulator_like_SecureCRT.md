---
title: "terminal emulator like SecureCRT"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by jwiener3 on 2007-06-05
I have searched the forums and found a few links but no real answers. 
I am a network engineer and I work on cisco products for different customers. I need to be able to save profiles,whether they be console, ssh, or telnet. Some with automatic logins.
I switched to ubuntu about a week ago and am looking for an alternative to securecrt or a way to make it work in wine. 
I really don't want something small (but crucial) to kill my ubuntu buzz ;).

---

### Post by rich.bradshaw on 2007-06-08
you know you can just use ssh, ftp, etc from Ubuntu with no extra software don't you?

Places/Add Server

Then it will appear in places.

Alternatively, in a terminal

ssh ADDRESS
telnet ADDRESS
rsh ADDRESS

etc.

What do you want to be able to do that those can't?

---

### Post by luvdemheels on 2007-06-08
Have you tried putty? You should be able to get it thru synaptic. Works for me.

---

### Post by rich.bradshaw on 2007-06-08
What's the point of puTTY though? It's all built in in Linux...

---

### Post by quietas on 2007-06-08
Putty does have all needed configurations in a gui. Also you can save your dozens of servers instead of having to remember.

---

### Post by jwiener3 on 2007-06-09
ya I am aware of putty and I know that you can do all those things in gnome-terminal. But there are still a few things that make securecrt more popular than hyperterm, or putty, or just a command line. It has alot nicer interface. It is easier to capture text than putty, and more configureable. It is also easier to organise all of the saved connections and setup login scripts if needed.

---

### Post by banditti on 2008-02-26
I use:  gtkterm and or putty



It works well for me.  They both support my usb to serial adapter.

```
sudo apt-get install gtkterm putty
```

---

### Post by PeterJS on 2008-02-26
On the ssh front you can set up ~/.ssh/config with aliases for commonly used hosts, for full documentation see the man page for ssh_config. The basic layout looks like:
```

Host *alias*
User *username*
Hostname *hostname/ip*
*Options*

```

---

### Post by pkiula on 2008-07-18
Hi. I am looking for this too. Yes SSH is nice and all, and I have aliases in my bash profile file. But this still does not remember the passwords. What should I do to make sure that when I use an alias, that I don't have to enter a password everytime? 

Thanks.

---

