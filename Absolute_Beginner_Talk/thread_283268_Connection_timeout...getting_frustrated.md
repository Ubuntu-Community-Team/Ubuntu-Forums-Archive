---
title: "Connection timeout...getting frustrated"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-23
When ever I try to run apt-get update or try to install a new package, I keep getting a connection timeout error. This is annoying as I currently cannot install anything. Here's the output I get from entering sudo apt-get update into the terminal:

```

matt@matt-laptop:~$ sudo apt-get update
Errhttp://repository.debuntu.org dapper Release.gpg
  Could not connect to repository.debuntu.org:80 (1.0.0.0), connection timed outErrhttp://easyubuntu.cafuego.net main Release.gpg
  Could not connect to easyubuntu.cafuego.net:80 (1.0.0.0), connection timed outErrhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch http://repository.debuntu.org/dists/dapper/Release.gpg  Could not connect to repository.debuntu.org:80 (1.0.0.0), connection timed out
Failed to fetch http://easyubuntu.cafuego.net/dists/main/Release.gpg  Could not connect to easyubuntu.cafuego.net:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
matt@matt-laptop:~$

```

Does anyone know how to fix this?

thanks

---

### Post by wieman01 on 2006-10-24
Open up this file:
> sudo gedit /etc/apt/sources.list
Paste the content here. 

Useful source-list generator: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by spamzilla on 2006-10-24
Here is my source list:

```


deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
deb http://easyubuntu.cafuego.net main easyubuntu

```

---

### Post by wieman01 on 2006-10-24
Make a safety copy of your source-list and paste this (remove all other contents from the file):
> # Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
Then try again.

---

### Post by spamzilla on 2006-10-24
The update still refuses to work:

Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outReading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.



Thanks anyway

---

### Post by wieman01 on 2006-10-24
Question: Are you behind a proxy? Perhaps university campus or so?

---

### Post by ojasvi rajpal on 2006-10-24
R u sure u r connected to internet ?? moreover if u r using a proxy server type the followinf command "$export http_proxy="http://proxy server adress column ":" port".(Alternatively u can type it in .bashrc and run it ).I hope this helps

---

### Post by wieman01 on 2006-10-24
Apparently he is connected... Otherwise he would not post messages. :-) Plus he has been a member of this forum for a few months (see join date). But you're right, we should not assume things. 

See screenshot for the proxy... Synaptic lets you configure it.

---

### Post by spamzilla on 2006-10-24
wieman01: Nope I am connected wirelessly to a router which goes out onto the internet...no proxies used!

ojasvi rajpal: Yeah I am connected to the net, which is how I am posting these messages :)

wieman01: So should I use a proxy, as I am connected directly to the net?

Thanks guys, your help is much appreciated :)

---

### Post by wieman01 on 2006-10-24
Can you open this link with a brower?
[http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by spamzilla on 2006-10-24
edit:

I get taken to the sites index of / page

---

### Post by wieman01 on 2006-10-24
Ok, can you check the proxy settings in Firefox or whatever browser you're using? Perhaps we are missing something.
> Firefox->Tools->Options->General->Connection Settings

---

### Post by spamzilla on 2006-10-24
it says I am directly connected to the internet. Should I change this option? If so what to?

Thanks :P

---

### Post by wieman01 on 2006-10-24
No, don't change it. 

There seems to be an issue with the signatures/GPG keys. Not sure what it means but I need to check tonight when I am in front of my own computer. Get back to you on this.

---

### Post by wieman01 on 2006-10-24
You have completely overwritten your source-list with the stuff I have given you, right?

---

### Post by spamzilla on 2006-10-24
Yep. and I now get the following message when trying to update

```

sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

```

---

### Post by wieman01 on 2006-10-24
You may either require a reboot or Synaptic is still open...

---

### Post by spamzilla on 2006-10-24
I have just rebooted and I still cannot download updates. I get connection time out over and over again :(

---

### Post by wieman01 on 2006-10-24
Ok, I'll check it out tonight. Find out how to update "signature" keys for the repositories in the meantime (GPG). This could be your problem.

See you later!

---

### Post by spamzilla on 2006-10-24
Ok thanks a lot mate. Enjoy your day :)

---

### Post by wieman01 on 2006-10-24
One last thing: You have not got a firewall, have? Obviously not because you can browse (using port 80) but perhaps there is an issue with it. If so, please turn it off for the time being (IP tables via script or Firestarter).

---

### Post by spamzilla on 2006-10-24
My router has firewall. Should I disable that? 

I don't think my laptop has a firewall, unless it's a standard application.

---

### Post by wieman01 on 2006-10-24
It's ok then. The router won't be a problem, either. I think this has to do with the GPG keys for signing the packages. Get back to you later, mate.

---

### Post by spamzilla on 2006-10-24
Ok, thanks a lot :)

---

### Post by wieman01 on 2006-10-24
Found this... Apparently this is a DNS issue. 

[http://forums.whirlpool.net.au/forum-replies.cfm?t=566985&r=8723206#r8723206]("http://forums.whirlpool.net.au/forum-replies.cfm?t=566985&r=8723206#r8723206")

What does this one say:
> sudo gedit /etc/resolv.conf

---

### Post by spamzilla on 2006-10-24
A file opened up which just said:

nameserver 192.168.1.1

Do you think I should change my DSN from 192.168,1.1 to 203.8.183.1, as suggested in that link?

Edit that worked :mrgreen: 

Thanks a lot mate! I really appreciate your help :)

---

### Post by wieman01 on 2006-10-24
> **spamzilla said:**
> A file opened up which just said:

nameserver 192.168.1.1

Do you think I should change my DSN from 192.168,1.1 to 203.8.183.1, as suggested in that link?

Edit that worked :mrgreen: 

Thanks a lot mate! I really appreciate your help :)
Good. Actually your router's IP address should be fine, however, the links suggested that some DSL modems are kind of malfunctioning. One off our list. :-)

---

### Post by spamzilla on 2006-10-24
Oh ok.

I now have another problem when trying to install some updates. They all installed fine apart from one, and I got this message:

> 
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


edit im hoping this works

wget [http://packages.freecontrib.org](http://packages.freecontrib.org) -O - | sudo apt-key add -

---

### Post by wieman01 on 2006-10-24
No problem, try this:
> sudo gpg --keyserver subkeys.pgp.net --recv **[COLOR="Red"]F120156012B83718[/COLOR]**
sudo gpg --export --armor **[COLOR="Red"]F120156012B83718[/COLOR]** | sudo apt-key add -
**[COLOR="Red"]F120156012B83718[/COLOR]** is the public key of the repository. Guess that will work.

_**EDIT:**_
Generally this error message will not be much of a problem. The package will install anyway, it's a simple warning message.

---

### Post by spamzilla on 2006-10-24
Excellent! This has also solved my problems with gaim connecting to the net!

thanks again mate :)

---

