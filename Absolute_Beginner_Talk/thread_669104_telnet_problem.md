---
title: "telnet problem"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2008-01-16
I have my linux machine with ip X.Y.Z.W  but when i try to telnet to it through another system it gives me the error connection refussed ( using the command telnet x.y.z.w ). The two machines are connected as i can ping the other machine. I think telnet services is dissabled on my linux machine. How do i enable telnet? please help

---

### Post by scizzo on 2008-01-16
Why use telnet when ssh is there to do a better job?

---

### Post by scizzo on 2008-01-16
If you still really want telnet installed and running.

```

apt-get install telnetd

```

Or check for telnet in the package manager. Or with apt-get

```
apt-cache search telnet
```

Once installed you have to restart the inetd.

```
sudo /etc/init.d/inetd restart
```

I do not suggest using telnet though.

---

### Post by quarkhirad on 2008-01-17
dear scizzo

I agree with you about telnet but the problem is that we have windows users out here. Any way i installed telnetd but still the problem persists. Also from my fedora system ssh is also saying connection refused. I am using ubuntu 6.06

---

### Post by hyper_ch on 2008-01-17
> **quarkhirad said:**
> dear scizzo

I agree with you about telnet but the problem is that we have windows users out here.

What is the problem with the windoze users out there?

---

### Post by quarkhirad on 2008-01-17
dear hyper_ch

The problem is that i cannot use ssh on windows without having third party stuff. That is if i click on start menu the run and then type ssh ip address it will say command not found. However in run command telnet ip ddress works. Now my problem is i am not able to telnet  to my linux machine from any other machine be it a windows or a linux machine. Can you help me?

---

### Post by Dr Small on 2008-01-17
PuTTy is lightweight and portable, so that could work for SSH, but as for you telnet problem, make sure you have the right port open for telnet on your host machine. (I forget what port it uses... I think it's port 21)

Dr Small

---

### Post by hyper_ch on 2008-01-17
Putty is great... used it for years...

---

### Post by quarkhirad on 2008-01-17
Dear Dr. Small

Thanks for the suggestion. I am aware of putty. Now to the problem can you tell me how to enable the port in ubuntu 6.06. Assume it is 21 and then tell me. I shall find out the correct one and replace 21 with it.
Thanks

---

### Post by hyper_ch on 2008-01-17
Port 21 is ftp and not telnet. Google should bring up pretty quickly the according port number for telnet.

---

### Post by Dr Small on 2008-01-17
Ok, do you have Firestarter on the host machine with telnetd ?
If not, install Firestarter:
```
sudo apt-get install firestarter
```

Then launch firestarter:
```
gksudo firestarter
```

Then under the policies tab, click down in the "Allow Service" field, then go up and click "Add Rule".

In the port box, enter "23" (I found out that is was 23), and click "Add".
Then click, Apply Policy, and it should open port 23.

Dr Small

---

### Post by hyper_ch on 2008-01-17
all ports are open by default... just not any services listening to them. So "configurating" iptables through firestarter isn't really needed.

Tested it with openssh-server hundreds of times ;)

---

### Post by Dr Small on 2008-01-17
> **hyper_ch said:**
> all ports are open by default... just not any services listening to them. So "configurating" iptables through firestarter isn't really needed.

Tested it with openssh-server hundreds of times ;)
Hmm, well, I've tested the same, and kept receiving connection refused for me, so that is why I always enter a policy in Firestarter to open the port.

---

### Post by hyper_ch on 2008-01-17
Well, I haven't tested it with telnet server only with openssh-server... after installing it through apt-get there's no iptables rule needed to connect to it. Maybe telnet server behaves differently.

---

### Post by quarkhirad on 2008-01-18
Dear Dr small

I installed firestarter and this is what i got

all@webbi:~$ sudo apt-get install firestarter Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After unpacking 1946kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe firestarter 1.0.3-1.1ubuntu4 [391kB]
Fetched 391kB in 6s (55.9kB/s)
Selecting previously deselected package firestarter.
(Reading database ... 83296 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
all@webbi:~$


Then i tried the following
 
all@webbi:~$ sudo su

root@webbi:/home/all# gksudo firestarter

(gksudo:9717): Gdk-WARNING **: locale not supported by Xlib

(gksudo:9717): Gdk-WARNING **: cannot set locale modifiers

(firestarter:9720): Gdk-WARNING **: locale not supported by Xlib

(firestarter:9720): Gdk-WARNING **: cannot set locale modifiers

(firestarter:9720): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I got an information dialogue box stating the following

A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.

I then click ok and it closes the dialogue box and returns me to the terminal

root@webbi:/home/all#


Any comments or suggestion on how i can start it up

Thanks reagrds
khirad

---

### Post by quarkhirad on 2008-01-23
Ok now guys i got firestarter working. Then i when i started it started the firewall wizard. i clicked forward . Then it asked me for the network device. I selected Ethernet device (eth0) (this corresponds to my wired lan connection ) Then it has two check box's one saying start the fire wall on dial out and the other saying ip address is assigned by DHCP. 

I checked the first one about starting the firewall . The second one i left unchecked as my network is manual and not DHCP. I then clicked Forward . 

On the next page i got a check box to enable internet connection  sharing. I checked that two. Then in the drop box i selected Ethernet device ( eth0). When i clicked next it said that the internet connection device and local network cannot be the same. Hence i clicked back and changed the network device to ipv6 (sit 0 ) (or something like that. Let the remaining settings same and then clicked forward. 

This time when i chose to enable internet connection sharing and chose Ethernet device (eth0) it allowed me. I then clicked save on the next page and then the programme gave me a error message stating 

Failed to start Firewall 
The device sit0 is not ready 

Please check your network device settings and make sure your internet connection is active. 


Help how do i get this correct . Please tell me how to set up firestarter

---

