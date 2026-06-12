---
title: "VNC / remote desktop question"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Atmosphere on 2007-05-18
I'm setting up a very simple file server and i got VNC to work from windows to connect but i want to be able to connect to the linux via VNC without having to log in on the linux box first am i missing a setting somewhere ?

---

### Post by PartisanEntity on 2007-05-18
Here is the VNC documentation with various methods of logging in explained:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by byenary on 2007-05-18
for a file server you should not be in need to use vnc, you should connetc trough ssh, on a windows machine you could do this trough ssh-secure-shell or something, and install open-ssh-server on the ubuntu

---

### Post by Atmosphere on 2007-05-18
it doesn't contain any sensitive information i am not worried about security, i just want to remote desktop as simple as possible ... unfortunately the instructions did not work. followed them down to a T and no problems. enabled that port in the firewall and still no go.

Ultra VNC says possible that the versions are incompatible or running a dsm plugin and realvnc says connection was close unexpectedly.

---

