---
title: "router port forwarding"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-07-02
Hi all,

if i forward my http requests  on port 80 for my webserver, how can i still use internet on the other computers behind my router?

Thanks.:popcorn:

---

### Post by Rhubarb on 2007-07-02
The other computers on the network should run fine on the internet, you don't need to change anything at all.

---

### Post by prostock3 on 2007-07-02
Thanks.  So if all web traffic is on port 80, and port 80 is forwarded to my server, then how does the web traffic get to my other computers.  I know there is a hole in my understanding of ports.  Could you please help clarify.

Thanks again.

---

### Post by Rhubarb on 2007-07-02
That's a very good question, and I can't answer that as it's above my understanding.
But I'll try this simple explanation:
You don't need to forward any ports to be able to look at a website that a client pc has requested, but you DO need to forward ports if your sever is expecting to receive unrequested traffic.

---

### Post by eternalsword on 2007-07-02
you only need to forward port 80 if you are running apache or similar server.  If you are running servers on multiple machines you'll have to look into some sort of virtual service that will dish off the requests to the proper server.

machines accessing websites connect to the outside servers' port 80, not their own.  hope that clears things up

---

### Post by HereInOz on 2007-07-02
Essentially, when you send out a request to a webserver (you want to view the web site), your computer sends a request to port 80 of the webserver containing the website.  The port used by your machine as the outgoing port is not port 80 - that is an inbound port only.  

Your NAT router then forwards that request to the remote webserver and assigns a port number for the response to be sent to.  The webserver responds to the port as assigned by the NAT router, which then forwards the response to the correct port on the correct machine.  

If you entered, in your browser address bar,  the address of the machine on your network which is receiving port 80 traffic,  eg, [http://server_IP_address](http://server_IP_address), then your webserver machine would respond and send back the response to whatever port your local computer had designated as the reponse port.

Hope this helps.

---

### Post by bikeboy on 2007-07-02
I may be wrong or only partially right, but the reason is that the data is sent in opposite directions. For your Desktop to access a webpage it starts with an outbound request on port 80, for others to access your server an inbound request would come to you. The Port Forwarding forwards inbound requests on port 80, but doesn't affect outbound.

---

### Post by eternalsword on 2007-07-02
this is basically how routers work.  for outgoing connections, the local machine sends it's ip address and the port it is currently using to the router as well as the ip address and port number it is connecting to.  the router then sends packet request signals and translates the local machine's ip address using Network Address Translation or NAT with the same port number.  The remote machine sends packets then to the NAT address which the router retranslates back to the local ip.

port forwarding is needed only where a remote machine is trying to send packet request signals to a local machine.  Since the local machine's address is behind NAT, the remote machine does not know which one it is, so the router must be told to forward those requests to a specific machine otherwise the router just drops the request.

---

### Post by prostock3 on 2007-07-02
Thanks all.  I think I got it.  Let me repeat with my setup:

I have:
1.  Linksys router.
2.  Laptop for webbrowsing
3.  Linux server


Say I want to open google webpage from laptop:

1.  Send request to google port 80 by first sending request to linksys router with info of response port of laptop.
2.  Then linksys sends request to google port 80 with linksys response port.
3.  Google sends back to response port specified by router.
4.  Router sends to laptop via response port specified by laptop.

If I want to setup my server with godaddy and i have dynamic external ip:
1.  Purchase domain name from godaddy.
2.  Use dyndns to create two name servers.
3.  Configure router to forward requests received on 80 to ip addy of server.
4.  Go to godaddy and add name servers created by dyndns.

Are these steps right?

After going through the steps, I came up with another question about step 3 for configuring dyn dns.  When you do port forward on router, are you forwarding port 80 of the router to the server? or some port of the router to port 80 of the server?  or port 80 of router to port 80 of server?


Thanks again for your explanations.  Now the picture is becoming more clear.

---

### Post by Bachstelze on 2007-07-02
And if you like a picture to sum it up :

[http://img214.imageshack.us/img214/1500/natuu5.png](http://img214.imageshack.us/img214/1500/natuu5.png)

As you can see, your router is on two networks : the internet, and your local network. It's the machine that does the "bridging" between the two.

Regarding your last question, you must keep in mind that there are two connections involved in the process, the connection between the internet machine and your router, and the connection between your router and your local machines. They don't have to be on the same ort, as most routers support forwarding on different ports.

For example, my ISP blocks incoming port 25, meaning that I can't recieve any connections on that port. Because I didn't want to go through the hassle of reconfiguring my mail server, I told my router to forward incoming port 2525 connections to the port 25 ot my router. So, when people do a 

```
telnet fkraiem.no-ip.org 2525
```

They're talking to my mail server, which is running on the port 25.

---

