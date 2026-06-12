---
title: "Synaptic has stopped working for me!!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Edifier1007 on 2007-10-07
Yes I know. No information at all actually :)

So here is what I wanted to write before I let my mouse go out of my hand and hit ENTER key !!

I tried cleaning up unwanted packages some 20 days ago.. which was all good.

I have been trying to install a few packages since past two days and figured out that the package manager does not connect to any servers !! It just times out.

I tried to check, update and clear broken packages and nothing works. Initially I thought this was network issue but it is not. 

I tried three different server repos and I can ping them. So, it has to be something with the package manager.

Any more info that you need, I can find out from my installation and paste. Last I used Xnix was some 4 years ago so I may be slow in finding things out!!

Thanks in advance.

---

### Post by bodhi.zazen on 2007-10-07
If you need help, please post more information, otherwise I may consider closing/moving this thread.

EDIT: ~ LOL ~ 

Try using apt-get. Synaptic is a gui front end for apt-get, post any error messages 

Open a terminal 

```
sudo apt-get update
sudo apt-get upgrade # or try installing something
```

---

### Post by taurus on 2007-10-07
If you want a quick help, provide the command that you ran and the complete error message.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by Edifier1007 on 2007-10-07
'sudo apt-get update' gives following output

0% [Connecting to in.archive.ubuntu.com (1.0.0.0)]

and stays there. Same with any repo that I try including the main server.

---

### Post by taurus on 2007-10-07
What's the output of this command from a terminal?

```
ping -c 3 www.google.com
```

---

### Post by Edifier1007 on 2007-10-07
'ping -c 3 [www.google.com](www.google.com)'

PING [www.google.com](www.google.com) (64.233.189.104) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (64.233.189.104): icmp_seq=1 ttl=245 time=278 ms
64 bytes from [www.google.com](www.google.com) (64.233.189.104): icmp_seq=2 ttl=245 time=270 ms
64 bytes from [www.google.com](www.google.com) (64.233.189.104): icmp_seq=3 ttl=245 time=273 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 270.457/274.234/278.968/3.539 ms

---

### Post by taurus on 2007-10-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Any chance you have proxy running on your machine?

---

### Post by Edifier1007 on 2007-10-07
-- I changed my repo from India server to Main server before this.

-- No proxy on my machine. Forgot to add that last time around.

/etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

