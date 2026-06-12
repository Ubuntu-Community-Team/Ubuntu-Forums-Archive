---
title: "[SOLVED] Remote Desktop to a Ubuntu computer using windows Remote desktop 6.0"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by jamesrfla on 2007-10-13
I can do a remote desktop using the VNC viewer from XP to Ubuntu. I want to try to use remote desktop 6.0 in windows XP to connect to the Ubuntu computer. I tried it and it came up asking for a user name and password. I put in the user name for my user on the Ubuntu computer and the password.
it said that it couldn't connect. What is the user name? Is this possible?

---

### Post by bodhi.zazen on 2007-10-13
Did you enable the vnc server on Ubuntu ?

[uwiki]VNC[/uwiki]

---

### Post by jamesrfla on 2007-10-13
I think I did. I went to system>preferences>remote desktop and enabled it there. I use a VNC viewer on my XP computer to access the Ubuntu computer.

---

### Post by bodhi.zazen on 2007-10-13
User name is your Ubuntu log-in name

Password is what you set at that configuration screen (System -> preferences -> Remote Desktop).

Make sure you un-tic the "Ask you for confirmation" box.

---

### Post by maybeway36 on 2007-10-13
[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Pg7&q=vnc+viewer&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Pg7&q=vnc+viewer&btnG=Search)

---

### Post by jamesrfla on 2007-10-13
I tried what you said bodhi.zazen but it didn't connect. It said couldn't connect to remote computer. Any other ideas?

---

### Post by bodhi.zazen on 2007-10-13
More details please. What vnc client are you using ? Try the vnc viewer :

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

Are you connecting over a lan ?

Firewalls ?

---

### Post by jamesrfla on 2007-10-13
I am using echo VNC viewer on my XP computer. I am over lan. All firewalls turned off.

---

### Post by bodhi.zazen on 2007-10-13
I would try the tight vnc viewer, it is available as a zip , no installation is required.

---

### Post by jamesrfla on 2007-10-13
I can connect using echo VNC. I just want to know if I can connect to the Ubuntu computer using windows remote desktop 6.0

---

### Post by jamesrfla on 2007-10-13
Is there a way to change the password for the remote access using terminal?

---

### Post by jamesrfla on 2007-10-13
I typed in sudo remote desktop. It asked for a password. What would be the password? I also tried sudo remote and it came up with the same thing. if I type sudo and then something it asks for a password.

---

### Post by mlentink on 2007-10-13
Jim. Windows RDP and VNC are different protocols. You can't expect to attach to a box equipped with one using the other. I would suggest to not try to remote control a linux box with a microsoft protocol.

---

### Post by mlentink on 2007-10-13
btw: typing in 'sudo' means something like 'as SUperuser (root) DO...'. The password asked for is your user password, since you will have, at installation time, established yourself as the superuser of your box. 

No magic there, just basic stuff.

---

### Post by jamesrfla on 2007-10-13
Okay thanks. I will just stay with the VNC viewer. I also wanted to say thanks to Ubuntu for their Secure and free file sharing. I like it so much.

---

### Post by Distortedgamer on 2007-10-24
> **bodhi.zazen said:**
> I would try the tight vnc viewer, it is available as a zip , no installation is required.

I downloaded this winVNC.exe and tried to run it from a jump drive from my work PC. I get the error "Another instance of winVNC is already running." So then I found out that my work uses winVNC to be able to remote to any of the workstations.

Is there a way to have multiple winVNC.exe to run? Or perhaps another method of desktop connection from winXP to linux, using an executable? (Not allowed to install anything)

---

### Post by bodhi.zazen on 2007-10-24
I use the tightvncviewer which is called "vncvewer.exe" from a removable drive.

It is a zip file, unzip and run :

[http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86_viewer.zip](http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86_viewer.zip)

I can run multiple instances :)

---

### Post by Distortedgamer on 2007-10-24
> **bodhi.zazen said:**
> I use the tightvncviewer which is called "vncvewer.exe" from a removable drive.

It is a zip file, unzip and run :

[http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86_viewer.zip](http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86_viewer.zip)

I can run multiple instances :)

Well, I got that one too. When I try to connect to my home network, it says "Failed to connect to server (hostname.org)


I tried using my hostname but nothing happened. Does this vncviewer use same protocols as ssh, through port 22? Or do I need to open a new port in my router?

---

### Post by bodhi.zazen on 2007-10-24
I HIGHLY advise you tunnel over ssh :

[uwiki]VNCOverSSH[/uwiki]

And see this for SSH security : [uwiki]AdvancedOpenSSH[/uwiki]

For vnc you need to forward port 5900 or 5901, 5902, ...)

An alternate is [uwiki]FreeNX[/uwiki]

---

### Post by Distortedgamer on 2007-10-24
Ok I will try that for now, thank you very much. I tried FreeNX but you have to install the client and I can't do that here.

---

### Post by bodhi.zazen on 2007-10-24
You do not (and should not) forward the 5900 ports of you tunnel over ssh :twisted:

---

### Post by Distortedgamer on 2007-10-24
Alright, so which ports do I forward for the VNC part? I have 22 forwarded for ssh. Your first post says "forward ports 5900..." then your second post says "do not forward ports 5900"???


**edit** 
So I followed the instructions on the [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH) Page. I got the ssh connection connected and then typed in 

> ssh -fCNT user@192.168.1.25 -L 5901:127.0.0.1:5901

Then typed in
> vncviewer localhost:1

and then I get
> VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Error: Can't open display:

How do I get the desktop to show up?

---

### Post by bodhi.zazen on 2007-10-24
> **Distortedgamer said:**
> Alright, so which ports do I forward for the VNC part? I have 22 forwarded for ssh. Your first post says "forward ports 5900..." then your second post says "do not forward ports 5900"???

Sorry, I should have been more clear.

If you are **tunneling your VNC connection over ssh**, you only need to forward the ssh port, 22 is default, but you should consider changing to an alternate port (your ssh server will get hammered by would be crackers).

If you are **NOT** using ssh to tunnel ssh, then you need to forward the VNC ports, 5900 == :0 (vino)
5901 == :1, etc ...

I hope that helps and that you understand your VNC ports from my previous links ...

---

### Post by bodhi.zazen on 2007-10-25
What client are you using to make the connection on windows ? Putty ? cygwin ?

Where did you enter that command > ssh -fCNT user@192.168.1.25 -L 5901:127.0.0.1:5901 ??

From your description it sounds as if you are making a ssh connection, which gives you a command line interface, and then entering those commands into the ssh (ubuntu) terminal?

What you need to do :

1. Set up a ssh server on Ubnutu (sounds like that is done).

2. Set up a VNC server on Ubuntu (I assume that is done as well). You need to know the port, 5900 ( :0 ) or 5901 ( :1) ???
[list][*]The default VNC server is "vino" and shares your desktop. This is port 5900.
[*]If you installed a vnc server, vnc4server, tightvncserver, that would use port you woul dstart it and declare the port :```
vnc4server :1
```This sets the port to 5901 (vncserver :55 = port 5955 ; vncserver :xx = port 59xx ).[/list]

3. Make a ssh connection from Windows. I suggest you use Putty (see the putty instructions on that link). **If you use cygwin** then you would open a cygwin terminal (on windows) and enter "ssh -fCNT user@192.168.1.25 -L 5901:127.0.0.1:5901" without quotes to make a ssh connection. **Once the ssh session has started, log into ubuntu, then that is all you need to do. You do not need to enter any commands into the ssh (ubuntu) terminal.**
[indent]Although if you would like increased security, DO NOT RUN a VNC server at all times. Rather ssh into Ubuntu and start the VNC server from the ssh command line, then follow #4 below. When you finish, close your vnc viewer, kill the vnc server, close the ssh session.[/indent]

4. Start your vnc client on windows. In the connection box enter localhost (no :0) for vino, or port 5900, or localhost:1 for vncservew (port 5901).

---

### Post by Distortedgamer on 2007-10-25
I am not sure what is going wrong here. I think I am just bound to get close to a solution in linux and then fail. (I have only been using Linux for about a month now.)

I use PuTTy from my winXP machine. I know that SSH works because I can do that through PuTTy. 

I get lost after connecting with SSH. I connect through PuTTY, then I open vncviewer.exe on the windows machine. It opens a Tight VNC client and asks for the VNC server: So I typed all of these and got the same result
> hostname.org
hostname.org:01
hostname.org:1
localhost:1
localhost (no :0)

"Failed to connect to server (hostname.org)"

I can remote into a second PC at home (with winXP) which has a VNC client installed. When I put the Linux box's IP in as the VNC server, it connects fine. But when I use hostname.org for the VNC server name it also gives me "Failed to connect to server (hostname.org)"



Since I wasn't sure what I was really using, I forwarded both ports for SSH and for VNC.

---

### Post by bodhi.zazen on 2007-10-25
Did you configure Putty to forward the (VNC) ports ?

Firewall ?

---

### Post by Distortedgamer on 2007-10-25
Firewalls: I have zonealarm and Peer Guardian, so I turned them both off and still get the same problem. No firewalls on the linux box. I can connect through a VNC client from a LAN PC by IP but not by hostname. 

As far as forwarding ports in PuTTy, when I first open PuTTy I put my hostname in the hostname textbox. I then click on ssh>tunnels. In the source port I put L5901 and in the destination I put: hostname.org:5901 then click add. I then went and saved that session and then clicked connect. I was able to connect with the SSH fine. I then open up VNCviewer.exe and put in hostname.org:1 in the server field and click connect. It comes up and says "Failed to connect to (hostname:1)".

Right now, only port 22 is forwarded.

---

### Post by kspear on 2007-10-25
I too am trying to get the desktop visible.  I have the SSH connection working. I then connect the vnc viewer and that works.  What i get is a window showing a command line terminal only.  

At this point, how do i startup the desktop? Is it possible?  The ubuntu box is now in the home "server closet" and headless.  

Do i need to re-attach keyboard & mouse to toggle some settings to get remote desktop to work?

Thanks for any help!

---

### Post by bodhi.zazen on 2007-10-25
@Distortedgamer: What vnc server are you using on Ubuntu ?

Once you make a ssh connection, the address in the vnc viewer is localhost:1 (because you have already forwarded the port via ssh , so you do not need hostname:1 or ip:1).

==============

@kspear: If you can ssh in, you can install and start a vncserver.

again, what vncserver are you using ? you will need to install one if you are running headless.

See [uwiki]VNCOverSSH[/uwiki]

You can use the tightvnc server or vnc4server, neither of which are installed by default ...


==============

---

### Post by Distortedgamer on 2007-10-25
It looks like tightvncserver and vncserver are installed on Ubuntu. 

Am I forwarding the ports correctly in the PuTTy session?

Under tunnel, I make the source port 5901 then for the destination port I put: <internal address>:1 and then click add.

Then on the vncviewer.exe I put this for the server name: localhost:1 then click connect.

Do I need to uninstall one of those vncservers? Which one?

---

### Post by bodhi.zazen on 2007-10-25
On the Ubuntu server, you need to :```
vncserver :1
```

On putty, forward 5901 to localhost:5901

On vnc viewer connect to localhost:1

You are using the wrong terminology other wise

---

### Post by Distortedgamer on 2007-10-25
Getting a lot closer now I think.

When I try to connect with VNCviewer it says:
> Connecting to localhost:1 ...
Status: Connection established.

Goes like that for a little while, then a popup comes up and says
> Connection Closed

---

### Post by Distortedgamer on 2007-10-26
I got tired of it not working so I installed Nmap and did a port scan on my network. For some reason port 5901 wasn't open at all. So I just used port 5902 and everything worked out great. 

Thank you so much for the help!!!!!

---

