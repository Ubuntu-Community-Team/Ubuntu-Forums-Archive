---
title: "how do I close port 23 Linux Mint"
date: 2011-03-31
forum: Any Other OS
---

### Post by donec on 2011-03-31
I know there is already a thread with this title, almost, but it is solved and the solve did not work for me. So I am creating a new thread.

I ran ShieldsUp and it reports that my port 23 Telnet is open. I have heard that having it open is not safe and I have heard that it doesn't matter if you do not have Telnet running. In truth I don't know and don't really care I just want it closed to err on the side of caution. Now here is what I have tried, what I have run and the results....
```
don@NV53A-MINT ~ $ sudo netstat -tunap|grep 23
[sudo] password for don: 
don@NV53A-MINT ~ $ 
```I think this tells me I have nothing using port 23.

```
NV53A-MINT ~ # ufw deny 23
Skipping adding existing rule
NV53A-MINT ~ # ufw enable
Firewall is active and enabled on system startup
NV53A-MINT ~ # ufw status
Status: active

To                         Action      From
--                         ------      ----
23                         DENY        Anywhere

NV53A-MINT ~ # 

```

I think this tells me I am running my firewall and my Firewall is set to not allow any traffic on port 23. 

I rebooted after doing that.

However ShieldsUp still reports my port 23 open.

How do I close it.

---

### Post by dgw on 2011-03-31
It's probably not your port 23 that's open. I would guess that you have a router and are sharing the internet connection with other people. One of them is running a service on port 23 and has it forwarded to their computer by the router. Assuming you're at home, if you don't know who is using port 23, look at the port forwarding section in your router's interface and see who port 23 is being forwarded to.

---

### Post by cwa on 2011-03-31
I know this isn't directly related  to your question. But if you use nmap to scan your local machine, you can see ports open as well as other information. 
you can also use ps aux to see a list of running services.

More of FYI

I agree with dgw, if you do have port forwarding turned on in the router, you can disable that or if you need Telnet. You can look into ssh, scp.

cwa

---

### Post by The Cog on 2011-03-31
This command: **netstat -lnt** will show what ports are open on your system. Telnet is almost certainly not amongst them.

My guess is that your router is accepting telnet connections. I found my new tp-link router accepts telnet and ftp from the internet by defualt, which horrified me. On the tp-link router, I fixed it by configuring a "virtual host" in the NAT configuration so that it has to forward all incoming connections to an internal server (which doesn't reply in my case).

---

### Post by donec on 2011-03-31
My wireless hot spot will not allow me to turn off Port Forwarding and shows that under port forwarding protocol both is selected.

Under NAT Setup I have DMZ Host Enabled, for the last 2 digits in my Host IP and under application I have FTP enabled but not SIP. Remote Administration and VPN passthrough are not enabled.

Are any of these enabled settings needed?

---

