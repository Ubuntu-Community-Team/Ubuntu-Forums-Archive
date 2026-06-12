---
title: "How do you check ssh port forwarded"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-20
I have successfully remoted into my XUbuntu server using Putty and TightVNC while inside my network.

I'm having trouble connecting from outside (internet)... I've my router port forwarded and changed my sshd_config file... is there something else to change?

Is there a command/utility that checks open ports on the server?

---

### Post by SomethingCronic on 2008-03-20
If it works internally, then it looks like your router is the issue. If you have a box outside the network I would suggest installing nmap to scan the gateway.

---

### Post by BlizzofOZ on 2008-03-20
> **SomethingCronic said:**
> If it works internally, then it looks like your router is the issue. If you have a box outside the network I would suggest installing nmap to scan the gateway.

I was doing just that!!!

Ok, the port that I have setup to forward in NOT listed when I do nmap localhost.  I do see the default 5901/tcp open vnc-1.

I may have been looking at this the wrong way...  

Say I want port forward 12345, for outside VNC.  Normally, the server used port 5901.
So, do I forward port 12345 in the router to the server IP and change the sshd_config file to have port 12345 in it?

---

### Post by wormser on 2008-03-20
Take a look at [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> Take a look at [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Thanks, I've done that... 

I just can't get TightVNC to connect over the internet.  I have setup a domain name with dyndns.com.

How exactly do you put in the name/ip in TightVNC?

Say my dns hostname is ozzy.homelinux.com?

How would I enter this into TightVNC?
ozzy.homelinux.com  ?
ozzy.homelinux.com:12345 ?

---

### Post by wormser on 2008-03-20
If you are going over the internet you should tunnel VNC with ssh.  Port forward ssh only. 

```
ssh -C -p 1234 -L 5900:localhost:5900 user@domain.com
```

-C is for compression
-p is for port number
-L binds your local port to the remote port

```
xvncviewer localhost:5900
```

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> If you are going over the internet you should tunnel VNC with ssh.  Port forward ssh only. 

I have Putty to tunnel... how do you enable TightVNC to tunnel?

```
ssh -C -p 1234 -L 5900:localhost:5900 user@domain.com
```

-C is for compression
-p is for port number
-L binds your local port to the remote port

```
xvncviewer localhost:5900
```

What does this command do?

---

### Post by wormser on 2008-03-20
> **BlizzofOZ said:**
> What does this command do?

Tunnels VNC through ssh.  Port forward ssh only.  Run the first command to connect then the second to open VNC.

---

### Post by BlizzofOZ on 2008-03-20
```
ssh -C -p 1234 -L 5900:localhost:5900 user@domain.com
```

What would be the [email]user@domain.com[/email] be?  Would that be the dns hostname I setup?

By the way, thanks for helping!!!

---

### Post by wormser on 2008-03-20
> **BlizzofOZ said:**
> ```
ssh -C -p 1234 -L 5900:localhost:5900 user@domain.com
```

What would be the [email]user@domain.com[/email] be?  Would that be the dns hostname I setup?

By the way, thanks for helping!!!

Your user name and the ip or domain name of the machine you are trying to connect to.

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> Your user name and the ip or domain name of the machine you are trying to connect to.
 
So, using my example above and assuming my username for Ubuntu is john, I would do:


ssh -C -p 12345 -L 5900:localhost:5900 [email]john@ozzy.homelinux.com[/email]  

forwarded port:  12345
user: john
dns name setup at dyndns:  ozzy.homelinux.com

Is that right???

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> Tunnels VNC through ssh.  Port forward ssh only.  Run the first command to connect then the second to open VNC.

Does that not run the viewer?  I want to run TightVNC from my Win PC at work, to access my server at home.

---

### Post by wormser on 2008-03-20
> **BlizzofOZ said:**
> Does that not run the viewer?  I want to run TightVNC from my Win PC at work, to access my server at home.

The first command connects you to the remote machine with ssh and binds your local port to the remote port.  The second on opens the VNC viewer to your local port which is now the remote port because of the first comman.  Run the first command then:

```
xvncviewer localhost:5900
```

---

### Post by BlizzofOZ on 2008-03-20
wormser,

Could you answer my previous question also... I want to make sure I have user and domain thing straight.

---

### Post by wormser on 2008-03-20
> 
ssh -C -p 12345 -L 5900:localhost:5900 [email]john@ozzy.homelinux.com[/email]


That looks right.

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> That looks right.

I don't think this is what I want to do...
This seems to have logged me on as [email]john@ozzy.homelinux.com[/email]

I'm trying to use TightVNC to connect to my server thru the internet.  I trying to see/understand how the 
forwarded port interacts with the server.

When I run nmap localhost, I get:
PORT    STATE  SERVICE
80/tcp  open     http
139/tcp open   netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open ipp
3306/tcp open mysq1
5901/tcp  open vnc-1
6001/tcp  open X11:1

Where does the port that I forwarded come here?

---

### Post by wormser on 2008-03-20
This is exactly what you want to do.  The ssh part just makes it secure.  You log in with the first ssh command.  Then open another terminal and run the second command.

---

### Post by BlizzofOZ on 2008-03-20
> **wormser said:**
> This is exactly what you want to do.  The ssh part just makes it secure.  You log in with the first ssh command.  Then open another terminal and run the second command.

I'm sorry if I'm not following you...

Where exactly does TightVNC come in?

---

### Post by wormser on 2008-03-20
Are you able to ssh into the remote machine?  You run the first command in one terminal to connect.  The second command opens the VNC session.


```
ssh -C -p 12345 -L 5900:localhost:5900 john@ozzy.homelinux.com 
```

In another terminal:
```
xvncviewer localhost:5900
```

---

### Post by BlizzofOZ on 2008-03-21
> **wormser said:**
> Are you able to ssh into the remote machine?  You run the first command in one terminal to connect.  The second command opens the VNC session.


```
ssh -C -p 12345 -L 5900:localhost:5900 john@ozzy.homelinux.com 
```

In another terminal:
```
xvncviewer localhost:5900
```

Well, sitting from home I can open ssh using Putty to my dns hostname, on the port I forwarded.  I assume this via the internet as I'm using the dns as opposed to the local IP address.

Unfortunatly this morning, I am working from home.  I can connect to my work's network via VPN.  I've tried to ssh thru Putty, via VPN, but no go.  Not sure if VPN is a roadblock in trying to do this...

---

### Post by SomethingCronic on 2008-03-21
Lets look at what you are trying to acheive. If you want secure remote connection, then you want SSH. If you want to be able to use graphic applications then I would suggest you use SSH with Xming.

Install putty on an external Windows PC along with Xming. Set X forwarding on Putty to localhost:0 then when you need to run x applications just type them in and they magically are brought forward to your screen. I don't think you need to mess around with VNC. All you should need to do is open up your SSH port on your router.

---

### Post by BlizzofOZ on 2008-03-21
> **SomethingCronic said:**
> Lets look at what you are trying to acheive. If you want secure remote connection, then you want SSH. If you want to be able to use graphic applications then I would suggest you use SSH with Xming.

Install putty on an external Windows PC along with Xming. Set X forwarding on Putty to localhost:0 then when you need to run x applications just type them in and they magically are brought forward to your screen. I don't think you need to mess around with VNC. All you should need to do is open up your SSH port on your router.


Yes, I want a secure remote connection to my GUI Xubuntu.

The reason I went with TightVNC is because they have a non-installable application viewer.  Meaning, I need the viewer app to run/execute and NOT install.  Reason: I want to do this at my work laptop, but I don't have admin capabilities to install software.

---

