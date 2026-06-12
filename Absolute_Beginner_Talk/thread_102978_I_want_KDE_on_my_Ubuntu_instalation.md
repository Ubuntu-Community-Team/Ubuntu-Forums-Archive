---
title: "I want KDE on my Ubuntu instalation"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by alikali on 2005-12-13
I want to install KDE on my ubuntu breazzy and searching google I ended up on this page:
                  file:///home/alikali/Desktop/%3A%3A%20Howtos%20%3A%20HOWTO%20Install%20KDE%203.5%20on%20Ubuntu%20Breezy%205.10.html

I've succesesfully completed the first part and I'm having problems with the second step. Here's what is happening

alikali@ubuntu:~$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jridd](http://people.ubuntu.com/~jriddell/kubuntu-packages-jridd) ell-key.gpg
--15:24:10--  [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.g](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.g) pg
           => `kubuntu-packages-jriddell-key.gpg.1'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26,430 (26K) [text/plain]

100%[====================================>] 26,430        52.67K/s

15:24:11 (52.48 KB/s) - `kubuntu-packages-jriddell-key.gpg.1' saved [26430/26430 ]

alikali@ubuntu:~$ apt-key add kubuntu-packages-jriddell-key.gpg
gpg: no writable keyring found: eof
gpg: error reading `kubuntu-packages-jriddell-key.gpg': general error
gpg: import from `kubuntu-packages-jriddell-key.gpg' failed: general error
alikali@ubuntu:~$


Can anyone help me ?
thanks

---

### Post by daller on 2005-12-13
Instead of "wget [http://people.ubuntu.com/~jriddell/k...packages-jridd](http://people.ubuntu.com/~jriddell/k...packages-jridd) ell-key.gpg"

it should be:

wget [http://people.ubuntu.com/~jriddell/k...packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/k...packages-jriddell-key.gpg)

But about the key... It doesn't really matter! - You will just be asked if you REALLY want to proceed without authentication!

---

### Post by estel on 2005-12-13
What's there preventing you from just doing:

```
sudo apt-get install kde-desktop
```

---

### Post by Stewie on 2005-12-14
I am trying to do similar to alikali and install KDE on Hoary Hedgehog.

[QUOTE=estel]What's there preventing you from just doing:

```
sudo apt-get install kde-desktop
```[/QUOTE]

When I type that in I get:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kde-desktop

And I can't get Daller's to work.
What should I be typing in the terminal exactly?

---

### Post by Mudbream on 2005-12-14
Hi,
I managed to do this by using the Synaptic Package Manager. I just searched for "kde" and then installed the "kde-base" package. It selected all the dependencies and everything installed fine.
After logging out and logging back in again everything worked fine, except automatically picking up my external USB harddrive. Still trying to figure it out though.

Hope that helps.

Mudbream

---

### Post by Stewie on 2005-12-14
[QUOTE=Mudbream]Hi,
I managed to do this by using the Synaptic Package Manager. I just searched for "kde" and then installed the "kde-base" package. It selected all the dependencies and everything installed fine.
After logging out and logging back in again everything worked fine, except automatically picking up my external USB harddrive. Still trying to figure it out though.[/QUOTE]

I am not allowed to do that. I get a nasty message.

Screen shot: [http://img439.imageshack.us/img439/5328/screenshot10xi.png](http://img439.imageshack.us/img439/5328/screenshot10xi.png)

---

### Post by Gadren on 2005-12-14
It sounds like you need to enable your universe and/or multiverse repositories.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by Mudbream on 2005-12-14
Uhm...do you have the latest repositries set? Here is my file: /etc/apt/sources.list

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


Try creating a backup of yours and putting this in. 
I'm sure someone else with loads more experience can pipe up about whether this is the right/wrong thing to do though.

---

### Post by Stewie on 2005-12-14
Many thanks. That's it working now.

---

