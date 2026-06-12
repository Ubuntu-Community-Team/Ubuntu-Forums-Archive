---
title: "Peer to Peer Networking Windows XP and Ubuntu 6.06"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by cde on 2007-02-28
I'm very new to the Linux operating system and I'm pretty unfamiliar with the Linux commands. Is there anyway to set up a peer to peer network between Windows XP and Linux using the Ubuntu GUI? I have the Windows machine configured how I would for networking to another Windows XP and Ubuntu seems to recognize my NIC. It allows me to configure it but I'm not entirely sure how to complete the setup. My hope is to share the Windows' internet connection through the network so I have assigned a static IP address in XP and made the same IP address a host in Ubuntu. What can I do now?

Any posts appreciated, thanks.

---

### Post by chggr on 2007-02-28
If you want to exchange files between a Windows PC and a Linux PC, you normally use SAMBA. More info can be found either on this forum or here: [http://us4.samba.org/samba/](http://us4.samba.org/samba/)

If you want to share your internet connection, the PC that is directly connected to the internet must act as a proxy server. If this PC is running linux, all you have to do is install squid ([http://www.squid-cache.org/](http://www.squid-cache.org/)). If this PC is a Windows PC, you should enable Internet Connection Sharing (more info here: [http://www.practicallynetworked.com/sharing/xp_ics/](http://www.practicallynetworked.com/sharing/xp_ics/))

After the proxy server is set up, you should configure the other machines to send all their internet packets to that server in order to be forwarded to the internet. In ubuntu, this can be done by clicking on System -> Preferences -> Network Proxy -> Manual Proxy configuration. You fill in those fields with the IP address (LAN) of the Proxy Server and the port the proxy service is listening to. Thats it.

PS. I advise you to use an UBUNTU machine as a proxy server and not a windows machine, because a) Windows are VERY vulnerable and b) this machine will always be connected to the internet. So I think that the proxy server should be a linux box with a properly configured firewall. In that way, your LAN computers will be protected,

---

