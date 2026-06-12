---
title: "How to turn my ubuntu into a server?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by gil michael on 2007-12-14
Hi,
I have ubuntu 6.10 installed on my computer. I want my brother to be able to connect my computer and transfer files. I have already defined a username and  password for him. How can i make my linux a server?

Regards,
Gil

---

### Post by kebes on 2007-12-14
> **gil michael said:**
> Hi,
I have ubuntu 6.10 installed on my computer. I want my brother to be able to connect my computer and transfer files. I have already defined a username and  password for him.l

There are different ways to transfer files (FTP, SFTP, Samba share, etc.)... so it depends what you want.

My recommendation is to install an SSH server on your computer. A good one is OpenSSH. So just use Synaptic to install the package "openssh-server" (or on the commandline use "sudo aptitude install openssh-server").

Once installed, a process called "sshd" will constantly run and allow anyone with a username/password on that computer to log-in using SSH or SFTP using that username/password. If you have any firewalls active, you may have to unblock port 22 to allow the SSH connection to go through.


If you prefer setting up FTP or something else, that can also easily be done... but SSH/SFTP is the most secure and flexible.

---

### Post by Tipo on 2007-12-14
You could try enabling SAMBA....

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by slimx3m on 2007-12-14
> **gil michael said:**
> Hi,
I have ubuntu 6.10 installed on my computer. I want my brother to be able to connect my computer and transfer files. I have already defined a username and  password for him. How can i make my linux a server?

Regards,
Gil

i would recommend you open ssh. it is really easy to use

---

### Post by Hospadar on 2007-12-14
I use ssh for remote access on my machine, and really enjoy it.  there's just a few things you'll need to do if you want to make full use of it.  First: install firestarter (unless you want to configure iptables manually - blech) and open up port 22 (this is the port ssh listens to) and if you are behind a router, you'll need to go into your router's setup and forward port 22 to your machine.

then from another (linux) machine just type "ssh <username on the server>@<IP address of the server or router>" or on a windows machine, use a client like putty to get terminal access, and if you want, install a windows x server like xming to be able to remotely use graphical applications (you'll be able to do that in linux with nothing extra).  also if you just want file transfer, you can use a file client like filezilla on windows or linux.

---

