---
title: "XDMCP/X forwarding issues"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by No_Code on 2006-06-07
This isn't exactly a problem with Ubuntu running on a Mac, so much as it is with OS X and I hope that maybe someone can help me or at least point me in the right direction.

I had Breezy Badger installed on an x86 which I used my OS X system to X forward into it using the X11 server built into OS X. This was never a problem. All I would have to do is type:
```
X -query 192.168.1.150
```
in the OS X Terminal window and I would be greeted with your standard Ubuntu graphical login screen (this is what XDMCP provides). Seeing as how I'm running this on my own personal LAN, I'm not too concerned about encryption, etc.

I decided to upgrade to that system to Dapper following the stable release, along with the rest of my Ubuntu systems. When I did that, the aforementioned functionality was lost. All I get is your standard blank X screen on my Mac. I figured that it was an issue with a magic cookie and I sought out instructions on how to make them and authorize them through the use of keys set up using xauth.

I have done the following:

**Mac:**
```

zack:~ zhzlot$ xauth list
zack/unix:0  MIT-MAGIC-COOKIE-1  1ddaefa1657fe91f15d2014374c5ab40
zack:0  MIT-MAGIC-COOKIE-1  1ddaefa1657fe91f15d2014374c5ab40
localhost:0  MIT-MAGIC-COOKIE-1  1ddaefa1657fe91f15d2014374c5ab40
192.168.1.150:0  MIT-MAGIC-COOKIE-1  120d4a3891558b9f5feee2a0d63f6bdc

```

**Ubuntu Host:**
```

zhzlot@dapper:~$ xauth list
dapper/unix:0  MIT-MAGIC-COOKIE-1  120d4a3891558b9f5feee2a0d63f6bdc
dapper/unix:10  MIT-MAGIC-COOKIE-1  4121a6eabc9b1543e7c2a751a4342f46
zack:0  MIT-MAGIC-COOKIE-1  1ddaefa1657fe91f15d2014374c5ab40

```

What is so perplexing about this problem is that if I run X -query 192.168.1.150 on a normal Linux system, it connects right away and presents me with an XDMCP login for the Ubuntu system. Also, this command seems to work on an older Mac that I have running an earlier version of OS X. I have also tried it on a newer iMac G5 running OS X 1.4.6 and a Powerbook G4 also running OS X 1.4.6. I checked that system's xauth list as well and it yields nothing. I have ensured that my mac will allow authentication and TCP connections to it's X server and the same thing with the Ubuntu host. Also, I have tried the same thing on a different Ubuntu Dapper host with the same results.

My Hardware/Software Environment Is As Follows:

Newer Mac:
867 MHz G4 "Quicksilver"
1024 MB of RAM
250 GB hard drive
OS X 10.4.6
X11 server version 4.4.0 (included with OS X)

Older Mac:
400 MHz G4 "Sawtooth"
1024 MB of RAM
10 GB hard drive
OS X 10.3.9
X11 server version 4.3.0 (included with OS X)

Ubuntu System:
1.47 GHz AthlonXP
1024 MB of RAM
300 GB hard drive
Ubuntu Linux 6.06 "Dapper Drake"
Stock kernel
X11 server version 7.0.0 (included with the Dapper Drake release)

Note, all X server versions are using protocol version 11, revision 0. This information was obtained by running X -version.

I'm not running any exotic software combination on the Ubuntu system, nor even on the OS X systems. I'm quite sure that there is something small that I am overlooking here. I know that I am most likely posting this in the wrong place, but any help would be appreciated regarding this matter.

Thanks in advance!

---

### Post by No_Code on 2006-06-07
Solved! On a hunch, I checked the /etc/hosts file on both the Mac and the Ubuntu machine and manually made the entries because my DNS setup hasn't been working quite properly lately. Hope nobody wasted their time on this :D .

---

