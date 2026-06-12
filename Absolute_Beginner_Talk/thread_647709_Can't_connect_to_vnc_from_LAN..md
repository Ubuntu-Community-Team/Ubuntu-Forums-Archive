---
title: "Can't connect to vnc from LAN."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Scrier on 2007-12-22
Hi I have set up the remote desktop on my server which aslso works as a internet router amongs others. Now I cannot connect to the server through vnc or anything although I can ping it and according to the remote desktop info the vnc should be setup accordingly. Any ideas where to look for fixes?

// Andreas

---

### Post by wormser on 2007-12-22
Sounds like the firewall could be blocking you.  Install Firestarter.  It will be listed under System> Administration> Firestarter

```
sudo apt-get install firestarter
```

---

### Post by Scrier on 2007-12-23
firestarter is installed.

---

### Post by wormser on 2007-12-23
> **Scrier said:**
> firestarter is installed.

Did you use Firestarter to open the VNC ports?  I believe they are ports 5900-5902.  You also should tunnel you VNC though ssh for security.  In that case you would open up port 22.  Search the forums because there are guides for tunneling VNC though ssh.

---

