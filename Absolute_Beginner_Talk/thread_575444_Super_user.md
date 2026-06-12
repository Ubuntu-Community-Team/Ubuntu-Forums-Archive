---
title: "Super user"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Ammaro on 2007-10-14
Alright well Im trying to install new ATI drivers and it says I have to be the super-user.

How do I become said superuser?

---

### Post by 001100 on 2007-10-14
try logging in as root and then try installing the ati driver(s)
root has the most control over the computer

---

### Post by wormser on 2007-10-14
Super User is root and with Ubuntu there is no need to become root.  Use the **sudo** command instead.  Just put sudo before the command you are trying to execute.  Then use your password.

---

### Post by Ant_Merlin on 2007-10-14
Hi Wormser is right, you should NEVER log in as root, its a big security risk and there is no need. all you need to do is type sudo before other commands. It will then ask for the password.
You might want to try Envy for driver installs, it is GUI and does everything for you:

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb")

---

### Post by 001100 on 2007-10-14
sorry for mis-leading you i for got that you could have just typed sudo for root instaed of logging in to root. I am still getting use to the linux commands

---

### Post by Ferri on 2007-10-14
Incidentally, are you sure you need the new ATI drivers?
I'm not sure about the actual versions in AMD site and in the "restricted" repositories, but they are usually quite up-to-date and it's likely that you'll have fewer problems.

---

### Post by Ammaro on 2007-10-14
> **Ferri said:**
> Incidentally, are you sure you need the new ATI drivers?
I'm not sure about the actual versions in AMD site and in the "restricted" repositories, but they are usually quite up-to-date and it's likely that you'll have fewer problems.

Yeah, the video when I try to run ubuntu is well ****.
And it tells me im missing drivers for my video card so yeah.

---

