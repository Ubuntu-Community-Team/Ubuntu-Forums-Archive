---
title: "Config SSH"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-21
How do I configure SSH? Or are there no settings to be made?

I just installed SSH-server with apt-get (guidance from [http://ubuntuguide.org)](http://ubuntuguide.org)). How do I configure what a SSH should do, what the password should be etc? Should I make a special user account for SSH? Is it likely my router will be a problem? What ports do I need to open?

Thanks a million times for helping us newbs oh great masters of Linux. :)

---

### Post by Wombley on 2005-06-21
[QUOTE=Trojan1313]How do I configure SSH? Or are there no settings to be made?

I just installed SSH-server with apt-get (guidance from [http://ubuntuguide.org)](http://ubuntuguide.org)). How do I configure what a SSH should do, what the password should be etc? Should I make a special user account for SSH? Is it likely my router will be a problem? What ports do I need to open?

Thanks a million times for helping us newbs oh great masters of Linux. :)[/QUOTE]

It'll work without new users, just connect with a ssh client and log in with a system account (your login name and password). There are some settings you can change (such as disabling root access) - these are in the file /etc/ssh/sshd_config . For going through a router you'll have to forward port 22 to your machine to access it from outside the network.

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=Wombley]It'll work without new users, just connect with a ssh client and log in with a system account (your login name and password). There are some settings you can change (such as disabling root access) - these are in the file /etc/ssh/sshd_config . For going through a router you'll have to forward port 22 to your machine to access it from outside the network.[/QUOTE]
 What Linux-mode should I be in then? Should I be at the login screen or what?
Didn't work the first time whe I tried SSHing from within the network.

EDIT: Got it working, it seems Linux has another IP within the network. :)

---

### Post by Wombley on 2005-06-22
[QUOTE=Trojan1313]What Linux-mode should I be in then? Should I be at the login screen or what?
Didn't work the first time whe I tried SSHing from within the network.[/QUOTE]

As ong as the machine is switched on with the sshd service running it should work (so the login screen should work). Try, at a terminal, typing: 

sudo /etc/init.d/ssh restart

And try connecting again

---

