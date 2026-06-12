---
title: "Trying to get Netgear WG311v3 to work."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by crazy757 on 2007-05-11
I am a very newbie.  I am probably more of a newbie than anyone else on this entire forum.  I have tried to install ndiswrapper onto my Ubuntu Linux 7.04 but have tried everything but it seems everyone has their own way of inputting codes into the terminal to do the same things.  I have seen lots of posts on making sure I have a certain Linux kernel and I don't understand that either.  I do not have access through the internet with Ubuntu Linux but when I get online.  I disconnect the IDE hard drive with Ubuntu installed on it and replug the SATA Raid 0 hard drives that contain Windows, so switching between the two are irritating.  WHen I download files, I burn them on disks and then switch again just to find out I don't know what in the world I am doing at all.  Ubuntu claims ndiswrapper is on the installation disk, but when I add the cd to the synaptic manager, ndiswrapper-utils is not listed, so I burned it onto a disk via internet and moved it to the Ubuntu along with ndiswrapper-1.43 just in case.  I also put on the disk ndisgtk so I will have a more friendly way of installing my wireless card.  I clicked on that first, on Ubutu and it said it was reliant on ndiswrapper.  That's more useful than the crazy codes I tried to input in terminal before.  Then I clicked on ndiswrapper-utils_1.1 and it said it was reliant on ndiswrapper-modules_1.1.  So, now I did a search for that and have found lots of forums that it is mentioned and it mentions it is included in a package of some sort.  Not sure which one.  Is it in the 1.43 compilation file I have previously downloaded?  I really don't know.  So, that is my story.  Ha, ha.  Maybe somebody will see how incredibly lost I am and help me.  Thanks.

---

### Post by dstew on 2007-05-11
You need to use Windows to download the debian package for [ndiswrapper from the Debian site]("http://packages.debian.org/testing/misc/ndiswrapper-utils") onto a disk, then transfer the package to your home or desktop directory in Ubuntu. Once the debian package is there, install it with the command:```
sudo dpkg -i ndiswrapper-utils-1.1_1.1-5_i386.deb
```

EDIT: It might be better to download debian packages from the [Ubuntu site]("http://packages.ubuntulinux.org/feisty/misc/ndiswrapper-utils-1.9"). If you get it there, use```
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
```You can also download the ndiswrapper-common package from the same site.

---

### Post by crazy757 on 2007-05-11
I saw that you had i386 at the end of your command.  I forgot to mention that my ubuntu is for the amd64, so would I enter it the same and replace i386 with amd64?

---

### Post by cajunaggie on 2007-05-11
I'm having issues with NetGear WG311T card as well. My computer is running a NetGear ethernet card and a NetGear WG311T. I did a fresh install for Feisty and the ethernet card works just fine.

When I go to System>Administration>Network, I see a configured wired connection but no option for a wireless connection. According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") page my card should work "out of the box." I tried "ifup ath0" (the previous title of my card) and got a reply telling me there was no such device. 

My etc/network/interfaces file looks like this:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

Suggestions?

---

### Post by dstew on 2007-05-11
Yes, you need to download the amd64 packages and install them. They are on the same pages as the i386 packages. The command would be:```
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb
``` for the ndiswrapper-utils package.

In fact, you can install any Ubuntu package this way. All the Ubuntu debian packages (essentially all the software) are available on the Ubuntu packages site for download and installation. This is good, because sometimes you can't get your internet working without some of this software.

---

### Post by dstew on 2007-05-11
Cajunaggie:

Try **ifup wlan0**

---

### Post by crazy757 on 2007-05-11
Thanks, dstew, but it still did not work.  This is the error I got.  Do you know what may be wrong.

Error:  dpkg: error processing ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb (--install)
:
cannot access archive: No such file or directory
Errors encountered while processing: ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb

To make sure there was nothing wrong with my os installation, I reinstalled it and then it still gave me the same answer.  Am I still missing a file.  I deleted all files but the two you recommended.  They were the Ndiswrapper-utils one and the Ndiswrapper-source one.  If it is of greater help, when I double click the utils one, it says it needs Ndiswrapper-common or something like that.  I looked on my add/remove programs after reinstalling and there is a program called Windows Wireless Drivers, but since I am not connected to the internet it does not download it.  Sigh.

---

### Post by cajunaggie on 2007-05-11
> **dstew said:**
> Cajunaggie:

Try **ifup wlan0**

I tried that. I'm getting the same no device response. I've also tried taking out the "auto [device name]" above the various devices (one at a time) to see if that does anything, but so far nothing.

---

### Post by cajunaggie on 2007-05-11
I figured it out. For whatever reason the ethernet card is keeping the wireless card from showing up. I remove the ethernet card and, presto, the wireless card exists again.

---

### Post by dstew on 2007-05-11
crazy757: Please post all the messages that show up when you try to install the package. Also, I did not recommend installing the source package. You only need the -utils and the -common packages. Maybe you need to install the -common package first.

---

### Post by crazy757 on 2007-05-13
Great!  Whew!  I finally got Ndiswrapper installed and I even have the graphical interface working on it.  Now, here comes another chapter in this quest...Does anyone know what amd 64 drivers will work on the amd64 version of Ubuntu?

---

### Post by nonewmsgs on 2007-05-13
what do you mean?  all my drivers work and im in x64, but most people say that i386 is easier.

---

### Post by crazy757 on 2007-05-14
I have read on this site that the 32-bit versions of wireless card drivers do not work on an AMD 64 version of ubuntu.  This is what kind of wireless card I have according to the lspci command:
Ethernet controller:  Marvell Technology Group Ltd. 88w8335 [Lisertas] 80 2.11b/g Wireless (rev03).  What driver will work on the AMD 64 version of Ubuntu for this card?

---

