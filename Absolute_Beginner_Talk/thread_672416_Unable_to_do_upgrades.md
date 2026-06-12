---
title: "Unable to do upgrades"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by amidude on 2008-01-19
My machine can't get past a problem with Network Manager and so it won't install anymore upgrades. It just hangs. I have an HP zd7010us laptop that I'm running Ubuntu on. It gets hung up trying to install the new Unix print system.

---

### Post by Ub1476 on 2008-01-19
Could you post the output of:

```
sudo apt-get update

sudo apt-get upgrade
```

Make sure you close Synaptic first (add/remove, package manager, updater)

---

### Post by amidude on 2008-01-20
when I run sudo apt-get update I get the following:

[B]Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Fetched 573B in 0s (646B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/B]


And when I run sudo apt-get upgrade I get this:

**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.** 

When I do run dpkg --configure -a it gets hung up on the Network Manager.

I get this:

[B]Setting up libavahi-compat-libdnssd1 (0.6.20.2ubuntu3.1) ...
Setting up network-manager (0.6.5-0ubuntu16.7.10.0) ...
  *Reloading system message bus config...                                                 [OK]
  *Restarting network connection manager NetworkManager
dpkg: error processing network-manager ( --configure ):
  subprocess post-installation script returned error exit status 2
Setting up libapache2-mod-php5 (5.2.3-1unbuntu6.3) ...[/B]

Then it just hangs forever...

---

### Post by amidude on 2008-01-22
Is this a stumper???

---

### Post by oldos2er on 2008-01-22
Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by JoshuaRL on 2008-01-22
> 
dpkg: error processing network-manager ( --configure )


I don't know from experience but you might try:

```

sudo dpkg-reconfigure network-manager

```

---

### Post by amidude on 2008-01-31
This is what I got from running that last command:

/usr/sbin/dpkg-reconfigure: network-manager is broken or not fully installed

---

### Post by amidude on 2008-01-31
This what I got from running that list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by amidude on 2008-02-08
I know this is a "windows" mentality but should I reinstall?

---

### Post by amidude on 2008-02-09
Anyone?....Anyone??

Beuhler???

---

### Post by nikoPSK on 2008-02-09
please don't bump as often... Anywyas:
```

sudo dpkg --configure -a
```

should do it.

---

### Post by amidude on 2008-02-12
Sorry to bump so much...was afraid I'd get lost. In my previous post I wrote this...
> When I do run dpkg --configure -a it gets hung up on the Network Manager.

I get this:

Setting up libavahi-compat-libdnssd1 (0.6.20.2ubuntu3.1) ...
Setting up network-manager (0.6.5-0ubuntu16.7.10.0) ...
*Reloading system message bus config... [OK]
*Restarting network connection manager NetworkManager
dpkg: error processing network-manager ( --configure ):
subprocess post-installation script returned error exit status 2
Setting up libapache2-mod-php5 (5.2.3-1unbuntu6.3) ...

Then it just hangs forever...

---

### Post by nikoPSK on 2008-02-12
> **amidude said:**
> Sorry to bump so much...was afraid I'd get lost. In my previous post I wrote this...

add sudo as I said. :)

---

### Post by amidude on 2008-02-12
Sorry...forgot to mention that I did run it as sudo...thought that's the only way we could. I still get that error message....then it hangs forever.

---

### Post by nikoPSK on 2008-02-12
> **amidude said:**
> Sorry...forgot to mention that I did run it as sudo...thought that's the only way we could. I still get that error message....then it hangs forever.
sorry, gotcha :oops:

---

### Post by amidude on 2008-02-12
So since that doesn't work are there any more options that I can try? :(:confused:

---

### Post by spiderbatdad on 2008-02-12
Are you running  from a wireless connection?

---

### Post by amidude on 2008-02-12
No...no wireless. well my computer does have wireless built in but I've got it shut off

---

### Post by amidude on 2008-02-15
I tried to remove network-manager and as you probably guessed it wouldn't let me. It said there were dependencies. So seriously...should I just wipe my drive and start over because this is getting frustrating. I have 47 updates and can't do any of them because of this problem.

---

### Post by amidude on 2008-02-20
Should I move this conversation to a more seasoned user base discussion group? If so, how would I do that?

---

### Post by spiderbatdad on 2008-02-20
looks like you are trying to connect to the server through a proxy. The server requires authentication.
You may just need to enter proxy settings into network manager.
[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

---

### Post by amidude on 2008-02-21
Thanks. I looked at that and it looks like it might work. My only question is that it's been set to "direct connect to internet" since I've installed it and this is the first time I've had this issue.

My laptop is connected to a 4-port hub that is connected to my cable modem. There are no proxie settings that I've set up that I am aware of at this time. Would I be using the proxy set up by the ISP?

Also, I was able to download some of the updates last night but it got hung up on the "cups" installation...so it seemed like it went further this time.

Thanks for the help.

---

### Post by spiderbatdad on 2008-02-21
That thought was somewhat of a shot in the dark, as connectivity seems to be at least part of the problem. I thought you may have set up a server, doesn't sound like it now, and you say you have a direct connection. For the moment, I'm stumped. Re-installing should be an absolute last resort imo...nobody learns anything.

---

### Post by amidude on 2008-03-17
I agree. The thing is that the only "thing" I'm learning is that this problem isn't going away. :-P

I have been able to do updates and am current except for the updates to the network manager. After every update I have to hard restart my machine. The changes are applied to the system but initial download and install always hangs up on restarting the network manager.

Ubuntu hates me. *sniff-sniff* :-(

---

### Post by amidude on 2008-03-22
Has anyone else had these problems with the network manager on an HP zd7010us?

---

### Post by zvacet on 2008-03-22
**In synaptic>edit tab>fix broken packages.**

---

### Post by ljfox4 on 2008-03-31
I am experiencing the same problem.  I have just reinstalled Ubuntu and network-manager is causing me utter chaos.  amidude's description seems exactly like mine.  I am using a Dell Inspiron E1705, which leads me to believe that it is not related to the make of computer.  I find it interesting that both of our problems occurred after installing, making me wonder if perhaps a more recent update of network-manager relies on another update that had not been installed for us yet.  I don't know, I'm just brainstorming, but maybe it will lead somewhere.

---

### Post by ljfox4 on 2008-03-31
Well, I fixed it now.  I have no clue how, but I fixed it.  I've just been messing around trying to remove it or complete the installation.

---

