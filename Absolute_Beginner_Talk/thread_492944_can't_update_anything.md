---
title: "can't update anything"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by blastthisinferno on 2007-07-05
I just recently installed Ubuntu-7.04-server-amd64.iso which is feisty I believe, and I'm trying to get an ssh thing going on.  I have run the "apt-get install ssh openssh-server" command already and followed this ([http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3))  tutorial on that.  When I go to "apt-get update" I always get "E: Some index files failed to download, they have been ignored, or old ones used instead."  Now I've tried installing something simple like gedit and it does the same thing.  I've tried inserting the cd-rom that I installed the OS with and it doesn't find the files on it or something.  If you need anymore information please ask.  I'm stuck.

EDIT:  I have my server connected to a Netgear 8-port switch and the lights are on but not blinking (so no activity).  I've also tried to ping [www.google.com](www.google.com) and even another computer connected through the switch but to no avail.  I doubt the problem is the switch.

---

### Post by Rui Pais on 2007-07-05
You probably have some repo listed on your sources that is not available anymore.
Its just a warning. apt has been updated. You can apt-get at your will...

If you want to post here your /etc/apt/sources.list we can see if we find the broke one(s).
:)

---

### Post by lamalex on 2007-07-05
> **blastthisinferno said:**
> EDIT:  I have my server connected to a Netgear 8-port switch and the lights are on but not blinking (so no activity).  I've also tried to ping [www.google.com](www.google.com) and even another computer connected through the switch but to no avail.  I doubt the problem is the switch.

so you can't ping google from this computer or another connected to the same switch? check your switch, or your uplink, that's probably your problem

---

### Post by Rui Pais on 2007-07-05
oops i haven't read your edit when i replied ...

ignore my previous post. It seems that you have an internet connection problem, a completely different issue.

---

### Post by blastthisinferno on 2007-07-05
Here is my /etc/apt/sources.list  file just incase you spot something wrong.

#deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to newer versions of the #distribution

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse



As for the network for the other computers, I can ping [www.google.com](www.google.com).  They have Windows XP on them.  I'm extremely new to linux, so I figured "ping www.google.com" would work.  Maybe that's not a correct command.  How else can you see if you're on the internet?  Also I'm working with a command line so I have no GUI (which I'm fine with for now) but I have tried installing ubuntu-desktop with the same update error I have been getting.  I really think that my problem is that I'm not on the internet. 

Thank you for the responses guys.

---

### Post by Rui Pais on 2007-07-05
hi again,
your apt-sources seems quite alright. If you don't plan to compile stuff from code you can make things faster by comment (put a symbol # on the beginning of lines) on the ones that started with deb-src.

Seems that you have an internet connection problem...
Can you describe how your network is made and how do you connect to internet?
 
can you post the output of:
```
ifconfig
```
please.

---

### Post by Raineer on 2007-07-05
Yeah this is just a network problem, ignore the apt-get thing for now.  Lets try that ifconfig output.

FYI, opening a console and typing ```
ping www.google.com
``` is correct, you are just not online at this moment.

---

### Post by blastthisinferno on 2007-07-05
Ok, I have a Win XP home desktop, Win XP pro laptop, and this new Ubuntu amd64 Linux server all connected via cat5e cable to a Netgear GS108 switch.  The internet cable plugs straight into the switch directly from the modem.   The two Win XP pc's both have internet and can ping [www.google.com](www.google.com) and each other.  The linux server cannot ping neither 192.168.1.46 (desktop) nor 192.168.1.47 (laptop).  I get the error "connect: Network is unreachable" when I try to ping the Win XP pc's.  When I try to ping [www.google.com](www.google.com) I get "ping: unkown host www.google.com".

Is there a built in firewall in the Ubuntu installation that I have to poke a port hole into?

I have edited  /etc/network/interfaces and followed this tutorial [http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3) .  The only thing I changed was the gateway to 192.168.1.1 because thats what the Win XP default gateway is.

---

### Post by Rui Pais on 2007-07-05
> **blastthisinferno said:**
> ...
I have edited  /etc/network/interfaces and followed this tutorial [http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3) .  The only thing I changed was the gateway to 192.168.1.1 because thats what the Win XP default gateway is.
only changing that in relation to what that article describe would give a non working network.
it should said something like:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

```

where in the line 'address 192.168.1.2' the 2 can be a number between 2 and 255.
Another problem is how IPs are set on your network. If windows assign them automatically (Dynamic DHCP) your linux server should do the same or they may colide.

in that case you should have only:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by blastthisinferno on 2007-07-05
The only problem with setting it to dhcp is that I thought it's better to have a static ip address for ssh'ing and vnc'ing into a computer.  So should I try either making all the Win XP pc's static as well, or all dynamic?  The main thing I want to do is ssh into the linux server over the internet, because I won't have the computer with me during the school year.

---

### Post by Rui Pais on 2007-07-05
> **blastthisinferno said:**
> The only problem with setting it to dhcp is that I thought it's better to have a static ip address for ssh'ing and vnc'ing into a computer.  So should I try either making all the Win XP pc's static as well, or all dynamic?  The main thing I want to do is ssh into the linux server over the internet, because I won't have the computer with me during the school year.

Well, i personally prefer static ips. 
The problem, keeping your Linux ip static with others dynamic, appears only if you turn your Linux box on *after* dhcp has set the IPs on windows, since one of them may get the same ip you set for Linux.

If you have your Linux server alway on, you can give that a static ip and on Windows boxs dhcp should be able to detect that ip is already used and assign different IPs to Windows. There should be too an option to limit the use of certain ips on dhcp configuration (don't know how that is done... but should be somewhere on windows network configuration). As an example you set your Linux as 192.168.1.2 and set dhcp to assign ips from 3 ahead.

But since your network is made of 3 ips+1 of gateway, maybe it would easier to set all static. DHCP is useful for large networks, where setting IPs one by one would be impractical...

Start by set your Linux static and see if it gets an internet connection... you can tweak things later.

---

### Post by blastthisinferno on 2007-07-05
Ok, here's what it's doing now.

**Case 1:       ping desktop**
   ping 192.168.0.46
result
   PING 192.168.0.46 (192.168.0.46) 56(84) bytes of data.
   From 192.168.0.48 icmp_seq=2 Destination Host Unreachable
   From 192.168.0.48 icmp_seq=3 Destination Host Unreachable
   From 192.168.0.48 icmp_seq=4 Destination Host Unreachable

**Case 2:       ping server itself**
   ping 192.168.0.48
result
   PING 192.168.0.48 (192.168.0.48) 56(84) bytes of data.
   64 bytes from 192.168.0.48: icmp_seq=1 ttl=64 time=0.042 ms
   64 bytes from 192.168.0.48: icmp_seq=2 ttl=64 time=0.005 ms
   64 bytes from 192.168.0.48: icmp_seq=3 ttl=64 time=0.004 ms

Correct me if I'm wrong but switches usually don't have firewalls or anything to protect the computer right?  I'm still completely stumped on how at least 2 machines are not even seeing each other.  Man I'm horrible at networking.

---

### Post by Rui Pais on 2007-07-05
> **blastthisinferno said:**
> Ok, here's what it's doing now.

**Case 1:       ping desktop**
   ping 192.168.0.46
result
   PING [COLOR="DarkRed"]192.168.0.46[/COLOR] (192.168.0.46) 56(84) bytes of data.
   From 192.168.0.48 icmp_seq=2 Destination Host Unreachable
   From 192.168.0.48 icmp_seq=3 Destination Host Unreachable
   From 192.168.0.48 icmp_seq=4 Destination Host Unreachable

**Case 2:       ping server itself**
   ping 192.168.0.48
result
   PING [COLOR="DarkRed"]192.168.0.48 [/COLOR](192.168.0.48) 56(84) bytes of data.
   64 bytes from 192.168.0.48: icmp_seq=1 ttl=64 time=0.042 ms
   64 bytes from 192.168.0.48: icmp_seq=2 ttl=64 time=0.005 ms
   64 bytes from 192.168.0.48: icmp_seq=3 ttl=64 time=0.004 ms

Correct me if I'm wrong but switches usually don't have firewalls or anything to protect the computer right?  I'm still completely stumped on how at least 2 machines are not even seeing each other.  Man I'm horrible at networking.

shouldn't be 192.168.1.46 and 192.168.1.48 (or 47 according to your previous post)?

---

### Post by blastthisinferno on 2007-07-05
correction my linux server is 192.168.0.48, but my Win XP's are 192.168.1.46 and 47.  Either way they don't work.  I did find something curious though...

When I  "ping 192.168.0.46" it attempts to send packets but doesn't do anything, but when I "ping 192.168.1.46"  it says "connect: Network is unreachable".  So is there something where all my ip's have to be the same three numbers or something?

---

### Post by Rui Pais on 2007-07-05
> **blastthisinferno said:**
> correction my linux server is 192.168.0.48, but my Win XP's are 192.168.1.46 and 47.  Either way they don't work.  I did find something curious though...

When I  "ping 192.168.0.46" it attempts to send packets but doesn't do anything, but when I "ping 192.168.1.46"  it says "connect: Network is unreachable".  So is there something where all my ip's have to be the same three numbers or something?

yes, i think it should be 192.168.1.X (not sure... but i think 192.168.0.X is another subnet)

---

### Post by blastthisinferno on 2007-07-05
OMG, that is what fixed it.  I changed the IP in linux to 192.168.1.48 and it works now.  I can ping [www.google.com](www.google.com) and the other Win XP's.  Thank you a lot Rui Pais for all the help.  I guess you can't follow a tutorial to the dot.

Now on to my next disaster.

---

### Post by Rui Pais on 2007-07-05
> **blastthisinferno said:**
> OMG, that is what fixed it.  I changed the IP in linux to 192.168.1.48 and it works now.  I can ping [www.google.com](www.google.com) and the other Win XP's.  Thank you a lot Rui Pais for all the help.

Now on to my next disaster.

:lol:
glad is working.

now that you mention you tried install ubuntu-desktop (that would be almost a disaster for a server... ;))
may i suggest this site [here]("http://www.psychocats.net/ubuntu/minimal#barebones") with nice tips for keep things light :)

it must be sufficient a:
```
sudo apt-get install xorg xterm fluxbox
```
and you still have you nice line command. 
When you need a GUI type '**startx**' and got a working minimal desktop.
 Have fun :)

---

