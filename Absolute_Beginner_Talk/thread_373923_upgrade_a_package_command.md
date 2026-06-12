---
title: "upgrade a package command"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by philip360 on 2007-03-01
Hi all, what is the command for upgrading a package?

Adept update shows an upgrade available for  sun-java5-jre  and sun-java5-bin
I clicked to do the upgrades but it freezes at 9% progress because it wants the license agreement and Adept does not show the "click here for accept"

see screenshot

So I want to do it by command. I searched and could not find the answer to my simple problem....

Thanks, Philip

---

### Post by nudnik on 2007-03-01
> **philip360 said:**
> Hi all, what is the command for upgrading a package?

Adept update shows an upgrade available for  sun-java5-jre  and sun-java5-bin
I clicked to do the upgrades but it freezes at 9% progress because it wants the license agreement and Adept does not show the "click here for accept"

see screenshot

So I want to do it by command. I searched and could not find the answer to my simple problem....

Thanks, Philip

You will have to install it manually. Go the Java site, find the Linux download appropriate for Ubuntu (not the RPM one). Download to your desktop, and click on the "instructions" tab on the website. Everything you need is there.

---

### Post by philip360 on 2007-03-01
Thanks, and do I need to remove the old one first? if so I can just do it with Adept right?

---

### Post by spoot on 2007-03-01
The commandline way of updating your system would be:

```
sudo apt-get dist-upgrade
```

or

```
sudo aptitude dist-upgrade
```

---

### Post by igknighted on 2007-03-01
Yeah, theres no reason to go to the sun site for that.  Open a command line and type "sudo apt-get install -f" and it should finish and give you the option to accept the licenses.

---

