---
title: "Cannot Connect using PING, SSH, VNC"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by WilliamMiller54 on 2007-01-01
My environment is Active Directory with DNS and DHCP on a Win2003 domain controller. I have setup and configured Ubuntu 6.10 (CE 2.0) with a fresh install. I cannot PING, SSH, or Remote Desktop (VNC) into the Ubuntu box, but can connect through it by setting the browser proxy on a Windows box within the domain. 

Details: 
I have just installed Ubuntu 6.10 (Ubuntu CE 2.0). I can connect to the internet, and ping other computers from my internal network. Since this Linux box will be a web filter for my environment (TinyProxy and Danguardian) I have configured the browsers of my other computers to proxy through the Ubuntu box. This works, so I can confirm that the Ubuntu box is on the network, has access to the intranet, and internet. I can also confirm that other Window boxes in the environment can proxy to it. 

The problem is that I can not ping, remote desktop, ssh (putty) into the ubuntu box. When I look into by AD DNS I can see the Linux box is online. I Have created a Static IP for it and added it to the DNS, and have configured Ubuntu to use this IP. 

I have searched the forums but did not find any issues like this. I have reinstalled twice. Many reboots. Downloaded all updates.  I have verified that remote desktop (GNOME System – Preferences – Remote Desktop) is setup. I can vnc locally (vncviewer localhost:0) however  it continues to spawn multiple vnc sessions.  IFCONFIG shows the correct network settings. 

Thank you in advance!

- William -

---

### Post by seijuro on 2007-01-01
have you installed the openssh-server package you can not ssh in to the machine only ssh from the machine till you have it installed. It shouldn't need any post install config less you want to change the default port(22) for more security.

---

### Post by scrooge_74 on 2007-01-01
Also have you check your firewall config?

---

### Post by WilliamMiller54 on 2007-01-01
Thanks for the response.

> have you installed the openssh-server package
OPENSSH-Server has been installed and is enabled. When I try to PuTTy in I get "NETWORK ERROR: Connection Timed out".

>  Also have you check your firewall config?
So far I am not going outside a firewall. So it should not be an issue. All the boxes are connected to the same switch, and I can connect to the UBUNTU box using the proxy. So that would tell me that this is not a firewall issue ...... right?

---

### Post by halitech on 2007-01-01
to me it sounds like your firewall is doing what it's supposed to do by blocking all but what has been configured for access. if all your network settings are correct and you can't connect or ping but proxy is working, I'd bet dollars to donuts it's your firewall.

---

### Post by scrooge_74 on 2007-01-01
> **halitech said:**
> to me it sounds like your firewall is doing what it's supposed to do by blocking all but what has been configured for access. if all your network settings are correct and you can't connect or ping but proxy is working, I'd bet dollars to donuts it's your firewall.

I second this, it seems your firewall is keeping everybody out.  You should tell it to allow connections from the internal LAN

---

### Post by WilliamMiller54 on 2007-01-01
Well, I wish I could say that I found an error in the kernel that was blocking all incoming connections.   However, now is the time to change all my email addresses and logons, and not let anyone know that the “problem” was that Ubuntu CE 2.0 has Firehol (Firewall program) preloaded and configured. 

Thanks for the help, and boy do I feel foolish! ](*,) 

- William -

---

