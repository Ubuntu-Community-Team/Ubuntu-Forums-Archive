---
title: "SSH From Windows to Ubuntu from Outside Home Network"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2007-12-08
Good Afternoon

Wondering if anyone has any insight into how I would SSH from my windows machine to my Ubuntu machine when outside my home network.

I believe it may have something to do with opening a port on my router with i.p address of my ubuntu machine, but I dont quite get the mechanics of this all ? If I foward say port 20 with ip address 198.161.1.102, how does SSH know when I am outside my home area to connect to my personal machine and not someone else who has the same ip address 198.161.1.102 which is an internal home address ?


any documentation would greatly help

Thanks,
Frank

---

### Post by scjudd on 2007-12-08
first you must find your external address:  [www.whatismyip.com](www.whatismyip.com)
then set up your router to forward port 22 (ssh) to your ubuntu machine's internal IP
when you want to connect, simply use: ssh user@external_ip

to use ssh from windows, download PuTTY

---

### Post by Dr Small on 2007-12-08
Greetings,
Please read these two wiki articles on SSH:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Good luck!

Dr Small

---

### Post by Hospadar on 2007-12-08
note that if you want to use graphical applications, your ssh client (secure shell, puTTY, etc) must be set up to foreward X connections in the preferences, and you'll need a windows X server like xming.

You also may need to use something like firestarter to open up port 22.

---

