---
title: "Remote desktop between ubuntu machines on WINS network"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by bjorn_johansson on 2007-04-17
Hi, I started using linux about a month ago, and I am really impressed by the easy of use.
I have a problem though,

At work I have two computers, a stationary and a laptop, wich both connect to a WINS network. I used to run both with Windows XP, and I used the stationary computer to control the laptop remotely using the Remote dektop built into windows.

 On windows I can connect both computers ( when BOTH run Windows) using only the computer name ("host name"). On ubuntu I cannot connect one computer to the other (with vncviewer when BOTH machines run ubuntu 6.10) using name, only IP number. I woul really like to be able to do this by only giving the name of the computer.

I have samba installed, and sharing files works very well. Printer sharing also works.

After googling around I have the gut feeling that I may need somthing called "winbind" for samba. However, all discussions on this are so far above my had that I cant even understand if this would solve my problem or not.

Do I really need DynDNS? I am behind a proxy, so that seems like a cumbersome solution.

Grateful for help!

/Bjorn

---

### Post by ohioboy757 on 2007-04-17
You can add the information for the other systems on your network to /etc/hosts.  The default order for lookup is hosts then bind.  There are examples in the file.

For more information:
```
man hosts
```

---

