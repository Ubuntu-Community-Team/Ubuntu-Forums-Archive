---
title: "wireless not working on iBook G4"
date: 2007-11-26
forum: Apple PPC Users
---

### Post by jmelton on 2007-11-26
I installed Feisty on my iBook G4 over the weekend.  I thought it was going to be fairly hassle-free since I was able to successfully resize my OS X partition using parted from the install CD, saving me a lot of time deleting and reinstalling OS X.  My ethernet connection worked fine, as did everything I've had time to check, except one small problem:  no wireless access.

So that's when the "fun" started--I have spent the better part of the last 2 days wrestling with my wireless connection, to no avail so far.  I'd really, really like to be able to run wireless in Linux as well as OS X, and I'm a relative newbie to Macs, so any help would be enormously appreciated.  I'd also like to hopefully help others avoid some of my mistakes!  :(  

A couple of important things to note about the Airport Extreme card used in a lot of late-vintage iBooks: it actually has a Broadcom 4318 chipset, as do a fair number of Intel (non-Mac) laptops.  This situation threw me for a loop, because a lot of the advice given about how to configure this fairly problematic type of wireless card for Linux just doesn't work on a PPC Mac.  For example, it's often recommended to install ndiswrapper, but that program won't work on pre-Intel Macs.  Generally that's the biggest problem I've run into with most of the sources I've found Googling around, is that it's often hard to tell if something someone suggests people try is even appropriate for a PPC laptop.

Anyway, where I am right now is as follows.  I've installed bcm43xx-fwcutter, used it to extract the firmware needed to run my card (from the AppleAirPort2 file taken off my Mac partition), and successfully loaded the bcm43xx module.  My wireless card was able to identify all of the wireless networks that are generally available in my neighborhood, including my own, but I wasn't able to establish a connection with any of them through Network Manager.  I also tried installing WICD and using that instead, but that didn't seem to help, so I went back to Network Manager.  I would be just fine with connecting my wireless from the command line and the hell with GUIs, but so far either I don't know what I'm doing well enough or I just can't get it to work (I tried).

So, some specific advice from someone who's gotten their G4 iBook wireless to work would be greatly appreciated.  What did you do to get it to work?  What do your /etc/network/interfaces and /etc/wpa_supplicant files look like? 

One problem I've discovered: Network Manager wouldn't allow me to enter my WPA passkey, but only WEP, which isn't the security I have on my wireless network (which, by the way, I can connect to just fine if I'm in OS X).  But I can't at this point access any wireless network, even an unsecured one.

---

### Post by kugn on 2007-11-27
Me thinks since your Network Manager can see wireless networks, there is no problem with your /etc/network/interfaces. As for connecting to them, have you tried the 'connect to other wireless networks' option and inputting the details manually? I use KNetworkManager, and clicking on any authenticated network doesn't open to box for me to put in the password, but resorting to the inputting all details manually works for me. I use WPA at home too, so there shouldn't be a problem.

---

### Post by guidop on 2007-11-27
When you tried Wicd, did you first remove network manager?

I think they might conflict if you have both installed.

I installed Wicd to work around the problem on my PowerBook running Xubuntu 7.04, and it worked for me.

The following steps worked for at least one other user:

Assuming you're using Ubuntu (Gnome desktop):

1 - Uninstall the gnome network-manager: sudo apt-get remove --purge network-manager (I think).
2 - The packages wireless-tools and wpasupplicant should already be installed by default, if not: sudo apt-get install wireless-tools wpasupplicant.
3 - Download the Wicd .deb file, I downloaded the stable version from here (you've apparently already done this plus step 4):
[https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")
4 - Double click on the .deb file and follow the prompts to install it. 
5 - There should then be a Wicd selection under your "Internet" or "Network" Menu (same menu you would find Firefox browser).
6 - Start Wicd, the GUI should be reasonably self-explanatory.

On my Powerbook, I'm running Xubuntu, so network-manager is not installed by default. My instructions above are an educated guess for what you would have to do under Gnome.


I don't know if it's still true, but Network Manager under _Feisty_ ppc has an endian (byte-order) problem that will prevent you from connecting to WPA networks:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857")
In my experience, knetworkmanager under Feisty ppc had the same problem, and seemed to override anything I tried to do by manually editing configuration files.

See these two posts for the source of the above:
[http://ubuntuforums.org/showpost.php?p=3459229]("http://ubuntuforums.org/showpost.php?p=3459229")
[http://ubuntuforums.org/showpost.php?p=3462779]("http://ubuntuforums.org/showpost.php?p=3462779")

---

### Post by Marius300482 on 2007-11-27
I had some problems to get a connection with the gnome-network manager too. Now I use "Wifi-radar" and it works fine! Never tried WPA but WEP.

---

### Post by jmelton on 2007-11-28
[QUOTE=guidop;3846499]When you tried Wicd, did you first remove network manager?

Yes, I did, and also removed wicd when I went back to trying Network Manager.

> I installed Wicd to work around the problem on my PowerBook running Xubuntu 7.04, and it worked for me.

Which problem?  Just not connecting?


> The following steps worked for at least one other user:

Assuming you're using Ubuntu (Gnome desktop):

1 - Uninstall the gnome network-manager: sudo apt-get remove --purge network-manager (I think).
2 - The packages wireless-tools and wpasupplicant should already be installed by default, if not: sudo apt-get install wireless-tools wpasupplicant.
3 - Download the Wicd .deb file, I downloaded the stable version from here (you've apparently already done this plus step 4):
[https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")
4 - Double click on the .deb file and follow the prompts to install it. 
5 - There should then be a Wicd selection under your "Internet" or "Network" Menu (same menu you would find Firefox browser).
6 - Start Wicd, the GUI should be reasonably self-explanatory.


I'll probably try wicd again unless I get something else to work first, but I think the above is pretty much what I did the first time.  Network Manager, as well as feedback from when I scan from the command line, shows all the local networks, but I can't connect to any of them whether they're encrypted or not even though it appears from output I receive when I enter the relevant commands that my wireless card picks up all the appropriate information about each network.  It just tells me "no DHCP offers received" and "sleeping" or something like that when I try to connect to a network from the command line.

---

### Post by guidop on 2007-11-28
Just reread your initial post again - you say you also can't connect to an _unencrypted_ network.

I have a Broadcom 4306 in my Powerbook - maybe that's why it works so easily in my case.

```
$ lspci | grep Bro
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"MyNetwork"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:01:02:03:04:05   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level=-38 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:14  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
$ sudo iwlist eth1 scanning
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:01:02:03:04:05
                    ESSID:"MyNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-41 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 80ms ago
          Cell 02 - Address: 00:01:02:03:04:06
                    ESSID:"MyNeighborsNetwork"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-80 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 2172ms ago

```

I assume that the above commands are similar to what you used to determine your card type and see available wireless networks.  If your output looked substantially different than the above, then there may be some additional troubleshooting steps to try.


I did find this comment and series of commands for configuring the Broadcom 4318 in this post by Larry Grover:
[http://ubuntuforums.org/showpost.php?p=1038069]("http://ubuntuforums.org/showpost.php?p=1038069")
> 
My laptop (iBook, G4) has a broadcom 4318 card. The lspci command
indicates that it is a "Broadcom Corporation BCM4318 [AirForce One 54g]
802.11g Wireless LAN Controller (rev 02)". I have been running the
dapper release since I got the laptop, about 3 months ago. It took a
bit of research/reading, and trial-and-error to get it working, and even
now, it does not work perfectly (more about this below), but it is
usable. Since my laptop is powerpc, not x86, ndiswrapper is not an
option. I went with the dapper development release so that I would get
the native linux broadcom driver.

The first thing you need to do is install the firmware for your wireless
card. I did this the hard way, by finding the right file from an OSX
install, running the bcm43xx-fwcutter program to extract and then
install the firmware. You can find instructions for installing the
firmware the easy way here:

[https://wiki.ubuntu.com/WifiDocs/Dri...%28broadcom%29]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Next, if you're lucky, the ubuntu gui network set up tools will work for
you, and you can just configure the card like you would any other
wireless network card. I wasn't lucky.

It seems that there are several variants of the broadcom chip (43xx).
Some seem to be easier to get working.

After lots or reading and trial-and-error, I figured out a set of manual
commands that would get my card working, and then I added them into my
/etc/network/interfaces file, so that the wireless network would come up
automatically when I boot. Here are the relevant lines:

```
iface eth1 inet manual
pre-up /sbin/modprobe bcm43xx
up /sbin/ifconfig eth1 up
post-up /bin/sleep 1
post-up /sbin/iwconfig eth1 rate 11M
post-up /sbin/iwconfig eth1 ap any
post-up /bin/sleep 1
post-up /sbin/dhclient eth1

auto eth1

```
On my system, the two "sleep" commands are essential, as are the
"iwconfig eth1 rate 11M" and "iwconfig eth1 ap any"; without them, my
card will not work at all.

I haven't tried to set up WEP or WPA. I don't know if they will work or
not. Also, the card stops working after a suspend/resume cycle. To
restart it I need to bring the interface down, remove the bcm43xx
module, re-insert the module and bring the interface back up. Kind of a
pain to do manually, so wrote a small script to automate this, which I
will be glad to share if you're interested.

If you haven't read this page yet:
[https://wiki.ubuntu.com/WifiDocs/Dri...%28broadcom%29]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
please do so now. It has more and better information than I have
provided here.

Regards,
Larry

I do hope something in the above helps, short of trying to find and buy an older Airport Extreme card which uses the Broadcom 4306 chipset.
- gp

---

### Post by jmelton on 2007-11-28
Thanks a lot!  In all the hours I spent searching for info. on getting this card going, that's one post I didn't come across.  I'll give it a try this afternoon and hopefully it will finally work.  

Even in OS X, this card doesn't exactly work great; no trouble getting connected (most of the time), but at least on encrypted networks the connection cuts out and I have to re-start the card whenever either the computer goes to sleep or I'm not surfing the 'net for a while.  Funny how Apple calls cards with these chipsets "Airport Extreme" like it's something special, when in fact it's basically the same crappy card that's in a lot of x86 laptops.  

Of course, that's one of the reasons figuring this out has been so confusing--most how-to's & threads on the Broadcom cards assume the user has an x86 laptop, so it's hard to figure out what does & doesn't apply to PPC.

---

### Post by jmelton on 2007-11-28
Alas, I tried the modifications to the interfaces file that worked for Larry Grover, and they didn't work for me.  I get some pretty inconsistent error messages, with there sometimes being an address listed for my router when I do iwconfig or scan and sometimes not.  Sometimes I get a message that my card is disabled or my eth1 interface does not exist; sometimes not.  I'm typing this from OS X so I can't check at the moment and be more exact about the feedback I got, but that's the gist of it.  I'm wondering whether there's something wrong with the installation of the firmware?  I don't know enough about Unix or wireless to know exactly why, but for whatever reason I can identify networks but not join them no matter which of the many configurations I've seen recommended I've tried.  This is getting just a wee bit frustrating!  :mad:

---

### Post by Lindarose84 on 2007-11-28
Ok so my response may not be as tech savvy as the others, but I have a Powerbook G4 that was giving me an absolute headache with wireless when I had Gutsy running on it. I needed to connect to my school's ultra secure network and couldn't. Network manager just stopped working all of a sudden and I couldn't get it back up and running. So I figured a downgrade to Fiesty would work and no it didn't. So as a hunch, I just cleaned out my entire linux partition and started from scratch and re-installed Gutsy and surprisingly, wireless (wpa and wpa2- both personal and enterprise) works great now. If all else fails I would recommend just doing a fresh re-install.

---

### Post by jmelton on 2007-11-29
> **Lindarose84 said:**
>  as a hunch, I just cleaned out my entire linux partition and started from scratch and re-installed Gutsy and surprisingly, wireless (wpa and wpa2- both personal and enterprise) works great now. If all else fails I would recommend just doing a fresh re-install.

That's a thought.  What kernel is your Gutsy running?  I've heard that the newest versions of the Linux kernel have a different, more up-to-date module for running Broadcom cards (b43 instead of bcm43xx) that presumably works better, but I don't know if Gutsy has a kernel with that module in it or not.  If you enter lsmod on the command line, does it show b43 or bcm43xx among your loaded modules?

Of course, the fact that your wireless wasn't working in Gutsy or Feisty but suddenly did when you re-installed Gutsy isn't explained by any of this, or anything else that I can think of!  :)

Since you have the same laptop as I do, I was wondering if I could find out a few more details about the way things are set up for your wireless now that it's working.  What files are there in your /lib/firmware directory?  What's in your /etc/network/interfaces and /etc/wpa_supplicant files?  Thanks!

---

### Post by Lindarose84 on 2007-11-29
Ok so I ran lsmod and it shows that I am utilizing the bcm43xx firmware- the strange thing is that before upgrading to gutsy the second time, I manually downloaded this firmware and loaded it in Feisty but my wireless was still a no-go. So I have absolutely no clue what the upgrade did to my wireless files to get them finally working. I didn't do anything after upgrading. The minute I rebooted for the first time into Gutsy, network manager immediately connected to my wpa wireless network. I'd be happy to let you know what kernel I was using if I knew how to get that info (all I know is that I did the update manager upgrade to Gutsy so I am assuming I have the latest kernel).

As for what files are in my lib/firmware directory, I've attached a screenshot with the filenames. 

Here's what's in the etc/network/interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp



And here is what is in my wpa_supplicant directory (there was no file in etc):

"ifupdown.sh" and "functions.sh"



Hope this helps!

---

### Post by guidop on 2007-12-01
I'm just making a guess here, but this page:

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Seems to say that the 4318 card needs the new b43 driver and version 4 firmware.

The only way I can think to try this is to compile a the newer b43 support into a recent kernel, or use the latest 2.6.24-rc3 kernel, which you may have to compile for ubuntu ppc to get other hardware to work on your Apple laptop anyway...

There is also some additional discussion in this thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=600097]("http://ohioloco.ubuntuforums.org/showthread.php?t=600097")

All I can think of is that while the bcm43xx driver and firmware work to let your 4318 see wireless networks, somehow the card is not compatible with the wireless stack in the Feisty kernel.

-gp

To answer your earlier question regarding Wicd.  
Prior to trying Wicd:
- I used bcm43xx-fwcutter to install the firmware
- Typing "sudo iwlist eth1 scanning" in a terminal showed the available (unmasked ESSID) wireless networks.
- Knetworkmanager under Feisty let me connect to my network when I tested it _unsecured_, but would not work when I set my network to use WPA.   
- Wicd _only_ solved the WPA problem for me.

---

### Post by jmelton on 2007-12-01
Thanks much for the info!  

I think the command for identifying the kernel version is uname -r (or maybe it's uname -v, or either--not in Linux at the moment).  

It's interesting that your interfaces file doesn't mention eth0 (which seems to be the default wired interface on our machines), but does have a bit of configuration info. for eth1 (the wireless).  There appear to be a number of different ways of doing wireless that have worked for some people with this machine, but for some reason none of them I've tried so far have worked for me.  :confused:

I'm thinking of following in your footsteps and upgrading to Gutsy and seeing what happens.  I understand that the kernel that comes with Gutsy at least has an updated version of the bcm43xx module that works a little better.  If that doesn't work, upgrading the kernel to one that uses the new b43 module as suggested by the comment below sounds like a good idea.  Hopefully I'll have wireless working soon!  

> **Lindarose84 said:**
> Ok so I ran lsmod and it shows that I am utilizing the bcm43xx firmware- the strange thing is that before upgrading to gutsy the second time, I manually downloaded this firmware and loaded it in Feisty but my wireless was still a no-go. So I have absolutely no clue what the upgrade did to my wireless files to get them finally working. I didn't do anything after upgrading. The minute I rebooted for the first time into Gutsy, network manager immediately connected to my wpa wireless network. I'd be happy to let you know what kernel I was using if I knew how to get that info (all I know is that I did the update manager upgrade to Gutsy so I am assuming I have the latest kernel)...


---

### Post by jmelton on 2007-12-01
> **guidop said:**
> I'm just making a guess here, but this page:

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Seems to say that the 4318 card needs the new b43 driver and version 4 firmware.

The only way I can think to try this is to compile a the newer b43 support into a recent kernel, or use the latest 2.6.24-rc3 kernel, which you may have to compile for ubuntu ppc to get other hardware to work on your Apple laptop anyway....

I wouldn't think I'd have to have a kernel with the b43 module in it since others with an iBook G4 and the 4318 card have gotten things to work with bcm43xx, but if something like simply upgrading to Gutsy doesn't work for me, yeah, upgrading to a kernel with the b43 module in it sounds like a logical next step.  Thanks for the links & info.

---

### Post by VCSkier on 2007-12-06
Where can I find help regarding how to install a kernel with the b43 module in it?  A flaky wireless connection is the only thing that is keeping me from switching my wife's computer over to Ubuntu (or maybe Linux Mint).

---

### Post by jmelton on 2007-12-11
> **VCSkier said:**
> Where can I find help regarding how to install a kernel with the b43 module in it?  A flaky wireless connection is the only thing that is keeping me from switching my wife's computer over to Ubuntu (or maybe Linux Mint).

Reading this might be a good place to start:
[http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

---

