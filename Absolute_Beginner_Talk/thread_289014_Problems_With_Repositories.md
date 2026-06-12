---
title: "Problems With Repositories"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by angus-higgins on 2006-10-30
I am currently getting a web server with a Ubuntu 6.06 LAMP installation on running, and I have run into a problem. I have had the same problem with my desktop Ubuntu 5.10 installation, and I am becomming slightly annoyed about it. 

The problem is that sometimes (quite often) I try to update the repositories with:

```
sudo apt-get update
```

I get this:

```
0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)]
```

For instance, when I was posting this message, I tried the aforementioned update again, and it started to work, however, now, it is bringing up the same message as mentioned before.

I have searched Google for hours on this subject, and as I have mentioned, it is affected my desktop installation of Ubuntu 5.10.

My internet connection is routed through a DLink DSL-G604T to both the server and the desktop, and I have successfully connected to the internet on both machines (in Firefox on the desktop, and I have "pinged" on the server, and also managed to update the repositories, and install open SSH, although, the problem is still there).

I would appreciate any help. (I am completely new to Linux :p)

Thanks,

Angus Higgins

---

### Post by Architeuthis on 2006-10-30
I dont completely get your problem, can you maybe post the entire output of "sudo apt-get update"? Is this error just 1 repository which never works and is noted everytime as not working?

---

### Post by ahaslam on 2006-10-30
Strange :-k I'm using the 'gb' repo's without problems.

Have you tried replacing your sources? Here's a good guide:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) 

Tony.

---

### Post by angus-higgins on 2006-10-30
> **Anthony Haslam said:**
> Strange :-k I'm using the 'gb' repo's without problems.

Have you tried replacing your sources? Here's a good guide:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) 

Tony.

I'm getting the same thing:

```
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
```

I'm not posting the full outcome, as every server comes with an error, my sources.list file is:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```

Thanks,

Angus Higgins

---

### Post by Aldoliel on 2006-10-30
I had this exact same problem. It's a problem with your network setup, DNS servers to be more exact.

You don't happen to have a D-Link router by any chance do you?

Anyway, you need to edit your "/etc/resolv.conf" (As root, i.e. With "sudo nano" or the like) to include:

```

nameserver x.x.x.x
nameserver x.x.x.x

```

Near the top somewhere. Substiuting "x.x.x.x" with the IP addresses of your ISP's name (DNS) servers.
You could use the OpenDNS ones if you like though:
> 
208.67.222.222
208.67.220.220

[http://www.opendns.com]("http://www.opendns.com")

---

