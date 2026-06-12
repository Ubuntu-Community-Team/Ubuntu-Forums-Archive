---
title: "Please Help... Can't update or use apt-get or synaptic"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by advojess on 2007-05-04
Hi,

I posted this question in another part of the forum but since I don't seem to be getting help there I thought I would try it here as well.  I've tried so many things to fix this, and it's been a while now... I'm determined to get it working w/o re-installing if there is any way to do it.

Anyway, so I don't re-post all the info, here's the other thread...
[http://ubuntuforums.org/showthread.php?t=431401](http://ubuntuforums.org/showthread.php?t=431401)

Thanks for whatever help you can give!

---

### Post by ziggykg on 2007-05-04
Are you by any chance accessing the 'net via a proxy?

---

### Post by advojess on 2007-05-04
> **ziggykg said:**
> Are you by any chance accessing the 'net via a proxy?

Well yes I am but there are several reasons I don't think that's the problem, at least not the proxy in my firewall...

1) I can access [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) just fine with a browser
2) I can update just fine from a LiveCD thru the same network
3) I get the same errors when I disconnect from my LAN or WAN and try to update thru a dial-up connection

I may be missing something, but otherwise that's not the issue.  It also could be a proxy on my local machine causing the grief.  I had started out with Ubuntu CE which has a content filter, firewall and proxy built in but then when I upgraded to 7.04 in March it broke it so I couldn't go online at all, so I uninstalled the firewall and proxy.  The updating worked after that.  (I have the same DansGuardian on my IPcop network firewall anyway.)

Any more ideas?  Where would you look if it was your system?

I'm not really new to Linux but this one has me stumped.  Thanks for your help!

---

### Post by advojess on 2007-05-04
Another note...

I also get the exact same errors when I chroot into my system from a LiveCD.

I think it's just something small, but I have no clue where to look...

---

### Post by dberg on 2007-05-05
I have a similar problem, nothing seems to be able to connect.

```
dberg@dberg-desktop:~$ sudo aptitude update
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US                   
Hit http://www.getautomatix.com feisty Release                                  
Hit http://www.getautomatix.com feisty/main Packages                            
Get:2 http://wine.lowvoice.nl feisty Release.gpg [191B]                         
Ign http://wine.lowvoice.nl feisty/main Translation-en_US                       
Hit http://wine.lowvoice.nl feisty Release                                      
Ign http://wine.lowvoice.nl feisty/main Packages                                
Hit http://wine.lowvoice.nl feisty/main Packages                                
Err http://security.ubuntu.com feisty-security Release.gpg                      
  Could not resolve 'security.ubuntu.com'
Err http://archive.canonical.com feisty-commercial Release.gpg                  
  Could not resolve 'archive.canonical.com'
Err http://archive.ubuntu.com feisty-backports Release.gpg                      
  Could not resolve 'archive.ubuntu.com'
Err http://us.archive.ubuntu.com feisty Release.gpg                             
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com feisty-security/main Translation-en_US           
  Could not resolve 'security.ubuntu.com'
Err http://archive.ubuntu.com feisty-backports/main Translation-en_US           
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com feisty-commercial/main Translation-en_US       
  Could not resolve 'archive.canonical.com'
Err http://us.archive.ubuntu.com feisty/main Translation-en_US                  
  Could not resolve 'us.archive.ubuntu.com'
99% [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [C

```

Also, I cannot connect to [http://archive.ubuntu.com/]("http://archive.ubuntu.com/") or [http://us.archive.ubuntu.com/]("http://us.archive.ubuntu.com/") in my browser.

Additionally, the automatic updates through the Update Manager can't download due to being unable to connect also.

Please help, thank you.

---

### Post by dberg on 2007-05-05
Forgot to mention in my last post, the windows machine on my network can connect to [http://us.archive.ubuntu.com/]("http://us.archive.ubuntu.com/") and [http://archive.ubuntu.com/]("http://archive.ubuntu.com/")

---

### Post by advojess on 2007-05-05
Anybody?  I don't want to re-install my system... :( :confused: :( 

BUMP...

---

### Post by apunc1 on 2007-05-05
have you tried to run in terminal 
```


dpkg --configure -a
```

---

### Post by advojess on 2007-05-07
Yep, doesn't change anything.  I've tried all those commands commonly suggested, I can't remember all of them right now.  I think pretty soon I'll try re-installing aptitude if I can't fix it any other way, but I'm not sure that will fix it.

---

### Post by dberg on 2007-05-07
I ran an update yesterday and everything connected fine, then I tried again today and it wasn't working again. This makes me suspect that there is a problem with the servers being down at some times and not at others.

Has anyone else experienced this?

---

### Post by Nythain on 2007-05-07
not sure if anyone has mentioned this but the main servers... us.archive and just regular no country code archive tend to get hit HARD often... you could try changing your country code to something less popular, like it for italy, not sure what canada and or australia's are, it might help your problem if you havent tried already

---

### Post by dberg on 2007-05-07
> **Nythain said:**
> not sure if anyone has mentioned this but the main servers... us.archive and just regular no country code archive tend to get hit HARD often... you could try changing your country code to something less popular, like it for italy, not sure what canada and or australia's are, it might help your problem if you havent tried already

I've seen other people suggest this. Is it possible to change what archives are used when trying to install something via the terminal, or when receiving updates automatically?

---

### Post by Nythain on 2007-05-07
gksudo gedit /etc/apt/sources.list
add less popular country code to the begining of each official ubuntu repo

---

### Post by Sef on 2007-05-07
Post your sources list please.  I think that you may be having a problem because of automatix.

Open the Terminal (Applications > Accessories > Terminal)

```
cat /etc/apt/sources.list
```

---

### Post by dberg on 2007-05-07
I don't know if Automatix is the problem because almost none connection attempts work, it is not only the Automatix ones. But you would probably know better than I would, so here it is.

```
dberg@dberg-desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by Nythain on 2007-05-07
yeah, i forgot, reason #123 for disdaining automatix... it likes to do its own thing to your xorg.conf EVEN when you tell it not to :)

---

### Post by kjaggu on 2007-05-08
I had a similar problem. 

So, as per instructions from fellow members, I updated my Sources file with help from Ubuntuguide.org. Now, it works without a hitch. 

It may help you too. Try your luck.

---

### Post by vdubber on 2007-05-09
I have the same problem, can anyone help? Using Dapper apt-get update has worked once in a week of trying. I've tried several different sources.list files with no effect. All I see is the following
```
jez@jez-ubuntu:~$ sudo apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://medibuntu.sos-sts.com dapper Release.gpg
  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Errhttp://it.archive.ubuntu.com dapper Release.gpg
  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

``` Below is my current sources.list file that gave the above error.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Is it a problem with my router?

Cheers

---

### Post by dberg on 2007-05-12
Alright, I changed my sources.list to use the Canadian (ca) mirrors and everything seems to work much better/more reliable.

thanks

---

