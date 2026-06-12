---
title: "how do I open ports?  tcp and udp to use telnet, ftp, finger, talk, ssh, etc..."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by sonhadorpr on 2007-10-21
Ubuntu newbie here.

Say I wan to connect to my PC at home, from the University, or to my Ubuntu machine at the university(from home).  This machine doesn't have a name (i.e.: ubuntu-machine.u.edu), all it has is an IP address.
How can I login back and forth from these machines?
I use also the math department's Ubuntu server, on this one, I CAN connect TO IT, from my house, using ssh, since it has a name, not just an IP address, but NOT FROM it to my home PC.

How can I open up the ports...both ssh and telnet tell me that the connection was refused, when trying to connect, to/from  PCs.
Thank you all for your help.

ROM

---

### Post by xpod on 2007-10-21
IF you dont use a router then the best bet is probably installing firestarter to configure your ports with and the openssh-server package for connecting *to* your pc from elsewhere.

Firestarter is just a gui frontend to the built in firewall iptables though so when you`ve done your "configuring" it`s quite safe to close firestarter and theres really no need to have it running at startup.
I use firestarter myself and it`s a great tool for the job.

So much simpler than tackling iptables itself anyway:)

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Something else that seems kinda appropriate too:wink:
[http://www.uluga.ubuntuforums.org/showthread.php?t=510812](http://www.uluga.ubuntuforums.org/showthread.php?t=510812)

---

### Post by kast on 2007-10-21
You should be able to connect to a remote computer using an I.P as long as that PC is capable/set-up for incoming remote connections. If you ask me that would be a preferred method, using a name instead of an IP you would have to make sure there is some DNS translation going on to take the name and find its  IP. using the I.P instead of a Host name skips that step.

If your looking to set-up a remote connection from somewhere to your computer then you could install OpenSSH and configure it for your computer.

As for the ports, you would have to make sure the ports where open, on your firewall (if using one) and or your router, again if your using one.

---

### Post by Austin_KW on 2007-10-21
If you are using a standard broadband connection then the IP address can probably change. I use a dyndns.com free a/c to maintain a dns mapping for my IP address (eg myUbuntuP.homelinux.org[/email]). Many modern routers will support dyndns or you can install a pc client.

If you install openssh it will open open port 22 on your PC. If you have a router you will have to forward port 22 to your PC.
You do not want to open ports for the other servers, telnet, ftp etc. These are not secure protocols.

---

### Post by sonhadorpr on 2007-10-21
No, I do not use any router in my house, its just the cable modem directly connected to the PC.
And the IP address change as soon as I turn off the PC and turn on again.

HOWEVER, The PC with Ubuntu I use at the University, is on a router, and it has a static IP.
So then, I need to install OpenSSH, and the firewall program?

Can somebody give me step-by-step instructions?

Thank you

ROM

---

### Post by kast on 2007-10-21
well lets do this one at a time here, first i would recommend installing a firewall ASAP so we can start there.

Open a terminal and run this command
[B]
sudo apt-get install firestarter[/B]

If that fails you might need to enable the **"universe"** repository in the */etc/apt/sources.list* file or in synaptic under *Settings->Repositories*

If you need to enable the "universe" repositories then you will have to run

**sudo apt-get update **
then
[B]
sudo apt-get install firestarter[/B] 

again. Post back after. If someone else here wants to write out the directions for the rest feel free! i have two little kids here so its not easy sitting at the computer :)

---

### Post by Austin_KW on 2007-10-21
Just to be clear, the firewall is already there. firestarter is a gui interface to allow you to manage the firewall iptables. 

All ports are closed until you install a server (eg openssh), the servers will then start listening on their ports (22 for ssh) for incomming connections.

Firestarter will allow you to create rules, eg just allow connections to port 22 from your remote pc's IP address.

to install ssh
```

sudo aptitude install openssh-server openssh-client

```

You can then test that you have ssh access
```

rsh ***yourUsername@***localhost

```

Or to test remote copy (eg to copy your .bashrc file from your home directory)
```

 scp ***yourUsername@***localhost:/home/***yourUsername***/.bashrc ./bashrc-copy  

```

Once you get ssh running, you can use it for anything, even remotely running your desktop

---

### Post by Austin_KW on 2007-10-21
Also once you get it running you should rsh to your remote PC and then from there verify that you can rsh back into your local PC

---

### Post by dwhitney67 on 2007-10-21
"firestarter" may be a wonderful tool, but you do not need it to install or use SSH.

Before I tell you how to install SSH, I need for you to confirm that you will have access to the university's computer (server) from home.  The server at the university may be behind a firewall that prevents direct access from the outside.  If you have control over the firewall, then you can tweak it to allow access.  Generally SSH uses port 22 ( however that can be changed).

What you need on your remote server is an SSH server.  To install that:

[FONT="Courier New"]$ sudo apt-get install ssh[/FONT]

After the install, verify that it is running:

[FONT="Courier New"]$ ps -ef | grep sshd[/FONT]

You should see that /usr/sbin/sshd is running.

If you want to connect from the university to your home, just repeat the steps above on your home system.

Barring any firewalls blocking port 22, you should be able to SSH from one machine to another.  The protocol is:

$ ssh userid@serverIP

If you do not have a fixed IP address on either end, then you need to rectify this by either memorizing your system's IP address, or more conveniently by creating an account with DynDNS (as someone else mentioned).  [DynDNS]("http://www.dyndns.com/services/dns/dyndns/") provides the ability for your system to register its IP address with a domain name of your choosing.  It's fairly straightforward to setup.

That's really all there is to it.  Once everything is setup, familiarize yourself with these commands:
[LIST]
[*]ssh
[*]scp
[*]ssh-keygen
[/LIST]

Let me know if you still have any questions.

P.S.  You should be able to determine a system's IP address by running */sbin/ifconfig*

P.S.S.  This link to the Feisty Ubuntu Guide concerning [setting up an SSH server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server") may prove useful.

---

### Post by kast on 2007-10-21
starting with installing Firestarter was just so he would have some kind of protection from the out side world, right now he doesn't have a router or a firewall and is now installing software to allow remote connections.

would be nice to show him also how to protect his SSH server. :)

---

### Post by Austin_KW on 2007-10-21
I am guessing that most of us run a Nat router and do not bother with firestarter.

Start firestarter, it will run a wizard, just tell it which interface is connected to the internet. 
The easiest way is to allow firestarter to block the incomming connection, then check the event log, then right click on the blocked entry and create a rule for the source IP address.

---

