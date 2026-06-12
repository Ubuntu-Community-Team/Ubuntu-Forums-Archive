---
title: "New to Ub.  Going on Vac next week and want remote acess to Ub.  Possible?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by mithbuntu on 2007-10-04
Greetings fellow ubuntuers (i hope that's a word.

First I would like to say that I am pretty new to the Ubuntu scene and linux/unix in general.  I have a little bit of experience, but I am by no means a master or even an adept.   That said, I am a rather quick learner and have decided it's time to learn a linux distro, so I am.

Moving on.   

I am going out of town for a little over a week tomorrow and I am bringing my macbook with me.  I have had a lot of experience connecting remotely to linux machines via "Chicken of the VNC" on my macbook, but no experience at all actually setting up a vnc server on my own.    I simply know how to ssh into the computer I'd like to RC to, then CL vncserver -geometry [dims] -depth [bits]. 

What I would like help with is directions/link to a guide/or a quick run through setting up a vnc server on my PC that I can remotely acess when I leave tomorrow.

I'd like to set this up so I can set up my new ubuntu install/learn the basics even if I do not have access to the physical computer.


Thanks.

---

### Post by Dr Small on 2007-10-04
Open port 5900 on the local machine, and forward port 5900 to your network IP, in your router, if you are behind a router.

Get a VNC viewer, and then connect to your IP. It will connect to port 5900, and then you will be in :D

---

### Post by mithbuntu on 2007-10-04
Any chance you could recommend a vnc viewer?

I am not familiar at all with 99.5% of linux software.

---

### Post by Dr Small on 2007-10-04
Well, I have no idea what a macbook is, of which you are going to be using to connect to your pc with, but if it is Ubuntu, just use vncviewer or the "Terminal Server Client".

If it is a Windows pc, use tightvnc.
If a mac, I have no idea.

Dr Small

---

### Post by mithbuntu on 2007-10-05
I still can not remotely connect to my machine.  I can connect to it on the LAN, but if I try to connect via WAN(internet), I get connection refused right away.

I am behind a DHCP dynamic IP router -- im sure that has something to do with it.   Can someone help me out here?  I have to go to the airport in an hour :(

---

### Post by kebes on 2007-10-05
**Edit:** If you're in a hurry, the main thing you need to do is open the port on your router. Check the steps 3, 4, 5 below (if you don't want to follow my suggestion about using SSH tunnels, you can just forward port 5900 instead of 22)...




By the way, opening a VNC port (5900 or whatever) is okay, but it is more secure to use SSH and then "tunnel" the VNC traffic over SSH. That way the connection is encrypted and secure. (VNC is not encrypted, so if you type a password while logged in that way, someone else could actually intercept it... this is not a worry on a LAN you trust, but may be a concern over the Internet.)

So, this is how I would set it up (I've done something highly similar in the past):


**On your Linux server (that you want to log into):**
1. Install a VNC server, like "tightvncserver" (I gather you've already done this). Also make sure you have an SSH server running (you mentioned SSH, so I assume you've already done this, too).

2. Launch a VNC server session. Normally you don't want to launch it on ":0" because that's reserved for your normal display. So pick some other number... in this example, I'll use ":4" (which means port 5904):
```
vncserver :4
```

**Configure your router:**
3. First you need to know the "internal IP address" of your Linux server. On the Linux machine, go:
```
ifconfig
```
You'll see some info, including:
```
eth0      Link encap:Ethernet  HWaddr 00:22:31:CC:CC:FF
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0

```
In the above example, the "192.168.0.109" is the Internal IP address of your server. You'll need this for the next step.

4. Log into your router. Usually this is done by visiting an internal web-page, like 192.168.0.1 (it depends on your router model). You'll need to enter your router's username/password.

5. In the router config, find the option for "port forwarding"... it may also be called "application rules" or something like that. Then you need to set a rule for port forwarding, like:
computer: 192.168.0.109
(put the IP address you got in step 3)
port range start: 22
port range end: 22
(or select "SSH" if it has a list)

This will tell the router than when it gets a request from the Internet for port 22 (SSH) it should forward it to 192.168.0.109 (your Linux server).


**On local computer (Macbook, in your case):**
4. Open up a terminal in Mac OS X, and SSH into your server, and create a "tunnel" for the VNC traffic
```
ssh mithbuntu@xxx.xxx.xxx.xxx -L 5904:localhost:5904
```
Obviously, replace the "mithbuntu" with your username on the Linux server, and replace "xxx.xxx.xxx.xxx" with the IP address of your **external** IP address. (The IP address that sites like [http://whatismyipaddress.com/](http://whatismyipaddress.com/) show you as having.)

The "-L" switch creates the tunnel for VNC port 5904.

5. Open your VNC program (Chicken of the VNC) and connect to "localhost" on port ":4" (or 5904, depending on what terminology that program uses).


You should now have a secure VNC connection that works from anywhere on the Internet. As long as you can SSH into your server (you know the IP address), then you can access VNC also. Of course, VNC over the Internet isn't very fast, but it gives you full control of your system.


I hope that makes sense! Good luck.

---

### Post by mithbuntu on 2007-10-05
I decided to unhook my PC from my router while I am gone to 
a) make setting up vnc easier
b) kill my wireless as my system vulnerability may be a tad higher while i am still fooling with ports

I am now getting this over and over and still can not connect.
```

x@y:~$ sudo vncpasswd /root/.vncpasswd
Password: 
Verify:   
x@y:~$ vnc4server

You will require a password to access your desktops.

usage: vncpasswd [passwdFile]

```

I haven't read your post yet but will now.

---

### Post by mithbuntu on 2007-10-05
Here's the result.  Looks like my SSH is still not happy.
```

x@y:~$ ssh x@aaa.bbb.ccc.ddd -L 5904:localhost:5904
ssh: connect to host aaa.bbb.ccc.ddd port 22: Connection refused

```

---

### Post by kebes on 2007-10-05
> **mithbuntu said:**
> I decided to unhook my PC from my router while I am gone to 
a) make setting up vnc easier
b) kill my wireless as my system vulnerability may be a tad higher while i am still fooling with ports

I am now getting this over and over and still can not connect.
```

x@y:~$ sudo vncpasswd /root/.vncpasswd
Password: 
Verify:   
x@y:~$ vnc4server

You will require a password to access your desktops.

usage: vncpasswd [passwdFile]

```





I don't use vnc4server, but my guess is that your error is coming from the fact that you are setting the password in the file /root/.vncpasswd (which is probably owned by root), but then you are launching vnc4server without sudo (as a normal user).

So, vnc4server can't access the password file.

Either set a normal-user-mode password with vncpasswd (without sudo) ... or launch the VNC server as root (using sudo). You may also have to pass the location of the password file as a parameter when launching vnc4server.


> I haven't read your post yet but will now.
Well, since you are bypassing your router, much of my previous post no longer applies. However as long as you have remote SSH access, you can set up VNC access later (while you're already away on your trip) using the procedure I outlined above.

---

### Post by kebes on 2007-10-05
> **mithbuntu said:**
> Here's the result.  Looks like my SSH is still not happy.
```

x@y:~$ ssh x@aaa.bbb.ccc.ddd -L 5904:localhost:5904
ssh: connect to host aaa.bbb.ccc.ddd port 22: Connection refused

```

If you're getting that error without a router being there, then it means:

1. You don't have an SSH server running. (But you can connect via SSH on the LAN, right?)

2. You are blocking port 22 on Ubuntu. Have you installed a firewall package (such as Firestarter) that might have closed port 22? Again, if you can SSH into the box on the LAN, then I guess this isn't the problem.

3. Your Internet provider blocks port 22. Most ISPs won't block port 22 ... but I guess it's possible. You can run SSH on a non-standard port to get around this...

---

### Post by BLTicklemonster on 2007-10-05
It's 

"Ubuntu-holics"

not

Ubuntuers.

:)

---

### Post by mithbuntu on 2007-10-05
Yes I can SSH through the LAN:

This is output from my laptop to show you:
```

Warning: Permanently added '192.168.1.100' (RSA) to the list of known hosts.
drew@192.168.1.100's password: 
Linux mithbuntu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri Oct  5 11:04:03 2007 from localhost
drew@mithbuntu:~$ 

```

but if i try via my ip, i get the connection refused on port 22 error


Also, yes I have firestarter but I have allowed port 22 traffic inbound.

I was able to open a vnc server on the 5905 port, but I still cant connect to it. 

I have to leave soon, but thanks anyways:)

---

### Post by kebes on 2007-10-05
> **mithbuntu said:**
> Yes I can SSH through the LAN ... but if i try via my ip, i get the connection refused on port 22 error

I was able to open a vnc server on the 5905 port, but I still cant connect to it. 

I have to leave soon, but thanks anyways:)

I don't think we're going to get this fixed before you leave... sorry!

As I said, you could try putting SSH on a non-standard port. Briefly:
-Edit "/etc/ssh/sshd_config"
-Add a line like "Port 3000" or whatever port # you want (higher than 1024).
-Restart ssh server: sudo /etc/init.d/ssh restart
-Open that port in your firewall
-When connecting via ssh, do something like:
```
ssh user@xxx.xxx.xxx.xxx -p 3000
```

That ~might~ work... but as I said port 22 is not usually blocked. So I'm not sure that will help.

---

### Post by mithbuntu on 2007-10-05
I've tried several ports-- no luck.

Strange thing though.  I rebooted just now and tried to restart the SSH server and I recieved:
```

drew@mithbuntu:~$ /etc/init.d/ssh start
open: Permission denied
 * Starting OpenBSD Secure Shell server...                                      
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
open: Permission denied

```

and yes even as superuser I get an error
```

drew@mithbuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]

```

Great Error Message [fail]


I'm pretty sure I had it set up right, but who knows.  if i could SSH through my LAN you'd think so?

---

### Post by phr0ze on 2007-10-05
Please review this. I think this is what I used and it worked perfect.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by mithbuntu on 2007-10-16
I'm still stuck with trying to remotely connect to the SSH server.  I can connect locally:
```

x@mithbuntu:~$ ssh localhost
x@localhost's password: 
Linux mithbuntu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
...

```

and over LAN, but not over the internet:
```

drew@mithbuntu:~$ ssh a.b.c.d
ssh: connect to host a.b.c.d port 22: Connection refused

```

How can I troubleshoot from here? I DO have port 22 open on my router.

---

### Post by mithbuntu on 2007-10-16
Port 22 is also Listening...
```

$  netstat -an | grep 22 | grep :::

tcp6       0      0 :::22                   :::*                    LISTEN     
udp6       0      0 :::22                   :::* 
```

What am I doing wrong?

I saw something about passkeys in another thread and thought I set them up, but maybe I didnt?

---

### Post by mithbuntu on 2007-10-16
Just checked... my port is open.

Success: I can see your service on xx.yy.zz.160 on port (22)
Your ISP is not blocking port 22

---

### Post by kebes on 2007-10-17
> **mithbuntu said:**
> How can I troubleshoot from here? I DO have port 22 open on my router.

The only things that I can think of:

1. I know you said port 22 is open on your router ... but ... Are you sure? Is it being forwarded to the right internal IP address? Maybe try rebooting the router to make sure changes take effect?

2. Have you changed your SSH config? By default, the SSH server should accept all connections, but perhaps you changed it at some point? (Maybe you installed some security-related package that altered the SSH settings?) Check in the file "/etc/ssh/sshd_config" and see if anything is restricted. (For example, switches like "AllowUsers" may be set for security reasons. A line like:
AllowUsers bob@localhost
would allow local login but deny remote login.

3. Do you have restrictive iptables rules? Maybe you installed some software that set a "deny by default" rule that you need to over-ride. (For example, installing Firestarter will, I think, create "deny by default" rules... you then you have to manually open port 22 again for remote access.) Also, check the files "/etc/hosts.deny", "/etc/hosts.allow" and so on ... maybe something in there is generating a restriction?

---

