---
title: "connecting the the internet"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by trynet on 2007-10-18
how do I set-up an internet connection on ubuntu? I'm so used to windows, this is confusing me.
I'm currently unable to access the internet in any form on my other computer. (running ubuntu)

---

### Post by k33bz on 2007-10-18
are you using dial-up, cable, or wireless?

---

### Post by Dr Small on 2007-10-18
Could you please post the output of 'lspci' from **Applications > Accessories > Terminal** ?

Dr Small

---

### Post by trynet on 2007-10-18
wireless

and not really, I'm stuck using a different computer to type this and its to much to type by hand.

---

### Post by 1337455 10534 on 2007-10-18
Odd. Try post the results of
```

ip

```
in your terminal
(acessories)

edit>>ooops, play w/ it a bit

---

### Post by Pumalite on 2007-10-18
Wireless(I hope it helps):

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by trynet on 2007-10-18
*runs back and forth across the house*
where OBJECT :{ link|addr|root|rule|neigh|tunnel|mddr|mroute|monitor|xfrm}
OPTIONS =  v[ersion] |- s[tatstics] | -r[esolve] |- f[amily] {inet | inet6| ipx|dnet|link}|o[neline]}

thats as accurate as I can get it.

---

### Post by Dr Small on 2007-10-18
You say that you can not get on the internet, but can you access your local network ?

---

### Post by trynet on 2007-10-18
I can't set it up on my other computer.
this one works. 
I read the help files and I was doing exactly what it said to do.
I was able to connect before I downloaded ubuntu to the computer, now I can't connect.

---

### Post by praveenpious on 2007-10-18
While issuing sudo pppoeconf i get the following error 

"Sorry, I scanned 1 interface(s), but the Access Concentrator of your provider did not respond. Please check the network card and modem cables. Another reason for the scan failure may be another running pppoe process which controls the modem"

Please help me out...

---

### Post by trynet on 2007-10-18
in case this helps this is the error message I get when I click "activate"
"could not enable the interface eth1"

---

### Post by trynet on 2007-10-18
bump!
what I'm doing in the network is-
network>wireless:
*my ssid here*

static
*IP on the bottom of my router here*
*225.225.225.0*
*no gateway*
___
not working

---

### Post by Dr Small on 2007-10-18
You must have a gateway to access the router. The gateway would be the router's IP Address.

Dr Small

---

### Post by trynet on 2007-10-18
it still gives me the same error message when I do that.

the IP I put in te "IP" box, should also be the one listed on the bottom, correct?
do the 2 settings below the Essid make a difference when connecting?
is an "Essid" the same as an "SSID"?

---

### Post by trynet on 2007-10-18
need help please.
*wishes never formated drive*

---

### Post by trynet on 2007-10-19
please? I can't use my other computer until I get the internet up.

---

### Post by justinmiller87 on 2007-10-19
> **trynet said:**
> please? I can't use my other computer until I get the internet up.
Like someone has said before, go into Terminal and type lspci and type or paste the output from there into the thread. It will be easier to help you if we know what that says.

---

### Post by trynet on 2007-10-19
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by trynet on 2007-10-19
did I just waste a 700 mb disk on a few bytes of text?

---

### Post by ugm6hr on 2007-10-19
> **trynet said:**
> did I just waste a 700 mb disk on a few bytes of text?

No.  But a USB stick is generally a better option for transfers!

This is the important line:
[B]
0000:01:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/B]

What version of Ubuntu are you using?

I suspect that this installer will solve the issue for you:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

If not, report back.

Or try this:
[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by trynet on 2007-10-19
:P I don't have a USB on me right now.

I just downloaded it yesterday, I guess I'm using the newest LTS version.

---

### Post by BrendanM on 2007-10-19
I don't know anything about your particular setup, but you might have better luck with hardware support if you upgraded to the newest version of Ubuntu, 7.10. The LTS version is good, but just because a version is not LTS does not mean it isn't stable. My impression is that sticking with LTS versions is mostly for businesses who don't plan on changing their hardware/software that frequently.

---

### Post by trynet on 2007-10-19
I just ran every EXE in that zip package ...
nothing, nothing at all happened.
I'll try the other link now.

---

### Post by trynet on 2007-10-19
nothing -_-
I never realised how dependent I was on the wireless network search with windows -_-

---

### Post by trynet on 2007-10-19
is there any way to get the wireless to work without using any other scripts? I'm out of disks.

---

### Post by Pumalite on 2007-10-19
Did you check all my links and you couldn't make it work with any of them?

---

### Post by trynet on 2007-10-19
yeah, I checked them all, the computer still cannot connect.

---

### Post by justinmiller87 on 2007-10-19
> **trynet said:**
> nothing -_-
I never realised how dependent I was on the wireless network search with windows -_-
Try following the instructions I created [here,](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)  with [these drivers](ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip) instead of the Airgonet in the instructions. I just updated the instructions to include the files for Gutsy if that's the version you're using.

---

### Post by justinmiller87 on 2007-10-19
Also, I saw in your list you have a 10/100 wired connection. Can you connect with that? At least you can be on the Internet then.

---

### Post by trynet on 2007-10-19
I didn't know I had any form of a wired connection, if I do, I have no clue how I would.
I'll read it now.

---

### Post by trynet on 2007-10-19
I already got rid of windows, I don't have any drivers left from windows, I had like 2 gigs left and HAD to format the drive.

---

### Post by trynet on 2007-10-19
is their any linux that has a network search thing like XP?...
I'm starting to get annoyed...*keeps messing with network*

---

### Post by Licurgo on 2007-10-19
Trynet:
Because there are many new hardware it is important to have the newest version of ubuntu 8with the latest drivers) but if you are unhappy with ubuntu you can try PClinuxOS in: [COLOR="Blue"]http://www.pclinuxos.com/index.php?option=com_ionfiles&Itemid=28[/COLOR]
This linux version is easy to install and automatically set it up the internet connection

---

### Post by trynet on 2007-10-19
I like ubuntu, its just frusturating that I can't set-up a connection on it.
I need an internet connection on it to get the latest drivers though,correct?
would the newest version actually help set up a connection? I don't have power ISO anymore and cannot burn anything on my other computer now, this is my mom's work computer so I can't install anything on this.
when I first looked to download, I thought the LTS and regular one were the same version.

---

### Post by trynet on 2007-10-19
please? I really am screwed if I can't get a connection

---

### Post by trynet on 2007-10-19
please? am I doing something wrong in the network settings?
I'm using a D-link router if it helps.

---

### Post by dhruva023 on 2007-10-19
please try to get the latest version.  i have the same wireless card.  it will recognize automatically and connected to internet.

if you can't download it. order it online only for i think 2 to 3 dollars.

also tell us where yo are from, if there is a local ubuntu user group out there , they will help you.

---

### Post by ugm6hr on 2007-10-19
The LTS is called Dapper - these links should help:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

Unfortunately, all the commands require a working internet connection.  

Since this is not the case, you would have to download all the relevant files, and then transfer manually prior to installing.  I have to go to work now, so can't explain how to do it at the moment, but, most have to be copied to "/var/cache/apt/archives" on your hard drive.

---

### Post by trynet on 2007-10-19
-_- I just upgraded...
still can't seem to connect
I'm entering my SSID in the network name box but cannot connect.

---

### Post by trynet on 2007-10-19
bump...please help

---

### Post by trynet on 2007-10-19
bump...please help

---

### Post by trynet on 2007-10-19
bump please

---

### Post by ugm6hr on 2007-10-20
Maybe start from the beginning....

Which version of Ubuntu are you using now?

What security does your wireless network use?

Do you "hide" your wireless SSID - if not - you should not have to enter it anywhere.

I believe that Ubuntu 7.10 will automatically install fwcutter driver, but only if you are already online via a non-wifi route.  Perhaps someone else can confirm this.

Either way - you can get connected.  You might just need to download some programs to install.

If you want to do your own research - search for BCM4318 in these forums, or in the ubuntu online documents.

---

### Post by justinmiller87 on 2007-10-20
What I said about a wired connection is when you take an RJ-45 Ethernet wire, stick it in the back of your computer, and then stick that in the back of your wireless router. I'm going on a wild guess is that you have to connect your wireless router to the Internet by some wired means or another, and most - if not all - wireless routers have ports on them with which you can connect a computer to it by an Ethernet cable. Go buy one if you don't have one and plug your computer into your router directly and you will be able to connect to the Internet through that. If you have the LTS, you're going to have to do three Distro upgrades to get to Gutsy and have your wireless card automatically found. Good luck with everything.

---

### Post by trynet on 2007-10-22
but my router is like all the way across the house...
I don't think I'll be able to get a long enough cable.

I'm using the newest one, I upgraded my LTS to the other one (7.10 I think it is)
it has no security at the moment.
no I don't

---

### Post by trynet on 2007-10-22
I'm installing the thing now (I've been using the live disk), I shouldda probbly partioned my 500 GB external drive -_-
I tried it on my 80 gig internal but I got an error.

---

### Post by trynet on 2007-10-22
bump...is their such a thing as an ethernet extention cord?

---

### Post by justinmiller87 on 2007-10-22
> **trynet said:**
> bump...is their such a thing as an ethernet extention cord?
The maximum length of an ethernet cable is 100 meters, or approximately 300 feet. If your house is that big, you might want to consider having your butler move your computer for you. I offered you a viable option to connect to the Internet, what's so difficult about moving your computer? You should at least move it there long enough to get the wireless working.

---

