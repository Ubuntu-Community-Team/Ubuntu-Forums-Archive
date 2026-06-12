---
title: "How do I configure TCP ports in Arch?"
date: 2008-03-31
forum: Arch and derivatives
---

### Post by handy on 2008-03-31
Having just installed Arch, & wanting to use torrents, I installed the Transmission torrent client which has served me very well on my Mac.

The problem I find I have is that ports are closed which stops me from accessing torrents.

Does anyone know how I can configure the TCP ports in Arch?  

Or can you give me a link to great info' on the subject?

Thanks in advance.

---

### Post by kpkeerthi on 2008-03-31
Arch has no firewall pre-installed unless you installed iptables or any of its derivatives intentionally. I would suggest you look in your [router]("http://portforward.com/") and forward appropriate ports.

---

### Post by handy on 2008-03-31
> **kpkeerthi said:**
> Arch has no firewall pre-installed unless you installed iptables or any of its derivatives intentionally. I would suggest you look in your [router]("http://portforward.com/") and forward appropriate ports.

Thanks for your reply.

I wonder about that, I have used quite a few different distro's on this hardware & never had to take such action.

I had better check out the Transmission web site, & pursue the problem there I think.

Thanks again for your help, you have pointed me in the right direction I think.

---

### Post by mips on 2008-03-31
iptables + [Firewall Builder]("http://www.fwbuilder.org/") should make it easy to specify tcp/udp ports.

Keep in mind you can run FB on any pc as it just genrates the required output for iptables and does not actually participate in the firewall process.

I always thought ip tables came as part of the kernel?

---

