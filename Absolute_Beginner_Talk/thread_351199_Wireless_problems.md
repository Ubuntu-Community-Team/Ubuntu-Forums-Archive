---
title: "Wireless problems"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by amosharper on 2007-02-01
Hi,

I've never used any other operating system then Windows, but after inspecting Vista I decided it was probably better to switch platforms, so I installed Ubuntu (Edgy Eft) on a different partition.

It installed without problem, but I couldn't connect to wireless. All the guides I could find assume you know how to use Ubuntu well already. I don't.

My wireless card is a Netgear WG311v3 (802.11g) card, and still works fine with Windows. On Ubuntu, it sees the card but does not let me connect to my wireless router (which has a hex code). Where do I start? Thanks,

- Amos

EDIT: I was mistaken. It doesn't see the card at all, or recognises it as a 'wired card' instead. See [http://i136.photobucket.com/albums/q187/amosharper/Screenshot1.png](http://i136.photobucket.com/albums/q187/amosharper/Screenshot1.png)

EDIT: Currently stuck: see post 12.

---

### Post by linux_kid on 2007-02-01
Does your wifi light turn on or not?

---

### Post by The Mekon on 2007-02-01
Have you looked at this article in the Wiki.

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking")

Brian

---

### Post by amosharper on 2007-02-01
Thanks for your quick replies.

> When booting with Ubuntu, the WiFi card light does not turn on, no.

> That article does not cover my problem sufficiently:

_[http://i136.photobucket.com/albums/q187/amosharper/Screenshot1.png]("http://i136.photobucket.com/albums/q187/amosharper/Screenshot1.png")_
shows the only options I have for my card (which, I just noticed, is not actually down as a wireless connection at all).

Any ideas what the next step is? Thanks,

- Amos

---

### Post by linux_kid on 2007-02-01
OK, first you will need to find your windows wifi drivers, probably from netgear's web site.
Come back when you have them.

---

### Post by RomeReactor on 2007-02-01
[Looks]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N") like your card has a Marvell chipset and you need [NdisWrapper]("http://en.wikipedia.org/wiki/Ndiswrapper"). [This]("http://ubuntuforums.org/showthread.php?t=179801&highlight=wg311v3") thread addresses your problem.

---

### Post by amosharper on 2007-02-01
Could you verify that [http://kbserver.netgear.com/release_notes/d102828.asp](http://kbserver.netgear.com/release_notes/d102828.asp) is the right driver for the following, please?

[IMG]http://i136.photobucket.com/albums/q187/amosharper/Screenshot2.png[/IMG]

Thanks,

- Amos

---

### Post by RomeReactor on 2007-02-01
[This]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") is the one you need.

---

### Post by amosharper on 2007-02-01
Thanks.

**wg311v3_1_0.zip**
|-WG311v3 V1.0
   |-Driver
   |  |-Windows 2000
   |  |  |-WG311v3.cat
   |  |  |-WG311v3.INF
   |  |  |-WG311v3.sys
   |  |  |-WG311v3XP.sys
   |  |-Windows 98
   |  |  |-WG311v3.INF
   |  |  |-WG311v3.sys
   |  |-Windows ME
   |  |  |-WG311v3.INF
   |  |  |-WG311v3.sys
   |  |-Windows XP
   |  |  |-WG311v3.cat
   |  |  |-WG311v3.INF
   |  |  |-WG311v3.sys
   |  |  |-WG311v3XP.sys
   |-Utility
   |  |-Setup.exe

That's the structure of the .zip. What do I do with it? Run the .exe with Ubuntu?

---

### Post by RomeReactor on 2007-02-01
From those you only need **WG311v3.INF** and **WG311v3XP.sys** from the **WinXP** folder; then follow the instructions from the 5th post on [this]("http://ubuntuforums.org/showthread.php?t=179801&highlight=wg311v3") thread.

---

### Post by amosharper on 2007-02-01
That's brilliant. The Linux Kid, Mekon and especially RomeReactor, you've been a great help. Thanks, and I'll update if I have further problems.

Thanks again,

- Amos

---

### Post by amosharper on 2007-02-02
I've run into problems with ndiswrapper-util. What follows is what I typed into the terminal and the feedback I got:
```
amos@Amos-Ubuntu:~$ sudo apt-get remove --purge ndiswrapper
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ndiswrapper**
amos@Amos-Ubuntu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ndiswrapper-utils**
amos@Amos-Ubuntu:~$ cd wg311v3
amos@Amos-Ubuntu:~/wg311v3$ sudo ndiswrapper -i wg311v3.INF
**sudo: ndiswrapper: command not found**
amos@Amos-Ubuntu:~/wg311v3$ 
```

What is ndiswrapper? Is it something I need to download? If so, where from, and what do I do with it?

Thanks in advance,

- Amos

---

### Post by RomeReactor on 2007-02-02
Probably you don't have Universe and Multiverse repositories enabled; open Synaptic (System-->Administration-->Synaptic Package Manager) click on "Settings", then "Repositories", and on the first tab check all cases. Close that window (not Synaptic) and click "Reload". Then search for "ndiswrapper" and from the results install "ndiswrapper-utils" (i also installed ndiswrapper-utils-1.1 and 1.8)

Edit: the smiley with glasses is an **eight**, so that is one-point-eight. After installing it, continue with

```
cd wg311v3
```

```
sudo ndiswrapper -i wg311v3.INF
```

---

### Post by amosharper on 2007-02-02
Are they already on the machine, or do they need to be downloaded? If they do, I'll have to do it with Windows one way or another.

EDIT: Looks like I need to download them using Windows, or find a different (temporary) way of connecting to my router. Any ideas?

Thanks,

- Amos

---

### Post by RomeReactor on 2007-02-02
One way to connect to your router is to use a Lan cable, but first, changes must be made to /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

then comment everything out **except**

```
auto lo
iface lo inet loopback
```

then add

```
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.1
```

Keep in mind that i'm using a Netgear router and the settings i use may not apply to you.

Aterwards, shutdown the pc, then the wireless router, then the wired box that's feeding your wireless one (not sure if you have that setup, though. If you do, then let's continue). Now power up the **wired** modem/router thing, then the wireless router, **then** your pc. you should have internet working now...

**BIG EDIT: TAKE NOTICE**: just unplug the Lan cable from your router and connect it to your pc. Should configure it automatically.

---

### Post by amosharper on 2007-02-02
[COLOR="Silver"]A couple of questions about that:

- What do you mean by 'comment out'?
- I replace 'address' and 'gateway' with my own settings (which I know), right?
- My (Safecom wireless) router does allow you to connect with a LAN cable - there's no second wired box.[/COLOR]

**Regarding your edit:**
- That would cause a problem for other members of the household using the wireless connection. Is there a different way to do this?

Many thanks,

- Amos

---

### Post by RomeReactor on 2007-02-02
Hmmm.... looks like we may have to use the way i edited out, then.

1.- Commenting out is putting a # at the start of a line; that makes it "invisible" to the system, or rather, it gets treated like a comment and ignored as a command (or something like that).

2.- I believe you should check the page of your wireless router vendor and see if they have specific instructions on how to get wired internet through your router. The instructions i posted (perhaps wrongfully) are for my Netgear router; can't guarantee they'll work on yours, though there's a chance they might. NOT SURE. Sorry.

**ANOTHER BIG EDIT**:Please post your Interfaces file before proceeding with anything else:

```
gedit /etc/network/interfaces
```

Wow. I'm so rusty...

---

### Post by RomeReactor on 2007-02-02
Also please run in a terminal:

```
iwconfig
```

and post the output.

---

### Post by amosharper on 2007-02-02
[COLOR="Silver"]I'll edit shortly with iwconfig and interfaces, but for now, [/COLOR]There's a major problem I'm facing:

Firstly, to wire my computer to the router would require me to install the correct PCI card (which I don't have). Secondly, my computer is about 6-10 metres away from the wireless router, in a different room across the corridor.

So either I splash out on the correct lead and card to link with wires, or I find a way of downloading what I need within Windows (is this possible?).

- Amos

EDIT:

**iwconfig**```
[COLOR="Silver"]amos@Amos-Ubuntu:~$ gedit /etc/network/interfaces[/COLOR]
amos@Amos-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

**Interfaces:**```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

sit0      no wireless extensions.
```

Thanks again.

---

### Post by RomeReactor on 2007-02-02
Alright, since you need to download from a different computer, [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c49fa124c9a644ddc4d126256060b93888fe0be3")    page tells you what to download and how to install the packages on your Ubuntu.

---

### Post by amosharper on 2007-02-02
> **RomeReactor said:**
> Alright, since you need to download from a different computer, [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c49fa124c9a644ddc4d126256060b93888fe0be3")    page tells you what to download and how to install the packages on your Ubuntu.
[SIZE="1"](Not a different computer, just through booting with Windows instead of Ubuntu (I'm using a dual boot - I can get to my Ubuntu documents in Windows but not vice versa).)[/SIZE]

Great - I've saved everything you linked me to. Would you mind walking me though this? Thanks.
I know to install the files by changing directory in the terminal to the correct place and using:
```
sudo dpkg -i ndiswrapper-common_*.deb
  sudo dpkg -i ndiswrapper-utils*.deb
  sudo dpkg -i --force-depends ndisgtk_*.deb
```
By the way, should I use ndiswrapper-utils-1.8 with 'AMD64 architecture' or 'i386'?
I have an AMD Athlon processor, if this is what it is referring to.

Thank you!

- Amos

---

### Post by RomeReactor on 2007-02-02
> By the way, should I use ndiswrapper-utils-1.8 with 'AMD64 architecture' or 'i386'?
I have an AMD Athlon processor, if this is what it is referring to.

It refers to the architecture of the os you installed. Did you install Ubuntu AMD 64 or Ubuntu i386 (the 64-bit version or the 32-bit? Or do you know the name of the image you downloaded to burn the Ubuntu cd?

---

### Post by RomeReactor on 2007-02-02
Also

```
uname -r
```

should tell you what kernel you have.

---

### Post by amosharper on 2007-02-03
```
amos@Amos-Ubuntu:~$ cd Desktop
amos@Amos-Ubuntu:~/Desktop$ sudo dpkg -i ndiswrapper-common_*.deb
Password:
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 88191 files and directories currently installed.)
Unpacking ndiswrapper-common (from ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
amos@Amos-Ubuntu:~/Desktop$ sudo dpkg -i ndiswrapper-utils*.deb
Selecting previously deselected package ndiswrapper-utils-1.8.
(Reading database ... 88201 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.8 (from ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils-1.8 (1.18-1ubuntu2) ...
amos@Amos-Ubuntu:~/Desktop$ sudo dpkg -i --force-depends ndistk_*.deb
[B]dpkg: error processing ndistk_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndistk_*.deb[/B]
amos@Amos-Ubuntu:~/Desktop$ sudo dpkg -i --force-depends ndisgtk_*.deb
Selecting previously deselected package ndisgtk.
(Reading database ... 88213 files and directories currently installed.)
Unpacking ndisgtk (from ndisgtk_0.6-0ubuntu1_all.deb) ...
**dpkg: ndisgtk: dependency problems**, but configuring anyway as you request:
 ndisgtk depends on ndiswrapper-utils; however:
**  Package ndiswrapper-utils is not installed.**
Setting up ndisgtk (0.6-0ubuntu1) ...
```

What did I do wrong?

Also, when I'd finished with that, I got a yellow tooltip on the Synaptic icon in the top right corner as follows:
```
An error occurred, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'.
```

So I opened the Package Manager and a dialogue box says:
'You have one broken package on your system! Use the "Broken" filter to locate it.'
I click Close, and filter by 'broken' and the package 'ndisgtk' is marked as Status: Broken (a red-orange square).

Will this cause a problem? What do I do next? Massive thanks,

- Amos

---

### Post by RomeReactor on 2007-02-03
This is from Synaptic on Ndisgtk:

> ndisgtk is a GTK based frontend for ndiswrapper, allowing an easy way to
 install Windows wireless drivers.

**Ndisgtk** is a package that provides a graphical interface to NdisWrapper, nothing more. Don't worry if it didn't install correctly, as the [thread]("http://ubuntuforums.org/showthread.php?t=179801&highlight=wg311v3") that contains the installation instructions doesn't require it. It's all from the command line.

---

### Post by amosharper on 2007-02-03
Cool. Do I start from step 1 in Macdo's instructions? Thanks.

---

### Post by amosharper on 2007-02-03
The (very, very) good news is that I'm posting this from within Ubuntu! Massive thanks to you, RomeReactor.

I have one last problem. At the moment, I have my WEP encryption off. How do I configure it so that I can use encryption? (i.e. where's the dialogue that asks me for a WEP key etc?) Thanks once again,

- Amos

---

### Post by amosharper on 2007-02-03
I've fallen into a sticky situation here:

When I first followed the instructions, I got access to the internet (after taking the encryption off my network).

I restarted, and now have no connection (and the wireless card isn't recognised again). I tried following th steps again, but with no success - the terminal throws various errors such as SET failed on device wlan0 and No working leases in persistent database - sleeping.

Help! Thanks,

Amos

---

### Post by RomeReactor on 2007-02-04
You're really close to having your wireless correctly setup; i suspect all that's left are details. First run

```
sudo dhclient
```

to see if that brings your card back to life; after that command, enter

```
ping -c5 www.google.com
```

to verify that you have connection again. **Please note that in Dapper i had constant connection, but after upgrading to Edgy i have to run SUDO DHCLIENT WLAN0 to bring my card back online after shutting down and starting up or after reboot. Haven't found a solution for that one yet**. If pinging Google returns a negative, then run

```
iwconfig
```

again in your terminal; this time it will tell you which is the correct designation for your wireless card (look for **wireless extensions**). And run 

```
man iwconfig
```

and scroll down to the section starting with **key/enc[ryption]**; it will tell you how to put your key there. It's something like

```
sudo iwconfig wlan0 key **********
```

and remember that wlan0 may not be the correct designation (iwconfig will tell you). Another way to do it is

```
sudo gedit /etc/network/interfaces
```

and writing

```
wireless-key **********
```

after

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid YOUR_ESSID
wireless-channel 11
```

where you substitute all the asterisks for your key. I think it only supports WEP, though. A good graphical program to manage your connection is, in my opinion, **kwifimanager**, which will let you set up your encryption key; you can also try with **wifi-radar**; though i think it's more limited. Both are in Synaptic (but i guess that'll have to wait until you get your wireless up and running without trouble). Also find out if your router is setup as DHCP or STATIC.

---

### Post by RomeReactor on 2007-02-04
I also recommend this: in the terminal:

```
sudo gedit /boot/grub/menu.lst
```

when that opens, write

```
acpi=off
```

between **### BEGIN AUTOMAGIC KERNELS LIST** and **## DO NOT UNCOMMENT THEM, Just edit them to your needs**; save and close. This will not allow the card to power down due to power saving features.Then:

```
sudo gedit /etc/modprobe.d/aliases
```

search for **alias net-pf-10 ipv6** and change to **alias net-pf-10 off**. Save, close and reboot. This will disable ipv6 globally on your computer and should make for faster browsing.

---

### Post by amosharper on 2007-02-04
RomeReactor, I could kiss you! Once more, I'm posting from within Ubuntu - and with the encryption on.

Thank you so much,

- Amos

EDIT: Damn it! Same as last time - I had it, I lost it.

Surely it shoudln't be this hard? Here's what KWifiManager and my Windows driver say about the signal strength - maybe that's a problem in Ubuntu?
[http://i136.photobucket.com/albums/q187/amosharper/Screenshot3.jpg]("http://i136.photobucket.com/albums/q187/amosharper/Screenshot3.jpg") (NOLANNET is the neighbour).

Any ideas/help **massively** appreciated.

Thanks,

- Amos

---

### Post by RomeReactor on 2007-02-05
Forgot to tell you that, if i remember correctly, channel 11 is used for Mexico. On macdo's [how-to]("http://ubuntuforums.org/showthread.php?t=179801&highlight=wg311v3") he says that running

```
sudo iwlist wlan0 scan
```

tells you what channel to use.

EDIT: Just saw that you indeed seem to run on channel 11 also; try

```
sudo iwconfig wlan0 channel 11
```

From the screenshot you posted looks like you forgot to tell iwconfig what interface to assign channel 11. Another way would be

```
sudo iwconfig wlan0 freq 2.462G
```

Also open up Networking (System-->Administration-->Networking) and make sure your wireless connection appears there and is checked; it would probably be best if you un-check the others.

---

### Post by RomeReactor on 2007-02-05
I find it easier to make changes to the card's configuration just editing the **/etc/network/interfaces** file. Here's mine

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-channel 11
```

Try making the changes there if issuing commands through iwconfig doesn't seem to work. Also, i find that keeping a text file detailing the step-by-step procedure to setup my wifi card is invaluable; my file contains 12 steps and hasn't failed me yet. You should keep one too and save it to usb storage/burn on cd/save to floppy. You're almost done configuring your card!

---

### Post by amosharper on 2007-02-05
The problem is, every time I reboot, it manages to forget everything I told it - it doesn't even see the wireless card anymore.

It seems I'm so close, yet so far!

---

### Post by RomeReactor on 2007-02-05
I just read macdo's how-to and it looks to me he skipped a couple of steps that are really important (these are the ones that make NdisWrapper load at boot time!); so i'm sending you my file and, since you already have the drivers installed, you should start with step No. 2 (just to make sure the drivers are still loaded correctly).

The text in the boxes is to be added to the files you open with the commands; the commands themselves usually are the ones that start each step. Hope this helps you!

---

### Post by amosharper on 2007-02-05
Ha - well, I'll try this out, and get back to you! (High hopes).

EDIT: My hugest, greatest, massivest (?) thanks to you, RomeReactor. The two real problems were the fact that ndiswrapper wasn't being told to boot and the fact that I had put speech marks around my ESSID ("default" instead of default).

Now I'm on, are there any codec packs, utilities etc which you would recommend? I've already installed Amarok at a friend's suggestion.

EDIT 2: And whilst I'm here, any suggestions as to how to connect to my workgroup and therefore share printers etc?

Once again, many thanks,

- Amos

---

### Post by RomeReactor on 2007-02-05
Glad you managed to get your connection working!

Regarding codecs, i suggest you install Totem-Xine, LibXine1, LibXine-Extracodecs, Mplayer, Mozilla-Mplayer, and w32codecs (all in Synaptic); also [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability") will help you setting up Totem for DVD play. Mozilla-Mplayer is the best Firefox video plugin i've found. If you want to be able to watch YouTube, you'll need [Flash 9]("http://www.ubuntuforums.org/showpost.php?p=2098044&postcount=2"). Regarding workgroups and sharing printers, sorry, i really have no clue.

Post back if you encounter any roadblocks :mrgreen:

---

### Post by dpmccoy on 2007-02-07
> **RomeReactor said:**
> [This]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") is the one you need.

I recently posted a thread regarding a problem I am having with my Netgear WG311v3 card as well.  It is posted here: 

[http://www.ubuntuforums.org/showthread.php?t=354954&highlight=wg311v3](http://www.ubuntuforums.org/showthread.php?t=354954&highlight=wg311v3)

I'm using the driver that you recommended above.  I believe that my card is a v3.1.1, not a v3.1.0.  The Windows CD that came with the card says "Version 1.1".  Should I install the drivers from the CD instead of the FTP site?  I think that my card is the newest version; I bought it on January 5th, 2007.  Thanks for any help.

---

### Post by RomeReactor on 2007-02-07
Hi. I don't think your issue is with the driver; perhaps you didn't tell iwconfig which mode to use?

```
sudo iwconfig wlan0 mode Managed
```

I could be wrong, but changing drivers shouldn't be that much of a problem, so maybe you could give that a try:

```
ndiswrapper -l
```

will tell you the name of the driver; and

```
sudo ndiswrapper -e NAME_OF_DRIVER
```

will uninstall it. Then 

```
ndiswrapper -i DRIVER.INF
```

to install the drivers you want. Also, i believe your interfaces file should look like this:

```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp


#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid {omitted from post}
wireless-key {omitted from post}
```

Note that every other interface (besides **lo** and **wlan0**) is commented out, so as to not interfere with the others. Maybe doing this instead of changing drivers will help you. Post back and tell us how it went.

---

### Post by dpmccoy on 2007-02-08
Thanks for the tips.  Luckily, yesterday I heeded the advice that was posted in my original thread about using network-manager.  I grabbed Knetwork-manager, installed it, and configured it.  Now, my connection stays up.  I connected using my wife's laptop and on one occasion my IP address dropped, but the Knetwork-manager brought it back up.  
Your 'iwconfig wlan0 Managed' comment is duly noted; however, now that my /etc/network/interfaces file is commented out (save for the loopback) for Knetwork-manager, do I need to input this now?   Your tips are appreciated, BTW.

---

### Post by RomeReactor on 2007-02-08
I think now that you managed to get your connection working the way you want it to, there's no need. If your connection keeps dropping/disconnecting though, you can try it out and see if it helps. Another way of doing that is to open the **/etc/network/interfaces** file and editing it by hand:

```
kdesu kate /etc/network/interfaces
```

and adding

```
 wireless-mode managed
```

below your **wireless-essid** and **wireless-key** entries.

---

### Post by dpmccoy on 2007-02-08
Everything is working fine now.  I'm using knetwork-manager, and reset my router to use WPA2-PSK encryption.  I downloaded the hotfix for my wife's Windows XP system to enable WPA2 as well, and I am having no problems with my connection right now.  I'm almost certain that the problem was my use of network-admin instead of knetwork-manager, since I'm using KDE exclusively. 
I appreciate your tips!  Thanks.
BTW, I'm an old Mandrake/Mandriva user (versions 9.0+).  The support on this forum for all versions of Ubuntu is top-notch; way better than I ever experienced with Mandrake/Mandriva.

---

