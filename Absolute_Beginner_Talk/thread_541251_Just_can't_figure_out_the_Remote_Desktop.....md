---
title: "Just can't figure out the Remote Desktop...."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Nameless on 2007-09-02
Ok, I have Ubuntu running on two computers at the moment and I want to be able to use remote desktop on my "server" to connect to it from my "laptop" (Ubuntu 7.04)
I've gone under Remote desktop on the server (Ubuntu 7.10) and enabled the top two checkboxes to allow sharing and control.  The options box says I should be able to see the computer by entering "vncviewer server:0"

On my laptop, in terminal, I enter "vncviewer server:0" and I only ever get "unable to resolve host by name: connection timed out (110)"

What more do I need to do to make get this working?

---

### Post by totalnub on 2007-09-02
have you thought about ssh with X11 fowarding?

you have to install the ssh server on your server:
```
 sudo apt-get install ssh 
```
then from the terminal type:
```
ssh -Y <usernamehere>@<ip of server>
```
and to get a display up, assuming nautilus is your file browser, just type nautilus in the terminal

---

### Post by Nameless on 2007-09-02
I'm definitely not opposed to using ssh (and I have intentions to get to it), but I just wanted to be able to talk to my server from my laptop while sitting downstairs.  

So I gave the above a try by installing ssh onen the server and then connecting from my laptop, I got the following error when I tried to connect: "connect to host <my ip> port 22: connection refused"

I am clearly missing some aspect of this, but I can't figure out what it is.  The part that bugs me the most is that I'm able to connect to my server via UltraVNC when I boot my laptop into Windows.  I just can't seem to figure out the trick to get Ubuntu to talk to the server.

....ugh...I've been at this for a chunk of the afternoon.

---

### Post by totalnub on 2007-09-02
did you forward port 22 on your router?

---

### Post by Nameless on 2007-09-02
totalnub, thanks for the replies. 

Hmm...well, I did go into the router and forward 22, yes.  But I wonder if I'm missing something to that part.  I assumed it was forwarded correctly b/c UltraVNC works in Windows for connecting to the server, but now that I think about it, I don't think that uses port 22.

I'll revisit the port forwarding.  Think I'm going to need to head to no-ip.com to look for a solution for my dynamic IP address.  My understanding is that a dynamic IP can cause problems with forwarding port 22...is that correct?

---

### Post by totalnub on 2007-09-02
not from the beginning, only after time will a dynamic ip become a problem. btw, would you mind sending me a pm with the server ip so i could try?

---

### Post by Nameless on 2007-09-02
I don't mind at all.  PM sent.

---

### Post by Dr Small on 2007-09-02
Make sure port 22 is opened on the openssh-server end.

Dr Small

---

### Post by Nameless on 2007-09-02
Dr. Small, how would I do that?

---

### Post by Jose Catre-Vandis on 2007-09-02
You need to know the IP of your server and enter this in your hosts file of your laptop. Your laptop does not know what machine "server" is unless you tell it the IP as well. You can always just use the IP as follows:

vncviewer 192.168.0.2:0

best to set your server up with a static IP address so this always works :)

---

### Post by Nameless on 2007-09-02
Jose, I tried entering the IP address instead of the name of my server and I got the same error message.

I just completed a shieldsup scan of my ports on both computers and it's showing that port 22 is closed on both.  

Any idea how I would open port 22?

---

### Post by scxtt on 2007-09-02
if you're using Vino (which is what "remote desktop" is via the menu for Gnome) you HAVE TO be logged in already on the host you're connecting to - if you're not, it doesn't work ...

you DO NOT need any form of port forwarding if you're connecting from w/in your own network ... as a matter of fact DON'T forward port 22 if you're not planning on connecting from the "outside" (any IP that's not your own) ...

you should install a stand-alone VNC server (like "vncserver" or "tightvncserver" and invoke it after you ssh into your "server" ... you'll also want to be sure the ssh daemon is running on the server - make sure you get something like sshd returned from **ps -ef | grep ssh** ...

---

### Post by Jose Catre-Vandis on 2007-09-02
Ah, is your server outside or inside your LAN?

I just did both vnc remote on a GUI install and a ssh remote on a CLI install this afternoon, on the same LAN with no problems about connection.

have you tried 

vncviewer IPaddress:1  (sometimes it screws up)

Did you uncheck the "confirmation" box on your server? Otherwise you will never be able to connect because your server is waiting for input from the "logged in user" AT THE SERVER!  :)

---

### Post by steveneddy on 2007-09-02
> **Nameless said:**
> Ok, I have Ubuntu running on two computers at the moment and I want to be able to use remote desktop on my "server" to connect to it from my "laptop" (Ubuntu 7.04)
I've gone under Remote desktop on the server (Ubuntu 7.10) and enabled the top two checkboxes to allow sharing and control.  The options box says I should be able to see the computer by entering "vncviewer server:0"

On my laptop, in terminal, I enter "vncviewer server:0" and I only ever get "unable to resolve host by name: connection timed out (110)"

What more do I need to do to make get this working?

OK - this means:

vncviewer server:0

That you will use the application "vncviewer" to **view** the remote desktop.

VNC stands for Virtual Network Connection.

Where it says "server:0", replace the word server with the IP address of your server. Just go to the router and look at the PC that are attached to the router, get their IP addresses, and if you only have two PC's, one is the laptop, the other is the server.

Should be easy as this.

You might go to Synaptic and see if vncviewer is actually installed. If not, install it.

Good luck.

:popcorn:

EDIT - 

If you put a 0 after the : - like this - server:0 - it will look at the current open screen. You may want to input the command like vncviewer serveripaddress:1. The 1 is a new session and shouldn't interfere with any current session.

---

### Post by scxtt on 2007-09-02
vino "shares" the :0 connection - it only runs when the users current :0 session is LOGGED IN ... if one user has vino configured to allow connections, but that user is NOT logged in - you won't be able to "remote desktop" to that host ...

if you want to be able to get a :0 connection and login w/ it - install **x11vnc** ...

you should forget about "remote desktop" aka vino - it's good in 1 situation, you'll get much more mileage out of a vncserver (w/ ssh to start the session) and x11vnc ...

i'm also fond of **xserver-xephyr** and **XDMCP** ...

---

### Post by Nameless on 2007-09-02
OK, I had to head out for a while, but I'm back looking at this again. 

> you should install a stand-alone VNC server (like "vncserver" or "tightvncserver" and invoke it after you ssh into your "server" ... you'll also want to be sure the ssh daemon is running on the server - make sure you get something like sshd returned from ps -ef | grep ssh ...

I got this result

```

nate      5414  5377  0 15:58 ?        00:00:00 /usr/bin/ssh-agent x-session-manager
root      5815     1  0 16:14 ?        00:00:00 /usr/sbin/sshd
nate      6353  5634  0 21:29 pts/0    00:00:00 grep ssh

```

The above makes me think I have ssh running, but I may be wrong. 

If I sit at the server and type "vncviewer server:1", I can actually get a connection to the server, so I'm assuming the vnc portion is working correctly.   Additionally, I can use vnc from a windows box to get to the server as well.  I just can't connect to it from another Ubuntu box

> 
Ah, is your server outside or inside your LAN?


I'm on a local network, so everything has the same IP address.  

I'm beginning to think that there is something wrong with my laptop settings, because I think I have all of the right programs installed on the server and I believe they are running. 

Is there another program that I could use instead of vncviewer?

---

### Post by scxtt on 2007-09-02
> Is there another program that I could use instead of vncviewer?any other program you would install would just be a frontend to vncviewer ...

what's the output of **aptitude search vnc** ... ?

are you saying you sit in front of "server", logged in w/ "remote desktop" enabled and you can use a VNC viewer in windows to view it?  but the same doesn't work from your laptop?

---

### Post by Nameless on 2007-09-02
> 
what's the output of aptitude search vnc ... ?


```


p   directvnc                       - VNC client using the framebuffer as displa
p   libsvncpp-dev                   - Subversion C++ library (development files)
p   libsvncpp0c2a                   - Subversion C++ shared library             
p   libvncauth-dev                  - Virtual network computing authentication h
p   libvncauth0                     - Virtual network computing authentication l
p   libvncserver-dev                - easy API to write one's own VNC server    
p   linuxvnc                        - VNC server to monitor a tty               
p   svncviewer                      - virtual network computing client software 
p   tightvnc-java                   - TightVNC java applet and command line prog
p   tightvncserver                  - virtual network computing server software 
p   tkvnc                           - Displays a list of (defined) machines to s
p   vnc-common                      - Virtual network computing server software 
p   vnc-java                        - VNC java applet and command line program  
v   vnc-server                      -                                           
v   vnc-viewer                      -                                           
i A vnc4-common                     - Virtual network computing server software 
i   vnc4server                      - Virtual network computing server software 
p   vncommand                       - VNC server which monitors a specified prog
p   vncserver                       - Virtual network computing server software 
p   vncsnapshot                     - A utility that takes JPEG snapshots from V
v   vncviewer                       -                                           
v   x0vnc-server                    -                                           
p   x11vnc                          - VNC server which uses your current X11 ses
p   x2vnc                           - A dual-screen hack - link an MS-Windows an
p   xtightvncviewer                 - virtual network computing client software 
i   xvnc4viewer                     - Virtual network computing client software 
p   xvncviewer                      - Virtual network computing client software 

```

I believe the right vnc viewers are installed based on the above, but maybe I'm wrong on that. 

> 
are you saying you sit in front of "server", logged in w/ "remote desktop" enabled and you can use a VNC viewer in windows to view it? but the same doesn't work from your laptop?


Yeah, that's basically it.  I've had this problem for months and it's now about the only thing keeping me from deleting the windows partition from my laptop. For the life of me, I haven't been able to use vnc from Ubunut to Ubutnu only Windows to Ubuntu....I'm not sure what made me decide today was the day I needed to figure it out....

---

### Post by scxtt on 2007-09-02
i know i didn't specify above, but which host was that output from - the "server" or the "laptop"?  please provide the output from both (well, the other one, now) ...

---

### Post by Nameless on 2007-09-02
Oh...I didn't think about that.  The above output was from the "server"; the below is from the "laptop"

```

p   directvnc                       - VNC client using the framebuffer as displa
p   libsvncpp-dev                   - Subversion C++ library (development files)
p   libsvncpp0c2a                   - Subversion C++ shared library             
p   libvncauth-dev                  - Virtual network computing authentication h
p   libvncauth0                     - Virtual network computing authentication l
p   libvncserver-dev                - easy API to write one's own VNC server    
p   linuxvnc                        - VNC server to monitor a tty               
p   svncviewer                      - virtual network computing client software 
p   tightvnc-java                   - TightVNC java applet and command line prog
p   tightvncserver                  - virtual network computing server software 
p   tkvnc                           - Displays a list of (defined) machines to s
i   vnc-common                      - Virtual network computing server software 
p   vnc-java                        - VNC java applet and command line program  
v   vnc-server                      -                                           
v   vnc-viewer                      -                                           
p   vnc4-common                     - Virtual network computing server software 
p   vnc4server                      - Virtual network computing server software 
p   vncommand                       - VNC server which monitors a specified prog
p   vncserver                       - Virtual network computing server software 
p   vncsnapshot                     - A utility that takes JPEG snapshots from V
v   vncviewer                       -                                           
v   x0vnc-server                    -                                           
p   x11vnc                          - VNC server which uses your current X11 ses
p   x2vnc                           - A dual-screen hack - link an MS-Windows an
i   xtightvncviewer                 - virtual network computing client software 
id  xvnc4viewer                     - Virtual network computing client software 
i   xvncviewer                      - Virtual network computing client software 

```

---

### Post by Genecks on 2007-09-02
Try doing this stuff with Live-CDs. You'll find that it works better. The reason is because sometimes wireless devices and ethernet devices clash with each other. Also, the network files might not be good. A live-cd gives a fresh configuration.

---

### Post by scxtt on 2007-09-02
i think we should get vino out of the equation ... do a **sudo aptitude install tightvncserver** on the server ... after it's done, type **vncserver** into a terminal window - it should start a session on :1 that you can connect to on the laptop ...

after you do **vncserver**, do a **lsof | grep TCP** so we can be sure it's listening ...

note: you can specify which DE to use, and you can set a password, we can worry about that later ...

---

### Post by Nameless on 2007-09-02
Ok, sounds good.  

On the server I installed the tightvncserver and then ran lsof |grep TCP which had the following output:

```

vino-serv 5452       nate   16u     IPv6      18493             TCP *:5900 (LISTEN)
firefox-b 5867       nate   36u     IPv4      26599             TCP server.local:57676->nz-in-f104.google.com:www (ESTABLISHED)
Xtightvnc 7343       nate    0u     IPv4      26848             TCP *:x11-1 (LISTEN)
Xtightvnc 7343       nate    3u     IPv4      26851             TCP *:5901 (LISTEN)

```

Looks like tightvnc was set up and is now listening on 5901 (if I understand the above correctly)

When I tried to vncviewer <ip address>:1 on the laptop, though, it just sits there.  Nothing happens in terminal and I need to do a ctrl+z to get back to a prompt....not sure what that is about.

edit: terminal just came back and timed out on me again.  

I wonder if I need to reinstall the software on the laptop side...

---

### Post by scxtt on 2007-09-02
what do you get from **lsof | grep TCP** (on server) when "it just sits there" after connecting w/ the laptop?

this is feeling like a networking issue ... what's the output of **ifconfig** on both the server and laptop?

---

### Post by Nameless on 2007-09-02
> 
what do you get from lsof | grep TCP (on server) when "it just sits there" after connecting w/ the laptop?


```

vino-serv 5452       nate   16u     IPv6      18493             TCP *:5900 (LISTEN)
firefox-b 5867       nate   37u     IPv4      28236             TCP 192.168.0.100:52082->nz-in-f147.google.com:www (ESTABLISHED)
Xtightvnc 7343       nate    0u     IPv4      26848             TCP *:x11-1 (LISTEN)
Xtightvnc 7343       nate    3u     IPv4      26851             TCP *:5901 (LISTEN)

```

I ran it twice just to be sure it wasn't changing when I was trying to get the vncviewer up and running on the laptop.  the lsof command from the server came back the same way both times as above.

ifconfig from the server shows the following: 
```

eth0      Link encap:Ethernet  HWaddr 00:11:95:23:7C:39  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe23:7c39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18333845 (17.4 MB)  TX bytes:115288668 (109.9 MB)
          Interrupt:11 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14766848 (14.0 MB)  TX bytes:14766848 (14.0 MB)


```

ifconfig from my laptop shows this 

```


eth0      Link encap:Ethernet  HWaddr 00:0F:B0:6C:76:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:55015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64827652 (61.8 MiB)  TX bytes:3731329 (3.5 MiB)
          Interrupt:20 Base address:0xe400 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:B0:6C:76:69  
          inet addr:169.254.6.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20795 (20.3 KiB)  TX bytes:20795 (20.3 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.205.1  Bcast:192.168.205.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.131.1  Bcast:172.16.131.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:AC:C6:B0  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:feac:c6b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52913504 (50.4 MiB)  TX bytes:3778474 (3.6 MiB)
          Interrupt:21 Memory:b0204000-b0206000 

```

---

### Post by scxtt on 2007-09-02
> **Nameless said:**
> edit: terminal just came back and timed out on me again.  

I wonder if I need to reinstall the software on the laptop side...could  be a decent idea ... i'd remove anything vnc viewing related on the laptop and just do **sudo aptitude install vncviewer** - i really don't get this problem, all i ever have to do is install vncserver/vncviewer ... never had any problems, and this also includes a laptop w/ wireless ...

---

### Post by shane2peru on 2007-09-20
> **totalnub said:**
> have you thought about ssh with X11 fowarding?

you have to install the ssh server on your server:
```
 sudo apt-get install ssh 
```
then from the terminal type:
```
ssh -Y <usernamehere>@<ip of server>
```
and to get a display up, assuming nautilus is your file browser, just type nautilus in the terminal

Hey that is a really cool trick!  Very nice, however when I try to copy files from or too the nautilus window to my account (transfer files from one computer with one account to another computer with another account)  it doesn't let me. 

Shane

---

