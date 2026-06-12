---
title: "Wireless Problems"
date: 2007-03-15
forum: Apple Intel Users
---

### Post by wootwoot123 on 2007-03-15
Hello I have a core 2 duo macbook and have been struggling to get my wireless card working. I recently put the wireless n enabler patch on that came from apple and I think that may be the reason for my problems. I have been trying to get ndiswrapper working with the driver that goes to the lenovo t60p but every time I have ndiswrapper display what it has loaded it shows that the driver is present but says nothing about the hardware. I have been trying with this thing for over a week and I am about to give up, help me please.

---

### Post by cyberdork33 on 2007-03-15
Start reading at step 10:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I could not get any drivers working with my iMac besides the drivers that were in the bootcamp cd, even though I had drivers for the same broadcom chipset.

---

### Post by oskarloko on 2007-03-15
You'll need ndiswrapper, just the MacBook C2D has a ew Atheros wifi card, and it is not suported by kernel now ( there's no ETA avalible )

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

There it explains how to do it.
If you have not WinXp you can download drivers from web ( 1.1 ver ) and use them

---

### Post by das_syndrom on 2007-03-15
> You'll need ndiswrapper, just the MacBook C2D has a ew Atheros wifi card, and it is not suported by kernel now ( there's no ETA avalible )

Have you really read _and_ understood the first post?

Ok...
Has wireless been working before the apple-update?
I'm using the lenovo-driver (NET5416.INF) on a macbook c2d without any problems.
Which ndiswrapper-version do you use? You need a newer version than the one that ships with Edgy Eft. (i use version 1.34, utils version 1.9)

Andi

---

### Post by Tribe on 2007-03-15
I had a similar problem and, as they say above, i had to update ndiswrapper compiling it from sources, version 1.37 to be exactly:

```
tribe@macbook:~/uni/ia/docs$ ndiswrapper -v
utils version: 1.9
driver version:        1.37
vermagic:       2.6.20-8-generic SMP mod_unload 586
```

Also in my case i'm using D-link DWA-645 Windows Driver from [http://www.dlink.com/products/support.asp?pid=489&sec=0](http://www.dlink.com/products/support.asp?pid=489&sec=0) . The file is a installer that you can run with wine for extracting the INF file ndiswrapper needs (net5416.inf in my box).

```
tribe@macbook:~$ ndiswrapper -l
net5416 : driver installed
        device (168C:0024) present
```

---

### Post by oskarloko on 2007-03-15
really, I didn't read it well... :oops: 

I used, on Egdy:
ndiswrapper 1.38 ( better )
ndiswrapper-utils1.8 

and 

driver 1.01 from D-LINK website...

It works fine !!
( 1.02 makes system to hang )

We've Christer Edwards, on PlanetUbuntu, looking for that...

Here [http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/) and on PlanetUbuntu


sorry for missunderstood...
 #-o

---

### Post by Zelut on 2007-03-16
I have a brand new c2d macbook (I brought it home two days ago).  One of the first things that I did was update the OSX firmware and software, which I heard might be part of the problem.

I have tried the D-Link driver.  I have tried the Lenovo driver.  Both of them install & I get the 'hardware present, driver present' response from ndiswrapper but no hardware device is created.

The next thing I'm going to try today is to use the driver Mac has as part of boot camp for XP.  I figure it might be a long shot but at least that driver is specifically for this hardware... I'll post those results once they are done.

---

### Post by ouilsen on 2007-03-16
I can only tell you how my way worked.

I use:

- Feisty
- OS X with all updates
- ndiswrapper 1.38
- lenovo T60 XP driver

AFAIK the main reason for failure is the ndiswrapper version.

---

### Post by david_edmundson on 2007-03-17
Whenever I modprobe ndiswrapper my computer completely freezes. (very annoying as I don't have a sysRq key) Has anyone else been experiencing this?
I've tried upgrading to ndiswrapper version 1.38, but the situation still occurs. Thoughts?

---

### Post by wootwoot123 on 2007-03-19
I have tried all of the drivers you guys suggest with no luck. I tried the dlink 1.02 drivers and the lenovo T60 drivers. I am using ndiswrapper 1.38 and ndiswrapper-utils 1.9. I don't know what is going on with this. Every time I get the driver present but the hardware does not show. I am getting really frustrated with this and want to make it work. I love ubuntu and want to use it more but this is forcing me to stick with OSX. Help me any way you guys can plz.

---

### Post by vh1 on 2007-03-22
I just got wireless on a macbook core2duo working (although it didn't seem like it would)

I used the net5416 drivers from the Bootcamp drivers CD and ndiswrapper-utils-1.9

in a nutshell, all I had to do was:

# sudo ndiswrapper -i net5416.inf
# sudo cat ndiswrapper >> /etc/modules
# sudo ndiswrapper -m
# sudo reboot

when it came back up I tried some normal commands to see if it worked:
```
mike@lua:~$ ndiswrapper -l
installed drivers:
net5416         driver installed
mike@lua:~$ iwlist wlan0 accesspoints
wlan0     Interface doesn't have a list of Peers/Access-Points
```

so randomly I tried just bringing it up with `sudo ifup wlan0` and what do you know. it connected!

---

### Post by cyberdork33 on 2007-03-22
Interesting that ndiswrapper -l did not say "hardware present", but can't complain too much if it is working...

---

### Post by thonuz on 2007-03-23
[QUOTE=vh1;2335304]I just got wireless on a macbook core2duo working (although it didn't seem like it would)

I used the net5416 drivers from the Bootcamp drivers CD and ndiswrapper-utils-1.9
......................

Is there anyway to get this driver without reinstalling bootcamp? Since I already have ubuntu osx dual booting and have installed bootcamp. If I now try to reinstall bootcamp it says I mut reformat my entire computer. Lose all data and start over, just to get the friggin driver.

---

### Post by cyberdork33 on 2007-03-23
There are ways to extract the contents in windows without actually installing it.

---

### Post by wootwoot123 on 2007-03-23
I got it working!!! I used whatever driver I installed last and was getting the same response as vh1. The driver was present but the hardware did not register as present. I did an ifup wlan0 and everything went without a hitch. Someone should make a note that you may not see the hardware present but your wifi may be working.

---

### Post by thonuz on 2007-03-23
edit.
How to create a drivers cd without installing or reinstalling bootcamp or wiping out hard drive.

Here is what I am now doing.
Go to applications: utilities
find the bootcamp icon. You need to show package contents. Im new to mac so its right-click or command click.
There is the action button that gives you show contents.
Double Click Contents and then open resource folder.
There you will see disk image. (diskimage.dmg)
Burn this.

---

### Post by trevelyn on 2007-03-23
Hey my wireless card doesnt work either, in fact: 

what a nightmare, i have never seen so many errors before in my entire life, than when i tried to use ubuntu and kubuntu.. The only thing i can come up with is that my hardware is COMPLETELY different from the users that posted all of the howto's.  I bought mine only 2 months ago, so here goes..

iSight, doesnt work.  I have copied and pasted the commands letter for letter, on each tutorial.
on guy had his own blog site, and said to use patches stating "well, the nre macbooks have newer firmwares" of course they do, right? well, i followed His tutorial (list of shitty commands) and when i issued the modprobe, i noticed my network connection was gone.. (i was using a ralink chipsetted usb cisco card) oh, and my mouse stopped...hrmmm... this is funny, i rebooted to see what effects might change like any other guy who used windows too long during the period of his life, and wouldnt you know it... one of the USB ports just stopped working.... okaaaay.. re-install.  (7655th time) used Kubuntu, i like KDE it's nice.  It installed wonderfully, i am happy the 915resolution gave me crisp eye pleasing graphics, and ooh, looky.. down here in the corner of the screen says "you have 182 updates waiting to be installed" good, maybe the updates will prove to be fruitful.  well took about 1.5 hours with dial up er, i mean DSL, same thing and i was happy everything looked fine for a while then in the console i opened another terminal and the font was magically different, it was like Times new roman from hell.. hrmm, that sucks, i thought.  Then when i was in the KDE menu there was a new folder called "LOST AND FOUND" that contained ALL of my programs?? hrmm, that sucks.. better do what i have been trained to do since 1995 - reboot.  i reboot and wow Xserver hangs with this cool blue and white pattern, the same pattern a nintendo cartidge would make if it lost proper connection with the contacts in the nintendo when i was a kid.  I editted xorg.conf, and nothing.. in fact this not only hung my xserver, but the WHOLE system was frozen.. re-install (7842565th time)
well, i decided to use ubuntu, and kick it with gnome for a while, this will be a cool experience, gnome, i used to like those little feet icons i would see during installs.  But i always laughed at them thinking how badly i didnt like gnome when i would select KDE.  Wow, i havent used gnome since... 10 years maybe??? its improved a lot, and .. just wow, its awesome. i am really liking it now.. heh, reminds me of OS X.  well, I tried once agin another tutorial on how to get the radeon drivers working, nope. googled all the errors i saw found a few solutions, installed okay, and then rebooted into a regular console with a big ugly ASCII decorative screen telling me i used the wrong drivers.  and so i tried to edit my xorg.conf, nope.. re-install (4569238745613452nd time)  
so the iSight, the video card, oh and the wlan card (the reason i was using my cisco USB) The tutorials i have read including those on this forum say that theres 2 different types of atheros based airport cards, one old one new, well, i just bought mine so im sure its the new one.. ("core 2 duo"  i guess is how they differentiate) then I followed the instructions to use the ndiswrapper, and the crappy windows .INF driver. no the install finally went well, no errors with the Ubuntu like there was in Kubuntu, but iwconfig showed nothing eth0, loopback, and sit.  well, maybe i had gotten the old card, tried the madwifi-ng which i have had experience with, i used to use a nice atheros based pcmcia card in my last laptop (which i dearly miss now.. oh the insert key, the pause key, the right mouse button, the pcmcia slot... /me drools) okay so i tried that, no nothing modprobe ath_pci gave me tons of errors dmesg was so full it stretched passed my buffer in xterm.  Well, i can use my usb card for now, it injects well enough, and i like it, i can change the MAC address and all..
The soundcard works great alsamixer is cool, and all.. the bluetooth adapter is found, i havent triued rfcomm, or hci-tools yet, bluesnarfer,.. mapping out the keys to make the lower enter key the "right mouse button" did nothing in kubuntu, havent tried with ubuntu yet... Theres a small red led that shines out of the headphones port on the left side of my macbook, that odd, i never saw that before anyone else?? and in kubuntu if i set the computer to suspend to RAM, it wouldnt wake back up.  havent tried it with ubuntu yet..well, im going to try more thing out with Ubuntu and Gnome now, if anyone has any ideas of my plight please reply - thanks in advance.

---

### Post by cyberdork33 on 2007-03-23
1. Try asking a question at a time or maybe use some whitespace... Most people are not going to want to read through your mind dump (i.e nobody will help you). Also, keep problems on topic. This is a wifi thread so I would a question about your wireless...

2. Try not configure everything at once. take things one at a time. When you get it working correctly then move on to the next item otherwise you are just compiling problems and you will never figure whats wrong.

See this page for most of the issues:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by trevelyn on 2007-03-23
sorry i just spent like a week trying to figure out why i couldnt get this working, i miss slackware, but, 915resolution was happy with it, so now that i am using Ubuntu, EVERYTHING started working.. that is relative to Kubuntu, which nothing worked.  Thanks for the advice, and tthe link, i *did* use that link when doing the Kubuntu, i just figured it would apply to both, no, I got the iSight up, Sound is great video is great, Enlightenment is really cool by the way, and the reason i am replying here on the "wireless questions.."  I folled the steps precisely, and everything installed no errors.. but iwconfig shows nothing and ifconfig -a shows nothing and the card isnt listed in the network manager assistant thinggy.  Any ideas??
thanks in advance :)  

post script: sorry about posting the angry nintendo nerd style review of my mishaps, i was trying to get the wireless working when i lost my mind tis all - thanks. - trev

---

### Post by oskarloko on 2007-03-23
Well. I'm using a Ubuntu Egdy install base, but I installed - after spending hours to config all - kubuntu desktop (meta)package; and sure it works

( well, gnome conf won't, really )

Thanks [ouilsen]("http://www.ubuntuforums.org/member.php?u=102346") , the Leono wireless driver works !!

(using wine on-the-air to extract drivers)



:guitar:

---

### Post by trevelyn on 2007-03-23
okay, update: 

>  trevelyn@Bell-Mobile:~$sudo ndiswrapper -l 
says   "NET5416.INF invalid driver!"

so maybe i *do* have a different card eh??

---

### Post by thonuz on 2007-03-23
[QUOTE=oskarloko;2343932]


(using wine on-the-air to extract drivers)

Im going to try this. THe bootcamp disk wont extract properly. But maybe madwifi will happen soon.

---

### Post by trevelyn on 2007-03-27
yeah im going to stick to my Ralink chipset linksys USB adapter working under the rt73 driver perfectly fine, but i hope it does get fixed soon :) i got the latest driver for the card NET.INF driver and still no luck, i dont have bootcamp, i have no use for it, i only use linux.
my macbook was just purchased though, so im thinkning my card is different... ndiswrapper still says "NET5416.INF invalid driver!!"

---

### Post by PictureThis on 2007-03-27
OK, I confess. I don't get it. I read the entire thread, followed [this tutorial](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/) and everything went peaches until ```
sudo ndiswrapper -l
```

The darn thing just won't acknowledge the device is present. My MacBook Core 2 Duo nfo:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

```
ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:       2.6.20-13-generic SMP mod_unload 586

```
```
sudo ndiswrapper -l
net5416 : driver installed
```

Now this would be a great moment to get the message "device (168C:0024) present". Alas.

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

KNetworkManager does not show my (or any other) wireless network. I'm on a leash... :cry: Cut me loose please..

---

### Post by PictureThis on 2007-03-27
OK, nothing beats setting yourself free. \\:D/ :D 

It turns out something was wrong with my /etc/network/interfaces setup. Enabling the lines:
```
auto wlan0
iface wlan0 inet dhcp
``` did the trick. Via KNetworkManager I could "connect to other wireless network" (encryption WPA2 Personal) and all is well except for KNetworkManager who crashes every time when clicking <name of my network> directly underneath "Wireless Networks" Wireless internet is still available after the crash though and since I can reproduce this crash it might well be a bug.

One more thing to figure out: 
```
sudo ndiswrapper -l
net5416 : driver installed

```

Still no sign of device present.. ;)

---

### Post by thonuz on 2007-03-28
I installed the windows driver from thinkpad with wine and then I set up the driver using the windows wireless driver utility. The driver is in the c: folder of wine.
After this I merely have to do "up" command after a bootup and it finds the network. Works no problem. My major problem is the keyboard right now. No right click)

---

### Post by Fornax-101 on 2007-03-30
[Madwifi]("http://madwifi.org/ticket/1001") has now experimental support for the wireless adapters in the C2D.

It works for me and I'm running Feisty(x64) :) .

---

### Post by trevelyn on 2007-04-01
Fornax-101 that fixed my problem, works perfectly now :) thanks a 10^6, man.

---

### Post by PictureThis on 2007-04-09
I'm still using ndiswrapper but all of a sudden my MacBook needs a couple (2 to 6)  attempts to connect to the wireless network whereas before the connection was established instantly (well, after entering the keyring/wallet password that is, getting rid of this annoying feature is on my todo list). NetworkManager (or KNetworkManager, I'm using Ubuntu/Kubuntu alternatively) will prompt me for a passphrase for my WPA2 encrypted network (I have used the same passphrase for a month without any problems) and only after several times cancelling the pop-up and trying to connect wlan0 is up. 

Other than that I'm still curious why 
```
ndiswrapper -l
``` shows
```
net5416 : driver installed

```

but does not return "device present"

---

### Post by vh1 on 2007-04-11
> **PictureThis said:**
> OK, nothing beats setting yourself free. \\:D/ :D 

It turns out something was wrong with my /etc/network/interfaces setup. Enabling the lines:
```
auto wlan0
iface wlan0 inet dhcp
``` did the trick. Via KNetworkManager I could "connect to other wireless network" (encryption WPA2 Personal) and all is well except for KNetworkManager who crashes every time when clicking <name of my network> directly underneath "Wireless Networks" Wireless internet is still available after the crash though and since I can reproduce this crash it might well be a bug.

knetworkmanager does work for you? I've got the exact same symptoms (ndiswrapper reports driver with no hardware but wireless still works) but knetworkmanager just stays at 28% and then gives up

I was hoping it was related to the no "hardware present" problem, but damn

also, that madwifi news is exciting. time to go play!

---

### Post by vh1 on 2007-04-11
wow, I am 100% *amazed* at how simple that was to setup

1. download and extract [http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz)
2. install build-essential and your kernel headers
3. make && sudo make install
4. add ath_pci to /etc/modules
5. reboot!

knetworkmanager even works! I'll still keep ndiswrapper around though, since the madwifi driver (reportedly) cannot connect to encrypted networks

---

### Post by Chrisj303 on 2007-04-11
It would be absolutely FANTASTIC if somebody who has got the new MadWIFI drivers working on the macbook c2d could provide copy/paste instructions on how to do it.
I've only been using ubuntu for a couple months and have got nowhere regarding wireless. It's the one thing a LOT of ubuntu/Mac users seem to be missing out on.


chrisj303

---

### Post by Chrisj303 on 2007-04-11
> **vh1 said:**
> wow, I am 100% *amazed* at how simple that was to setup

1. download and extract [http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz)
2. install build-essential and your kernel headers
3. make && sudo make install
4. add ath_pci to /etc/modules
5. reboot!

knetworkmanager even works! I'll still keep ndiswrapper around though, since the madwifi driver (reportedly) cannot connect to encrypted networks


Could you help me *please*!

1. I've downloaded the tarball - now where should i extract it?
2. I'm completly lost on this step
3. I assume i cd into the madwifi directory (were i've extracted the .tar) - then execute that command?
4 + 5 . Not a problem!


cheer,
chrisj303

---

### Post by vh1 on 2007-04-12
> **Chrisj303 said:**
> Could you help me *please*!

1. I've downloaded the tarball - now where should i extract it?
2. I'm completly lost on this step
3. I assume i cd into the madwifi directory (were i've extracted the .tar) - then execute that command?
4 + 5 . Not a problem!


cheer,
chrisj303

here goes nothing:
sudo apt-get install build-essential
wget [http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.10/madwifi-hal-0.9.30.10-r2257-20070410.tar.gz)
tar zxvf madwifi-hal-0.9.30.10-r2257-20070410.tar.gz
cd madwifi-hal-0.9.30.10-r2257-20070410/
make
sudo make install
sudo reboot

the `sudo make install` may prompt you about existing files, just press r to replace them.

I just ran an apt-get upgrade, and doing so broke the madwifi driver. recompiling and reinstalling it worked like a charm though. adding ath_pci to /etc/modules wasn't even needed, knetworkmanager seemed to connect fine on its own

---

### Post by ronocdh on 2007-04-12
> **Chrisj303 said:**
> It would be absolutely FANTASTIC if somebody who has got the new MadWIFI drivers working on the macbook c2d could provide copy/paste instructions on how to do it.
I've only been using ubuntu for a couple months and have got nowhere regarding wireless. It's the one thing a LOT of ubuntu/Mac users seem to be missing out on.


chrisj303

Chrisj303, have you been able to get wireless up using ndiswrapper? I'm on a CD2 MBP 15", that's what I use. So are you entirely without wireless, or do you just want to use madwifi ones?

---

### Post by Chrisj303 on 2007-04-13
> **ronocdh said:**
> Chrisj303, have you been able to get wireless up using ndiswrapper? I'm on a CD2 MBP 15", that's what I use. So are you entirely without wireless, or do you just want to use madwifi ones?

I am entirely without wireless. I have installed ndiswrapper and tried the NET5614.inf drivers, but am just getting "invalid drivers" when i 'ndiswrapper -l". And all my wireless utilities don't even reconise any device.
Like i said i'm new to Linux, and it is very difficult to retrive information that i can decipher.

Thanks VH1 - i am going to try this today, fingers crossed!


chrisj303

---

### Post by Chrisj303 on 2007-04-13
UPDATE!

Right, i installed the driver, and now my macbook is picking up wireless networks!yay! - i can't seem to connect though, it seems to be having problems with WEP encryption. But it's definitley a step in the right direction.

There is a text file within the madwifi folder about WEP connection, but it's advice dosen't seem to work..
I'm going to need WPA encryption from next week onwards, so thats the next mission for me!

---

### Post by vh1 on 2007-04-14
just a little update. ndiswrapper now works with knetworkmanager for me. I'll stick with it over madwifi for now (each time I do an apt-get upgrade, madwifi doesn't want to work without being rebuilt). but I can't wait for things to get more stable over there

---

### Post by Chrisj303 on 2007-04-14
Regarding ndiswrapper, i followed this guide : [http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)

And when i ' ndiswrapper -l ' all i get is ' NET5416:invalid driver' ??


What driver are you using?




606

---

### Post by vh1 on 2007-04-18
I've got the exact same result.

the driver from the bootcamp driver cd caused a kernel panic, same with the d-link one. the lenovo one has been the best so far.

but as I said, running `ndiswrapper -l` doesn't report hardware present, but it still works fine

when you load the model and run ifconfig, does it list wlan0? if so, try running `sudo ifdown wlan0 && sudo ifup wlan0`

---

