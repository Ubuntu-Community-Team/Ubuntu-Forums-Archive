---
title: "Simple Computer Communication"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-03-04
i'm trying, oh so hard, to set up an ftp server. my only problem seems to be that people who are outside of my router can't access my server, because i can't get my server to run off of my external IP address. how do i do that?

please please PLEASE. somebody help me. this is killing me.

---

### Post by Whiffle on 2008-03-04
What you need to do is set a static IP for your server on your local network.  Next, forward the ftp port you'd like to use (the usual one is 21 iirc), to that static address.  In theory, that should work.

---

### Post by Rocket2DMn on 2008-03-04
You need to enable port forwarding in your router.  Standard FTP uses port 21, SFTP uses port 22 (the same as ssh).  How you go about that is specific to your router make/model, so refer to the user manual which you can find on google.
The port needs to be forwarded to your internal IP address which you can see by running
```
ifconfig
``` in terminal.

---

### Post by Sinkingships7 on 2008-03-04
> **Whiffle said:**
> What you need to do is set a static IP for your server on your local network.  Next, forward the ftp port you'd like to use (the usual one is 21 iirc), to that static address.  In theory, that should work.


is there any way that you could explain that to me? everywhere i go, i see people telling me to simply "set up a static ip". alas, that is my problem. i have not a single clue how to go about doing that.

---

### Post by Whiffle on 2008-03-04
Sure thing!  What kind of router do you have?

---

### Post by Sinkingships7 on 2008-03-04
thank you so much.

i'm behind a D-Link DI-604

---

### Post by Whiffle on 2008-03-04
I had this all typed up then I hit the back button and lost it.  Here goes again:

1) Go to [http://192.168.0.1](http://192.168.0.1)
2) Put in your routers admin name/password
3) Click the DHCP button on the left panel
4) Scroll down to the Static DHCP section
5) Enter the name of your server
6) Pick an IP address for your server.  On mine it has to be greater than 151 otherwise it interferes with the DHCP service and screws everything up. 
7) Open up a terminal on your server and run ifconfig, it will give you a list of network interfaces.  We need the MAC address of your network interface, I put stars around it below:
```

eth0      Link encap:Ethernet  HWaddr *00:10:C6:DD:82:27*
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

```
Type that into the MAC address field, without the colons.
8) Click the apply button

Next, go to the advanced tab.

It seems that D-link calls the port forwarding function "Virtual Server", which might be the source of your confusion.
Anyway, put name of your server, the ip address we just assigned to it, set the protocol type to TCP, and then select ports.  The standard one is 22 for ftp, and is the one that is default for ubuntu.  Put 22 and 22 in these two boxes.  Then click the Always radio button, and click apply.  

That should be it on the router end of things.  You'll want to restart your computer or just the networking for it to get the new ip address from your router.  If everything is working correctly, you should be able to get to your ftp server from the outside world by putting in your public ip address (the one assigned to your router by your ISP, listed under Status, under the WAN section).

For example:

[ftp://123.456.678.888](ftp://123.456.678.888)

Hopefully that'll work for you.  *crosses fingers*  Any questions just ask.

---

### Post by Rocket2DMn on 2008-03-04
To restart networking, you can do
```
sudo /etc/init.d/networking restart
```
Otherwise a reboot works great, too (though you rarely ever NEED to reboot a linux machine).
Port 22 is for SFTP (which should be what Ubuntu uses).  Port 21 is standard FTP which you might be using if you're using a different ftp program.  You probably already know which port you're using.

---

### Post by Sinkingships7 on 2008-03-04
> **Whiffle said:**
> I had this all typed up then I hit the back button and lost it.  Here goes again:

1) Go to [http://192.168.0.1](http://192.168.0.1)
2) Put in your routers admin name/password
3) Click the DHCP button on the left panel
4) Scroll down to the Static DHCP section
5) Enter the name of your server
6) Pick an IP address for your server.  On mine it has to be greater than 151 otherwise it interferes with the DHCP service and screws everything up. 
7) Open up a terminal on your server and run ifconfig, it will give you a list of network interfaces.  We need the MAC address of your network interface, I put stars around it below:
```

eth0      Link encap:Ethernet  HWaddr *00:10:C6:DD:82:27*
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

```
Type that into the MAC address field, without the colons.
8) Click the apply button

Next, go to the advanced tab.

It seems that D-link calls the port forwarding function "Virtual Server", which might be the source of your confusion.
Anyway, put name of your server, the ip address we just assigned to it, set the protocol type to TCP, and then select ports.  The standard one is 22 for ftp, and is the one that is default for ubuntu.  Put 22 and 22 in these two boxes.  Then click the Always radio button, and click apply.  

That should be it on the router end of things.  You'll want to restart your computer or just the networking for it to get the new ip address from your router.  If everything is working correctly, you should be able to get to your ftp server from the outside world by putting in your public ip address (the one assigned to your router by your ISP, listed under Status, under the WAN section).

For example:

[ftp://123.456.678.888](ftp://123.456.678.888)

Hopefully that'll work for you.  *crosses fingers*  Any questions just ask.

I am almost positive that that worked. I can now connect from my own computer, but tomorrow, I will test it to see if another person can connect.

i'm pretty sure it's connecting. i do get one problem. on the client, when i try to connect, it goes through everything it should and looks okay, but at the end it says something along the lines of "failed to list directory.

but that may be because i'm on my own machine. i'll post back tomorrow.

thank you so much.

---

### Post by hyper_ch on 2008-03-04
you need to forward port 20 and 21 from your router to your computer. Best to use a static IP in your lan.

---

