---
title: "limiting remote login via ip address or network"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-03
I'd like to be able to use remote login on my network at home. I'm not sure how secure this will be though. Is there anyway to limit logins only to a specific ip address or address range?

---

### Post by oerd on 2008-02-04
Do you mean graphical remote login or just shell?

A secure answer to both is sshd (openssh daemon). You can allow login only by authorization keys (DSA) and even run it with the -X option to allow the remote graphical applications to use your *local* X server.

There are many tutorials out there how to set up a secure shell server and client and further secure it. A strong advice: disallow password login, and generate public/prite key pairs for login, also think of a good passphrase to encrypt your private key locally... but any serious guide would tell you that ;)

---

### Post by Liet_Kynes on 2008-02-05
I have setup ssh and that's working okay. I was just wondering if there was a way to set up a set of rules for which ip ranges or networks are allowed to access gdm via xdmcp.

---

### Post by oedha on 2008-02-05
maybe you can try firestarter.......
basically firestarter is just the GUI version of iptables

---

### Post by Liet_Kynes on 2008-02-05
I remember setting up something similar a couple of years ago (not sure how relevant this is anymore) with a file called hosts.allow. (I think it was a firewall ruleset i'm not sure anymore :)) does the default installation of ubuntu enable a firewall and if so where do i configure it?

---

### Post by oerd on 2008-02-05
You are right, you may want to take a look at hosts_access(5) and hosts_options(5) man pages for more information. It is a ruleset for the tcpwrapper and portmapper IIRC.

Also, if you want a full blown firewall then firestarter is probably your best bet.

--
have fun.

---

