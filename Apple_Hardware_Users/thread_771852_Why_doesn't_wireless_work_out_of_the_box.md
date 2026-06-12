---
title: "Why doesn't wireless work out of the box?"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by wootwoot123 on 2008-04-28
Madwifi is included in the 2.6.24 kernel so why does it not work out of the box on a 2nd gen macbook? I am getting so frustrated with my macbook and the crappy linux wifi support that I am very close to buying a laptop that has the right components to run OSX and linux flawlessly. This may not be 100% legit but the situation here is ridiculous. I have tried installing from svn but I am still not able to get this working. Why is this wireless chipset such a piece and how can I definitively make it work?

---

### Post by GeneralSunTzu on 2008-04-28
> **wootwoot123 said:**
> Madwifi is included in the 2.6.24 kernel so why does it not work out of the box on a 2nd gen macbook? I am getting so frustrated with my macbook and the crappy linux wifi support that I am very close to buying a laptop that has the right components to run OSX and linux flawlessly. This may not be 100% legit but the situation here is ridiculous. I have tried installing from svn but I am still not able to get this working. Why is this wireless chipset such a piece and how can I definitively make it work?

Whoa, don't get mad.
First responsible are the Atheros twits, who have no open source driver for their pathetic cards, not exactly ultra-high tech.
Second, as in many FOSS projects, after a while people lose interest and move on to a variant of the original project (madwifi), dropping the old one and apparently incapable of realising that many people rely on that.
So please don't take it against the good Canonical (Ubuntu) people.

Now, as to solve your problem, given the bewildering combination of card models, the stupidity of Apple who keeps calling the machines with the same name when they actually have a very different hardware, in order to allow more experienced gurus than myself, like cyberdork, or perhaps even myself, to assist you, we need to know:

1. card model (to find out, issue sudo lspci under ubuntu-it is not necessary to be connected to the internet);
2. precisely the Macbook model (to find out, About this Mac under OS X, then More info, and finally what we are looking for is the 'Model identifier';
3. whether you got cabled ethernet access to the internet or not;
4. which way were you trying to install (upgrade, Live CD or Alternate CD)?

Please supply these data and somebody will try to assist, if not me.

---

### Post by cyberdork33 on 2008-04-28
> **GeneralSunTzu said:**
> First responsible are the Atheros twits, who have no open source driver for their pathetic cards, not exactly ultra-high tech.
In their defense, a fully open driver is out there, it just doesn't yet include support for these cards, so we are stuck with the older madwifi until it is added. see [ath5k]("http://madwifi.org/wiki/About/ath5k")

The main reason is that support for the Airport cards has never been included in a full release of madwifi, only the developmental versions have, thus you must get one of those and compile. Ubuntu uses the stable and tested versions on madwifi, and this version only supports the 1st gen Macbook (Pros).

---

### Post by russo.mic on 2008-04-28
May I recommend you consider ndiswrapper for the atheros card?  I have only ever been able to get mad-wifi to compile under 64 bit for some crazy reason (usually that is more of a pain).  Even when I got it working, it dropped out on me many times.

I guess the perception around these parts is that madwifi is the prefered method,  maybe because it's fully open source?  IDK.  But ndiswrapper has treated me quite kindly.  Seems reliable, and WEP seems to always work okay, the few times i've had to make that work.

Russo

---

### Post by cyberdork33 on 2008-04-28
> **russo.mic said:**
> I guess the perception around these parts is that madwifi is the prefered method,  maybe because it's fully open source?  IDK.  But ndiswrapper has treated me quite kindly.  Seems reliable, and WEP seems to always work okay, the few times i've had to make that work.

Actually, the viewpoint can be quite the opposite... ndiswrapper is known to be buggy, and prone to drop connections... 

madwifi is preferred because it is the "most" open source, but do what works best for you.

---

### Post by Hatfield on 2008-04-28
Wireless is the red-headed step child for 2nd gen MacBooks.
I had it up and running in 7.04.  Upgraded to 7.10 and lost it never to get it.  Now a clean install of 8.04 has proven elusive.

I can totally understand some getting frustrated.  I have patches of bald spots from ripping my hair out.:lolflag:

---

### Post by Pc_Madness on 2008-04-29
> **GeneralSunTzu said:**
> 
1. ...
2. ...
3. ...
4. ...


Sorry to hijack, but I'm in the same situation. :(

1. 02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
2. Macbook2,1
3. Yep
4. Fresh install with the LiveCD.

Any help would be much appreciated. :)

Edit: Yeah, I was in exactly the same situation Hatfield. :p I kinda assumed that after I got it running on 7.04 that 7.10 would include the necessary fixes to get it working out of the box.. but apparently not. Enter 8.04 and still nothing. :(

---

### Post by cyberdork33 on 2008-04-29
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

---

### Post by wootwoot123 on 2008-05-01
> **GeneralSunTzu said:**
> 

1. card model (to find out, issue sudo lspci under ubuntu-it is not necessary to be connected to the internet);
2. precisely the Macbook model (to find out, About this Mac under OS X, then More info, and finally what we are looking for is the 'Model identifier';
3. whether you got cabled ethernet access to the internet or not;
4. which way were you trying to install (upgrade, Live CD or Alternate CD)?



1. AR5418
2. Model Identifier:	MacBook2,1
3. yes I have cabled ethernet access to the internet
4. I installed from the Live CD 64 bit.

---

### Post by GeneralSunTzu on 2008-05-01
> **wootwoot123 said:**
> 1. AR5418
2. Model Identifier:	MacBook2,1
3. yes I have cabled ethernet access to the internet
4. I installed from the Live CD 64 bit.

All right. Now we are in business.
I will lead you through two operations:
a. install the right madwifi driver (not obvious...);
b. replace the NM-applet with wicd, far better.

Other than for the Mac Model, we are in the same situation (Atheros card, etc.), so most of what applies to me should apply to you.

First of all, ensure you are cable connected to the internet and that you have access (Firefox will do).

Then, to be on the safe side, issue in terminal:
sudo update

Installing now the right madwifi driver.

Issue in terminal:
sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi -r3403
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local

The instructions are taken from the MacBook Pro wiki, as the MacBook wiki is incorrect for Atheros cards.

While still connected to the internet via cable, please continue as follows.

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. 
Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. 
Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.
In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

Now reboot and you should see, top right, wicd.
It should work without additional voodoo, now.

Disclaimer: rather than linking to URLs which might screw up (as happened to me many times...), I have quoted their text and adapted it, so that you only need two windows to install.
One to see these instructions and one for a terminal window.

Good luck, buddy - please report back!

---

### Post by wootwoot123 on 2008-05-03
I followed your instructions to a T and now I do have wireless and am connected to my network but I have no dns resolution.

---

### Post by GeneralSunTzu on 2008-05-03
> **wootwoot123 said:**
> I followed your instructions to a T and now I do have wireless and am connected to my network but I have no dns resolution.

How do you know? 
Please paste also the output of the following terminal commands:

sudo route -n
sudo iwconfig
sudo ifconfig

These commands ascertain whether there is a DNS visible somewhere, plus the status of all interfaces, including ath0, the Atheros card interface.

---

### Post by eddietours on 2008-05-05
wow you got just rock:guitar: finally my wireless works thanks to all

---

### Post by tonymoyoy on 2008-05-07
i had a problem with the svn download because i was behind a proxy. solved.

and now i have wireless. 

Wicd is nice

gracias.

---

### Post by suchawato on 2008-05-07
Same issue, except, a direct connection deosnt work either.
Seems to think the network is "secure"
I am almost done with all this open source stuff.
I want my hardware to work.
I don't care if the source is open or not.
I want it to work.

---

### Post by cyberdork33 on 2008-05-07
> **suchawato said:**
> Seems to think the network is "secure"
This sounds like you are trying to connect via WiFi. If this is a message that you are getting connecting over the wire, then you need to check the settings of your network.

---

### Post by ringostar on 2008-07-12
Youhou my wifi works thanks to this post !
Thank you GeneralSunTzu

I searched a lot for this solution.
I've still never seen the 3 lines with sed !
Maybe this must be in the Macbook documentation ? Something like : if you have the Atheros 5418 card, see the Macbook Pro tutorial.

---

### Post by guzzos on 2008-07-13
I wonder if this solution will work on a Macbook 4,1 which has the broadcom 43xx wireless card.

---

### Post by cyberdork33 on 2008-07-15
> **guzzos said:**
> I wonder if this solution will work on a Macbook 4,1 which has the broadcom 43xx wireless card.
no. madwifi is for atheros chipsets only. For your Mac, you need to use ndiswrapper.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup]("https://wiki.ubuntu.com/MacBookPro/Penryn#head-e5409d2a7a72b4cec1c51303bb2247a83a5659dc")

---

### Post by RAgrella on 2008-07-24
Has anyone been able to get the wireless working with madwifi on a MBP like the following

MacBookPro 3,1
Ubuntu 8.04.1 (kernel 2.6.24-19)
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

I followed the writeup by GeneralSunTzu and i can see that the wireless is picking up signals but i am not able to get a DHCP address from any wireless networks. Any thoughts?

---

### Post by Diggs808 on 2008-07-25
OH MY GOODNESS!!!!  

IT WORKED!

sorry for the shouting...I am just happy that this worked!!!!

---

### Post by GeneralSunTzu on 2008-07-26
> **RAgrella said:**
> Has anyone been able to get the wireless working with madwifi on a MBP like the following

MacBookPro 3,1
Ubuntu 8.04.1 (kernel 2.6.24-19)
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

I followed the writeup by GeneralSunTzu and i can see that the wireless is picking up signals but i am not able to get a DHCP address from any wireless networks. Any thoughts?

You better be more specific.
The WiFi network you wish to hop on, has which security?
None, WEP, WPA Personal, what?
Have you tried getting into Wicd and setting the preferences right, so that it will, upon boot, try to get onto that network?
If not, please do so.
Also, please describe your WiFi router: is it an Apple device or not?

---

### Post by GhettoYhetti on 2008-07-27
GeneralSunTzu:

Sorry to "hitch a ride" on this thread, but I am in the same boat as well . .. and just for good measure I am unable to get X going (in ubuntu hardy, xubuntu 6.10 I can get X but no wireless access)

1. Will post in a few minutes . . . have to boot from CD to find out.
2.  
  Machine Model:    PowerBook G4
  CPU Type:    PowerPC G4  (2.1)
  Number Of CPUs:    1
  CPU Speed:    667 MHz
  L2 Cache (per CPU):    256 KB
  Memory:    512 MB
  Bus Speed:    133 MHz
  Boot ROM Version:    4.2.9f1

3. Wireless access to the net only
4. LiveCD

---

### Post by GeneralSunTzu on 2008-07-27
> **GhettoYhetti said:**
> GeneralSunTzu:

Sorry to "hitch a ride" on this thread, but I am in the same boat as well . .. and just for good measure I am unable to get X going (in ubuntu hardy, xubuntu 6.10 I can get X but no wireless access)

1. Will post in a few minutes . . . have to boot from CD to find out.
2.  
  Machine Model:    PowerBook G4
  CPU Type:    PowerPC G4  (2.1)
  

Pal, not that I do not want to help, but we are dealing in this thread with MacBook Pro or Macbook computers, both with Intel CPUs, not PowerPC.
Adding to that that I believe PowerPC-based computers are not officially supported by 8.04, I do not have enough expertise to assist.
So sorry.

---

### Post by GhettoYhetti on 2008-07-27
Oops . . .  sorta missed that.  Thanks.

---

### Post by BasiliusCarver on 2008-07-29
I have a MacBookPro 3,1.
Ubuntu 8.04.1.
Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter.
I don't have access to wired net as everything at the Uni I'm at has wireless.
Is this an issue or is it easy enough to download the files needed while I'm booted in Leopard and use the same instructions as in this thread omitting the download steps, although I figure if I'm skipping the downloading parts I'll have to enter more instruction on where to find the files it needs while I'm in the terminal..
Am I on the right track or completely lost? haha.

---

### Post by cyberdork33 on 2008-07-29
> **beatbophiphop@gmail.com said:**
> I have a MacBookPro 3,1.
Ubuntu 8.04.1.
Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter.
I don't have access to wired net as everything at the Uni I'm at has wireless.
Is this an issue or is it easy enough to download the files needed while I'm booted in Leopard and use the same instructions as in this thread omitting the download steps, although I figure if I'm skipping the downloading parts I'll have to enter more instruction on where to find the files it needs while I'm in the terminal..
Am I on the right track or completely lost? haha.
you will need to download the madwifi source as instructed in the wiki page and get it onto your Ubuntu system somehow. You can use the cdrom as a source for other packages required to compile that. such as the build-essential package. To do this, I think you only need to put the Ubuntu CD in the drive and run:```
sudo apt-cdrom add
```

Then any future apt commands will try to use the packages on the CDROM.

```
sudo apt-get install build-essential
```

---

### Post by BasiliusCarver on 2008-07-30
thanks for that cyberdork. I have an issue though because I can connect to my wireless network but in the network settings when setting up a PPPoE connection to connect to the internet I can only select eth0 as the place to connect through, in mac when creating one it says 'ethernet: ethernet or airport' but I can only choose ethernet in ubuntu. would installing wicd help? Remembering I still have no form of internet and I have tried to install wicd without it but can't figure it out.

---

### Post by cyberdork33 on 2008-07-30
I have never had to use PPPoE so I have no idea.

---

### Post by BasiliusCarver on 2008-07-30
I'm posting this from ubuntu so what I did worked. typing pppoeconf into the terminal brought up a simple gui which asked questions and set up my pppoe for me.

---

### Post by cyberdork33 on 2008-07-31
> **beatbophiphop@gmail.com said:**
> I'm posting this from ubuntu so what I did worked. typing pppoeconf into the terminal brought up a simple gui which asked questions and set up my pppoe for me.
Good hint.

PS You might want to PM an Admin and get them to change your username to avoid getting spam.

---

### Post by Diggs808 on 2008-07-31
Okay....

So I used this the other day to get my wireless working.  Thanks BTW!

However I now have another problem.  When I updated the Kernel via automatic updates I can no longer connect to WIFI.  I would stick with the older kernel however a realy frustrating screen flicker problem on my external monitor got fixed with the 2.6.24-20-generic kernel.  The one that worked was 2.6.24-19-generic.

When I try to scan for a wireless network (using either WICD or command line) my entire system locks up and I have to hard boot the computer.  :-(

Apple MacBook 2,1
Ubuntu Hardy 

I have recompiled the program using make and make install.  I am now confused and scratching my head....Can someone help a fella out??

---

### Post by Diggs808 on 2008-07-31
Okay...scratch this....my stupidity.  Got it working.

---

