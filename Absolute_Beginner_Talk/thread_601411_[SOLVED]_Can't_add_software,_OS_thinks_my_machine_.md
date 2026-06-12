---
title: "[SOLVED] Can't add software, OS thinks my machine is a 386"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by dmillergv on 2007-11-03
I have installed 7.10 on a Pent 4 3 GH HT Dell 8300. It is a dual boot along with XP pro.
When I try to add a program thru Add/Remove, I get a message that I cannot add because it thinks I have a 386 machine. How do I remedy this.
I am a newbie to Unix having shunned it since the early 80s because it never caught on in the early PC world. If the fix to this requires entering commands, please give step by step instructions.
Thanks,
Dick Miller
Old retired IBM Systems Engineer

---

### Post by Dr Small on 2007-11-03
Use i386 software, because it appears that you install x86 version of Ubuntu.

---

### Post by jw5801 on 2007-11-03
Try opening a terminal (Applications > Accessories > Terminal, I think... I'm not at my Ubuntu machine at the moment), and running ```
sudo apt-get update
sudo apt-get install *whatever-package-you-wanted*
```and you might get some more informative error messages (post them here if you're unsure about them). Also give us the output of ```
uname -a
``` for some extra information.

---

### Post by taurus on 2007-11-03
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by ByteJuggler on 2007-11-03
> **dmillergv said:**
>  I get a message that I cannot add because it thinks I have a 386 machine. How do I remedy this.

What exactly is the message?  To clarify, the term "i386" is used to sometimes identify generic 32-bit versions of x86 based software.  Messages containing "i386" does not neccesarily refer specifically to the 386.  There are 2 flavours of X86 Ubuntu, a 32-bit "i386" version, and a 64-bit "x64" or "AMD64" version.  Most modern Intel and AMD processorts support both, so you can install either.  The 64bit version obviously has advantages such as a larger memory address space.  But the more important point is this: If you've initially installed the 32bit version, then you cannot install 64bit packages on it, and vice versa.  It is possible that you originally installed the 64-bit version and are now trying to install 32bit packages, or vice versa, hence the messages you're getting, but without more information my comments are pure guesswork and speculation.

---

### Post by dmillergv on 2007-11-03
what follows is the message I get. This was from trying to add Abi Word.


Canonical Ltd. provides technical support and security updates for AbiWord Word Processor
AbiWord Word Processor cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by philinux on 2007-11-03
Use system admin and then select synaptic package manager search for abiword and try to install it from there.

---

### Post by dmillergv on 2007-11-03
Tried Synaptic package manager. Abiword not there. Thunderbird (not in normal add/remove) was found and installed. 7zip installed and wouldn't the other way.
T-bird showed up in the Applications drop down but 7zip didn't. How do I get a program name and link into the Apps menu? 
Just like genealogy, 1 ancestor found and creates 2 more questions.

---

### Post by SunnyRabbiera on 2007-11-03
a really odd one, as I have a Pentium 4 and the x86 packages work for me...

did you accidentally download the 64 or sparc version of ubuntu?

---

### Post by SunnyRabbiera on 2007-11-03
ignore the spammer folks, nothing to see there.

---

### Post by philinux on 2007-11-03
> **dmillergv said:**
> Tried Synaptic package manager. Abiword not there. Thunderbird (not in normal add/remove) was found and installed. 7zip installed and wouldn't the other way.
T-bird showed up in the Applications drop down but 7zip didn't. How do I get a program name and link into the Apps menu? 
Just like genealogy, 1 ancestor found and creates 2 more questions.

It sounds like to need to add some repos to your sources list.

Read through this stick particularly about installing software.

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by dmillergv on 2007-11-03
I installed with the 7.10 ISO I downloaded. The Install menu option from the live CD was used. I just sat by and watched.

---

### Post by SunnyRabbiera on 2007-11-03
> **dmillergv said:**
> I installed with the 7.10 ISO I downloaded. The Install menu option from the live CD was used. I just sat by and watched.

I was asking as I know there are different versions.
But I am living proof that you can install x86 packages on a p4, this is an odd one for sure.

---

### Post by mikewhatever on 2007-11-03
I get the same message when the repository I try to install from is unavailable. It seems to be something generic for Add/Remove. You guys can test it by disconnecting from the internet and trying to install something.

dmillergv, do what taurus told you, post the content of your sourses.list.

> cat /etc/apt/sources.list

---

### Post by SunnyRabbiera on 2007-11-03
It might be best to fish for more repositories via synaptic:
Just make sure to get some extra repositories just in case it doesnt work, dont worry this is easy to manage:
first to change the repositories, just go up to "settings" once synaptic is up and running
then click on "repositories"
then a new windows will pop up saying "software sources"
(you can also do this via, system> administration> software sources, its practically in the same place where you found synaptic)
anyhow once this window pops up in the "ubuntu software" tab just click off pretty much all the boxes (except the source code one) and if you are having issues with the server just select another one, there is a little box here that says "download from" next to it and depending on what nation you are from it will say it
(example if it says united states then your servers in the united states)
just click on it and you can select others too such as the main server and the "other" servers
just make sure to choose a location that is closest to you (the main servers will do just as fine as the main one by default)
in the "others" section you can choose other servers in your country, or nations close to your country, if american you can select a Canadian one if you wish and if you have a higher connection rate such as highspeed some of the european ones will do such as UK)
after you are done selecting a server you are confident with you can close this window and click the "reload" button.

---

### Post by dmillergv on 2007-11-03
Sources list:

dick@dick-8300-Ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partndick@dick-8300-Ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
dick@dick-8300-Ubuntu:~$ 
er
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
dick@dick-8300-Ubuntu:~$ 

The sources list shows release i386. How did that happen? What's the cure?

I have to go out for a couple of hours. Looking forward to answers when I return.

Thanks all,

---

### Post by jw5801 on 2007-11-03
Yup that's your issue. You weren't connected to the net when you installed so the installer commented out all the lines that would otherwise direct it to a repository. Open up the file ```
gksudo gedit /etc/apt/sources.list
```and uncomment (remove the # from the start of the line) all the lines starting with deb or deb-src. Then run "sudo apt-get update" or open synaptic and it should update automatically, then you'll be able to get the right packages that work.

---

### Post by dmillergv on 2007-11-03
Thank You jw5801
I did as you instructed and that answered the problem of add/remove.
My system is on a very weak wireless connection. 7.10 found the adapter and connected
when installed. It should have been connected. Although the house has 4 2.4 Gig phones and one might have been in use. At times they knock out the wireless.

Should I live with a 386 or should I reinstall from scratch?

Thanks again to all

---

### Post by ByteJuggler on 2007-11-03
> **dmillergv said:**
> 
Should I live with a 386 or should I reinstall from scratch?


To repeat what I said before, the "i386" does **_*NOT*_** refer to the 386 chip specifically, but to **_*all*_** _32 bit_ x86 chips since the Intel 80386.  

The other x86 based release that could've possibly been relevant here, is the x64 (sometimes known as AMD64) release, which is the_ 64 bit_ x86 variant.  

However, your P4 does _not_ support 64bit, so the _only_ option is the one you've got already, which is the 32bit x86 release, aka the "i386" release. 

The short answer: You must stick with what you have as (for a P4) there's no alternative.

Hope that clarifies/helps. :-)

---

### Post by Dr Small on 2007-11-03
> **ByteJuggler said:**
> To repeat what I said before, the "i386" does **_*NOT*_** refer to the 386 chip specifically, but to **_*all*_** _32 bit_ x86 chips since the Intel 80386.  

The other x86 based release that could've possibly been relevant here, is the x64 (sometimes known as AMD64) release, which is the_ 64 bit_ x86 variant.  

However, your P4 does _not_ support 64bit, so the _only_ option is the one you've got already, which is the 32bit x86 release, aka the "i386" release. 

The short answer: You must stick with what you have as (for a P4) there's no alternative.

Hope that clarifies/helps. :-)
Wasn't that what I was trying to say in the first response ? O.o

---

### Post by dmillergv on 2007-11-03
Again, Thank you all.
The problem was probably caused by my loss of wireless net, I now can add/remove without and command language. I have other problems but let's consider this thread closed.

---

### Post by jw5801 on 2007-11-03
There's a button to "mark thread as solved" under thread tools :)

---

### Post by Dr Small on 2007-11-03
> **jw5801 said:**
> There's a button to "mark thread as solved" under thread tools :)
I second that. ;)

---

