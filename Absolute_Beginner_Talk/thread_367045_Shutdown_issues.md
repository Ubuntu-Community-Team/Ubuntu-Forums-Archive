---
title: "Shutdown issues"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by grEnAlEins on 2007-02-21
I just installed Ubuntu 6.10 on my notebook about a week ago.  I had to reinstall it to the partition it was on and reinstall it last night (deleted the partition and then remade it).  Everything is fine accept for two things:

1) After I shutdown, the notebook turns completely off.  After a minute or two, the notebook boots up without me doing anything.  It is not as if it reboots, but it completely shuts down, kills the power, the machine goes silent, and then after a minute or two it boots back up.  I cannot figure out what happened.  This happens regardless of if the notebook is opened of closed.  Did I do something wrong?  If so what, and how do I fix it?

2) Ubuntu will not recognize my wireless card.  This is not a big issue, as the person who originally set up Ubuntu for me made it work the first time, and should be able to do so again.

I really do not know much about Linux at all at this point, so if the advice could be "dumbed down" that would be terrific.  I did the base install, performed the ~135 updates and then did/added the following:

changed the color of terminal to green on black
typed  (interminal):
sudo passwd root
my password
my new UNIX password x2

I then exited terminal.

Adobe Flashplayer (ver. 9, .tar .gz, IIRC, it was not the .rpm one)
Xine Media Player
Gweled
A theme package for Gaim

I have no idea what to do.  I have tried google, and also the search feature here.

Thanks in advance for your assistance,

Nick

---

### Post by mahy on 2007-02-21
Not sure about the shutdown issue. Never heard anything like that before.

To install things, you can use "apt-get install [packagename]", or GUI programs such as Synaptic and Adept. This is the preferable way. Otherwise you have to download an archive (.tar.gz usually) and there are 3 possible ways (only 1 at a time):

1.) just unpack it and run
2.) unpack and run some installation script
3.) compile and install (the last resort ;) )

EDIT: I don't recommend Flash 9. It doesn't support Opera and causes my Firefox to crash... Drat!

---

### Post by teaker1s on 2007-02-21
I read about dodgy shutdown and random restarts on laptops recently, it was a bios issue-try seeing if your manufacturer has a newer bios firmware

---

### Post by grEnAlEins on 2007-02-21
> **teaker1s said:**
> I read about dodgy shutdown and random restarts on laptops recently, it was a bios issue-try seeing if your manufacturer has a newer bios firmware

I bought the notebook a little over two weeks ago (on or about 2/5/2007).   The BIOS on my machine should be new, right?.

It was not doing this before I reinstalled it.  It worked perfectly until I reinstalled the OS, so I am thinking that I maybe did something wrong:confused: ??

---

### Post by teaker1s on 2007-02-21
between manufacture and shipping could have been weeks-worth checking to see latest avaliable bios

---

### Post by grEnAlEins on 2007-02-21
> **teaker1s said:**
> between manufacture and shipping could have been weeks-worth checking to see latest avaliable bios

There is an update, but I seem to be having difficulty.  There are two versions.  My laptop is a Compaq Presario C500.  How do I know whether I have the C500EU or C500EA?  I have a funny feeling that I have EA, but I do not know if I do, or why I think that:confused:

EDIT: Ok, so I ran HP's auto update from my Windows Vista Partition.  It says that my BIOS and/or ROM is up to date.  It is version F.11, but I saw version F.14a online for C500EA and EU.  My machine says C500 on the service sticker, but there are no letters

---

### Post by linux_kid on 2007-02-21
Its probably a vista problem :)
Look at the white HP sticker on the bottom of your laptop and see the product number above the word "warranty"

---

### Post by teaker1s on 2007-02-21
the update checker is crap, you want to chat using hp live chat and confirm the exact model as a wrong bios update will kill computer:KS 

when your sure on model full battery and power connected and update:popcorn:

---

### Post by grEnAlEins on 2007-02-21
> **teaker1s said:**
> the update checker is crap, you want to chat using hp live chat and confirm the exact model as a wrong bios update will kill computer:KS 

when your sure on model full battery and power connected and update:popcorn:

Just did what the above two posts said.  I am flashing the BIOS right now...

It figures that it would be a Vista Problem :rolleyes: :p 

After that I will give it a try and let you all know how it goes.  Thank you sooooo much for the quick help:)

---

### Post by linux_kid on 2007-02-21
I know it's not normal to do this in forums, but...

Your Welcome  :guitar:

---

### Post by teaker1s on 2007-02-21
:guitar:  air guitar lol

hows the firmware update

---

### Post by grEnAlEins on 2007-02-21
Updating the BIOS worked like magic, so now it is on to my wireless card issue...

[QUOTE=mahy]To install things, you can use "apt-get install [packagename]", or GUI programs such as Synaptic and Adept. This is the preferable way. Otherwise you have to download an archive (.tar.gz usually) and there are 3 possible ways (only 1 at a time):

1.) just unpack it and run
2.) unpack and run some installation script
3.) compile and install (the last resort )[/QUOTE]

I know the general idea of using synaptic, but how do I know what to download?  I tried downloading a GUI application that was supposed to detect windows wireless cards that I read about on another forum (which I found while google searching).  This program could not detect the card either.  Vista can detect and use it, so I at least know that it is there and functional... I recall seeing the person who initially set up Ubuntu/ the wireless access for me using apt-get something, but I do not recall exactly what.  He also used the grep command to find something and download something relating to it.  I know that grep is essentially a search, but I do not know much more than that.  Can anyone give me a "dummy version" of what to do?

---

### Post by linux_kid on 2007-02-21
Two things:
1. change the thread topic to somthing envolving wireless cards

2. what wireless card do you have?

---

### Post by teaker1s on 2007-02-21
terminal ```
lspci
```

little L at start not i

---

### Post by grEnAlEins on 2007-02-21
I got a long list of output, but I think that what I'm looking for is one of these two:

Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

or

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

My guess is that it is the first one.  Is that what I am looking for?

---

### Post by linux_kid on 2007-02-21
yes, thats what we want...
Try searching this forum for Ndiswrapper for how to use your card

Worse comes to worse, you can always use Linuxant (google it)

---

### Post by teaker1s on 2007-02-21
better still I helped with the wiki page:KS 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
also in my signature below broadcom it's the exact model you have

---

### Post by pixeldotz on 2007-02-23
do you have an update on this issue by any chance?

reason i ask is because i just bought this laptop today and havent installed ubuntu yet but i'm itching to do it in dualboot (only so i can run the partition image incase i ever need to send it in for repair or whatever)

---

### Post by grEnAlEins on 2007-02-24
Not yet.  I had a bit of a hectic week and this was not a priority, as my wireless card works on my windows partition.  I will update on Tuesday when I get a chance to fiddle with it again.

---

### Post by grEnAlEins on 2007-03-14
I tried going through the steps from the wiki entry and it did not work.  I followed the steps exactly, and got an error during step 3, preparing the Linux build environment.  I got an error installing the Linux headers.  Does anyone have any input?

---

### Post by teaker1s on 2007-03-14
linux headers require either alternate.iso(downloaded under other options ie.-not live install iso) or a working ethernet connection as they are downloaded from either cd or internet.

for cd 
```
sudo apt-cdrom add
```
```
sudo apt-get update
```
now search and install packages


ethernet internet
```
sudo apt-get update
```
now search and install packages

---

### Post by grEnAlEins on 2007-03-14
sudo apt-get update

and

sudo apt-get install build-essential

both worked.

then next step lines of code is where I ran into trouble...

---

### Post by teaker1s on 2007-03-14
are you getting package not found or  a command error?

if an error then you need to carefully retype the command as we are telling ubuntu to install headers matching the current kernel

---

### Post by grEnAlEins on 2007-03-14
i typed it right, it gave a bunch of error messages that files could not be found or did not exist.  I tried to start over, and now I cannot uninstall ndiswrapper [sigh]

---

### Post by teaker1s on 2007-03-14
try this it's a gui way
```
uname -r
``` this output is your kernel version
```
gksudo synaptic
```
search "linux-headers" select one to match your kernel and install.

if you have no internet access we could try ndiswrapper from repository(alternate.iso)
```
gksudo synaptic
```
hit reload (should ask for cd, if not hit edit and add cdrom, then reload)
search ndiswrapper-if you are running edgy you should see a load of ndiswrapper packages
tick ndiswrapper related
ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8 (or there may be 1.9)
install
search with synaptic "network-manager-gnome"
when installed in terminal
"ndiswrapper" if it comes up with a list of commands then you can carry on and install your windows driver

---

### Post by grEnAlEins on 2007-03-14
all of them that matched were installed, but I re-installed them anyway.

It still will not work...

---

### Post by teaker1s on 2007-03-14
please give more detail have you installed your windows driver **and blacklisted native driver?**
```
sudo ndiswrapper -i nameofdriver.inf
```

output of```
 sudo ndiswrapper -l
```

if it says driver and hardware present then

```
sudo modprobe ndiswrapper
``` light on?

---

### Post by grEnAlEins on 2007-03-14
> **teaker1s said:**
> please give more detail have you installed your windows driver **and blacklisted native driver?** [COLOR="Red"]I did blacklist the native driver, I think I installed the windows driver, I got it from compaq's site.[/COLOR]
```
sudo ndiswrapper -i nameofdriver.inf
```

output of```
 sudo ndiswrapper -l
```
[COLOR="Red"]bcmwl5                  driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)[/COLOR]
if it says driver and hardware present then

```
sudo modprobe ndiswrapper
``` light on?
[COLOR="Red"]did nothing, and the light on my wlan on/off did not turn on, nor did it when the wireless was working the first time (but I reformatted my partition some time ago, which spawned this issus)[/COLOR]

see above, my reply is in red

---

### Post by teaker1s on 2007-03-14
what do you get with 
```
iwconfig
```

---

### Post by grEnAlEins on 2007-03-14
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/\ that is the output for iwconfig

---

### Post by grEnAlEins on 2007-03-14
the smillies are supposed to be a ":" followed by a "o"... LOL!

---

### Post by teaker1s on 2007-03-14
> **grEnAlEins said:**
> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
         [COLOR="Red"] Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B[/COLOR]   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/\ that is the output for iwconfig
as I understand it your wireless is now on (red)
```
gksudo gedit /etc/modules
```

Add the word "ndiswrapper" if not there already and save the file using "save as" this will then load everytime you boot 

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by grEnAlEins on 2007-03-14
> **teaker1s said:**
> as I understand it your wireless is now on (red)
```
gksudo gedit /etc/modules
```

Add the word "ndiswrapper" if not there already and save the file using "save as" this will then load everytime you boot 

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

output was:

(gedit:7422): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and a file opened that said this:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


I assume that this file is where I add ndiswrapper

---

### Post by teaker1s on 2007-03-14
yes correct then:-"file tab" and "save as" and save it

---

### Post by grEnAlEins on 2007-03-14
done.  I rebooted, and it still is not working...lol.

---

### Post by teaker1s on 2007-03-15
you may not be able to see it as it's refered to as eth1 
if you read the tutorial I recommended it comments on this and how to force to become wlan. 

Further to this if you still can't see wireless with network-manager-gnome then the tutorial suggests and tells you how to turn the afterburner feature off. 

If gui wireless won't work, the tutorial advices how to configure via terminal your essid and network key.
other than this If you feel that you have covered all the guide completely then a polite pm to **frodoB** may get you a suggestion or 2

---

### Post by grEnAlEins on 2007-03-16
It is working now, well, sort of...

I am able to access my school's wireless network now, but the steps from the wiki page that were suppossed to make everything work with network manager (auto scanning for networks and whatnot, as well as the WPA support) are not working so well for me (so no scanning or wpa support).  I am able to control the card through terminal, but I have a question about this.  Because it will not auto scan, I have to manually scan through terminal and pick the network I want, then input the network name and keys manually... correct?

I was not able to make this work, but I did take it to one of the IT guys at my school.  He made it so it was able to use the school's network, but I am not quite sure how.  He did some crazy things in terminal.  I have no clue what...

I really do appreciate all of the help you (teaker1s) have given.  Thanks a million:biggrin:

---

### Post by teaker1s on 2007-03-16
glad you have a partial solution, the problem with ndiswrapper is we are using windows drivers, If this chap at your school is keen on linux you may be able to get him to try wifi radar instead of  network-manager-gnome. 
But I suggest if it's working that you do the above only with his help, in case it won't work

---

### Post by grEnAlEins on 2007-03-22
I installed wifi radar and it works like a charm.  Sorry to up this thread (again).

Thanks for all the help,

Nick

---

### Post by teaker1s on 2007-03-25
:guitar: :guitar: :guitar:  result

---

