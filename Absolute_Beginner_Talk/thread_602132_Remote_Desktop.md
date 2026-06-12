---
title: "Remote Desktop"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-03
How would I go about making my ubuntu box accessable from other computers?  I'd like to have a remote desktop application, very similar to vnc, but able to be run off of a remote windows box?
Is anyone really familiar with this? I'm quite new when it comes to things like this.

---

### Post by jflaker on 2007-11-03
System-->Preferences-->Remote Desktop

Enable......

connect via VNC or remote desktop using VNC from a linux box

---

### Post by SmileyChris on 2007-11-03
I was just wondering about this too, 10 minutes ago.

---

### Post by jordank on 2007-11-03
> **jordank said:**
> but able to be run off of a remote windows box?.

Also, i'm not great at setting things up, like what would i have to do in terms of ports, clientside, etc. Any walkthroughs?
Is it even possible to access a linux box from a windows box?

---

### Post by newlinux on 2007-11-03
VNC is good and simple an easy. If you will be doing this over WAN then I recommend nxserver, which has a client for windows. ([www.nomachine.com](www.nomachine.com) has a free version) It is much faster than VNC over WAN, and can be used to create a new session as opposed to connecting to and sharing an existing session. If you search the forums there is a how-to somewhere, but really all you need to do is download and install the .debs on the server and then install the client on a windows machine.

---

### Post by newlinux on 2007-11-03
> **jordank said:**
> Also, i'm not great at setting things up, like what would i have to do in terms of ports, clientside, etc. Any walkthroughs?
Is it even possible to access a linux box from a windows box?

If you are using VNC, you will want to probably go through your ssh port (forward your VNC connection through ssh) for security reasons.

Lots of howtos out there on this. Here's a quick one I found:

[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

---

### Post by Lord C on 2007-11-03
Ports are 5800 and 5900 TCP. You will need to forward these from your router, to your PC's network IP.

Ubuntu comes with a VNC viewer pre-installed (Applications > Internet > Terminal Server Client).

To install the server, type 'sudo apt-get install vnc4server', or tightvncserver.

The difference between the tightvncserver and the normal vncserver is the
data encoding, optimized for low bandwidth connections.

Now it's just simple case of typing vnc4server in a terminal window. The server will ask for a password which your client will use.

Do a man vnc4server or vnc4server --help if you need more info on the server.

To view your pc remotely, you'll need a VNC viewer. A free one can be downloaded from tightvnc.com. Type your IP and hit connect. Enter your chosen password when prompted.

---

### Post by jordank on 2007-11-03
what does that exactly mean?
and what is a wan server? ssh?
would putty be a better choice, i see that used with ssh more often.

---

### Post by jflaker on 2007-11-03
> **Lord C said:**
> Ports are 5800 and 5900 TCP. You will need to forward these from your router, to your PC's network IP.

Ubuntu comes with a VNC viewer pre-installed ........

Careful when enabling VNC and opening this port to the world.  I can tell you that you can be guaranteed a hostile takeover of your PC if it is discovered.  I worked for a company which used VNC and one remote user I was assisting had their machine taken over and they attempted a virus infection!

use care.  Use VNC behind a firewall only.

---

### Post by jordank on 2007-11-04
i'm not using a router at all, are the ports you mentioned open by default, or how do i open them if not with my router?

---

### Post by jordank on 2007-11-04
couple quick questions.
i did sudo apt-get install vnc4server
then i ran it:
vnc4server
it prompted me for a password, i entered it.
from there, i tried to connect to it through vncviewer
i typed
vncviewer
into the terminal.
it gave me the error: connection refused.

a) why was my connection refused? does this have somthing to do with ports? i'm not running through a router. Do i need to edit some port options somewhere in ubuntu?
b) after installing vnc4viewer, does that mean it's going to start up at bootup every time, or am i going to have to initialize it with the
vnc4server
command each time i want to have a server running?
c) will this be viewable from a windows box?
d) when i need to remove, how will i go about this?
and finally,
e) what is the difference between vnc4server and tightvncserver?

thanks

---

### Post by Sapphiron on 2007-11-04
Exact same error here...

---

### Post by newlinux on 2007-11-04
> **jordank said:**
> couple quick questions.
i did sudo apt-get install vnc4server
then i ran it:
vnc4server
it prompted me for a password, i entered it.
from there, i tried to connect to it through vncviewer
i typed
vncviewer
into the terminal.
it gave me the error: connection refused.


What computer are your running vncserver on and what computer are you running vncclient on? Are they on different LANs? Are you sure you ports are open on both networks if they are two separate networks?

> 
a) why was my connection refused? does this have somthing to do with ports? i'm not running through a router. Do i need to edit some port options somewhere in ubuntu?


Hard to know without knowing more about how you are trying to connect and your networks. Do these computers have firewalls involved? I strongly recommend against opening up the VNC ports on your LAN and I recommend forwarding VNC through ssh for security and encryption.
> 
b) after installing vnc4viewer, does that mean it's going to start up at bootup every time, or am i going to have to initialize it with the
vnc4server
command each time i want to have a server running?


By default, no vncviewer will not start up at boot everytime. vncserver does not initialize vncviewer. They are two separate apps. Vncserver should be started on the machine you want to connect to, and vncviewer should be used on the machine you want to connect from. 
> 
c) will this be viewable from a windows box?

Yes. You can download a few different vnc clients (vncviewer apps) for windows.

> 
d) when i need to remove, how will i go about this?

sudo apt-get remove [whichever viewer and server you installed]

You don't really need to remove them. Just don't start the server and disable any ports you enabled to connect, depending on how you set this up.
> 
and finally,
e) what is the difference between vnc4server and tightvncserver?

thanks

The difference between the tightvncserver and vncserver is the data encoding, optimized for low bandwidth connections. Later versions of vncserver (> 3.3.3r2) support a new automatic encoding that should be equally good as the tightvnc encoding.

---

### Post by jordank on 2007-11-04
> **newlinux said:**
> What computer are your running vncserver on and what computer are you running vncclient on? Are they on different LANs? Are you sure you ports are open on both networks if they are two separate networks?



Hard to know without knowing more about how you are trying to connect and your networks. Do these computers have firewalls involved? I strongly recommend against opening up the VNC ports on your LAN and I recommend forwarding VNC through ssh for security and encryption.

.

I'm actually trying to connect to the same computer i'm running the server on.  This theoretically should be doable, no? Eventually i'm going to be connecting to this computer from my girlfriends house, so no, they're not the same lan.  And no, i have no idea about the ports.  I'm running a regular install of ubuntu, and havent played around with any port settings, nor would i know how to? (please let me know if this is possible)  My girlfriends computer (the windows box) is running a firewall, but i can deal with that without a problem, but this box (ubuntu), i dont think is running a firewall, unless of course there is one enabled by default. I haven't installed one.  As for opening up vnc ports, then forwarding through ssh (for security) i have no idea how i would go about doing this.  Would putty be a better choice? can vnc be used for ssh, and ultimately, how would i forward vnc through ssh?
Thanks.

---

### Post by jordank on 2007-11-04
anyone know if it's possible to connect to the same computer you're running the server on with a viewer?

---

### Post by newlinux on 2007-11-04
Theoritically it is doable. I just tried it with vncviewer and it basically ends up looking like an infinite loop of windows, which makes sense because you're looking at your shared desktop inside your shared desktop, inside your shared desktop... etc. So it isn't too useful.

If you are over a WAN (meaning two computers from different networks connecting over the Internet), I would use VNC over ssh. for security.  Step by step instructions:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

Before I started using nxserver (which is much faster over typical internet connections) this is what I used.

---

### Post by mlentink on 2007-11-04
Why are you double posting? If the answers given you aren't to the point, or do not solve your issue, you might as well say so in your original [post..]("http://ubuntuforums.org/showthread.php?t=602970").

---

### Post by kinemagician on 2007-11-05
I just installed nxserver on UBUNTU 7.10 following the steps I found on this forum:


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-pack...?os=linux&id=1](http://www.nomachine.com/select-pack...?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------
Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.

-----------------------
Step 3 - Configure
-----------------------
Load up your /etc/ssh/sshd_config file into an editor:

sudo nano /etc/ssh/sshd_config

Add the following line & save the file
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

Restart sshd by typing:
sudo /etc/init.d/ssh restart

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status

This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration. If not, then NX Desktop Server should be installed.

You should then install the windows client on your PC if you want 
connect to your ubuntu machine.
You can dwon load the windwos client from 
the nomachine website [www.nomachine.com](www.nomachine.com).



Remember to open port 22 on your router!

It works really fast.  I recoommend it.

---

### Post by newlinux on 2007-11-05
An NXserver satisfied customer. As you can see, it's a pretty straight forward install, has cross platform clients, resumable sessions, creation of new sessions, and is fast right out of the box with little configuration. Way better than VNC if you ask me...

---

### Post by jordank on 2007-11-07
hey, i followed your advice for the nx machine, but upon typing:
Restart sshd by typing:
sudo /etc/init.d/ssh restart

it yields: sudo:  /etc/init.d/ssh: command not found

any idea why?

would it make a difference if i edited the file with gedit instead of nano? (i just find that easier to use)

anyways, after trying:

sudo /usr/NX/bin/nxserver --status
it gives the message:

jordan@jordan-laptop:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 110 NX Server is stopped.
NX> 999 Bye.

is this because i didn't restart the server?
what should i do?

---

### Post by jordank on 2007-11-07
sorry to double post, but i forgot to add that i didn't download from the exact sites you specified, because your first link didn't work.
however, i did use this page:
[http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6)
i believe it is the same thing, just with all 3 links in one.
is this the right thing to download?

---

### Post by newlinux on 2007-11-07
Have you installed openssh-server?

---

### Post by jordank on 2007-11-07
not that i know of, i did everything the guy told me to do a couple threads before.

is it just
sudo apt-get install openssh?

---

### Post by jordank on 2007-11-07
i installed openssh-server, and now everything seems to be working pefectly, i got:

jordan@jordan-laptop:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 900 Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
NX> 110 NX Server is running.
NX> 999 Bye.


but now, i want to check if it's actually working.  How do i open the nx client?

---

### Post by newlinux on 2007-11-07
Should be in you applications menu if you installed the client in Linux.  Otherwise the nxclient executable is probably located in /usr/NX/bin/.

---

### Post by newlinux on 2007-11-07
also, since you installed ssh after modifying /etc/ssh/sshd_config, I'm not sure what the /etc/ssh/sshd_config file will contain.

---

### Post by jordank on 2007-11-07
awesome. thank you sir.
and this is secure, ya?

---

### Post by newlinux on 2007-11-07
yep. works through ssh encryption, which is pretty secure.

---

### Post by jordank on 2007-11-07
you're very helpful, thank you :)

---

### Post by newlinux on 2007-11-07
I try... Hope it works well for you. I use it from my windows machine at work to connect to my home machine and it works well. If this works well for you, you might want to mark this thread solved, as this helps out the community.

Also since, I'm thinking about this now, you said your computer at home is not connected to a router, correct? Just directly to the your Internet connection. If that is true, your computer  is already not very secure if you don't have a firewall setup. Something to consider. Also, I strongly recommend you read the following thread for securing your ssh connection. [http://ubuntuforums.org/showthread.php?t=450853](http://ubuntuforums.org/showthread.php?t=450853)

I use denyhosts, but if you are only using keys to allow access to ssh, you won't need it.

---

### Post by jordank on 2007-11-08
yeah, i'm not connected to a router,but i just don't feel it necessary to install denyhosts for a multiple of reasons.
a) the main one being i don't understand what it is/what it does.
b) i'm on a university campus, so my ip address changes very frequently, which seems to be a security measure in itself
c) the only way, according to that thread, to crack ssh is by bruteforcing my password
d) i just dont think i'll be attacked.

Are these valid thoughts?

---

### Post by maybeway36 on 2007-11-08
It might be a good idea to change SSH from port 22 to something more obscure, jsut in case. You can use -P option on command-line SSH, and PuTTY has a port option too.

---

### Post by jordank on 2007-11-08
by typing ssh -p (port here) it doesnt seem to change anything.
i'm running an nxserver, is that entirely based off the ssh server? would i have to change the nxserver port, or just the ssh port setting?

---

### Post by newlinux on 2007-11-08
> **jordank said:**
> yeah, i'm not connected to a router,but i just don't feel it necessary to install denyhosts for a multiple of reasons.
a) the main one being i don't understand what it is/what it does.
b) i'm on a university campus, so my ip address changes very frequently, which seems to be a security measure in itself
c) the only way, according to that thread, to crack ssh is by bruteforcing my password
d) i just dont think i'll be attacked.

Are these valid thoughts?

Fair enough. Your assessment is correct (although I can't speak for d). All denyhosts does really is block people who keep trying the same username with different passwords, or usernames that don't exist, or  restricted names. To what degree it does these is configurable. The defaults it starts with are pretty good and would ward of most dictionary attacks. It only takes one person to make you reassess how secure your system is. but you IP address changing all the time is annoying, yet somewhat effective deterrent.

 I used to have attacks everyday. Installed denyhosts which helped. then  switching the port killed the rest of them, so far. 

If you change your ssh port you will need to change what port nxclient connects to be the same. I don't think there is anything you'd need to do with nxserver (I don't run my sshd of of port 22 and I didn't do anything special with my nxserver install).

Just for clarity,
ssh -p doesn't change the port your sshd daemon listens to, it changes the port your client tries connects to your ssh server on. To change the port your server listens on (if you don't have a router that does port forwarding) you would modify the line in your /etc/ssh/sshd_config file that states:

Port 22

to 

Port 53234
or whatever valid port number you like. And restart ssh.

---

### Post by jordank on 2007-11-19
Hey, i reinstalled linux, using a 64 bit version this time.  Is there a place that i can get nx client for a 64 bit machine?  or is it safe to force this application to install? if so, how would i do that?

thanks

---

### Post by jordank on 2007-11-19
sorry, i meant server instead of client. i found the 64 bit client, but i cant see an appropriate server/node for 64 bit ubuntu.
Anyone?

---

### Post by robertsaron on 2007-11-20
> **jflaker said:**
> System-->Preferences-->Remote Desktop

Enable......

connect via VNC or remote desktop using VNC from a linux box

OK  so I have system but not preferences? I am using gutsy gibbons 7.10. several people have said go to preferences-remote desktop but where the **** is it?

---

