---
title: "NIC Settings...config file...?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by ravosava on 2008-02-15
Is there a configuration file that holds your NIC settings, and how do I get to it?

---

### Post by jordanmthomas on 2008-02-15
You can use ifconfig to configure it.
What setting are you looking for exactly?  There's many files related to networking.

---

### Post by ravosava on 2008-02-15
> **jordanmthomas said:**
> You can use ifconfig to configure it.
What setting are you looking for exactly?  There's many files related to networking.

well i wasnt really asking for myself...somebody asked me if I knew and I said I'd look into it :-/

---

### Post by kevdog on 2008-02-15
Yes the /etc/network/interfaces file.  In the networking forums look for a WPA post by Weiman01.  It provides at least an example that shows you what to do.

---

### Post by jordanmthomas on 2008-02-15
Hmm.
I can name some files that may be of interest at least
```
/etc/hosts         #has your hostname and others too if you wish
/etc/resolv.conf          #has information on how you look up hostnames
/etc/nsswitch.conf        #configuration file for resolving hostnames
/etc/network/interfaces   #config file for Ubuntu that tells how to connect.

```
Somewhere in the menus exists a GUI for editing your networking information (called networking maybe?) I don't use Ubuntu and don't have a tool like this.

If you want a lot of information on your nic:
```
sudo lshw -class network
``` will tell you the name of your card, what driver it's using, etc.

Hopefully something here will be of value to your friend.

---

### Post by ravosava on 2008-02-15
Thank you, your information helped. I love how knowledgeable everyone is!

Maybe one day I could answer these questions on my own...:)

---

### Post by jordanmthomas on 2008-02-15
Of course you can.  Now that you know this, you can answer it next time it comes up.  The more you use Linux, the more often you'll wonder how to do something.  

Look it up, do it wrong (most of the time), fix it, do it again.  

The process of learning.

---

### Post by ravosava on 2008-02-15
> **jordanmthomas said:**
> Of course you can.  Now that you know this, you can answer it next time it comes up.  The more you use Linux, the more often you'll wonder how to do something.  

Look it up, do it wrong (most of the time), fix it, do it again.  

The process of learning.

So I'm told. However, when it comes to computers, I'm a little dim-witted. I'd be on here daily asking questions if I couldnt call my friend when I break something (which is a lot) 

and I could do it 10 times in a day, and still not remember how to fix it.

I'm a techs worst nightmare lol

---

### Post by PeterJS on 2008-02-15
> **ravosava said:**
> I'm a techs worst nightmare lol

Don't worry about it, you're not, our worst nightmare is the person that comes back ten times per day but isn't willing to try learn.

---

### Post by ravosava on 2008-02-15
> **PeterJS said:**
> Don't worry about it, you're not, our worst nightmare is the person that comes back ten times per day but isn't willing to try learn.

haha i feel better now.

---

