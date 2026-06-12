---
title: "Controlling home computer from work"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-28
I need to be able to control my home computer from work. There are many things I learn which I want to try out immediately on my home machine, rather than waiting the whole day and doing them once I get home.
 
I use Win XP at work and Ubuntu at home.
 
I know for sure that my workplace network is firewalled and most all ports are blocked. I also do not have control over changing and/or modifying these.
 
I did a cursory search on this and found that I could 
1) Remote Desktop to my home machine
2) Set up DynDNS and use that to point to my home machine.
 
 
Could someone give me a detailed insight into either of these? Which one would be easier ?
Will DynDNS allow me to use the native apps installed on my home machine?

---

### Post by aeiah on 2007-06-28
you'll be needing VNC software ideally, although i dont know much about it myself. you'd need to install a VNC client on your work computer, which they may not let you do. you could also ssh into your home pc, which would enable you to control it via the CLI

---

### Post by Inxsible on 2007-06-28
> **aeiah said:**
> you'll be needing VNC software ideally, although i dont know much about it myself. you'd need to install a VNC client on your work computer, which they may not let you do. you could also ssh into your home pc, which would enable you to control it via the CLI
 
I have admin privileges on my work laptop, and I already have VNCViewer (for XP) installed. Can I simply install a VNC server on my Linux box at home and be done with it ?
 
Will this traffic be monitored, as in will they know what I do over VNC?

---

### Post by mlentink on 2007-06-28
> **Inxsible said:**
> Will this traffic be monitored, as in will they know what I do over VNC?
Well, yes, in the sense that they will see traffic on port 5900. But since that traffic is encrypted, they could not see what that traffic was. And iif you would tunnel VNC over SSH, I doubt if they could ever see what it was you were doing. 
They could block outgoing traffic on ssh and vnc, which you would have to circumvent by using other ports, which they then would block, which you circumvented by using yet other ports......

---

### Post by Inxsible on 2007-06-28
> **mlentink said:**
> Well, yes, in the sense that they will see traffic on port 5900. But since that traffic is encrypted, they could not see what that traffic was. And iif you would tunnel VNC over SSH, I doubt if they could ever see what it was you were doing. 
They could block outgoing traffic on ssh and vnc, which you would have to circumvent by using other ports, which they then would block, which you circumvented by using yet other ports......
 
LOL. True, but I am gonna try this once...and if they have blocked it I might just wait until i get home to do stuff.
 
But this could be real helpful for me to log into my parent's machine and rectify something. They currently have Win XP, which is slower than a sloth and I need to kinda go in and get rid of the temp files and other basic stuff. 
 
I would rather do it myself than explain the instructions to them over the phone, if you know what I mean  !!!  ;)
 
The next time I visit, I plan to put them on Ubuntu too.

---

### Post by Inxsible on 2007-06-28
Secondly, I do not think they would block port 5900, mostly because we use VNC to remotely operate machines on other sites of our company. 
 
Even if they do, they have to keep VNC an "allowed" software, if you will.
 
Kinda works out for me :D

---

### Post by mlentink on 2007-06-28
sure does!

I use VNC everyday to keep an eye on what's going on at home. Works for me...

---

### Post by Inxsible on 2007-06-28
> **mlentink said:**
> sure does!
 
I use VNC everyday to keep an eye on what's going on at home. Works for me...
 
So what VNC Server do you use? RealVNC is paid..so its out.
 
Do you use TightVNC or UltraVNC or any other?

---

### Post by Fanatico on 2007-12-24
I am also looking for the application which will allow me to remotely access my home computer from work.
At work I have Windows XP, at home I use Linux Ubuntu 7.10. What I need is to be able to run remotely some commands in terminal window on my home computer from work.

Two applications were mentioned above TightVNC or UltraVNC. I read their pages and still not quite sure whether the link will work between Linux and Windows. Any suggestions or recomendations?
Can anyone recommend other application(s) which will allow me to access  home Linux computer from work Windows Xp?

Thanks

---

### Post by kpkeerthi on 2007-12-24
> **Fanatico said:**
> What I need is to be able to run remotely some commands in terminal window on my home computer from work.

I suggest you SSH onto your home PC. Putty is a free SSH client for windows

**Other things to note:**

1. Install [SSH Server]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH")
2. You should know the public IP of your home pc to be able to SSH. Alternatively, use [DynDNS]("https://www.dyndns.com/services/dns/dyndns/") to get yourself a DNS name that maps to your dynamic IP address. 
3. Make sure you set up your router to [port forward]("http://portforward.com/") the incoming SSH connections to your home computer. 
4. Also, open the SSH port in Firestarter/IPTABLES

---

### Post by aparmley on 2007-12-26
Total newb question I know - 

Will running Putty (SSH client for windows OS) give you GUI connection to your Ubuntu box at home (Given you've installed a SSH server, configured it to listen to the right port, forwarded the port on your router and properly set up DynDNS account)? Sound and all?

---

### Post by aparmley on 2007-12-28
Well, after installing everything and running putty at work I was only able to gain a command line connection with my Ubuntu Box at home. I was unable to get the vnc client to connect.

---

### Post by AndyCooll on 2007-12-28
Putty itself (and SSH protocol) are command line only. What you'll need to do is create the SSH link using the Putty client and then open up a VNC session. 

It's like starting an application (e.g. Nautilus) on your local machine from the command line. You open up a terminal first and then type in the programs command (e.g. gksudo nautilus). This in turn opens up the Nautilus gui application.

This is similar except that once you've opened up the terminal you first need to connect to the remote machine. Once you've done that away you go.

:cool:

---

### Post by aparmley on 2007-12-28
What I tried was connecting with putty. Once connected with putty I tried both Real VNC and tightvnc to connect to the same IP address I used with putty. The right error message might make all the difference here so I won't guess at what it was. I'll have to try again next week and report back. Thank you for sounding off Andy (thats a good name)

Andy

---

### Post by AndyCooll on 2007-12-29
> **aparmley said:**
> What I tried was connecting with putty. Once connected with putty I tried both Real VNC and tightvnc to connect to the same IP address I used with putty. The right error message might make all the difference here so I won't guess at what it was. I'll have to try again next week and report back. Thank you for sounding off Andy (thats a good name)

Andy

And you tried doing so through your SSH connection yes? I ask because you realise that you don't make a direct vnc connection to a remote pc don't you? That is you can't just type open up vnc and type in the same IP address that you used for SSH.

:cool:

---

### Post by Belerophon on 2007-12-29
I also want to control my desktop at home...controll a machine running XUBUNTU from other running UBUNTU.

The objective is to get access to a remote desktop. For now, I'm just making tests with two computers within my home network.

I was told that, to VIEW AND CONTROL a remote desktop, I needed only a ssh server (openssh) and the *-X* option when I do a ssh:
*ssh -X user@home*

Is this true?...I've manged to make a ssh connection to the server, and open gui applications. But what I really want is to see the Xubuntu desktop, and controll it.
...or can't this be done without VNC software???

---

### Post by Belerophon on 2007-12-30
Well, after some help of a friend, I found out that, after having a secure shell with X forwarding, I can simply type *xfce4-session* and done! I have my remote desktop.

(I've done this in a failsafe terminal: log out from my session making sure I'm connected to the network, go to options and choose failsafe from sessions. Made a ssh to my server, and then typed *xfce4-session* and the entire desktop is loaded!)

It's not the desktop that is already open in the remote machine. It's just a new session of Xfce, My icons are there, its all there, but the windows/applications that might already be open in the server, don't appear in this new session.

So, I think that I cannot control what is already open "in the other side" without any extra software, but I can easily create a new "instance" of my desktop only with the ssh client and server.
Are my thoughts right?
And if they are, what is VNC? what are its advantages??

---

### Post by Fanatico on 2008-01-02
> **kpkeerthi said:**
> I suggest you SSH onto your home PC. Putty is a free SSH client for windows

**Other things to note:**

1. Install [SSH Server]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH")
2. You should know the public IP of your home pc to be able to SSH. Alternatively, use [DynDNS]("https://www.dyndns.com/services/dns/dyndns/") to get yourself a DNS name that maps to your dynamic IP address. 
3. Make sure you set up your router to [port forward]("http://portforward.com/") the incoming SSH connections to your home computer. 
4. Also, open the SSH port in Firestarter/IPTABLES

kpkeerthi, thank you for your response.

Could you provide more details about step 4 "Also, open the SSH port in Firestarter/IPTABLES" or refer me to any tutorial, explanation, etc

One more question:
I realize that SSH is command line only tool. As I understood there are other  full screen VNC applications, like TightVnc for example. My question is if I want to use TightVnc, should I install TightVnc in addition to SSH, or TightVnc is  independent  tool which doesn't required SSH. Or I should install TightVnc in addition to SSH?

Thanks

---

