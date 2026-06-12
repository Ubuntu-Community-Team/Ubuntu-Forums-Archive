---
title: "Airport wireless card drivers"
date: 2011-03-09
forum: Apple Hardware Users
---

### Post by spiky001 on 2011-03-09
I posted here [http://ubuntuforums.org/showthread.php?t=1681984](http://ubuntuforums.org/showthread.php?t=1681984) about the wireless card in my Ibook, I,m still looking for help on getting it running correctly any help plz

---

### Post by linuxopjemac on 2011-03-09
install firmware-linux-nonfree

---

### Post by spiky001 on 2011-03-10
Thks for reply linuxopjemac made no difference. But it did add to another problem I have with reportories here [http://ubuntuforums.org/showthread.php?t=1702180](http://ubuntuforums.org/showthread.php?t=1702180) Maybe this is contributing to the problem, as it also gave a 404 error for firmware-linux-nonfree. Anyway to correct these 404 problems?

---

### Post by snafu006 on 2011-03-10
hey follow this post [http://ubuntuforums.org/showthread.php?t=1676488](http://ubuntuforums.org/showthread.php?t=1676488) some guy posted on my thread saying he got his Ibook wirless to work.

---

### Post by snafu006 on 2011-03-10
DO this if you downloaded the drivers all you need to do is this and it will get you on the net.

sudo aptitude install wicd

Follow the instructions. Next, 

sudo aptitude remove network-manager

Follow the instructions.

Next, open up WICD which should be in your applications area, find your network, click properties and enter the password in. Click connect.
__________________

---

### Post by rsavage on 2011-03-10
There is plenty of information on this forum and the net.  Try doing a google search on the forum instead of using the built in search facility as I've found you get more results.

G3 installation is described in this blog: [http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/](http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/)

The same person has posted advice on the mintppc forum: [http://mintppc.org/forums/viewforum.php?f=10&sid=6e074fab26c9ad699babe836b3f77db9](http://mintppc.org/forums/viewforum.php?f=10&sid=6e074fab26c9ad699babe836b3f77db9)

---

### Post by rsavage on 2011-03-10
snafu006 you informed me that the gnome network manager didn't work with you, but wicd did?  Are you using airport classic?  I don't understand why one program could work, but another can't.  Presumably they use the same driver?  Are you using wpa?  It would be good to get the bottom of this for the benefit of others.  The FAQ could then be updated as answers/solutions are all over the place on this forum.

---

### Post by snafu006 on 2011-03-10
Ya on my Imac g3 the classic airport card was not not working with the other wireless manager. So i looked around for a bit and found that install wicd and uninstalling the defalt wireless manager would allow me to connect to the net and yes it works with wpa1-2 and wep. 

 So give it a shoot.

---

### Post by rsavage on 2011-03-10
snafu006, what I wanted to know was have you tried the default network manager after trying wicd? Your private message to me implied that you had, but now I am not so sure?  Wicd gives you the option to join the "netdev" group when you install it.  As far as I am aware this is why you are seeing wifi working using wicd.  You should be able to get the default network manager to work after installing wicd because you are now part of the netdev group.  I have posted an easier way to join "netdev" on your thread.

I don't have any experience with airport classic, but reading stuff on here and mintppc I am led to believe that you have to download some updated drivers to get wpa.  Have you done this?  If this is not the case then that maybe of some use to people.  Maybe this is the reason why mintppc are having such problems?  They have scripts that automatically update their drivers and perhaps they really shouldn't afterall.

---

### Post by barbaGNU on 2011-03-10
here there is an usefull howto (altough for a different distro):
[http://cruxppc.org/Airport](http://cruxppc.org/Airport)


c u,

---

### Post by snafu006 on 2011-03-10
> **rsavage said:**
> snafu006, what I wanted to know was have you tried the default network manager after trying wicd? Your private message to me implied that you had, but now I am not so sure?  Wicd gives you the option to join the "netdev" group when you install it.  As far as I am aware this is why you are seeing wifi working using wicd.  You should be able to get the default network manager to work after installing wicd because you are now part of the netdev group.  I have posted an easier way to join "netdev" on your thread.

I don't have any experience with airport classic, but reading stuff on here and mintppc I am led to believe that you have to download some updated drivers to get wpa.  Have you done this?  If this is not the case then that maybe of some use to people.  Maybe this is the reason why mintppc are having such problems?  They have scripts that automatically update their drivers and perhaps they really shouldn't afterall.

Yea i try the defalt wireless manage after i installed wicd but it would not allow me to connect to the SSID. Now see thats why this guy need to try it your why. Because he has a ibook not imac g3. Now form what i know is that the wicd will help the info for the netdev properties so you can join your wireless network. What he need to do is.

If he can see the wireless network.

Install the wicd after that if he can join the network uninstall the wicd and see if the defalt wireless manager will work.

---

### Post by spiky001 on 2011-03-11
My problem seems to be with drivers, LSPCI dosn't show any wireless device, Network manager dosn't show any wireless devices in the area. Occasonally it dose shows wireless connections in area but is very hit and miss!! I have updated and tried hardware devices none installed on this system. Hence my link to [http://ubuntuforums.org/showthread.php?t=1702180](http://ubuntuforums.org/showthread.php?t=1702180) where I have problems with respotoies. Even if I do get Network Manager to show networks LSPCI still dosn't show a device on Ibook

---

### Post by rsavage on 2011-03-11
You may find your answer on this post [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143) that I've just written.  It is basic things that everybody needs to do IMHO.  Have you followed any of the advice that has already been given to you e.g. trying out wicd?  If network manager is showing connections (albeit occasionally) then surely the driver is loaded.  Have you right clicked on the applet and made sure wireless/networking is enabled?  Has some fix that you've found on some random forum caused your problem?  What steps have you taken? I shall find my repository list for you.  Hold on....

---

### Post by rsavage on 2011-03-11
My  /etc/apt/sources.list .....

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (20100428)]/ lucid main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security main restricted
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security universe
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid-security multiverse

---

### Post by spiky001 on 2011-03-12
Ok an update so far. Used your sources list rsavage cured resportories problem even network manager started up, but still wont connect. Followed your other advice [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143)   I have never got wicd to connect to an ad hoc (WEP) connection even when using Back Track on another laptop ( Bad Password )    But I did install wicd so as to try all possibilites but no go. I did check iwconfig eth1 frequency is wrong it should be  2.412 which is channel 1. My frequency is set to 2.422 ghz I cant get it to change. The network card dose work because iwlist scan lists networks.    So the problem is channel selection. I tried from terminal to stop eth1 then restart in channel1 but it will not let me.

---

### Post by rsavage on 2011-03-12
I'm currently updating that thread as I have found new info, but I think your problems are beyond my capabilities.  There is a lot of information out there.  You are just going to have to plough through it.  I can't help thinking though that you've done something that you really shouldn't have done.  There is a lot of bad advice out there.

---

### Post by rsavage on 2011-03-12
Don't know if the information in [http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco) means anything to you.  See the known issues section.

I thought you had wireless working at one point?  I thought the problem was you just lost it on shutdown if you didn't log out first?  Is this still the case?

Wicd needs the agere_sta_fw.bin file.  Was this is place when you tried it?

---

### Post by spiky001 on 2011-03-12
I did have it working as said when I 1st loaded the system then I updated had problems with reps, As wireless was tempremental I used cable. As It was 1st time I had updated I thought I would see how wireless was working and here I am. I have not tried any fixes for wireless until now, I think I have the bug to fix it.

---

### Post by rsavage on 2011-03-12
snafu006, can you tell me if you have the package linux-firmware-nonfree installed?  I am trying to work out if this is necessary.  I am wondering if this is bringing in corrupted versions of files.

Also, the output of 

~$ dmesg | grep airport

and 

~$ dmesg | grep b43

and

~$ ls /lib/firmware/agere*

and 

~$ groups

please! Thanks!

---

### Post by rsavage on 2011-03-12
Linuxopjemac, if you have time could you cast your eye over this thread [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143).  I've tried to pull together all the different workarounds and have been updating the thread this evening so it may have changed since you read it.  I would value your opinion.

Btw, is this the bug that is causing you problems in MintPPC? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/715438)
[U]

[/U]

---

### Post by linuxopjemac on 2011-03-13
It seems that this bug is affecting the Airport Classic users. There are others with Airport Extreme cards which get the "bad password" error in wicd no matter what they try. This is another bug:
[https://bugs.launchpad.net/wicd/+bug/594676](https://bugs.launchpad.net/wicd/+bug/594676)
[http://ubuntuforums.org/showthread.php?t=1595106](http://ubuntuforums.org/showthread.php?t=1595106)
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)
etc etc

It's driving me nuts. It makes Linux not very useful on laptops.

PS I like the FAQ you put up, if it's working for everyone facing these problems I don't know.

---

### Post by spiky001 on 2011-03-13
I spent all night with my friend google I also found that usig this card for adhoc is not possible or at least the reports I found. So maybe a replacement card is in order. Maybe someone will get a fix for it someday.

---

### Post by snafu006 on 2011-03-13
hey did you install b43 fwcutter drivers i remember i installed that and yes i have linux-firmware-nonfree installed as well. I am not at me imac right now but when i get to it ill look at every think i did.

---

### Post by snafu006 on 2011-03-13
Oh and what wireless router do you have please tell me you have a linksys54g the old blue and black ones.

---

### Post by spiky001 on 2011-03-14
No router I have adhoc set up with main pc, as I said earlier maybe the card cant do adhoc connections, Hope some one can prove it wrong but hey ho

---

### Post by rsavage on 2011-03-14
I assume you and google have found this document [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) ?  It includes manual setup.

On the orinoco page (the link I posted before) it says that ad hoc is supported.  I would always take the advice of an official publication over forum gossip.

Since you don't want to use wicd I would:

install network manager
remove wicd
remove the agere files since you only want to use wep
reboot 

This should bring you back to the situation where you can connect and only lose it if you shutdown before logging out?  Am I correct?  This seems a liveable with situation.  You could probably write some script though that automates logout?  It must be possible, but don't ask me how!

Manually setting up the ad hoc connection also seems a possibility to me.  See the example at the bottom of the ad hoc page for a script to automate this.

I assume you have checked your hardware over like the aerial is inserted correctly/far enough into the card?  It has been known.

If you type "dmesg | grep airport" at a terminal you will get details of firmware and what is supported by the card.  You should see two messages about ad hoc.

---

