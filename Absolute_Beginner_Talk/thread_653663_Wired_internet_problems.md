---
title: "Wired internet problems"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by iainr86 on 2007-12-30
having installed xubuntu im having problems getting my internet to work. im connected to a wired router but i cant browse the net at all. Once or twice ive managed to get onto google and do a search, but then havent been able to open any other sites. I'm able to ping sites with no problems. I was having a similar problem in pclinuxos where i couldnt get firefox to do anything, but the other browser that came with it worked fine. any suggestions?

---

### Post by iainr86 on 2007-12-30
please? anyone?

---

### Post by eyezdk on 2007-12-30
well. you can always try to reinstall fire fox  with synaptic. 
If you say another browser works fine, it might be firefox.

---

### Post by laidback on 2007-12-30
Could it be an ipv6 issue. I doubt it as I haven't read of people getting such restricted/no access to the net before. But just in case here's how to disable it (it's not needed at all):-

Blacklist ipv6 (from previous Ubuntu forum thread)

$ sudo gedit /etc/modprobe.d/blacklist

type in your password

in Gedit:-

type 'blacklist ipv6' (i.e. add the line blacklist ipv6 to the file)

save and exit

You're set

blacklist.bak is original

Not sure whether it is enacted immediately so try a reboot if in doubt.

---

### Post by laidback on 2007-12-30
Another thought:-

Could you be using DHCP when in fact you ned Static IP, or the reverse?

---

### Post by iainr86 on 2007-12-30
> **eyezdk said:**
> well. you can always try to reinstall fire fox  with synaptic. 
If you say another browser works fine, it might be firefox.

i would, but it appears that in xubuntu i dont have any internet at all so i cant even download new apps. i'll give this ipv6 thing a bash tho

---

### Post by iainr86 on 2007-12-30
> **laidback said:**
> Another thought:-

Could you be using DHCP when in fact you ned Static IP, or the reverse?

I've got it set on DHCP, andhave double checked with the other computers running off my router and they're all set up as DHCP too so i dont think its that

---

### Post by iainr86 on 2007-12-30
> **laidback said:**
> $ sudo gedit /etc/modprobe.d/blacklist.

one slight problem...........

The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found
iain@iain-desktop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gedit

---

### Post by laidback on 2007-12-30
Gedit is being used as a simple text editor, anything else would do.

---

### Post by Joeb454 on 2007-12-30
gedit is for the Gnome installation of Ubuntu (the default variant) Xubuntu uses XFCE.

What's the default text editor called in Xubuntu?

---

### Post by laidback on 2007-12-30
A friend missed this one:-

On the Network Connections screen against the Connections tab > Wired Connection; on the LHS there's a little box, it needs to be ticked. In the Properties section Disable Roaming.

---

### Post by iainr86 on 2007-12-30
> **laidback said:**
> $ sudo gedit /etc/modprobe.d/blacklist

Once i worked out to use mousepad instead of gedit and did this it solved the problem after a restart. Thanks so much, you're a legend!!

---

### Post by iainr86 on 2007-12-30
ok maybe not as solved as i thought. Firefox is now working fine, but im having problems with add/remove... as soon as i open it up i get the following message 'the list of available applications is out of date. To reload the list you need a working internet connection'

I click reload and it says downloading package information, but it only gets to 7 of 16 then just sits there with download rate: unknown. I clicked show progress of single files and it gives a list of failed stuff.

If i click cancel it says could not download all repository indexes.


Any ideas?

---

### Post by willie_wang on 2007-12-30
maybe configuring your network interfaces might help?

```
sudo mousepad /etc/network/interfaces
```

to configure your eth0 interface if that's your wired interface under all the lo configuration, add:

```
auto eth0
iface eth0 inet dhcp
```

...

if that messes up your config, just remove those lines again. i'm doubtful it will.

another note: i always get a whole load of failed statuses when updating the repositories, however it's only the unneccessary english translations that fail to download. i'm pretty sure this is supposed to happen.

try updating your sources from the command line:

```
sudo apt-get update
```

see if that makes any difference. nb. sometimes it does take quite a while to update the repositories info depending on your connection speed. i.e. the first time i do it, it takes forever.

---

### Post by iainr86 on 2007-12-30
> **willie_wang said:**
> 

```
auto eth0
iface eth0 inet dhcp
```

.

I tried this but both those lines were already in the file. also tried updating through the terminal like you suggested and again it gets to a certain point then just sits there until it eventually throws a hissy fit and gives up. annoying!!

---

### Post by laidback on 2007-12-30
I always update my repositories via Synaptic, which if memory serves is available in Xubuntu. Look for Synaptic package manager on the systems or Admin menus. It's the same as above but via a gui rather than command line.

---

### Post by laidback on 2007-12-30
Another thought, is your router blocking some port(s) used by Xubuntu. I have little idea of how to check them or what to do but it may worth checking. Query the forum!

---

### Post by willie_wang on 2007-12-30
> **iainr86 said:**
> I tried this but both those lines were already in the file. also tried updating through the terminal like you suggested and again it gets to a certain point then just sits there until it eventually throws a hissy fit and gives up. annoying!!

try taking the section eth0 out of the /etc/network/interfaces file. strange as it seems, i had to do this to get networking working on my old ibm thinkpad. if that fails, i don't know what to do! sorry

---

### Post by laidback on 2007-12-30
I'm pleased to read that Firefox is now working, progress indeed.
I'm sorry that you've had these problems though, I never cease to be amazed at the different experiences uses have of Ubuntu as well as other Linux distros. Ubuntu has been the best by far for me, it's hardware detection seems to be the best I've experienced. Guess it's all to do with the huge number of variables that there are.

---

### Post by willie_wang on 2007-12-30
may need to restart your network interfaces after you do any changes to your network/interfaces file

```
sudo ifdown -a
sudo ifup -a
```

you might want to check if you /etc/apt/sources.list is the same as mine. just because it seems odd that you can download half and not all of your repositories...

here's mine:

```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

