---
title: "VNC Problem"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by -suo on 2007-06-18
I have an ubuntu 6.10 server. I use this server for my gaming business. I’m very new too linux and had it setup for me. I have lost my help and I’m all alone. Here is my problem, I need to use VNC. Now I can access and use VNC fine but every other day I try to connect and it says, “The server is already in use.” A friend created a file to fix the bug but it closes all my applications and it’s basically the same as restarting the server. The server is fully updated except for VNC4Server because my friend says it has a major bug and will make VNC unusable. I think my server has xVNC and I connect threw RealVNC.

Help please,

Or my business will fail.

---

### Post by Clay_Banger on 2007-06-18
try using x11vnc on the ubuntu box, here is a how to:
[http://ubuntuforums.org/showthread.php?t=363236]("http://ubuntuforums.org/showthread.php?t=363236")

---

### Post by -suo on 2007-06-22
Do I have to delete the old version? Also how to I find what version I have?

Im so confused. This is why I use VNC cause I cant work in SSH very well.

---

### Post by Rocket2DMn on 2007-06-22
> **-suo said:**
> Im so confused. This is why I use VNC cause I cant work in SSH very well.
SSH (and command line in general) is an extremely powerful tool.  I suggest that if you are building a business that runs off linux machines, you should do your best to learn how to use the command line.  We are always here to help you out with it - it may be different than you're used to, but don't be afraid of it!  SSH also uses significantly less bandwidth than VNC.

Installing the x11vnc is your best bet - you can connect to it with realvnc.

Good luck!

---

### Post by -suo on 2007-06-23
So how do I install x11vnc? Do I have to delete the old version? How do I tell what version I have.

Im thinking about moving to windows server, I dont understand why vnc is so unstable.

---

### Post by Clay_Banger on 2007-06-24
> **-suo said:**
> So how do I install x11vnc? Do I have to delete the old version? How do I tell what version I have.

Im thinking about moving to windows server, I dont understand why vnc is so unstable.
yes you will need to uninstall your original vnc server software, depending on how you installed it, you should be able to "sudo apt-get remove" it.

as for how to install x11vnc, i posted a link to a how to in my message above.

---

### Post by -suo on 2007-07-04
I installed x11vnc and the issue is the same. Im lost and about to invest in Windows server 2003 becauase this is unuseable.

Why is it that after a day or two vnc keeps telling me someone is connected?

---

### Post by lintoon on 2007-07-04
I've never used x11vnc so I can't compare but check out FreeNX Server and connect with the FreeNX client.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

I have set up a number of systems using freenx and it works wihout issues.  Very fast.  Works very good over the internet too.

---

### Post by mlentink on 2007-07-04
I use RealVNC on a daily basis to access my home Ubuntu-box from work. If I leave it connected, it will quite often tell me that the connection needed to be reset. This is due to a lot of things. After the connection is reset, it will look as if there are more than one users connected, but in actual fact I'm still the only one.

So I wouldn't worry too much. RealVNC has turned out to be quite solid for me

---

