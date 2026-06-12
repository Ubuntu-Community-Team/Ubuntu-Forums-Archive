---
title: "ssh problems"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-07-16
I am trying to learn how to setup a server. I used the instructions in Ubuntu Hacks. It has been interesting working just from command lines in the server. Anyway, on my client box I can transfer files to and from my server without any problem at all. The problem comes when I try to use command lines in my client and I get 
ssh: connect to host 192.168.1.4 port 22: Connection refused.
why is my connection refused in terminal and not in xwindows? Oh, the client is running Kubuntu but I have the same problem in Ubuntu. It seems if it were a firewall issue I wouldn't be able to see my files on the server. I haven't tried to connect with my laptop's XP . . . I have enough of a headaches right now. Anyone have any ideas where the problem might be? Am I posting in the right forum . . . I am an Absolute Beginner!!!
TM

---

### Post by mithion on 2007-07-16
Are you certain you have openssh running on your server?  The second thing I just thought is that you seem to be using a router just by looking at your IP.  I have had a lot of problem trying to figure out how to access a computer behind a router.

Here's something you could try.  Setup your router to portforward ssh inquiries to your sever.  And then try finding what your real IP address by going on 

[http://whatismyip.com/](http://whatismyip.com/)

Then try to ssh to that address and see if that works.  Besides that, networking is a difficult thing to setup.  I was able to setup a simple FTP server on a computer with a static IP.  But that's pretty much the easiest thing you can do.  If you've got a router involved, that makes things more difficult.

EDIT:

Look at this page first to see if your ssh is configured correctly in first place.

[https://help.ubuntu.com/7.04/server/C/openssh-server.html](https://help.ubuntu.com/7.04/server/C/openssh-server.html)

---

### Post by p_quarles on 2007-07-16
In what way does a router make things more difficult? Networking *without* one is difficult. If you can't ssh to a LAN IP address, though, you're looking at router configuration problems, and not a problem with routers per se. And, no, it's not really a good idea to set up an SSH server that's available via the public IP address. That's an open invitation for hackers. 

SVWander: Like mithion said, you'll need an ssh server before you can use the service. If you don't have access to the server (other than for filesharing), you might need to plug in a keyboard and monitor to do this. The book you mentioned has good instructions for doing this (I used it to set up my server). 

If you've already done this, it might be a router setup issue.

---

### Post by SVWander on 2007-07-16
> **p_quarles said:**
> In what way does a router make things more difficult? Networking *without* one is difficult. If you can't ssh to a LAN IP address, though, you're looking at router configuration problems, and not a problem with routers per se. And, no, it's not really a good idea to set up an SSH server that's available via the public IP address. That's an open invitation for hackers. 

SVWander: Like mithion said, you'll need an ssh server before you can use the service. If you don't have access to the server (other than for filesharing), you might need to plug in a keyboard and monitor to do this. The book you mentioned has good instructions for doing this (I used it to set up my server). 

If you've already done this, it might be a router setup issue.

I checked my router port forwarding option and I think it is set up correctly. I have uninstalled and reinstalled ssh server on this Kubuntu machine. I have the keyboard and monitor on the server right now and had to use them to set the different files needed to setup the server. Maybe I screwed up somewhere along the line. I had never used vim before. Maybe I should just reinstall the server and start over. tm

---

### Post by p_quarles on 2007-07-16
I've done a few clean installs since starting with Linux. It seems like a hassle, but it is a great way to allow yourself to fool around and make mistakes. 

The only thing I can think of is that you said you installed the openssh-server package on the Kubuntu machine? Maybe I misunderstood, but you need to install that on the server itself.

---

### Post by SVWander on 2007-07-16
> **p_quarles said:**
> I've done a few clean installs since starting with Linux. It seems like a hassle, but it is a great way to allow yourself to fool around and make mistakes. 

The only thing I can think of is that you said you installed the openssh-server package on the Kubuntu machine? Maybe I misunderstood, but you need to install that on the server itself.

That is the part I don't understand!  That was about the part of the installation referred to in the book. apt-get install openshh-server (it is on page 394). Here they are referring to the desktop system but I thought it would just need the client . . . anyway, I am going to keep messing with it. As you said you learn a lot each time.

tm

---

### Post by Yasumoto on 2007-07-16
One thing I'd do would be to check out which ports you have open. In order to do that, install a program known as nmap.

```
sudo apt-get install nmap
```

(There's also a GUI, nmapfe, but I just use the command line version)

Once that's installed, run

```
nmap localhost
```

to check out your current computer, or 

```
nmap 192.168.1.4
```

will work for you too, since 192.168.1.4 is the internal IP address assigned to your computer from the router. It should come back saying that port 22 is open for ssh. 

Here's what happens when I run it

```

$ nmap 192.168.1.107

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-16 18:52 PDT
Interesting ports on localhost (192.168.1.107):
Not shown: 1696 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh


Nmap finished: 1 IP address (1 host up) scanned in 0.146 seconds

```

---

### Post by Yasumoto on 2007-07-16
> **SVWander said:**
> That is the part I don't understand!  That was about the part of the installation referred to in the book. apt-get install openshh-server (it is on page 394). Here they are referring to the desktop system but I thought it would just need the client . . . anyway, I am going to keep messing with it. As you said you learn a lot each time.

tm

whatever computer you want to connect to, you should install the openssh server. This will open up port 22, and let other computers to connect to your server.

---

### Post by SVWander on 2007-07-16
[QUOTE=
Here's what happens when I run it

```

$ nmap 192.168.1.107

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-16 18:52 PDT
Interesting ports on localhost (192.168.1.107):
Not shown: 1696 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh


Nmap finished: 1 IP address (1 host up) scanned in 0.146 seconds

```[/QUOTE]

Wowza! here is what I get when I run it:

Nmap finished: 1 IP address (1 host up) scanned in 0.441 seconds
george@timsdesktop:~$ nmap 192.168.1.4

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-16 21:24 CDT
Interesting ports on 192.168.1.4:
Not shown: 1694 closed ports
PORT    STATE SERVICE
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.479 seconds

When I run as localhost I get:

Not shown: 1690 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
744/tcp  open  flexlm
2049/tcp open  nfs

How do I go about setting my ssh port to 22 instead of 80 and HOW the hell did that happen. IO problem . . idiot operator!

Tm

---

### Post by Yasumoto on 2007-07-16
Well port 80 is open for http, which seems like it'd mean that you have the apache webserver installed. (This would let you set up a website on your computer) Are you running the Kubuntu server edition or something?

What happens when you

sudo apt-get install openssh-server

?

---

### Post by p_quarles on 2007-07-16
[quoteThat is the part I don't understand! That was about the part of the installation referred to in the book. apt-get install openshh-server (it is on page 394). Here they are referring to the desktop system but I thought it would just need the client . . . anyway, I am going to keep messing with it. As you said you learn a lot each time.[/quote]

Hmm. I just looked that up, and you're right, the language in the section is really ambiguous. But, no, you don't need to install that on any machine except the one(s) you want to use remotely.

Re: the nmap report: port 80 isn't ssh, it's http (that's the default, and that's what the output indicates, so it's correct). Why port 22 isn't open, or how to open it, I can't help. 

You didn't run any firewall stuff, did you? Tinkering with IPtables, or installing the firewall discussed in Ubuntu Hacks could both cause this kind of problem.

---

### Post by SVWander on 2007-07-16
> **Yasumoto said:**
> Well port 80 is open for http, which seems like it'd mean that you have the apache webserver installed. (This would let you set up a website on your computer) Are you running the Kubuntu server edition or something?

What happens when you

sudo apt-get install openssh-server

?

Here it is:
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so it is installed. It is just Kubuntu from the disk supplied by the shipit program. I did install apache on the server. Should I remove it until I get all these problems cleared up? tm

---

### Post by SVWander on 2007-07-16
> **p_quarles said:**
> [quoteThat is the part I don't understand! That was about the part of the installation referred to in the book. apt-get install openshh-server (it is on page 394). Here they are referring to the desktop system but I thought it would just need the client . . . anyway, I am going to keep messing with it. As you said you learn a lot each time.

Hmm. I just looked that up, and you're right, the language in the section is really ambiguous. But, no, you don't need to install that on any machine except the one(s) you want to use remotely.

Re: the nmap report: port 80 isn't ssh, it's http (that's the default, and that's what the output indicates, so it's correct). Why port 22 isn't open, or how to open it, I can't help. 

You didn't run any firewall stuff, did you? Tinkering with IPtables, or installing the firewall discussed in Ubuntu Hacks could both cause this kind of problem.[/QUOTE]

I hope this doesn't post twice. Firefox crashed while I was typing this message. I was trying to remember the command to get into the firewall so that is one thing I HAVE NOT messed with. I am going to call it a night. My eyes are blurry . . . Tm

---

### Post by SVWander on 2007-07-17
How can I get ssh on 22 I ran nmap and it shows:

Not shown: 1694 closed ports
PORT    STATE SERVICE
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

I don't have apache installed on this machine.

I run ssh and get:
ssh george@192.168.1.4
ssh: connect to host 192.168.1.4 port 22: Connection refused

running local host I get:

Interesting ports on localhost (127.0.0.1):
Not shown: 1690 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
744/tcp  open  flexlm
2049/tcp open  nfs

What am I doing WRONG!!!???

---

### Post by p_quarles on 2007-07-17
When you run "nmap localhost," are you doing so on the server or on the desktop? I'm assuming the former, but just wanted to check.

The only other thing I can think of is that perhaps you never set the server up so that it had a static IP address. Try the running the following command from your desktop, and post the results ```
ping -c 5 192.168.1.4
```

This sounds really frustrating. In my case, getting SSH running was a breeze, and it was getting the filesharing set up that was a pain.

---

### Post by SVWander on 2007-07-17
> **p_quarles said:**
> When you run "nmap localhost," are you doing so on the server or on the desktop? I'm assuming the former, but just wanted to check.

The only other thing I can think of is that perhaps you never set the server up so that it had a static IP address. Try the running the following command from your desktop, and post the results ```
ping -c 5 192.168.1.4
```

This sounds really frustrating. In my case, getting SSH running was a breeze, and it was getting the filesharing set up that was a pain.

It is frustrating to the highest degree right now. 

ping -c 5 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_seq=1 ttl=64 time=0.280 ms
64 bytes from 192.168.1.4: icmp_seq=2 ttl=64 time=0.181 ms
64 bytes from 192.168.1.4: icmp_seq=3 ttl=64 time=0.176 ms
64 bytes from 192.168.1.4: icmp_seq=4 ttl=64 time=0.177 ms
64 bytes from 192.168.1.4: icmp_seq=5 ttl=64 time=0.169 ms

--- 192.168.1.4 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.169/0.196/0.280/0.044 ms

I am not sure what that means. It is getting through to the server from what I can gather. LOL at the same time I am trying to get a Briggs & Stratton engine to run and having little luck there either!

Tm

---

### Post by p_quarles on 2007-07-17
Yeah, that means the address is correct and the connection is good. It sounds like you've everything configured correctly, so I don't really know what the problem could be. 

I'd suggest you either a) reinstall the server system, or b) install a program called "Webmin" on the server. Webmin is a https based GUI that allows you to administer a machine remotely. I use it mainly to maintain a website (easier than using copying files from in the shell, and more secure than ftp), but it has a very wide range of functions, the command line interface among them.

---

### Post by mithion on 2007-07-17
I have another idea.  What if you're missing a couple of packages.  I see that there is the openssh-client/openssh-server packages which you need.  But I've also found a metapackage called ssh.  Try running 

```
sudo apt-get install ssh
```

and see if that doesn't install any additional packages you might need.  Other than that, I have to agree, sounds like a router configuration problem.  When I set my ssh server up, it worked immediately.  Also, did you install a firewall by any chance?  If there is one up, it will block the network traffic unless configured to do otherwise.

---

### Post by SVWander on 2007-07-17
> **p_quarles said:**
> Yeah, that means the address is correct and the connection is good. It sounds like you've everything configured correctly, so I don't really know what the problem could be. 

I'd suggest you either a) reinstall the server system, or b) install a program called "Webmin" on the server. Webmin is a https based GUI that allows you to administer a machine remotely. I use it mainly to maintain a website (easier than using copying files from in the shell, and more secure than ftp), but it has a very wide range of functions, the command line interface among them.

That Webmin program would be installed on the server right? I might do that before I mess with reinstalling the server . . . unless you can  tell me how to mount with permissions a floppy drive or a usb drive so I don't have to hand type the smb.conf by hand in vim.

I want to thank you for your continued help.

tim

---

### Post by SVWander on 2007-07-17
> **mithion said:**
> I have another idea.  What if you're missing a couple of packages.  I see that there is the openssh-client/openssh-server packages which you need.  But I've also found a metapackage called ssh.  Try running 

```
sudo apt-get install ssh
```

and see if that doesn't install any additional packages you might need.  Other than that, I have to agree, sounds like a router configuration problem.  When I set my ssh server up, it worked immediately.  Also, did you install a firewall by any chance?  If there is one up, it will block the network traffic unless configured to do otherwise.


I gave that a try and  the same mess. I don't know whether the problem is server related or in this box. It really wouldn't be a big deal to reinstall the server even if I have to hand type the smb.conf by hand in vim

I didn't have Firestarter running but opened it up and added an Allow from host 192.168.1.4
still cannot connect using ssh. I will try that web program. ](*,)

---

### Post by p_quarles on 2007-07-17
A floppy should mount automatically, and it will show up as something like /dev/fd1/. You can just copy files from that into the appropriate directory. You won't need special permissions of you use sudo.

But, yeah, I'd try installing WebMin first (yes, on the server). It just occurred to me that one of the many things it can do is configure SSH. So, you might even be able to use it to fix that problem.

---

### Post by steve.horsley on 2007-07-17
Pardon me jumping in. I've only scanned the thread quickly, but I think you're still in the position that you have installed openssh-server on the wrong machine. It should be installed on the machine you are going to control remotely - the server, and it should not be installed on the desktop machine that you are connecting from. 

To make sure, the command "netstat -lt" should not mention ssh, but when that command os run on the server, then it should mention ssh.

---

### Post by SVWander on 2007-07-17
> **steve.horsley said:**
> Pardon me jumping in. I've only scanned the thread quickly, but I think you're still in the position that you have installed openssh-server on the wrong machine. It should be installed on the machine you are going to control remotely - the server, and it should not be installed on the desktop machine that you are connecting from. 

To make sure, the command "netstat -lt" should not mention ssh, but when that command os run on the server, then it should mention ssh.

YOU GOT IT! I still have a problem with the passkey mess but you hit the nail on the head. Installed on the server it did what is needed to do. I kept thinking it was strange to install it on the desktop!
Tm

---

