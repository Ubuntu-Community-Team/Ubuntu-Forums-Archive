---
title: "Samba Issues"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-27
I installed Samba last night per the how-to on the forums.

Now that I have it installed how do I navigate to my wifes laptop on the LAN?
I pretty much just wanted to copy some video and music from her laptop to my ubuntu box...

I noticed that in the "places" menu there is now a "connect to server" and "network servers" choice but when I pull either up I can see an icon for "windows network" but there is nothing in the file???

---

### Post by jorn on 2006-09-27
Have you configured the laptops firewall to accept filesharing.
Might not be the problem.

---

### Post by thephantomlinguist on 2006-09-29
A couple of things to check:

1. Make sure you've set the workgroup in your Samba config to the same thing as your wife's laptop.
2. Make sure whatever folders you want to share are shared on your wife's laptop.
3. Make sure you have an account to log into those shares with (if your wife is the only user on the laptop and doesn't log in with a password, you may need to give her a password--windows is sometimes touchy about that).

Hope this helps!

---

### Post by hyper_ch on 2006-09-29
I dunno, maybe I misunderstand that.
I assume your wife uses windows right? If that is the case, then samba offers in the network a share on the linux box. This means, if write access is enabled, you can from the windows box put data into the samba share which will then be on the linux box and you can use that there..

---

