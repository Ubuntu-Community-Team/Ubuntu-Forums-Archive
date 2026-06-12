---
title: "SSH port forward to Ubuntu server works with Windows client, not with Ubuntu client"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2008-04-09
OK I'm pretty sure I'm missing something simple here but I'm not sure what it is.

I'm trying to SSH to my LAN from an outside location somewhere in the world and port forward ports 5900 back to my laptop (running Ubuntu). The overall goal is to SSH to a gateway SSH server (while forwarding port 5900) and then SSH from there to any other computer on my LAN and forward those port 5900 as well to enable remote desktop access (using Tight VNC) to any computer on my LAN through this gateway computer to my laptop. I have port forwarding on all the routers/firewalls set up properly. 

The thing is that when I use putty from a Windows computer to SSH to my LAN (74.xxx.xx.xx) and set up the port forward, it works. I can use Tight VNC viewer in Windows to access the desktop of the gateway SSH server (emachines-ubuntu 192.168.0.108 ) which runs Ubuntu. (This is where the firewall and router forward all connections on port 22 to.) However, when I use the Ubuntu command line of that computer to try to connect to another computer (server-ubuntu 192.168.0.106) the port forwarding will not go through and I get the following error:

```
everyone@emachines-ubuntu:~$ ssh -L 5900:192.168.0.106:5900 192.168.0.106 -l bryan
bryan@192.168.0.106's password:
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
Linux SERVER-UBUNTU 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Apr  9 09:37:09 2008 from emachines-ubuntu.local
bryan@SERVER-UBUNTU:~$
```

The same thing happens if I use the -R instead of -L to forward the ports.

Now, the same type of thing happens if I want to get into my LAN using the SSH port forwarding command.
```
bryan@thinkpad-ubuntu:~$ ssh -L 5900:74.xxx.xx.xx:5900 74.xxx.xx.xx -l everyone
everyone@74.xxx.xx.xx's password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
Linux emachines-ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Apr  9 09:46:13 2008 from cu-nat-2.clemson.edu
everyone@emachines-ubuntu:~$
```

However, if I use VNC's command for using SSH:
```
vncviewer -via everyone@74.xxx.xx.xx localhost:0
```
Everything works perfectly, just as if I were to use putty and Tight VNC viewer in Windows.

My question is, what is the problem with the default SSH command I'm using? What command should I be using? And can I even port forward 5900 from server-ubuntu (192.168.0.106) using emachines-ubuntu (192.168.0.108) as a gateway to forward everything back to my laptop which is out in the outside world?

Sorry about being so wordy, but if anyone can help me out that would be amazing.

---

### Post by kebes on 2008-04-09
My best guess is that the problem is because you are using port 5900, which translates in VNC terminology to ":0" or "display 0". The reason this might cause a problem is because on your client end, display 0 is already being used (to display the normal screen). This is why it's usually a good idea to run VNC on ":4" or ":5" (which then appears on port 5904, or 5905).

So, try shutting down VNC on the remote machine and re-launch it using ":4". Then try to connect with port-forwarding on 5904 and see if that works. (This is what I do, in any case.)

---

### Post by bodhi.zazen on 2008-04-09
Looks to me like you already have port 5900 forwarded, from a previous ssh session ?

check 

```
ps aux | grep ssh
```

but that would be why a new ssh session fails and the vnc connection works with localhost:0

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by AngryMallard on 2008-04-12
So I didn't really figure out what the problem was, except that I was forwarding to the default session a couple of times. Even after I fixed that, my method still wasn't working so I found out that just executing this command:

```
ssh -L 5908:192.168.0.106:5900 everyone@74.xxx.xx.xx
```

gets the job done. A shell is opened up on 74.xxx.xx.xx and then that computer relays port 5900 from 192.168.0.106 through 74.xxx.xx.xx back to localhost:8. (Important note: the 74.xxx.xx.xx computer's LAN address is 192.168.0.108. My firewall forwards all incoming connections on port 22 to that local address, so connecting to 74.xxx.xx.xx is the same as connecting to the local address 192.168.0.108.)  Then I just have to run terminal server client and connect to localhost:8. The only potential problem is that data between the gateway and the remote computer is sent over the LAN in the clear, but since it's my LAN i'm not too worried about that.

Any way, thanks for your help. You definitely pointed me in the right direction.

---

