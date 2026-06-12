---
title: "Add SSH"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by tw9u on 2007-10-15
How do I add an SSH client.I am using a live CD in order to learn.

---

### Post by Dr Small on 2007-10-15
The openssh-client should be preinstalled on the livecd as well as the default installation of the operating system. If it is not, you can run:
```
sudo apt-get install openssh-client
```
To install it. But since you are running off of the livecd, you would have to install that every time, if it is not already preinstalled.

Learn more about SSH here:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Dr Small

---

