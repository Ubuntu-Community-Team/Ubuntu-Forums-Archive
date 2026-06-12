---
title: "Accessing Ubuntu computer on network from Windows box"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Generalspuddog on 2006-12-27
Ok i can access the internet on the Ubuntu box. I can even see the windows network on it too but I can not see the ubuntu box from my XP machine. 

I enabled remote desktop as I want to use the ubuntu box as a file server for storing lots of music etc. It would be great if I could "dial in" to the ubuntu box and control it from my XP machine. Idealing all i want the ubuntu box to be hooked up is the power cord and ethernet cord to my network router/hub.

Any idea what i need to do? Thx

---

### Post by pay on 2006-12-27
Try using VNC

---

### Post by Generalspuddog on 2006-12-27
VNC? I tried using that command that it tells you to use for Remote desktop. It was...

VNCviewer Server:0 

I tried using that command under the command promt but it didn't work. I have been reading some posts and I am now looking into Samba. Not sure if that will help me with all of the things i want to do

---

### Post by DSn0wMan on 2006-12-27
I would try using NX from NoMachine. It's quite a bit faster than VNC, and more secure. 

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by Generalspuddog on 2006-12-27
Excellent. That program looks sweet. Do I install it on the linux, windows or both boxes?

---

### Post by DSn0wMan on 2006-12-27
You install the NX Client, Sever, and Node on the linux box, and then install NX Client on the windows machine you are going to access your linux box with.

I think there is a how to: in the ubuntu wiki.

---

### Post by DSn0wMan on 2006-12-27
Try this method. It's more up to date than the Ubuntu wiki. The steps look similar to what I did.

[http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake)

---

### Post by Generalspuddog on 2006-12-27
I am following the instructions from the link you suggested and it starts to install the first app then i get this message...



server@Server:~$ cd /home/server/Desktop
server@Server:~/Desktop$ sudo dpkg -i nxnode_2.1.0-12_i386.deb
Selecting previously deselected package nxnode.
(Reading database ... 88235 files and directories currently installed.)
Unpacking nxnode (from nxnode_2.1.0-12_i386.deb) ...
dpkg: dependency problems prevent configuration of nxnode:
 nxnode depends on nxclient (>= 2.1.0); however:
  Package nxclient is not installed.
dpkg: error processing nxnode (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxnode

---

### Post by DSn0wMan on 2006-12-27
You have to install the packages in this order.

1) NX Client
2) NX Node
3) NX server

Node is dependant on client, and sever is dependant on client and node.

---

### Post by Generalspuddog on 2006-12-27
Ahh ok. The walk through has it like this..

   1. NX Node
   2. NX Client
   3. NX Server

---

### Post by Generalspuddog on 2006-12-27
I went to install the client and i was missing 

libstdc++2.10-glibc2.2_2.95.4-22_i386.deb

found that but then i couldn't install that cause i had a broken dependency so i had to run Sudo sy(something) Then had to turn on the filter to broken and find the red square and delete it. After that it all installed just fine. Wow this Linux stuff is challenging but i like it ](*,) 

Now i am off to set up NX. Wish me luck!

---

### Post by houstonbofh on 2006-12-27
To mount a file share from a Windows system, you need samba running and configured on the Ubuntu system.

To remote control, you can use ssh, which is like a secure telnet.  You get a command line.  (On windows you need Putty)  (If you also get Xming for Windows you can tunnel individual X apps over Putty)  This is somewhat slow.

You can also use VNC.  The Client and Server are built into Ubuntu, you just have to enable them.  On windows install a VNC client.  I personally like tightvnc.

---

### Post by Generalspuddog on 2006-12-27
Ok everything is installed (NX client, node, and server) on the linux box and the client is on the win box. I can access the linux box from the linux client but i cant access the linux box from the windows box (Connection refused) I follow the [Wiki]("https://help.ubuntu.com/community/FreeNX?highlight=%28NX%29") and changed the port from 22 to 8888 but still no luck. I even went into the router and made sure 5800 and 5900-5910 were forwarded but alas no luck. 

Any other ideas?

---

### Post by houstonbofh on 2006-12-27
Did you install ssh?  Can you ssh to your box from the windows box?  (You will need putty on windows)

As to the port change...  That is to keep out the port scanners.  You could leave it on port 22, but install fail2ban.  I do not like non-standard ports, and I LOVE fail2ban!

---

### Post by Generalspuddog on 2006-12-27
I honestly dont know what i have and haven't installed yet. I think I am just going to reformat and start over again. What is easier to set up NX or VNC? Right now I have tried both and they both give me the (Connection Refused) error.

---

### Post by DSn0wMan on 2006-12-28
> **Generalspuddog said:**
> Ok everything is installed (NX client, node, and server) on the linux box and the client is on the win box. I can access the linux box from the linux client but i cant access the linux box from the windows box (Connection refused) I follow the [Wiki]("https://help.ubuntu.com/community/FreeNX?highlight=%28NX%29") and changed the port from 22 to 8888 but still no luck. I even went into the router and made sure 5800 and 5900-5910 were forwarded but alas no luck. 

Any other ideas?

I just leave it on port 22, and enable ssl encryption. You will need to configure your firewall to let you in on port 22. Connection refused means you are probably getting rejected by a router or firewall.

OK I forgot one small thing.

To get your windows client working you should copy your .nxs file from your linux machine. You'll find it in /home/*your_user_name*/.nx/config/

You can copy that to your windows client. You can find the windows .nx folder under documents and settings. The important part is that the .nxs file contains your server key.



good luck!

---

### Post by houstonbofh on 2006-12-29
> **Generalspuddog said:**
> I honestly dont know what i have and haven't installed yet. I think I am just going to reformat and start over again. What is easier to set up NX or VNC? Right now I have tried both and they both give me the (Connection Refused) error.
Well, don't give up yet because we can fix this.  Bring up Synaptic, and go to "search" and type "ssh."  You should see Open-ssh, ssh-client, and ssh-server.  (As well as a bunch of other stuff.  If you look at Open-ssh you will see it is just a dependance package for the client and server.  Once you have the server installed, it should work.  Use ssh from the command line of a unix system, or putty from a Windows system to check.  You need to have a good ssh working for NX or X tunneling to work.  For now I would not mess with moving the ports around.  If you have ssh-server installed, you can remove it, and reinstall to get the defaults.  Once you have a solid ssh working we can go on.

As to NX, VNC or X tunneling, you have to decide.  I do not use NX.  I did not like the install.  (It does not seem clean to me)  VNC works well and is solid, but slow.  ssh and X tunneling works well, is well tested, and slow, but you only run the screen you need so it is not so bad.  Also, you can do the second two strictly with packages in synaptic.  I use both VNC and ssh with X tunneling.

---

### Post by Soarer on 2006-12-29
I use NX a lot and find it much faster than VNC - though I agree the installation is not very clean. The other problem I have is that it doesn't leave the sound on the XP machine when connecting to Windows via RDP. Gnome-RDP does though, so I use that for XP access.

It sounds like you have a firewall blocking the ports you need - either in the router or on the Windows machine. Turn off Windows firewall for now (maybe forever, it's not very good) and try it. Also see if your router blocks ports between Ethernet ports on the LAN side. If so, you will either have to reconfigure it (not always easy) or get a hub to plug all your LAN machines into, with one uplink to the router. The hub should not block LAN accesses.

BTW - you ARE using static IP addresses on your LAN boxes, aren't you? Or some kind of working internal DNS (and if the latter, you're a better man than me :))

---

### Post by WilliamMiller54 on 2007-01-01
I am new to Ubuntu and have the same issue. I want to use Ubuntu (6.5.x) as a Parental Blocker, so will end up just sticking the box in a server rack without a monitor \ keyboard. So I will need to get VNC working. 

From the Ubuntu box I can Ping other computers on the network, and can reach the internet. 

From my other boxes I can connect to Ununtu by using it as a proxy (Tiny + Dansguardian), but I can not ping, ssh, or VNC. It is using a static IP. 

I did install the VNC server. But still no luck. Any idea?

- William -

---

### Post by Soarer on 2007-01-01
That's very curious. Usually SSH will work if nothing else does, which leads me to assume your server must have a firewall between it and your PCs blocking ports. I assume you have tried to connect using the IP address of the server, not its name?

If you are using a router between the boxes, that could be blocking ports and only allowing port 80 (for web) through. This would be a typical default configuration.

Can you tell us a bit more about your set-up and connections - this may make it easier to help you? Thanks.

---

