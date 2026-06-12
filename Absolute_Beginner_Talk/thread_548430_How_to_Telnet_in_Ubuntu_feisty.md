---
title: "How to Telnet in Ubuntu feisty?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by aozkaya on 2007-09-11
Hi,
I am working in  a closed network, where I have over 10 PCs. All of them have been recenlty  installed Ubuntu feisty, and they are in the same subnetwork. They all have 10.0.0.x IP addresses.
I am trying to telnet and I get this error:

student@student-desktop:~$ sudo telnet 10.0.0.1
Trying 10.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Why I am getting this error? I really appreciate it if you give me any advise.

Thanks,
Aslihan

---

### Post by hyper_ch on 2007-09-11
(1) Don't use telnet... deinstall it

(2) Use ssh:
```

sudo apt-get install openssh-server

```

(3) Login:
```

ssh user@10.0.0.x

```

(4) 10.0.0.1 seems to be the IP address of your router...

---

### Post by asmoore82 on 2007-09-11
I would install and use openSSH ...

```
~$ sudo apt-get install openssh-server
```

you can verify that the ssh server is activated in Gnome by
opening "System -> Administration -> Services"
and it shows up as "Remote Shell Server (ssh)"

then you can connect to the machine from any other *NIX box with
```
~$ ssh -l *<remote_username> <remote_ip_address>*
```
'-l' = "-(lowercase L)"

you can also enable X11 forwarding to use graphical applications
remotely by adding the '-X' switch.

---

### Post by asmoore82 on 2007-09-11
with SSH, you can also install the client "**clusterssh**" to
run commands on multiple remote hosts simultaneously ...

after apt-ing **clusterssh**,
it is in "Applications -> Internet -> ClusterSSH"
and it's command line is simply **cssh**

---

### Post by aozkaya on 2007-09-11
Thank you for your fast reply,
I have installed the openssh-server and it show up in System-->Administration--> Services as Remote shell server
And it is activated.
But this time I get this error:
student@student-desktop:~$ sudo ssh 10.0.0.1
ssh: connect to host 10.0.0.1 port 22: Connection refused
student@student-desktop:~$ sudo ssh student@10.0.0.1
ssh: connect to host 10.0.0.1 port 22: Connection refused

(They all are connected to a hub) Is there any suggestion?
Thanks 
Aslihan

---

### Post by Dr Small on 2007-09-11
Make sure the server where you installed openssh-server has port 22 opened.

Dr Small

---

### Post by aozkaya on 2007-09-11
this time, I have installed the openssh-server to the other PC now it is connected.
Thanks a lot!
But is there any way to use telnet. Because thi network isn't connected to the internet. There is no risk. And we are following a manual book which uses telnet, and it also has some experiments about the differences with telnet and ssh. In order to see the differences I need also telnet.
Thanks,
Aslihan

---

### Post by Dr Small on 2007-09-11
SSH can do everything telnet can do, and more. I use ssh over my network, and it works great. You can access the pc, run commands, and even port the display over to your monitor. There is alot you can do with SSH.

Dr Small

---

### Post by asmoore82 on 2007-09-11
> **aozkaya said:**
> Thank you for your fast reply,
I have installed the openssh-server and it show up in System-->Administration--> Services as Remote shell server
And it is activated.
But this time I get this error:
student@student-desktop:~$ sudo ssh 10.0.0.1
ssh: connect to host 10.0.0.1 port 22: Connection refused
student@student-desktop:~$ sudo ssh student@10.0.0.1
ssh: connect to host 10.0.0.1 port 22: Connection refused

(They all are connected to a hub) Is there any suggestion?
Thanks 
Aslihan

you don't need all the "sudo"s to use ssh.

---

### Post by aozkaya on 2007-09-11
But as I know I can't crack passwords by usign traffic from ssh. In the manual (that we are following) there is an experiment that snoops passwords from telnet and ftp session. 
Therefore I need telnet? Could you please help me to use telnet? do I neet to install it?

---

### Post by asmoore82 on 2007-09-11
> **aozkaya said:**
> But as I know I can't crack passwords by usign traffic from ssh. In the manual (that we are following) there is an experiment that snoops passwords from telnet and ftp session. 
Therefore I need telnet? Could you please help me to use telnet? do I neet to install it?

the telnet server package name is **telnetd**

---

### Post by Dr Small on 2007-09-11
In order to use telnet, you may have to install telnetd, and then open port 23 on the server.

Dr Small

---

### Post by aozkaya on 2007-09-11
I have tried but still not able to,
I have installed telnetd and the dependencies tcp and openbsd-inetd.
This is what I have done:
student@student-desktop:~/tel2$ sudo dpkg -i tcpd_7.6.dbs-11ubuntu0.1_i386.deb Selecting previously deselected package tcpd.
(Reading database ... 88255 files and directories currently installed.)
Unpacking tcpd (from tcpd_7.6.dbs-11ubuntu0.1_i386.deb) ...
Setting up tcpd (7.6.dbs-11ubuntu0.1) ...
student@student-desktop:~/tel2$ sudo dpkg -i openbsd-inetd_0.20050402-3_i386.deb 
(Reading database ... 88276 files and directories currently installed.)
Preparing to replace openbsd-inetd 0.20050402-3 (using openbsd-inetd_0.20050402-3_i386.deb) ...
Unpacking replacement openbsd-inetd ...
Setting up openbsd-inetd (0.20050402-3) ...
 * Not starting internet superserver: no services enabled.
student@student-desktop:~/tel2$ sudo dpkg -i telnetd_0.17-35ubuntu1_i386.deb (Reading database ... 88276 files and directories currently installed.)
Preparing to replace telnetd 0.17-35ubuntu1 (using telnetd_0.17-35ubuntu1_i386.deb) ...
Unpacking replacement telnetd ...
Setting up telnetd (0.17-35ubuntu1) ...
student@student-desktop:~/tel2$ telnet 10.0.0.3
Trying 10.0.0.3...
telnet: Unable to connect to remote host: Connection refused
student@student-desktop:~/tel2$ sudo telnet 10.0.0.3
Trying 10.0.0.3...
telnet: Unable to connect to remote host: Connection refused

Is there anything wrong?
Thanks
aslihan

---

### Post by prabbit237 on 2007-09-11
You installed telnetd on the machine you want to telnet TO or just the one you want to telnet FROM? The telnetd is the server that needs to be run on the remote computer (telnet is the client program that runs on the local machine that you're seated at.)

---

### Post by prezory on 2007-09-11
If you search for telnet in the package manager you'l find a telnet client and an telnet server.
In the case of telnet, you'l probably have to reboot for the server to start.
____________________________
Ceep your path clean! ;)

---

