---
title: "Network neighbourhood"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-29
So, I have PC number 1 up and running, feisty, and even managed to connect a printer. Thanks to all who helped. Next step- computer number 2. The installation of feisty was easy, double booting with XP also no problem. But whereas I can see and connect to computer 2 from number 1 via SAMBA when number 2 is on windows, when it's on ubuntu I can't. Or more probably, I don't know where I should be looking. I'd sort of thought t would have been as easy as SAMBA (and it probably is)- but where does Ubuntu keep its equivalent of Network Neighbourhood?

---

### Post by Kobalt on 2007-05-29
I think Samba is for Windows/Ubuntu sharing, as SMB is Microsoft networking. Between 2 Ubuntu computers you can use SSH : go to Places > Connect to a server. Select SSH, give the IP address, login name and the folder you want to access, and here you go. You can now navigate, right from Nautilus, into your remote computer.

---

### Post by ginestre on 2007-06-02
Thanks for the reply. I followed, I thought well, but got this:

Could not open location 'ssh://richard@192.168.0.4/%5Chome' ACCESS DENIED


What did I do wrong?

---

### Post by ginestre on 2007-06-08
> **ginestre said:**
> Thanks for the reply. I followed, I thought well, but got this:

Could not open location 'ssh://richard@192.168.0.4/%5Chome' ACCESS DENIED


What did I do wrong?

OK, so it's a permission thing, I suppose. It looks to me as though I need to do some set up here, presumably on all machines, but how? My newly-purchased 'Linux cookbook'  tells me just to connect, that it's easy, and that the machines will work it out- but it's not true- same error as above. 

man ssh tells me to check and distribute my keys, (makes sense, but where do I keep them?) but I get this

 ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key: No such file or directory

Is there a step-by-step HOWTO somewhere for this?

---

### Post by ginestre on 2007-06-08
solved: I just needed to install the ssh server on EVERY machine. Then it works.

---

