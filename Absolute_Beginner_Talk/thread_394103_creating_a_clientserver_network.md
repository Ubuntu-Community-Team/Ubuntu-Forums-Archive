---
title: "creating a client/server network"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by freelancer1995 on 2007-03-26
ok, i am still new to ubuntu, but i am trying to replace my current windows client/server network with a linux client/server network.  can anybody point me the right direction?

here is my current setup.

windows 2003 server 
+ authenticating users(server side user management)
+ storing roaming profiles 
+ users "documents and settings"
+ file sharing, group shares
+ printer sharing
+ DCHP
+ Proxy
+ DNS
+ firewall
+ mirrored drives

windows xp pro workstations
+ part of the AD/domain
+ no locally stored user documents
+ authenticate from server

over the pass few years, i have been making the shift to open source products, ie; openoffice instead of microsoft office, or away from ms in general, ie; avoided ISA and using another proxy product.  can you help? 

thanks in advance

---

### Post by fakie_flip on 2007-03-26
For managing a Linux computer, you should use ssh. That requires a ssh server running on the computer. For sharing folders and printers with windows computers, Samba is used. However you do not need Samba to share printers with windows computers. I have done that with Cups. If you only plan to have file sharing with other Linux and unix computers, then use nfs. the software for a proxy server is called squid. The firewall in Linux is iptables. It is difficult to use, so many people use programs like shorewall or firestarter (has a gui) to configure the firewall. For installing Ubuntu with raid, this is a [good guide]("http://users.piuha.net/martti/comp/ubuntu/raid.html"). For all guides to all the other things I mentioned, you can look here at the [official ubuntu documentation for servers]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html") or here at the [community documentation for servers]("https://help.ubuntu.com/community/Servers").

---

### Post by freelancer1995 on 2007-03-28
thanks, that'll get me started :)

---

