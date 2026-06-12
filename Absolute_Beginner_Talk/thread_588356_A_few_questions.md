---
title: "A few questions"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Rey Merin on 2007-10-23
Hello, I'm a new user that just started using Ubuntu. I've used Windows for most of my life, but after hearing some friends discuss Linux, I decided to play around a little bit. So, I installed Ubuntu on my laptop and here I am.

I'm not the most computer savvy, but I'm slowly learning. I'm definitely not educated at all with Ubuntu. I've encountered a few problems so far, and I'm here to ask for assistance.

**1** - My update manager was working fine until just recently. When I open it, it runs for a little bit, then the status bar stops and I get the following message: 

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5 Input/output error), E:The package lists or status file could not be parsed or opened.'

What's going on here? When I open Add/Remove apps, I get a somewhat similar message that I believe is related:

> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

**2** - Originally, I had installed Kubuntu because that's what my friend was trying out. However, I couldn't get any connection to the Internet. I'm on a laptop, but it wouldn't say anything about my wireless card. I even plugged the Ethernet cable straight in and no dice. However, the second I installed Ubuntu, I was able to connect. And idea about this?

**3** - Another Internet question. When I go to my uni for classes, I can get a wifi connection. On XP, whenever I opened up Firefox, I was taken to my uni's site automatically which required me to log in to use the Internet. When I open Firefox in Ubuntu, however, I am just taken to the default homepage and cannot go anywhere. How would I be able to connect, if it's possible?

Thanks for any help I get. I'll probably end up with more questions as I explore...

---

### Post by Lord_Dicranius on 2007-10-23
1) Could you post the contents of /etc/apt/sources.list?  From a terminal, type

```

gksudo gedit /etc/apt/sources.list

```

2) I had that same problem.  Never really asked why after switching to Ubuntu, I don't plan on switching back anytime soon heh

3) On XP, the login...is that an extra box that pops up requiring username/password?  Or is the username/password coded onto the uni's homepage itself?  And by "cannot go anywhere" (if the username/password is coded into the page itself), you mean when you click on links nothing happens? (obviously this 2nd question doesn't apply if another box prompts for the username/password when you try to access the uni's homepage).

---

### Post by Celegorm on 2007-10-23
> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Welcome to the world of useful error messages. The first thing to do is open up Synaptic package manager (under the system administration menu I believe) and click on "broken" on the list on the left. If there are any packages listed there, click on "Fix Broken Packages" under the edit menu. If that doesn't fix the problem, open up a terminal window (applications->accessories->terminal) and post the output of ```
ls -l /etc/apt/sources.list
``` (if you have never used the terminal before, just copy and paste the command and press enter). Also post the contents of the file /etc/apt/sources/list.

As for question 3, if I remember correctly, the default homepage is a file on your computer, and not the internet. Try loading up any site on the internet and see if that takes you to the right site.

One other thing, if you post one problem per thread with more informative titles (for instance, "add/remove not working") you will be more likely to attract the people who will have some idea how to fix the problem.

---

### Post by Rey Merin on 2007-10-23
I haven't really touched it. Here we go:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://mirror3.ubuntulinux.nl/ dapper-seveas freenx
```

And when I open Firefox, my homepage doesn't come up but instead the Internet gateway page of the university which asks me to log in. And by that, I meant I can't use the Internet at all, hah.

Another question too:

**4** - Should I use Linux? Yeah, I know, why ask a question like that somewhere like this. But I'm just wondering. I have a desktop with XP on it that handles some heavier software and that can handle it with ease. With my laptop, I'm just looking for something simple and clean for school stuff, web browsing, etc.

---

### Post by Celegorm on 2007-10-23
> **Rey Merin said:**
> And when I open Firefox, my homepage doesn't come up but instead the Internet gateway page of the university which asks me to log in. And by that, I meant I can't use the Internet at all, hah.

So you can't even log in on the gateway page?

Looks to me like the problem with add/remove and update-manager is entirely due to not being connected to the internet.

---

### Post by Rey Merin on 2007-10-23
> **Celegorm said:**
> Welcome to the world of useful error messages. The first thing to do is open up Synaptic package manager (under the system administration menu I believe) and click on "broken" on the list on the left. If there are any packages listed there, click on "Fix Broken Packages" under the edit menu. If that doesn't fix the problem, open up a terminal window (applications->accessories->terminal) and post the output of ```
ls -l /etc/apt/sources.list
``` (if you have never used the terminal before, just copy and paste the command and press enter). Also post the contents of the file /etc/apt/sources/list.

As for question 3, if I remember correctly, the default homepage is a file on your computer, and not the internet. Try loading up any site on the internet and see if that takes you to the right site.

One other thing, if you post one problem per thread with more informative titles (for instance, "add/remove not working") you will be more likely to attract the people who will have some idea how to fix the problem.
Hah, when I try to open the package manager, I get this:

> E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

And concerning the homepage, I was taken there automatically on Windows, without regards to the homepage I had set already. My previous posts details it more.

And sorry about the thread title. I wasn't sure what to put because who knows what varied problems I'm going to have, hah.

Thanks a lot guys :]

---

### Post by Rey Merin on 2007-10-23
> **Celegorm said:**
> So you can't even log in on the gateway page?

Looks to me like the problem with add/remove and update-manager is entirely due to not being connected to the internet.
No, that was to my problems concerning getting online at school. Sorry.

---

### Post by Celegorm on 2007-10-23
So right now you are not at school and definitely connected to the internet? I'm not finding any problems in your /etc/apt/sources.list. Try these two commands in the terminal ```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by Rey Merin on 2007-10-23
> **Celegorm said:**
> So right now you are not at school and definitely connected to the internet? I'm not finding any problems in your /etc/apt/sources.list. Try these two commands in the terminal ```
sudo apt-get update
sudo apt-get install -f
```
Yes, I am at home posting on the computer that's having problems.

When I did those commands, it got to 95% and gave me this:

> Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by Celegorm on 2007-10-23
Post the output of ```
ls -l /etc/apt/sources.list
```

---

### Post by Rey Merin on 2007-10-23
> -rw-r--r-- 1 root root 5013 2007-10-23 13:16 /etc/apt/sources.list

Wow, I completely forgot about doing that even though it was said already. Sorry, that's what I got.

---

### Post by Celegorm on 2007-10-23
Well... those are the correct permissions for /etc/apt/sources.list. I can't find a problem with /etc/apt/sources.list itself, but there is some problem with multiple applications not being able to read it, which would seem to imply that there is a problem with the file... I don't suppose there is any chance you missed one or two characters at the beginning or end when you posted the contents here?

---

### Post by Rey Merin on 2007-10-23
Did it again and checked; it's right.

Hmm... this is a tad frustrating. I'm just trying to install things :[

Thanks a lot for the help you've been giving me.

---

### Post by staticsage on 2007-10-23
> **3** - Another Internet question. When I go to my uni for classes, I can get a wifi connection. On XP, whenever I opened up Firefox, I was taken to my uni's site automatically which required me to log in to use the Internet. When I open Firefox in Ubuntu, however, I am just taken to the default homepage and cannot go anywhere. How would I be able to connect, if it's possible?

Thanks for any help I get. I'll probably end up with more questions as I explore...

I could be wrong, but to me this sounds like it could possibly be a proxy issue. In windows check your connection settings in firefox: Tools | Options | Advanced | Network tab | Connection Settings button

If it is set to anything other than automatic or direct, you will have to mimic that setup under Ubuntu. Post back with your results/questions. I'll check back on the thread.


And as for question 4: yes, you should use Linux! It is great to learn and to be familiar with it... you know, in case Microsoft decides to turn on you. ;)

---

### Post by ItsMitsHere on 2007-10-23
Dear rey merin,

try this code at terminal

**sudo apt-get clean** 

then 

**sudo apt-get --fix-missing**

and finally

**sudo apt-get update**

followed by 

**sudo apt-get upgrade**

cheers!!!

---

### Post by Rey Merin on 2007-10-23
> **ItsMitsHere said:**
> Dear rey merin,

try this code at terminal

**sudo apt-get clean** 

then 

**sudo apt-get --fix-missing**

and finally

**sudo apt-get update**

followed by 

**sudo apt-get upgrade**

cheers!!!
This worked. Thank you so much!

And thanks to all that tried helping me; I greatly appreciate your time!

---

### Post by ItsMitsHere on 2007-10-23
now if it really worked for u, i would suggest u should really give a serious try to ubuntu or any other linux distro. the things are quite simpler then windows and more predictable so when you get to know the things. after 5 years many more people will be using linux then today and if you keep using linux, who knows you might be next linux guru??? any way i myself am a linux nub and have started using ubuntu just 1 month back. u will feel the power of linux yourself only if u stick to it!!!

---

### Post by Rey Merin on 2007-10-23
I'm definitely going to start using Ubuntu on my laptop all the time now. I would seriously love to learn how to use it effectively. Time to start reading up like crazy...

---

