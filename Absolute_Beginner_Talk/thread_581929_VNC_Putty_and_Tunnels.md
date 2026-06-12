---
title: "VNC Putty and Tunnels"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by k9brand on 2007-10-19
I have looked at the other threads and I haven't been able to solve this one.

I have putty installed, it can SSH to my server.  I have also set up tunnels in my Putty configuration.

I have done this exactly like I do in windows.  When I start VNC, I try to connect to:

localhost
localhost:1
localhost:2 ...etc

I first SSH into the server, then I try to VNC and It doesn't connect.   When I use Putty in linux, should I still try to connect to "localhost" when tunneling? 

I have also verified on my other computer that the VNC servers are working correctly.

---

### Post by bluefrog on 2007-10-19
if you are using linux then open a terminal and
```

ssh -L 5901:localhost:5900 your-user@your-remote-ip

```

then use VNC and connect to localhost:1

of course you should make sure first that you can connect to the VNC server in the first place.

James

---

### Post by Malibu Illusion on 2007-10-19
Well, if you're making this connection from Linux to another Linux/Windows box, you needn't use PuTTY.  You can do all of the required forwarding from the CLI:

```
ssh -p22000 -L 5900:localhost:5901 user@host.com
```

That, for example, will connect to host.com with username of "user" on port 22000.  It will then forward local port 5900 to port 5901 on host.com's box, which is the port your VNC server should be listening on.

You should then instruct VNC on your machine to connect to localhost port 5900.  This will then redirect down the tunnel to your server's port 5901 where the VNC server will be listening.

---

### Post by k9brand on 2007-10-19
It doesn't seem to be working...

I'm going to explain this more....

I am first connecting to an IP address using PUTTY and SSH... this IP is my load balancer.  I then use PUTTY to tunnel over to the webservers, which are using VNC server.

The load balancer is BSD and using putty I can connect fine to it.

[IMG]http://img.photobucket.com/albums/v225/elboaconstricto/puttysetup.jpg[/IMG]

Then I set up the tunnels and when I use VNC it just works (except in ubuntu)...

-------------------------------------------------------------------------------------------------
Also, when I try both of the 2 methods above, my load balancer gives the error-
$ channel 3: open failed: administratively prohibited: open failed
-------------------------------------------------------------------------------------------------

---

