---
title: "Creating a Static IP Address"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-24
Me and a friend are trying to port forward some ports for his BitTorrent client using this [guide]("http://portforward.com/english/routers/port_forwarding/Edimax/AR-7064G+A/Utorrent.htm") as his router is a *Edimax AR-7064G+A*. We need to create a Static IP address to continue but have no idea how to. Can someone please explain in very **basic** steps? Thanks. We can also post whatever information is needed (I hope). We are on Ubuntu 7.10 Gusty Gibbon.

Cheers guys.

---

### Post by HereInOz on 2008-02-24
First, find out the IP addresses of your ISP's DNS servers.

Go to System > Administration > Network, put in your password, and find your active network connection. Click on Properties and then:

1. Disable roaming mode
2. Select the option of Static IP address
3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)
4. Enter the IP address of your gateway in the appropriate field.
5. Click OK

Then in the network dialog box, click on the DNS tab, and enter the address(es) of your ISP's DNS servers and then click close.

You may then need to restart your network interface.

---

### Post by Crumpets and Jam on 2008-02-24
> **HereInOz said:**
> First, find out the IP addresses of your ISP's DNS servers.

Thanks for the response.

How would I find out this information? Thank you again.

---

### Post by ScottyBoyNow on 2008-02-24
Write down the old DNS servers that you are using (should be dispayed in a info menu) or use OpenDNS server (which are faster).

---

### Post by steveneddy on 2008-02-24
The link to the instructions ask for the static IP address of your router.

It is already set from the factory.

Just type in the address of your router.

Easy.

Most routers have the address of

192.168.1.1 or 192.168.0.1

This a private IP address available only on a local LAN and cannot be used outside of your home LAN, like on the internet.

---

### Post by superprash2003 on 2008-02-24
open dns server ip's are 208.67.222.222 and 208.67.220.220

---

### Post by kooolrock on 2008-02-24
> **ScottyBoyNow said:**
> Write down the old DNS servers that you are using (should be dispayed in a info menu) or use OpenDNS server (which are faster).
i did this. it works

---

### Post by Grone1985 on 2008-02-25
> **HereInOz said:**
> First, find out the IP addresses of your ISP's DNS servers.

Go to System > Administration > Network, put in your password, and find your active network connection. Click on Properties and then:

1. Disable roaming mode
2. Select the option of Static IP address
3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)
4. Enter the IP address of your gateway in the appropriate field.
5. Click OK

Then in the network dialog box, click on the DNS tab, and enter the address(es) of your ISP's DNS servers and then click close.

You may then need to restart your network interface.

Could anyone explain more in detail steps 3 and 4 please?
Thanks in advance!

---

### Post by Crumpets and Jam on 2008-02-25
> **Grone1985 said:**
> Could anyone explain more in detail steps 3 and 4 please?
Thanks in advance!

Yeah, it would be appreciated.

---

### Post by jan quark on 2008-02-25
here is my static ip configuration
see attachment

the ip is my laptop ip

the subnet mask is standard

and the gateway is the ip of my router

---

### Post by philinux on 2008-02-25
I use Deluge and there is hardly any setup at all. It just works.

---

### Post by akiratheoni on 2008-02-25
> **Grone1985 said:**
> Could anyone explain more in detail steps 3 and 4 please?
Thanks in advance!

I'm not an expert in networking but I'm taking it so maybe I can explain a little.

> 3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)
4. Enter the IP address of your gateway in the appropriate field.

Your gateway IP address means the IP address of your side of the router. As said before, to enter the configuration of the router, you typically use:

192.168.0.1 or 192.168.1.1

So now that you have your IP for your router, you simply choose an IP address which is in the same subnet, which means if your gateway's IP address is 192.168.0.1, you can pick, say, 192.168.0.2 or 192.168.0.3. If you can see your subnet, it should be:

255.255.255.0

Compare to your gateway's IP address:

192.168.0.1
255.255.255.0

Notice how the 255's each match the 192, the 168, and the 0. This means that if you're picking a static IP address, DO NOT change the 192, 168, or 0. ONLY change the 1 to a value of 2-255. So IP addresses you could pick could be:

192.168.0.103
192.168.0.54
192.168.0.7

Things like that. But keep the first 3 octets the same. (The first three octets are the 192, 168, and 0)

I probably got some terminology wrong but it's the very basics of networking. It gets a LOT more complicated than that but I'm not going to go into that because my knowledge is wrong.

Hope this helps!

---

### Post by Grone1985 on 2008-03-02
Thanks for the answer but it didn't work at all... I lost the connection when I tried that, completely and I think I set all the parameter correctly. So I don't know, any other ideas?
Thanks!

---

