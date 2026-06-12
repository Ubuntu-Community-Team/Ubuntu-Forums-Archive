---
title: "Not Connecting to Wired Network Automatically"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Gibran on 2007-03-29
Hello. I have a single connection on the computer and each time it loads I have to click on the connection icon on the tray and select "wired connection" to enable it. How can I make it use the same connection each time I boot up Linux? Thanks in advance!

---

### Post by david_kt on 2007-03-29
Edit your fstab to mount it automatically.

DK

---

### Post by compwiz18 on 2007-03-29
> **david_kt said:**
> Edit your fstab to mount it automatically.

DK

Wait - isn't fstab for filesystems, not network connections?

---

### Post by david_kt on 2007-03-29
It could mount network connection as well. Even if you need to key in user name and password, both could be done automatically i.e. we do not need to key in anymore.

Offcourse you will need to install some applications if needed (for example smbfs), depend of what kind of network connection you have. And the command to mount network connection is slightly different.

DK

---

### Post by Gibran on 2007-03-29
Do you know what steps I would need to take to do this? It was done automatically before I upgraded to Feisty, and I have a broadband connection that does not require a password. (I am fairly new to Linux, hehe) Thanks again!

---

### Post by david_kt on 2007-03-29
When you said "broadband connection", I think we are talking a completely different issue. Do you mean you want to connect to internet? I thought you want to connect to other computer/server in the network that is way I said to edit fstab.

If you want to connect to internet, you just need to configure your network card. I am still using dapper now, but I guess it is quite similar:

Admin>networking

And see if your network card is detected. If yes, make sure it is activated, and configure according to your broadband setting (check with your provider, or modem that you use).

DK

---

### Post by tonyr1988 on 2007-03-29
Try going to System >> Administration >> Networking and see which ones pop up in the list. If there are others, try to de-activate them (double-click them and uncheck the "Enable" box). Maybe it's trying to use another connection by default. Maybe not, but it's worth a shot, right? :)

---

### Post by zvacet on 2007-03-30
In Feisty connection is set by network manager,but it is not good enough(from my point of view).Remove it.
[http://ubuntuforums.org/showthread.php?t=385975&page=3&highlight=network]("http://ubuntuforums.org/showthread.php?t=385975&page=3&highlight=network")
Read last post.

---

