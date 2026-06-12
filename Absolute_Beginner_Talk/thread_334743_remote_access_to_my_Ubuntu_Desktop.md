---
title: "remote access to my Ubuntu Desktop"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by blumagic on 2007-01-09
Hi All,

While at work, I would like to access my Ubuntu desktop machine. I would like to practise linux and work on my Oracle application. At home, I use a router to connect several computers. I would like to know what server or services I need installed on my Ubuntu desktop and what application I need on my windows xp computer at work? I am using Brezzy Badger 5.10 Ubuntu software at home.

Thanks very much,

blumagic...

---

### Post by Modernity on 2007-01-09
Ubuntu comes with VNC installed, so you have that covered. All you have to do is install VNC viewer on your computer at the office to connect. (I am not sure what kind of environment you are in at the office, so if you have an Adminstrator at the office, check with them first.)

The next step would be to aquire an IP address for your home. Which requires you to bridge your modem at home to use your router for forwarding your port to your Ubuntu machine.

---

### Post by marianom on 2007-01-09
Yeap, VNC is the answer.

I would also suggest accessing your ubuntu with ssh (you need Putty installed in your windows to do so). You would get just terminal access but it's a great way of learning commands and survive without GUIs.

For extra security I suggest a vpn server in your desktop. Eg.: openvpn

---

### Post by Modernity on 2007-01-09
Agreed. Putty would be a must if you plan to get used to working with the system. It would also get you into a good habit of using Linux proficiently.

---

### Post by blumagic on 2007-01-10
Hi All,

First, I appreciate the replies to my question. I am still having problems connecting. I have installed putty on my office windows xp computer and I still cant connect.  The connection gets refused. I added port forwarding to my router and even checked iptables, still cant connect. If anyone has another hint or tip, I would really appreciate it.

Thanks again in Advance,

blumagic

---

### Post by steven_mckenz on 2007-01-10
> **Modernity said:**
> Ubuntu comes with VNC installed, so you have that covered. All you have to do is install VNC viewer on your computer at the office to connect. (I am not sure what kind of environment you are in at the office, so if you have an Adminstrator at the office, check with them first.)

The next step would be to aquire an IP address for your home. Which requires you to bridge your modem at home to use your router for forwarding your port to your Ubuntu machine.

Maybe I'm retarded, but I can't seem to find where VNC is installed at in Ubuntu.  I'm running 6.10 right now, and don't see it anywhere.  Can someone point me in the right direction?

Thanks!

---

### Post by xpod on 2007-01-10
I think what you are looking for is "remote desktop" which you`ll find under System>preferences.

---

### Post by blackened on 2007-01-12
For ssh you'll need to install the openssh-server package on your ubuntu machine. Because ssh is so prone (not necessarily susceptible, but prone) to brute force attacks, it might be a good idea to limit the ssh protocol to only your work domain with an iptables rule.  Also make sure you forward port 22 on your router for the ssh protocol.

---

