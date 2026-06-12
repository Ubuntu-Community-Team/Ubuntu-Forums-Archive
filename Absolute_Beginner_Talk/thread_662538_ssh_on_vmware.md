---
title: "ssh on vmware"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by mabathom on 2008-01-09
Hi guys, 

I'm running ubuntu on VMWare and XP as a host OS. when I try to run the ssh command I get this error message "Name or service not known", and the name of the server is correct.

what could be wrong?

please help!!!!

---

### Post by hyper_ch on 2008-01-09
Did you install openssh-server?

---

### Post by mabathom on 2008-01-09
Hi, thanks for your response,

yes I did install openssh -server but it still gives me that error message, do you thing I should change network settings.

---

### Post by hyper_ch on 2008-01-09
can you, on the server, ssh into itself?

```

ssh root@localhost

```

---

### Post by CadetD on 2008-01-09
> **hyper_ch said:**
> can you, on the server, ssh into itself?

```

ssh **root**@localhost

```

Usually, SSH comes with ROOT remote access disabled. So just do:
  
   [COLOR="Blue"]ssh localhost[/COLOR]

---

### Post by hyper_ch on 2008-01-10
> **CadetD said:**
> Usually, SSH comes with ROOT remote access disabled. So just do:
  
   [COLOR="Blue"]ssh localhost[/COLOR]

Define "usually" ;)

"Usually" on a debian server it comes with root remote access enabled ;)

---

### Post by firestorm_v1 on 2008-01-10
Hmm...

I'm going to go out on a limb here and guess at a lot..

Host is XP, Guest is Ubuntu.
Guest has openssh-server and I assume that you're using something like PuTTY as the ssh client on the XP machine?

Have you tried using the IP of the network interface on your Ubuntu server?  Unless your network has DNS which resolves to the IP of the Ubuntu VM, Putty will barf on trying to DNS resolve that name.

---

