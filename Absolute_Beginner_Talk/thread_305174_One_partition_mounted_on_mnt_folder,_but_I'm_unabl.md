---
title: "One partition mounted on mnt folder, but I'm unable to use it!! Why??"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by rksenthilkumaar on 2006-11-22
Hi,
 I have installed EdgyEft on my sys!
So far It's been so so good, compared to XP! Just a few tweaks & it gets going gr8!
I don't know if it's a silly question, but as I'm an absolutely new beginner, I would like to find the answer out!

I have 160 GB SATA! I have only Ubuntu on this big space!! No other OS!!

One of my partition (46GB) is mounted on "mnt".
Another on "usr" (46GB)!!
I'm unable to create any folders or files or do anything!!:( 
When I right clicked it & went to Permissions, it says "You are not the owner so you cannot change these permissions"!! What does this mean??:-k 

Can't I use that space??:confused: 

I'm able to use the partition mounted in "Home" (52 GB) folder only !!

Please advise me on how to use those space (92 GB) effectively??
Should I re-size them using GParter (I have a Live-CD of it)??

Please help me out!
Thanks in Advance!

---

### Post by taurus on 2006-11-22
In Linux or Unix, you can only read and write to your own $HOME directory.  If you want to write outside of your $HOME, you need to be root and in case of Ubuntu, you can do that with the sudo command.  For instance, you would like to create a new folder called test in /opt, you can open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo mkdir /opt/test
```
Or if you would like to have a graphical sudo, then type

```
gksudo nautilus
```

---

### Post by CatKiller on 2006-11-22
> **rksenthilkumaar said:**
> I'm able to use the partition mounted in "Home" (52 GB) folder only

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

You've dived in deeper than I did - I just let the installer make the **/** and **swap** partitions.

Welcome to the community.

---

