---
title: "SSH Server???"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by ftaylor on 2007-12-19
Hello.

I have a Laptop with gutsy and a Desktop with gutsy. My university has a lab of linux computers that I can connect to over the internet and access the files and programs using SSH. What I want to be able to do is connect to my desktop at home from my laptop anywhere. The laptop is connected to my home network via wireless, the desktop directly to the router.

I try and make an SSH connection between the 2 and it just says "192,168.1.2" is refusing connection.

What do I have to do? Do I need to setup an SSH Server or something? Just want someone to point me in the right direction please.

Thanks

---

### Post by LaRoza on 2007-12-19
> **ftaylor said:**
> 
I try and make an SSH connection between the 2 and it just says "192,168.1.2" is refusing connection.

What do I have to do? Do I need to setup an SSH Server or something? Just want someone to point me in the right direction please.

Thanks

```

sudo aptitude install ssh

```

The router must also be configured, have it forward port 22.

---

### Post by ftaylor on 2007-12-19
Do I do that on both of them or just the desktop? Does that automatically setup a server that I'll be able to connect to from anywhere? With right usn and password of course.

---

### Post by LaRoza on 2007-12-19
> **ftaylor said:**
> Do I do that on both of them or just the desktop? Does that automatically setup a server that I'll be able to connect to from anywhere? With right usn and password of course.

That will enable to computer it is installed on to be connected to.

You don't need it on both.

---

### Post by ftaylor on 2007-12-19
Thanks very much. Haven't tried it yet but I've bookmarked and I'll give it a go later.

---

### Post by Belerophon on 2007-12-22
Hi. I am trying to do the same thing as ftaylor...the idea is to set up a server at home, in such a way that I can control my desktop at home from anywhere. This is done with a ssh server right(openSSH or something right)?
Can I have access to my ubuntu desktop running the server??

Like him, I am used to make such connections like xxxx@somewhere. Will I be able to do this with my ssh server?(my desktop is connected to a router and the router is connected to a modem) How do I set up the "*@somewhere*" for my server???

And about security? How do I set up ssh server, with a user and password, or using encryption keys?

I would be greatly appreciated if someone could post some GENERAL guidelines to achieve these goals, starting with the installation of the server...:D

Thank you.

---

### Post by hyper_ch on 2007-12-22
ssh will give you a command line login.

And you will need to know the IP address of your home server... and as it is behind a router, you will need to forward the port on the router to your server...

If you don't have a fix IP address, then you should make use of a dyn. ip service like [www.no-ip.com](www.no-ip.com) or [www.dyndns.com](www.dyndns.com) - they have daemons for linux which will then auto-update the domain...

e.g. belerophon.no-ip.com

---

### Post by syutzy on 2007-12-22
As hyper_ch said, you need a way to access your machine from the outside world.  Dynamic DNS services such as those mentioned, or [http://www.zoneedit.com]("http://www.zoneedit.com") allow you to set up your machine to automatically update its IP address as it changes at the whim of your ISP.  (This is also how people run web servers at home behind their router, forwarding port 80)

Once you know your IP address, set the router to forward port 22 to whichever machine you want,  192.168.1.2 in this case.  Port 22 is used by default for the ssh server, but you can change it if you want.

Next, install the ssh server.```
sudo aptitude install openssh-server
``` or ```
sudo apt-get install openssh-server
```

The ssh server install will generate your keys and start the server.  If you want to edit your server config (change port, enable/disable users that can login remotely) consult the documentation for sshd_config, edit /etc/sshd_config, and restart the server```
sudo /etc/init.d/ssh restart
```

---

### Post by Belerophon on 2007-12-28
Ok.
Thanks for the replies!! ;) About the stuff related to be able to work over seas :) with my server, I'll see that later! I don't really know much about what are "Dynamic DNS"...but i'll look into it later!

I have installed the ssh server in a machine inside my home network.
with another machine also inside the network, I did a normal ssh to the machine that has the server...it works :D

I read somewhere that I should alter the ssh_config file to "see windows" from the remote server. I put:

X11Forwarding yes
ForwardAgent yes
ForwardX11 yes

So, now if I do a ssh to the server with -X, I am able to open things like gvim.
But what I really want is to do an ssh and SEE THE ENTIRE REMOTE DESKTOP, being able to control it.
How can I do this?

(sorry about my english 8-[ )

---

### Post by Belerophon on 2007-12-29
By the way, the remote desktop I want to see, belongs to a machine running Xubuntu 7.10!
And the machine that makes the connection is running Ubuntu 7.10...is there any problem in this??

---

### Post by hyper_ch on 2007-12-29
if you''re outside your lan you will need to forward the ports accordingly. Your router does not know by default what machine you are trying to communicate with. So in your router you will have to forward port 22 to the machine you want to ssh in.

---

### Post by drjunior on 2007-12-30
Hello "sir Belerophon"...I do not have time to read carefully all the details of conversation. However i understood your question. After you have a secure shell connection between your two machines, like you can start the application qvim, you can too start the application that control all the environment and the desktop in your operative system. You have to pay attention, depending on what machine you really want to start your session. Because the application varies with distribution in ubuntu. Following you can see 3 examples ( application that control what you want) depending your distro:

UBUNTU (GNOME): gnome-session

KUBUNTU (KDE): startkde

XUBUNTU (XFCE): xfce4-session

Sorry for my English...

---

