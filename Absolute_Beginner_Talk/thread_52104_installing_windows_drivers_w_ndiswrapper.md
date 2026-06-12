---
title: "installing windows drivers w/ ndiswrapper"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-07-26
I have been following along with the tutorial I found here:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

I got all the way to:
Installing the Windows Drivers
step 1.

The drivers that I found for my Linksys WMP54GS card has the extention of .exe (WMP54GS_20050406.exe) . In the tutorial it said that the extension should be .inf. Do I need to change this .exe file to a .inf some how?? if so, how? 

does it make a different that I'm using k/ubuntu? I didn't think so..

I did a ```
lspci
``` and found:
...
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
...

this is the only thing holding me back from full enjoyment of kubuntu linux.

thanks for the help.

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=xnszxdotnet]I have been following along with the tutorial I found here:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

I got all the way to:
Installing the Windows Drivers
step 1.

The drivers that I found for my Linksys WMP54GS card has the extention of .exe (WMP54GS_20050406.exe) . In the tutorial it said that the extension should be .inf. Do I need to change this .exe file to a .inf some how?? if so, how? 
[/QUOTE]

No. Email that to one of your Window's friends and then get them to open it and send you the .inf files.

---

### Post by xnszxdotnet on 2005-07-28
ahhh,
how hard can this be!...

OK
I did the
```
dpkg -i --force-overwrite ndiswrapper-utils_1.1-1_i386.deb
``` 

and got:
```
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages ...
etc.
etc

``` 

and same with the:
```
dpkg -i --force-overwrite ndiswrapper-modules-$(uname -r)_1.1-1_i386.deb
```

so i take it that this dpkg didn't work for both of these files. I did a ls command and found them both sitting in my /usr/src folder.

what gives??
how can I fit this. plus there seems to be two files of my card. WMP54GSa.inf it says that the file is plain text document and a wmp54gs.inf says that the file is a program. when I get to that point wich one do I use??

thanks

---

### Post by Zelut on 2005-07-29
If you're trying to use the broadcom drivers to setup your wireless card it can be pretty simple.  I got mine installed (onboard broadcom 54g) in about 5 commands.  Try the following & see if this helps at all.  The first commands are to cleanup anything you've previously tried, and the second set should install the driver you need.

(this tutorial is using the bcmwl5.inf/sys files.  Try those or replace with your version)
REMOVAL:
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

INSTALLATION:
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
edit .conf files in /etc/ndiswrapper/bcmwl5/ and change RadioState|1
to RadioState|0

Check Network & Activate the wireless.  It should be listed at this point & you'll be set.  More than happy to help with additional questions.

---

### Post by xnszxdotnet on 2005-07-29
I did all the removel commands and everything seemed to be OK, no files or dir were found on a lot of them. 

I did the first install command of:
sudo apt-get install ndiswrapper-utils

and the last line of a long string says:
E: Couldn't find package ndiswrapper-utils

?? now what ??

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=xnszxdotnet]I did all the removel commands and everything seemed to be OK, no files or dir were found on a lot of them. 

I did the first install command of:
sudo apt-get install ndiswrapper-utils

and the last line of a long string says:
E: Couldn't find package ndiswrapper-utils

?? now what ??[/QUOTE]


Did you change you sources.list? Change it back if you did.

if not:

> sudo apt-get update

---

### Post by xnszxdotnet on 2005-07-29
I was messing around with the sources.list file but I changed it back to this::

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe
``` 

I then did  sudo apt-get update and got the same error when trying to install again.

---

### Post by Zelut on 2005-07-29
be sure to check out the ubuntuguide & update your sources.list according to what is listed there.  ndiswrapper-utils may be in another repository that you dont have listed, that is why it isn't finding it.  (repository how-to is one of the first items on the ubuntuguide.org)

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=kuyaedz]be sure to check out the ubuntuguide & update your sources.list according to what is listed there.  ndiswrapper-utils may be in another repository that you dont have listed, that is why it isn't finding it.  (repository how-to is one of the first items on the ubuntuguide.org)[/QUOTE]


No...Don't listen to this. The ndiswrapper-utils are on the hoary CD. You don't have internet, so change the sources.list after you get it to work.

If push comes to shove, you can download ndiswrapper packages and install them by hand.

search for "ubuntu packages" in google.

---

### Post by xnszxdotnet on 2005-07-29
yeah, that guide is were I found how to do this stuff.
I was going along with that guide I just 

mv the ..._backup ...sources.list
apt-get update

I get:
E: some index files failed to download, they have been ignored, or old ones used insted.

I went to synaptic searched for ndiswrapper and found nothing.

screw it!
I'm just going to install everything over again and clean up anything that I might have screwed up when I was playing around. I've got a full work 5.04 system that I'm working on now. I've been installing software and getting audio codecs and everything , I'm love it so far. It's just this one stupid card holding me back. I need this card to work so I can get a HTPC working.

---

### Post by xnszxdotnet on 2005-07-29
OK I reinstalled everything and did the install commands
> INSTALLATION:
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
edit .conf files in /etc/ndiswrapper/bcmwl5/ and change RadioState|1
to RadioState|0 
everything seemed to work jsut fine but I went to 
System -> Administration -> Networking
and found nothing but a grayed out Modem connection the card isn't showing up.

---

### Post by dcraven on 2005-07-29
Maybe try:
```
sudo modprobe ndiswrapper
```

~djc

---

### Post by poofyhairguy on 2005-07-29
Have you seen this?

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by xnszxdotnet on 2005-07-30
OK I'm completely confused.

i have a a LInksys wireless -g PCI adapter with speedbooster
model # WMP54GS

after getting the windows drivers from Linksys.com in a Drivers folder coming from the .exe file there are 5 files:

bcmwl5a.sys
bcmwl5.sys
WMP54GSa.inf
wmp54gs.cat
wmp54gs.inf

which ones do I use to work with the other post?
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)
HOW TO: Configure wireless cards with Broadcom chipsets

I think that is my problem. I used the bcmwl5.sys file and the wmp54gs.inf file. 
it now shows up in my System -> admin -> Networking which is farther then I've every gotten before. I enter my WEP key prefect. it's not HEX so I do
s:**********
into the WEP key

still nothing ](*,)

---

### Post by xnszxdotnet on 2005-07-31
I took the linksys card out and returned it. I went and got a d-link DWL-G520 that is "works out of the box". and it doesn't. back to square one

grrr
 :mad:

---

