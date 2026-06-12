---
title: "network problem-one of the two network not working"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2008-01-26
On one of my office computer i installed ubuntu. this computer has two network cards. first one for internet and other for local intranet. the local intranet is not working while the internet card is working.

can anyone help me resolving the problem?

---

### Post by mikeyphi on 2008-01-26
> **Guruprasad said:**
> On one of my office computer i installed ubuntu. this computer has two network cards. first one for internet and other for local intranet. the local intranet is not working while the internet card is working.

can anyone help me resolving the problem?

Look under Systems/Administration/Network Tools......in the 'network device' window - scroll down to the intranet card and then select 'configure'....fill in the needed info in the new window.
It might also need to be enabled under System/Administration/Network

If the card is not listed here....check it is recognised under System/Preferences/Hardware  information.......

Post the results!!

---

### Post by Guruprasad on 2008-01-26
Hi thanks for the reply...

I have configured the network card. provided the necessary static IP address.

I tried pinging its own IP address, the result was sucessful. But it cannot access any other IP.

---

### Post by mikeyphi on 2008-01-26
> **Guruprasad said:**
> Hi thanks for the reply...

I have configured the network card. provided the necessary static IP address.

I tried pinging its own IP address, the result was sucessful. But it cannot access any other IP.

OK - so we know that the network card is good.
Now - to connect to your internal network, apart from the static address etc, you also have to add the domain name under the 'general' tab and check that DNS server and search domains are setup (under DNS tab)

You should also configure System/Administration/Shared Folders...which will prompt you to install Samba.

Post results!!

---

### Post by Guruprasad on 2008-01-27
DNS servers have been mentioned.

No search Domains are mentioned. What should be the search Domains? Normally for other computers on LAN we do not mention Search Domain.

Samba is also installed... Still no success..

---

