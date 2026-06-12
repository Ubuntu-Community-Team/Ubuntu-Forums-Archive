---
title: "Can't ping router"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by cherm on 2007-09-19
I am having problems networking my linux box and windows box via samba.  I have read Stormbringer's awesume howto on how to setup a peer to peer with windows.  I have followed his instructions to the tee, but am still having problems.

I think my problem may be in communication with the router.  I can successfully ping the router with my windows machine, but when I try to ping either my windows box or the router I get a Destination Host Unreachable error.  I do have internet connection via this router.

Can someone give me some guidance as to "fix" the connection with the router and/or windows box?  Any help is appreciated.

---

### Post by finer recliner on 2007-09-20
which machine cannot ping the router?

if its linux open a terminal and type
```
ping 192.168.1.1 
```

this will ping the router. 

while you the terminal open type this as well:
```
ifconfig 
```
this will return your IP address (as inet addr) in one of the available interfaces
(eth0 is your ethernet port, eth1 is wifi)

if you are correctly connected to the router, your ip address will probably be 192.168.1.x where x is another number > 255

if you are having troubles in windows:
do start > programs > accessories > command prompt
type "ipconfig" (without quotes) and that will return your IP address. once again it should be 192.168.1.x

you can also ping the router the exact same way as in linux (but in the windows command prompt)

hope this helps a bit

---

### Post by HermanAB on 2007-09-20
Verify your IP setup with 'ifconfig' and 'route'.  The IP addresses of all machines must be in the same subnet and you should have a default route pointing to your gateway.

See this guide for debug tips: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by cherm on 2007-09-22
Thanks for the replies fine recliner and HermanAB.  Fine recliner - my linux box can not ping the router.

HermanAB - can you expand on what is meant by "should have a default route pointing to your gateway".  What is a default route?

cherm

---

### Post by st33med on 2007-09-22
Usually, routers do not allow pinging to them. This is so it is secure to buffer overflows. To disable this default action, go into your favorite web browser, type '192.168.1.1' (or, sometimes it is '192.168.100.1') and find the option that makes WLAN pinging disabled.

---

