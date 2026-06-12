---
title: "Remote Desktop"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by glen4cindy on 2007-06-09
How can I change the port used by Remote Desktop.

When I go to the configuration screen, it tells me to vnc viewer <address>:0

So, I tried vnc viewer 192.168.2.2:0 but it does connect. I can VNC into my Suse 10.0 box, but, on the configuration screen for that one uses port vnc viewer <address>:5901 so I use vnc viewer 192.168.2.2:5901 and I'm in with no problems.

Thanks!

---

### Post by wormser on 2007-06-09
I would recommend tunnelling you vnc sesion with ssh.  It is more secure this way.

```
ssh -L 5901:localhost:5901 username@domain.com
```

Your vnc address will now be:

```
localhost:5901
```

---

### Post by glen4cindy on 2007-06-11
Thanks, I'll try that.

---

