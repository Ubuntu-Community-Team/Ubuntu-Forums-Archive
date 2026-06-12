---
title: "adding system calls"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ahsonbol on 2007-11-02
I am new to linux and using ubuntu 7.04 live CD with kernel 2.6.20. I am trying to add a system call.
All tutorials suggest that I make like a copy of the kernel before editing, tutorials also say that the kernel can be found at /usr/src/linux. However, I can only found /usr/src/linux-headers-2.6.20.

So, How can I get the kernel code using the live cd?

---

### Post by lolindrath on 2007-11-02
Hi There,

First, to answer your question about the kernel source code:

```
sudo apt-get install linux-source
```

this will put a tar.gz in your /usr/src directory, you extract that and you'll get a /usr/src/linux-source-2.6.20 directory.

Then you symbolically link that to /usr/src/linux


Second, I don't know if you can do all this on the live CD, let me know how you do. If it does work the changes will only be temporary so if you reboot you'll lose your changes so make sure you backup onto a usb drive or something.

--Lolindrath

---

### Post by ahsonbol on 2007-11-16
Actually , I failed to do it on the live CD
I installed Ubuntu and following the steps. However, I failed to extract the .tar because I don't have the permissions. How Can I set my permissions? or this can be done by the root account?

---

### Post by ahsonbol on 2007-11-17
Well , I found a way around.
First of all the password for the root account is locked in ubuntu for safety reasons. However, if you want to do some tasks that need root's privileges, you can use the sudo word bedore your normal command. this will help you to get the required privileges
for more information on RootSudo follow the link
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

