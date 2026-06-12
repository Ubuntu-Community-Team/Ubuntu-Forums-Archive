---
title: "Ubuntu 10.04 iBook G3 wifi help"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by WackyRicanMan on 2010-05-04
I have a iBook G3 Dual USB with 600mhz/640mb/80gb

I installed Debian 5.0 (lenny) and it ran great wifi worked and everything. I had a problem with Mozilla and the browsers started not working so I just installed Ubuntu 10.04. 

I love it, the only problem I have is that my WIFI isn't connecting to my network, so I'm connected via eithernet right now. 

Networks show up so I assume the card works its not an AirPort EXTREME. It's a regular AirPort card. 

At first my router was a WEP 128 BIT PASSPHRASE and it wouldn't connect so I tried taking the security off and still won't connect. 

Is there anything special I have to do to configure my AirPort card to be able to connect to my network? 

and if some one can also help me on installing flash/java I'd appreciate it. 

Thanks!

---

### Post by WackyRicanMan on 2010-05-04
This is really inconvenient having to be stuck to an eithernet cord all day just to use my laptop..

there's gotta be some type of configuration settings or something, I'm new to linux.. I've tried searching and can't find anything that works..

---

### Post by avtolle on 2010-05-04
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) regarding Flash/Java (there is no Flash for ppc linux). As to your main question, I'll be no help.

---

### Post by WackyRicanMan on 2010-05-04
I tried to do what it said for JAVA... this is what came up..

```

laptop:~$ sudo apt-get install icedtea-gcjwebplugin
[sudo] password for cesar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea-gcjwebplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  icedtea6-plugin
E: Package icedtea-gcjwebplugin has no installation candidate

```


edit NVM just saw the "how ever the following packages replace it so I used..
```
 sudo apt-get install icedtea6-plugin 
``` and that worked.

---

### Post by avtolle on 2010-05-04
Yes, some of the "instructions" are a bit out of date. I would do ```
sudo apt-get update
sudo apt-get install icedtea6-plugin
```

---

### Post by WackyRicanMan on 2010-05-04
this wifi problem is really bugging me, that wiki says that AirPort cards should work right out of the box in ubuntu.. and it does, it shows all the networks, it just wont let me connect to them..it just stops trying.

---

### Post by avtolle on 2010-05-04
I have the same issue with the airport card in one of the Cubes I'm running; sees the wireless networks, but cannot connect. I just wonder whether there's an issue with the driver and signal reception somehow.

---

### Post by WackyRicanMan on 2010-05-04
This has to be a common problem, but Lucid is so new, so it's prob going to be a while before this issue is resolved.. I think I'd be better off getting a usb network adapter lol

---

### Post by WackyRicanMan on 2010-05-04
I read up on different net work managers and got wicd network manager

```
 sudo apt-get install wicd
```

then i open it up and it shows all the connections and my network 81%.. I try to connect it and it keeps saying bad password but im entering the right password. the preshared key. 

I even tried a static IP and nothing.

---

### Post by WackyRicanMan on 2010-05-04
```
-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: UniNorth/Pangea GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:03:93:9d:24:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.2.4 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:1f:fb:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

```

It says network DISABLED. How do i Enable it?

---

### Post by linuxopjemac on 2010-05-05
I never understand that people switch to better looking OS-es without having their basics working...Debian seemed to have airport support at least, which, to my opinion, is vital for laptops like an iBook. I am afraid that I can't be of much help. You might want to have a look what this guy did to get the orinico WPA working:
[http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/](http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/)
Also this is a good thread:
[http://ubuntuforums.org/showthread.php?t=1114297&highlight=ibook+g3](http://ubuntuforums.org/showthread.php?t=1114297&highlight=ibook+g3)

Please let us know how you got it working...

---

### Post by pcblues on 2010-05-05
Hi there. 

This worked for me:

If you run this:
sudo lshw -c network

And under the wireless interface it says:
firmware=Lucent/Agere 9.48

Try the following:

WEP worked for me when I renamed /lib/firmware/agere_sta_fw.bin to something else, and then ran:
sudo pccardctl eject; sudo pccardctl insert
which does a reload of the internal card.

When I rebooted again, I had to run sudo pccardctl eject; sudo pccardctl insert
again, but YMMV.

Flash/Java can be installed with:
sudo apt-get install ubuntu-restricted-extras
which loads all the good stuff (Java, MS fonts, movie codecs, etc.)
More info here (plus how to install codecs for encrypted DVD playback etc.)
[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

Aside from this problem, U10.04 is sweet, even on my old laptop (Dell C610)

> **WackyRicanMan said:**
> I have a iBook G3 Dual USB with 600mhz/640mb/80gb

I installed Debian 5.0 (lenny) and it ran great wifi worked and everything. I had a problem with Mozilla and the browsers started not working so I just installed Ubuntu 10.04. 

I love it, the only problem I have is that my WIFI isn't connecting to my network, so I'm connected via eithernet right now. 

Networks show up so I assume the card works its not an AirPort EXTREME. It's a regular AirPort card. 

At first my router was a WEP 128 BIT PASSPHRASE and it wouldn't connect so I tried taking the security off and still won't connect. 

Is there anything special I have to do to configure my AirPort card to be able to connect to my network? 

and if some one can also help me on installing flash/java I'd appreciate it. 

Thanks!

---

### Post by WackyRicanMan on 2010-05-05
> **pcblues said:**
> Hi there. 

This worked for me:

If you run this:
sudo lshw -c network

And under the wireless interface it says:
firmware=Lucent/Agere 9.48

Try the following:

WEP worked for me when I renamed /lib/firmware/agere_sta_fw.bin to something else, and then ran:
sudo pccardctl eject; sudo pccardctl insert
which does a reload of the internal card.

When I rebooted again, I had to run sudo pccardctl eject; sudo pccardctl insert
again, but YMMV.

Flash/Java can be installed with:
sudo apt-get install ubuntu-restricted-extras
which loads all the good stuff (Java, MS fonts, movie codecs, etc.)
More info here (plus how to install codecs for encrypted DVD playback etc.)
[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

Aside from this problem, U10.04 is sweet, even on my old laptop (Dell C610)


How exactly do I rename it...etc.. I'm a n00b to linux.. so if you don't mind a little more detail lol

---

### Post by linuxopjemac on 2010-05-05
this won't work for you. He has no airport card...Ask [an2ne]("http://ubuntuforums.org/member.php?u=250019"), he is into airport and Ubuntu...

---

### Post by kensanata on 2010-05-05
All I can say is that when I installed 9.10 on my iBook G3 wireless just worked. When I upgraded to 10.4, it kept working. The only thing I remember noticing was that the Network Manager Applet would tell me I was "disconnected" and networking "disabled" - all I had to do was enable it (right click on the applet, checkbox). Then I noticed that the next time I started the computer, it was required again. I finally realized that I had to log out instead of power down in order to "save" this.

---

### Post by WackyRicanMan on 2010-05-05
> **kensanata said:**
> All I can say is that when I installed 9.10 on my iBook G3 wireless just worked. When I upgraded to 10.4, it kept working. The only thing I remember noticing was that the Network Manager Applet would tell me I was "disconnected" and networking "disabled" - all I had to do was enable it (right click on the applet, checkbox). Then I noticed that the next time I started the computer, it was required again. I finally realized that I had to log out instead of power down in order to "save" this.


ok i right clicked and enables wireless... my network is there but is grayed out. I can't select it. 

Is this because im using WPA security? Do you think if I use WEP I'd be able to connect to it this time?

---

### Post by WackyRicanMan on 2010-05-05
here's what I get with WICD Network manager 
[IMG]http://bayimg.com/image/dambhaacg.jpg[/IMG]



[IMG]http://bayimg.com/image/damblaacg.jpg[/IMG]


keeps saying bad password everytime... I am putting the right WPA key... 

but with the default network manager, my network shows up but greyed out. I can't choose it. I think it's cause its WPA.

---

### Post by linuxopjemac on 2010-05-05
I can advise you to have a look at an2ne's site, where he discusses to get WPA working with an iBook G3. It's still written for 9.10, so I don't know if it works for 10.04 too, but you might want to give it a try:

[http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/](http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/)

---

### Post by WackyRicanMan on 2010-05-05
tried it, rebooted, still didn't work. When it tries to connect it keeps trying then just stops and says disconnected. then it goes back to my wired connection.

---

### Post by linuxopjemac on 2010-05-06
Try Linux Mint LXDE PPC, it will work ;)

---

### Post by WackyRicanMan on 2010-05-06
> **linuxopjemac said:**
> Try Linux Mint LXDE PPC, it will work ;)



Isn't that like Debian Lenny 5.0? I already had Debian I liked it but Ubuntu looks so much better, and I love it basically.. just really wish I can get the Airport card to connect to a network.. it wont even connect to unsecure networks... is there a way to use a USB network adapter?

---

### Post by linuxopjemac on 2010-05-06
You don't like the looks of Linux Mint LXDE ?
[http://mac.linux.be/files/Screenshot.png](http://mac.linux.be/files/Screenshot.png)

---

### Post by WackyRicanMan on 2010-05-06
Ill pass for now, this is a temporary laptop any ways I guess Ill settle with not being able to use my wifi.. I leave for training on the 26th then I'm gonna buy a Macbook pro and an imac this was just a little beater computer I got.

---

### Post by linuxopjemac on 2010-05-06
fair enough ;)

---

### Post by WackyRicanMan on 2010-05-06
> **linuxopjemac said:**
> fair enough ;)


Yeah and the only reason I put linux on my ibook is cause my old hard drive fried and I dont have any original Mac OS cd's and my Panther or Tiger copies didn't work cause I need originals which are super expensive :[ So I put linux on instead :/

---

### Post by linuxopjemac on 2010-05-06
so we won't be seeing you here anymore then I presume...

---

### Post by WackyRicanMan on 2010-05-06
> **linuxopjemac said:**
> so we won't be seeing you here anymore then I presume...


I actually really like Linux. This is my first time working with it and I honestly love it... So who knows... I will be keeping this laptop so I'll just keep tinkering with it and stay active on this forum. 

I wonder if this WiFi problem is only on Lucid...

---

### Post by linuxopjemac on 2010-05-07
The thing that notice is that both the ibook G3 with a classic Airport (orinoco module) and iBook G4 (Broadcom chipset, b43 module) have the problem. It looks like it has nothing to do with the module itself...I don't believe in so much coincidence. I think it has to do with WPA or something. Can you try to connect to a WEP encrypted network, or a completely open network ? Then we know where the problem resides...

---

### Post by WackyRicanMan on 2010-05-07
Well I thought I mentioned it, but no I can't. I took the security off my network and still couldnt connect, I changed it to WEP and still couldn't connect.

---

### Post by linuxopjemac on 2010-05-07
sorry, didn't read you already tried wicd. I am a bit stuck here...

---

### Post by linuxopjemac on 2010-05-07
other people are reporting the same issues...Can you try to establish a connection in the command line with wpa_supplicant ?

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/554987](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/554987)

---

### Post by WackyRicanMan on 2010-05-07
> **linuxopjemac said:**
> sorry, didn't read you already tried wicd. I am a bit stuck here...


Yup, I tried Wicd and Wifi Radar.

---

### Post by WackyRicanMan on 2010-05-07
> **linuxopjemac said:**
> other people are reporting the same issues...Can you try to establish a connection in the command line with wpa_supplicant ?

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/554987](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/554987)

I'm new to linux, so I don't know what to input in Terminal. There is to many things in the command line, I dont know what exactly I have to copy and paste.

---

### Post by WesHertlein on 2010-05-08
> **pcblues said:**
> 
This worked for me:

If you run this:
sudo lshw -c network

And under the wireless interface it says:
firmware=Lucent/Agere 9.48

Try the following:

WEP worked for me when I renamed /lib/firmware/agere_sta_fw.bin to something else, and then ran:
sudo pccardctl eject; sudo pccardctl insert
which does a reload of the internal card.



Also an iBook G3 here.  Give or take this worked for me.  My steps:

sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak

The pccardctl commands did nothing for me, but after powering off the wireless started working immediately after booting and logging in with the key information I had entered earlier.

Thanks for the tip!

---

### Post by linuxopjemac on 2010-05-08
can other people also try this to see if this is a workaround?

---

### Post by WackyRicanMan on 2010-05-08
> **WesHertlein said:**
> Also an iBook G3 here.  Give or take this worked for me.  My steps:

sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak

The pccardctl commands did nothing for me, but after powering off the wireless started working immediately after booting and logging in with the key information I had entered earlier.

Thanks for the tip!


ok so Here is what came out I did 

```
cesar@cesar-laptop:~$ sudo lshw -c network
[sudo] password for cesar: 
  *-network               
       description: Ethernet interface
       product: UniNorth/Pangea GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:03:93:9d:24:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.2.4 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:1f:fb:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
cesar@cesar-laptop:~$ sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak
cesar@cesar-laptop:~$ 

```


With your command it didn't say anything so does that mean it worked? I haven't rebooted yet cause I want to know if I did it right.

---

### Post by WackyRicanMan on 2010-05-08
I rebooted now under network manager under wireless it says disconnected.
But wireless is enabled. idk what the hell is going on now. it doesnt show any networks now.

Here is what it says now, idk if its different. im starting to get really annoyed.

I just noticed the firmware number changed.. ?

```
sudo lshw -c network
cesar@cesar-laptop:~$ sudo lshw -c network
[sudo] password for cesar: 
  *-network               
       description: Ethernet interface
       product: UniNorth/Pangea GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:03:93:9d:24:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.2.6 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:1f:fb:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.70 link=no multicast=yes wireless=IEEE 802.11b
cesar@cesar-laptop:~$ 

```
Does anybody know if its possible now to install Mac OS X and format my drive completely with an OSx install disk? Even though my hard drive only has ubuntu on it?

---

### Post by linuxopjemac on 2010-05-08
Just go for Debian or Ubuntu Karmic.
If you insist on OSX, yes, just format the whole drive and install OSX.

---

### Post by WackyRicanMan on 2010-05-08
> **linuxopjemac said:**
> Just go for Debian or Ubuntu Karmic.
If you insist on OSX, yes, just format the whole drive and install OSX.

Lol, I did sudo mv and reversed the the command and rebooted so now i can see wireless networks just still cant connect to them.. this is such a weird conflict. 

And about OSX I was asking cause before, I bought this 80gb hard drive completely formatted and couldn't install OSX, I would put the disc in and it wouldnt show up nor my hard drive. I read around and people said it was cause I didnt have the Original disc and that I need to buy a retail disc. I dont have the $$ to buy Tiger on CD which is like $200+ 

I got this laptop with 10.1 on it and downloaded 10.3 & 10.4 off the internet and was able to upgrade. But something happen to my old hard drive. So now I had a blank hard drive and none of those discs worked. So I installed Linux. 


What im thinking about doing is downloading 10.1 install disc of the internet to see if that will work now. I don't see why it wouldn't. I'm just stumped. Maybe I was trying to boot from the CD wrong idk Ill just give it a shot and this time put the CD in first then reboot holding C to see what happens. Cause before the OSX menus wouldnt even show up. :(

---

### Post by WackyRicanMan on 2010-05-08
> **linuxopjemac said:**
> Just go for Debian or Ubuntu Karmic.
If you insist on OSX, yes, just format the whole drive and install OSX.


If I put Ubuntu Karmic on here will my wifi work? If it will I will do it right now. 

Do I have to download and burn another CD? If so I will still do it, Just wondering if there was a way to do it without having to burn another CD.

---

### Post by WackyRicanMan on 2010-05-08
I had to download the alternate CD cause the Desktop iso was 705mb I can't burn over 700mb..

I love my 2mb/s connection

[IMG]http://bayimg.com/image/famkpaach.jpg[/IMG]

---

### Post by WackyRicanMan on 2010-05-09
> **WackyRicanMan said:**
> I had to download the alternate CD cause the Desktop iso was 705mb I can't burn over 700mb..

I love my 2mb/s connection

[IMG]http://bayimg.com/image/famkpaach.jpg[/IMG]

i found mac osx tiger install cds and they worked, formatted my drive and im installing tiger right now.. i liked linux as well so im gonna install karmic for dual boot...do you know roughly how much i should partition for each? i have an 80gb HD..and to dual boot would i just hold down option key at boot and choose karmic or mac osx?

---

### Post by BrendanOD on 2010-05-09
I got it working on my ibook g4 with an airport extreme card.

In synaptic software manager add b43-fwcutter.

When it installs allow it to download the right firmware.

The details about the firmware are here:

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

That's it!

Ain't Linux Great!!!

---

### Post by linuxopjemac on 2010-05-09
that's the way to do it Brendan. I presumed people knew that here...

---

### Post by epfnc on 2010-05-09
Please don't assume people know anything - for me, this is day 1 of Linux and I am not a computer whiz of any sort. I come to these forums looking for simple advice - not remarks to support the prejudices amongst many users that "Linux is for geeks". I have to say I am a bit disappointed so far because people have told me  "After years, finally a version of Linux that everybody can use -  Ubuntu". And yet, here I am, struggling to get WiFi to work....

Anyway, I'm trying out Ubuntu 10.04 (Desktop version running off the CD for now) on my old iBook G3. I can't get WiFi to connect to my WPA / WPA2 router. I have installed the B43-fwcutter "thing" that is mentioned, but still no luck. Any other suggestions?

---

### Post by linuxopjemac on 2010-05-09
the b43-fwcutter extracts the firmware out of Broadcom wireless cards. After a reboot it SHOULD work. I don't want to disappoint you but every new release of Ubuntu, support for PPC is further away it seems.

I always advize Debian. But people here only want Ubuntu.

---

### Post by epfnc on 2010-05-09
Thanks, but still no joy. I've now got Ubuntu 10.04 installed on the iBook and have installed b43-fwcutter and reinstalled. As before, I can see all the WiFi networks in the neighbourhood including mine. It knows I require a WPA / WPA2 password. I give it the password but if just seems to try, try, try...and then ask for the password again.

Any other suggestions?

Thanks,

Ed

---

### Post by linuxopjemac on 2010-05-09
You could just try it again, maybe something went wrong. **Be sure to have an internet connection with a cable!**

```
sudo apt-get remove --purge b43-fwcutter
sudo apt-get install b43-fwcutter
```

Ubuntu's community documentation about this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing BCM43xx drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing BCM43xx drivers)


let b43-fwcutter do its job of extracting firmware. If that is finished, reboot and then it really should work. There is no other way. I have a similar Sonnet PCMCIA card in my Pismo PowerBook G3, which has a Broadcom chipset too. It was done in the same way. The only difference is that I use Mintified Debian Lenny LXDE.

I hope it works for you after this. If not, I would seriously think about another version of Ubuntu (Karmic Koala) or Debian Lenny.

---

### Post by linuxopjemac on 2010-05-09
Ed, can you give me the output of:
```
lspci -vnn | grep 14e4

```

if your card is Broadcom 4306 rev 2, you need b43legacy, otherwise b43...
[http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy](http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy)

---

### Post by igor_av on 2010-05-09
> **linuxopjemac said:**
> You could just try it again, maybe something went wrong. **Be sure to have an internet connection with a cable!**

```
sudo apt-get remove --purge b43-fwcutter
sudo apt-get install b43-fwcutter
```

Ubuntu's community documentation about this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing BCM43xx drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing BCM43xx drivers)


let b43-fwcutter do its job of extracting firmware. If that is finished, reboot and then it really should work. There is no other way. I have a similar Sonnet PCMCIA card in my Pismo PowerBook G3, which has a Broadcom chipset too. It was done in the same way. The only difference is that I use Mintified Debian Lenny LXDE.

I hope it works for you after this. If not, I would seriously think about another version of Ubuntu (Karmic Koala) or Debian Lenny.

It won't work. The g3 iBook uses the original airport card wich is based on the WaveLAN / Orinico Gold Wi-fi adapter. It doesn't have a Broadcom chipset.

I have a 900 mhz G3 iBook, and I'm stuck too. WEP is working in 9.10 but I had no success connecting to my router with WPA. Neither WEP or WAP work with 10.04.

---

### Post by linuxopjemac on 2010-05-09
You are right, in early iBooks they have the legacy airport cards. They work with the orinico kernel module...

Ed: Can you give me the output of:
```
lsmod
```
thanks. I want to know whether you have an iBook G3 or G4 ;)

---

### Post by WackyRicanMan on 2010-05-09
> **igor_av said:**
> It won't work. The g3 iBook uses the original airport card wich is based on the WaveLAN / Orinico Gold Wi-fi adapter. It doesn't have a Broadcom chipset.

I have a 900 mhz G3 iBook, and I'm stuck too. WEP is working in 9.10 but I had no success connecting to my router with WPA. Neither WEP or WAP work with 10.04.


I had the same problem, After I installed OSX 10.4.11 my WPA didn't work and checked it out on Apple and WPA is too new of a Technology for our iBooks that's why WPA won't connect but im connected now after I changed it to WEP. I will  be dual booting 9.10 instead of 10.04 since the wifi doesn't work in Lucid.

---

### Post by linuxopjemac on 2010-05-09
> After I installed OSX 10.4.11 my WPA didn't work and checked it out on Apple and WPA is too new of a Technology for our iBooks that's why WPA won't connect but im connected now after I changed it to WEP.

AHA! I didn't know that. There is no way to upgrade the firmware to have WPA?

---

### Post by WackyRicanMan on 2010-05-09
> **linuxopjemac said:**
> AHA! I didn't know that. There is no way to upgrade the firmware to have WPA?


[http://support.apple.com/kb/HT2594?viewlocale=en_US](http://support.apple.com/kb/HT2594?viewlocale=en_US)

---

### Post by igor_av on 2010-05-09
> **WackyRicanMan said:**
> I had the same problem, After I installed OSX 10.4.11 my WPA didn't work and checked it out on Apple and WPA is too new of a Technology for our iBooks that's why WPA won't connect but im connected now after I changed it to WEP. I will  be dual booting 9.10 instead of 10.04 since the wifi doesn't work in Lucid.

My home network is WPA encrypted (not WPA2) and I have no problem connecting to the router with my g3 iBook with Mac OS 10.4. You must set the WPA algorithm to TKIP (the earliest algorithm) instead of AES (the newest).

---

### Post by linuxopjemac on 2010-05-10
The document says that you can connect to WPA. You only need the right software.

---

### Post by cirdanlevancien on 2010-05-12
Mine works now, too!  NOTO BENE:  Only tried with WEP.

iBook G3 dual usb 500 MHz / 10GB / 320MB / (original) airport card (lucent) / NetGear WG111v2 (Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111(v2) 54 Mbps Wireless [RealTek RTL8187L])

The RealTek chipset in the NetGear dongle was immediately recognized out-of-the-box, which is nice if I want 802.11g speeds.  Even the LED on the dongle shows activity (previous 'working' drivers didn't).

The original airport card (lucent/agere Orinoco) did NOT work out of the box and kept asking for wireless keys.

I eventually installed Debian Lenny (5.04) PowerPC XFCE + LXDE nCurses installer.  It worked with keys and wireless IDs entered during installation.  Yet while rutilt could see wireless access points, it kept complaining that it couldn't load the keys.  I'm not sufficiently proficient with the CLI and the concepts of wpa_supplicant to make it all go from the command line, nor do I care that much (OK, lies... I could do it but it required tedious mucking around with /etc/network/interfaces and much ifups and ifdowns).  I broke the system mixing testing with Lenny while trying to install wicd (don't ask how; I don't know).

So -- thanks to y'all, I had confidence that a reinstall of Lucid would work and now I'm happily back in the fold.

Only particularly goofy thing -- had a few errors on first reboot.  No nm-applet showing on 2nd reboot.  Works like a charm on 3rd reboot.  Go figure.

Just do as the nice man said:

sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak ; sudo pccardctl eject ; sudo pccardctl insert

reboot reboot reboot

THANKS TO ALL OF YOU!

...CirdanLeVancien...

Bonus:  Get your whole screen working (Rage Mobility M3 AGP 2x) with this /etc/X11/xorg.conf (just open a terminal, type sudo nano /etc/X11/xorg.conf and then paste this there -- type <ctl>-o  <ctl>-x, and reboot. Yay!)

Section		"Device"
	Identifier	"Configured Video Device"
	Driver		"r128"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"	"true"
EndSection

Section		"Monitor"
	Identifier	"Configured Monitor"
	HorizSync	60-60
	VertRefresh	43-117
	Option		"DPMS"
EndSection

Section		"Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Depth 	24
		Modes  "1024x768"
	EndSubSection
EndSection


Note that it thinks it's smarter than me and says it's using the driver:aty128fb.  Whatever.  Works.  Ciao for now!

> **WesHertlein said:**
> Also an iBook G3 here.  Give or take this worked for me.  My steps:

sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak

The pccardctl commands did nothing for me, but after powering off the wireless started working immediately after booting and logging in with the key information I had entered earlier.

Thanks for the tip!

---

### Post by Semperfive on 2010-06-06
I just upgraded to 10.04 on my Powerbook G4/500 and the wifi stopped working just as described by all the others.  I did this:

sudo mv /lib/firmware/agere_sta_fw.bin  /lib/firmware/agere_sta_fw.bin.bak

sudo pccardctl eject

sudo  pccardctl insert

restart

Now it works perfectly

Thanks to all!!!

---

### Post by Verus on 2010-06-08
> **WackyRicanMan said:**
> i found mac osx tiger install cds and they worked, formatted my drive and im installing tiger right now.. i liked linux as well so im gonna install karmic for dual boot...do you know roughly how much i should partition for each? i have an 80gb HD..and to dual boot would i just hold down option key at boot and choose karmic or mac osx?

Have you already settled on a setup? I dual boot Lucid & Tiger on  a PowerBook G4 1.33GHz. I've got my 60GB drive partitioned so each OS has a 10GB partition with a 40GB shared data partition.

Yaboot should prompt you for which to boot: 'L' for Linux & 'X' for OS X & 'C' for CD

---

### Post by sliderda2b on 2010-06-23
I was having the same problem with my G4 Cube, so I installed wicd - it didn't work for me either. However, once I removed wicd and re-entered my WEP password into the default WiFi manager (I use a 128 bit Hex key), it suddenly started working! Thanks for starting this thread.

---

### Post by Cavin on 2010-07-21
I have an iBook G3. Doing what the guy earlier said:
```
sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak
```

No, I didn't do all that whatever eject; whatever insert or whatever it is haha. I just restarted and it worked!

Thanks a ton!

---

### Post by danpwright on 2010-08-06
Dear all,

I have been reading this thread with much interest.  I have an iBook G3 700Mhz and an original airport card ( I think!)

I have similar problems to you all, but when I typed in the command that everyone else did, I just got "no such file or directory".

Any ideas?  And did I need to be connected to the internet via cable at the time?

Also...my card upon first install could see networks, now I have rebooted it, it can't see any!

Been very frustrated with this, hope someone can help!

Exact result: mv: cannot stat ' /lib/firmware/agere_sta_fw.bin': no such file or directory.

---

### Post by pencilfish on 2010-10-27
I, too, have been reading this thread with great interest.

My problem is the same ("bad password" with WICD), but with a dual-booting Titanium Powerbook G4. Original Airport card. Ubuntu 10.10 (Started with 10.4, problem continues in 10.10). WEP-Open, custom passphrase. I also cannot connect to the university's wireless network. It refuses to "obtain an IP." (In Mac OS X, I have no issues with connecting at home or at the university)

I have combed these resources and many others, and pretty much tried everything I found. 

Installed WICD and purged Network-Manager (which kept asking for the password and never connecting). No success.

Set network to 802.11b, rather than combo b/g, no luck.

Performed in terminal the renaming of the wireless card driver as detailed in previous posts, and the eject/insert of card. and restart. more than once. No luck.

Dinked around with various other options in WICD and router interface, resulting in no success. WEP-shared, etc....

I'm now wondering if this Ubuntu version simply will never ever work on G4 with original Airport card. I had hopes that this old Powerbook would have a new lease on life and give me something different to play with. I really love the Ubuntu interface. And it was super easy to install. And it was recommended for use on G4 Macs.

Thanks for your efforts.

---

### Post by marklogan on 2010-11-03
> **Cavin said:**
> I have an iBook G3. Doing what the guy earlier said:
```
sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak
```No, I didn't do all that whatever eject; whatever insert or whatever it is haha. I just restarted and it worked!

Thanks a ton!

Cavin, Once it worked for you?  when u rebooted again later was it still working? I think I tried this method before...and it worked but once i rebooted a couple of times....something went wrong and then NONE of my connections were showing and I could not connect.  I am a noobie to Ubuntu.

How is it working now for you?

Thanks, mark

---

