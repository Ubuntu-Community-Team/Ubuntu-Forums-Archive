---
title: "Updater not working"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by the_penguin on 2008-02-08
Hi everyone

I'm trying to get the restricted drivers for my nVidia card by the Ubuntu updater.

However, it fails to connect on ALL mirrors. I have tried a variety from all over the world.

My internet connection is fine- I'm typing this in Firefox right now.

The only thing I've done since installing Ubuntu was turn ipv6 off in the modprobe.d file so the internet would work.

Any help is appreciated.

Thanks.

---

### Post by amo-ej1 on 2008-02-08
what error is given when it fails ?

---

### Post by the_penguin on 2008-02-08
Thanks for your reply.

After trying to download the files for around 10 mins it says this:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

And then a list of all the files it tried to get below. While trying to download the files, it stays stuck on 7 out of 14 of them right from the beginning (don't know if this is relevant).

The same thing happens for all servers.

Thanks for your help.

---

### Post by jordanmthomas on 2008-02-08
What happens if you type
```
sudo apt-get update
``` in a terminal?
What does it stall on?

---

### Post by hyper_ch on 2008-02-08
run in the terminal:

```

sudo apt-get update

```

and paste the output.

EDIT: Damn, jordan was a moment faster ;)

---

### Post by Bubba64 on 2008-02-08
Lately on my ancient IBM A21m Thinkpad the update will not not work until I do a reload in synaptic which will give you updates. I reloaded update manager but it still does it. The laptop is not my main computer so I haven't really worried about it. After I due reload in synaptic the manager works.

---

### Post by the_penguin on 2008-02-08
Thanks everyone.

This is what I get in the terminal:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_AU
Err [ftp://mirror.internode.on.net](ftp://mirror.internode.on.net) gutsy-updates Release.gpg                                        
  Could not connect to mirror.internode.on.net:21 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                                          
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [ftp://mirror.internode.on.net](ftp://mirror.internode.on.net) gutsy-updates/main Translation-en_AU                             
  Could not connect to mirror.internode.on.net:21 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_AU                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [ftp://mirror.internode.on.net](ftp://mirror.internode.on.net) gutsy-updates/restricted Translation-en_AU                       
  Could not connect to mirror.internode.on.net:21 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU                               
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [ftp://mirror.internode.on.net](ftp://mirror.internode.on.net) gutsy Release.gpg                                                
  Could not connect to mirror.internode.on.net:21 (1.0.0.0), connection timed out
37% [Connecting to mirror.internode.on.net (1.0.0.0)]

Reloading the package list just does the same thing as the updater.

Thanks.

---

### Post by jan quark on 2008-02-08
and changing the server does not help?

> system > administration > sources

---

### Post by the_penguin on 2008-02-08
Yea, same thing happens on all servers.

---

### Post by kesman on 2008-02-08
Weird IP for all servers, 1.0.0.0. Maybe someone could give you an ip-address to some apt-mirror, since I am at work with this *@!** windows, I cannot give it to you myself...

---

### Post by jan quark on 2008-02-08
can you please post the output form the source.list
```

cat /etc/apt/sources.list
```

---

### Post by the_penguin on 2008-02-08
Ah yes- didn't notice that!

Well that's probably what's causing it...but what would be making it use that IP and how do I change it to whatever is the right one?

Thanks!

---

### Post by the_penguin on 2008-02-08
> **jan quark said:**
> can you please post the output form the source.list
```

cat /etc/apt/sources.list
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [ftp://mirror.internode.on.net/pub/ubuntu/ubuntu/](ftp://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
# deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) gutsy-updates restricted main
# deb [http://mirror.pacific.net.au/linux/ubuntu/](http://mirror.pacific.net.au/linux/ubuntu/) gutsy restricted
deb [ftp://mirror.internode.on.net/pub/ubuntu/ubuntu/](ftp://mirror.internode.on.net/pub/ubuntu/ubuntu/) gutsy restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Everything is a comment isn't it?

Cheers

---

### Post by hyper_ch on 2008-02-08
Almost everything is... use this instead:

```

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu gutsy partner

```

---

### Post by jan quark on 2008-02-08
just wanted to ask if everything is fine

you can uncomment the sources you want to use by removing the hash mark

---

### Post by the_penguin on 2008-02-08
> **hyper_ch said:**
> Almost everything is... use this instead:

```

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu gutsy partner

```

Where do I add this in the file? I just put it at the end and it hasn't helped- all it did was select all the software package options in the software sources manager.

Thanks.

---

### Post by hyper_ch on 2008-02-09
put them into your sources.list

---

### Post by the_penguin on 2008-02-09
> **hyper_ch said:**
> put them into your sources.list

I did like I said- at the end of the file.

Any ideas?

---

### Post by kesman on 2008-02-09
can you do
```

ping au.archive.ubuntu.com

```
and check if there's response? I can do it from here. Also, can you put that address to your firefox and check if it connects?

---

### Post by the_penguin on 2008-02-09
Yep, I can ping that address and connect to it through Firefox.

Any ideas?

Cheers

---

### Post by smothpocket on 2008-02-09
Not all of your previous sources.list commands have been commented which could create problems by adding the same sources.

I would recommend making a backup of your current sources.list file:

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

and make a new sources.list file with the above mentioned repos

```
sudo gedit /etc/apt/sources.list
```

and insert the previously mentioned repos:

```
deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu gutsy partner
```

save it and then run:

```
sudo apt-get update
```

---

### Post by the_penguin on 2008-02-09
Thanks smothpocket, but on luck.

To disable ipv6 so the net would work I did this:

1. sudo gedit /etc/modprobe.d/aliases
2. Change line alias net-pf-10/ipv6 to off
3. Save and reboot.

Could that possibly affect the updater?

I am going to reinstall Ubuntu, but I doubt this will help. I've already tried once before.

Anyone have any idea what's going on?

Cheers

---

### Post by the_penguin on 2008-02-09
I just reinstalled Ubuntu. The only thing I've done is disable ipv6 to get the internet working.

No luck.

---

### Post by the_penguin on 2008-02-09
During the install it said it couldn't access the update repositories. It said this as well:

"commented out entries for security.ubuntu.com have been added to sources.list".

I just tried uncommenting this entries with no effect.

---

### Post by smothpocket on 2008-02-10
If you can ping the repos then I wouldn't think this would be a problem, but are you behind some sort of firewall?

---

### Post by the_penguin on 2008-02-10
There's no software firewall that I've had anything to do with.

I'm trying to work out how to disable my hardware firewall to check now.

Thanks.

---

### Post by the_penguin on 2008-02-10
Just disabled the router firewall...no help:confused:

---

### Post by the_penguin on 2008-02-10
Just fixed it- DNS server problem.

Thanks for everyone who helped me out,really appreciate it.

---

### Post by kesman on 2008-02-10
Nice to hear that you got it working. Could you please tell us how you did it so that somebody with similar problems would get the answer from this thread? Also, mark the thread solved.

---

