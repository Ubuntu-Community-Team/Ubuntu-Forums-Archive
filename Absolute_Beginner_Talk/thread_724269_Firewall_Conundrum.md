---
title: "Firewall Conundrum"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by dogdog on 2008-03-14
I am an experienced Windows user but new to Linux.
I have a Dell PC with Windows Vista Ultimate as the operating system. I have a second older Dell PC on which I have just installed Ubuntu (v 7.10) – Ubuntu installation via downloaded image for alternate installation disk (I only have 128MB of RAM on older PC).
I am trying to set up a home network with these two PC’s. I have a cable modem to a wired Linksys Router with the 2 PC’s connected to router. In particular I want to see the ubuntu PC from the Vista PC and transfer files from Vista PC to Ubuntu PC. I have finally succeeded but with one particular conundrum that I just do not understand.
Having set up the ubuntu PC – file sharing, workgroup name, samba installation and configuration etc – the only way I can access the shared folder on the ubuntu PC from the Vista PC is to disable the firewall using Firestarter. However, perversely, if I set an inbound traffic policy rule using Firestarter to allow the Samba (SMB) service via ports 137-169 445 for the IP address of my Vista PC, then I can restart the firewall and retain the connection between the 2 PC’s.
If I then restart the ubuntu PC I have to go through the same process of disabling the firewall to obtain a functioning link to access the ubuntu PC from the Vista PC (even though the inbound traffic policy rule remained in place). Again I can then restart the firewall and keep the PC to PC link.
Can anyone explain to me what is going on???

As a supplementary:
My access to the shared folder on the ubuntu PC seems to be without any security. Is there some way to enforce passwords or to only allow access from my specific Vista PC?
Many thanks in anticipation.

---

### Post by dogdog on 2008-03-14
A supplementary query:

I have just come accross another linux firewall - Guarddog.

Is Guarddog compatible with ubuntu??

Which is better Guarddog or Firestarter??

---

### Post by hyper_ch on 2008-03-14
neither firestarter nor guarddog are firewalls... the firewall included in the linux kernel is called iptables. Guarddog and firestarter are just graphical interfaces for basic configuration of it...

In most cases you don't need either one however, as I learned not too-long-ago, once you install firestarter there will be rules set...

---

### Post by dogdog on 2008-03-14
I understand that Firestarter and Guarddog are not firewalls but the front ends to simplify the rule setting - I was using the term losely - sorry.

Still awaiting an answer to my connundrum and my comparison query.

---

### Post by dogdog on 2008-03-14
> **hyper_ch said:**
> neither firestarter nor guarddog are firewalls... the firewall included in the linux kernel is called iptables. Guarddog and firestarter are just graphical interfaces for basic configuration of it...

In most cases you don't need either one however, as I learned not too-long-ago, once you install firestarter there will be rules set...


What did you mean by "once you install firestarter there will be rules set"??

---

### Post by timcredible on 2008-03-14
you're spending a lot of time and effort on something you don't need.  run the linux machine without a firewall.  unless you have a server application running that's actively listening on a port, there's nothing to protect with iptables.  and yes, guarddog and firestarter are just GUI frontends to iptables.

---

### Post by dogdog on 2008-03-14
BUT why is the conundrum occuring?? It always worries me when something is happaning that just seems crazy!!

---

### Post by dogdog on 2008-03-14
MY PC link will not work unless I first use Firestarter to disable firewall. Without this the LAN does not work!! Even though I can then use Firestarter to restart firewall and LAN remains OK.

How does this make sense???

---

### Post by EvilBro on 2008-03-14
> **dogdog said:**
> Even though I can then use Firestarter to restart firewall and LAN remains OK.
I think I've experienced this once. If the connection is active (established), it will remain even if the rules wouldn't normally allow that. My guess is that if you ifdown/ifup your network interface, you won't be able to connect to the LAN.

---

### Post by dogdog on 2008-03-14
I do not think that this can be the answer as the connection is only preserved with firewall restarted if inbound policy is set; without this the connection is not preserved??

---

### Post by EvilBro on 2008-03-14
> **dogdog said:**
> I do not think that this can be the answer as the connection is only preserved with firewall restarted if inbound policy is set; without this the connection is not preserved??
Is this statement the result of you actually trying what I said or are you just going with your gut?

---

### Post by dogdog on 2008-03-14
Your statement is correct. Had already observed that. But if your explanation were correct then it would not matter what inbound rules applied when firewall was resarted; as it does matter your explanation that connection is just preseved cannot be right - the connection is not preserved unless inbound policy rule exists.

---

### Post by EvilBro on 2008-03-14
> **dogdog said:**
> as it does matter your explanation that connection is just preseved cannot be right - the connection is not preserved unless inbound policy rule exists.
This is not how I remember it, but I guess I'm simply mistaken. That being the case I cannot help you as I have left Firestarter for Shorewall (Firestarter would just not do what I wanted it to do when it came to VPN).

---

### Post by hyper_ch on 2008-03-14
well, in another thread I was told that once you isntall firestarter that it will close all ports and then you have to open them... while by default no port is closed..

---

### Post by The Cog on 2008-03-14
There are two possible reasons for your conundrum:

1)
Making the initial connection requires some other protocol, like a service location query, and you have not enabled this other protocol in.

2)
The iptables rules the firewall sets include a rule to permit established connections to continue, but otherwise don't allow the protocol that you are using at all.

Ihave no idea which of the two it might be. Try getting your firewall to log dropped packets and see if you can make sense of the log.

---

### Post by EvilBro on 2008-03-14
> **The Cog said:**
> Try getting your firewall to log dropped packets and see if you can make sense of the log.
I think this is already done in syslog if I remember correctly...

---

### Post by dogdog on 2008-03-14
Very grateful for everybody's comments and help.

> **hyper_ch said:**
> well, in another thread I was told that once you isntall firestarter that it will close all ports and then you have to open them... while by default no port is closed..

I suppose the fundamental question is - if firestarter is running with an appropriate inbound traffic policy rule [allow samba (SMB)] - why doesn't the LAN work OK?? If firestarter closes all ports then inbound traffic policy allows samba (ie opens the required ports) then surely I shouldn't then need to disable firewall for LAN to work??

---

