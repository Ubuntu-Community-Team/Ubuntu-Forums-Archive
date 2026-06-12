---
title: "Synaptic and Add/Remove won't connect to teh Internets!"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by greener2 on 2007-05-04
Hi all, first post! I'm reeeeally new to Ubuntu, installed Feisty about 3 weeks ago, and I am having some problems downloading software for it.

I open the Add/Remove Programs program, and it tells me that "The list of available applications is out of date" and "To reload the list you need a working internet connection". 

As you can guess, from the fact that I've posted here, I have a working internet connection, so I clicked reload and a box comes up saying that it's downloading file 1 of 16. However, it doesn't download anything. Same thing happens in Synaptic.

any gurus here that have an idea what I'm doing wrong? I am on my university wired network here, but it also doesn't work when I'm on the university Wifi network. could the university be blocking it?

cheers d00ds

---

### Post by Seisen on 2007-05-04
Post your source list by putting this in the terminal

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Cypher on 2007-05-04
Open a terminal with Applications->Accessories->Terminal and type
```

cat /etc/apt/sources.list
sudo apt-get update

```
and show us the results of both commands..

---

### Post by davahmet on 2007-05-04
That would be my first guess.  Because of past legal issues concerning copyright infringement, some universities are fairly aggressive in their efforts to block any traffic that looks even remotely like file-sharing.

---

### Post by Cypher on 2007-05-04
> **davahmet said:**
> That would be my first guess.  Because of past legal issues concerning copyright infringement, some universities are fairly aggressive in their efforts to block any traffic that looks even remotely like file-sharing.
I would buy that story if APT used a unique port to itself,  but it just uses the standard HTTP port 80, so it doesn't appear any different than a web browser as far as a router goes..

---

### Post by greener2 on 2007-05-04
ok first off, the source list.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main multiverse universe
```

then the terminal output from those 2 commands:

the cat /etc/apt/sources.list command gives the same thing as above.

the sudo apt-get update gives:
```
~$ sudo apt-get update

Err http://security.ubuntu.com feisty-security Release.gpg                                             
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
0% [Connecting to archive.ubuntu.com (91.189.89.8)] [Connecting to security.ubuntu.com (82.211.81.138)]
```

hope it helps!

---

### Post by compmodder26 on 2007-05-04
I'm having problems as well.  I think the repos may be on the fritz.

---

### Post by Seisen on 2007-05-04
Put this in the terminal and post what it says.

```
gksudo gedit /etc/apt/apt.conf
```

---

### Post by greener2 on 2007-05-04
emmm ok, that *gksudo gedit /etc/apt/apt.conf* comes up as a blank gedit window. strange...?

---

### Post by Seisen on 2007-05-04
Here is what mine says.

```
Acquire::http::Proxy "false";
```

---

### Post by Pobega on 2007-05-04
Because apt.conf doesn't exist; Have you tried pinging the server using the ping command?

---

### Post by compmodder26 on 2007-05-04
> **compmodder26 said:**
> I'm having problems as well.  I think the repos may be on the fritz.

I got it back after bringing my internet connection down and then back up again.  So problem was on my end.

---

### Post by greener2 on 2007-05-04
oh ok...mine doesn't say a thing. shall I try entering that line?

---

### Post by Seisen on 2007-05-04
You can try that to see if it works.

---

### Post by greener2 on 2007-05-04
no dice. excuse my n00balicious ignorance, but how does one "ping the server"? what server should I ping?

---

### Post by Seisen on 2007-05-04
In the terminal 

```
ping 82.211.81.138
``` and post what it says.

---

### Post by greener2 on 2007-05-04
ok i pinged, and it didn't pong so to speak. here's what happened:

```
~$ ping 82.211.81.138
PING 82.211.81.138 (82.211.81.138) 56(84) bytes of data.


```

and waited. I left it like that for about 3 and a half mins. then pressed ctrl-C and it said:

```
--- 82.211.81.138 ping statistics ---
202 packets transmitted, 0 received, 100% packet loss, time 201106ms
```

---

### Post by Seisen on 2007-05-04
I starting to wonder if the university didn't block the IP addresses because you should be able to use apt or synaptic as long as you can access the internet.

---

### Post by greener2 on 2007-05-04
it wouldn't surprise me. I can download anything and everything on XP home (dual boot) except using things like P2P and torrents. Maybe they have a blacklist of IP's or something that prevents me from downloading.

---

### Post by compmodder26 on 2007-05-04
See what happens when you reset your network connection (I'm assuming your NIC is given the identifier eth0):

```
sudo ifdown eth0
sudo ifup eth0
```

Then try updating again.

---

### Post by greener2 on 2007-05-04
> **compmodder26 said:**
> See what happens when you reset your network connection (I'm assuming your NIC is given the identifier eth0):

```
sudo ifdown eth0
sudo ifup eth0
```

Then try updating again.

same again, nothing happens. i get this:

```
~$ sudo apt-get update
Err http://security.ubuntu.com feisty-security Release.gpg                                             
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err http://security.ubuntu.com feisty-security/main Translation-en_IE                                  
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err http://archive.ubuntu.com feisty Release.gpg                                                       
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
0% [Connecting to archive.ubuntu.com (91.189.89.8)] 

```

and on and on...

---

### Post by Cypher on 2007-05-04
Go the[ Ubuntu Mirror list]("https://wiki.ubuntu.com/Mirrors") and find the mirror in your nearest country (UK?) and start pinging them to see which one will respond.

When you find a mirror that works, change the archive.ubuntu.com from your sources.list file to the working mirror and see if you have better luck.

---

### Post by greener2 on 2007-05-05
it appears my computer wont ping anything. I tried some of the mirrors for Ireland (where I am) and nothing happened. I even tried pinging things like en.wikipedia.org to no avail. it says 100% packet loss, which I assume means that no packages are getting sent back to me.

any ideas?

EDIT: This also happens when i ping in Window$.

---

