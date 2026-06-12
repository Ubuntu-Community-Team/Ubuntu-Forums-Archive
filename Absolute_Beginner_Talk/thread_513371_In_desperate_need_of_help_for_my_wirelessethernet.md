---
title: "In desperate need of help for my wireless/ethernet"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-07-30
Hey folks. I've been working futily to regain some sort of connection for my nc8000 notebook. I've been trying to find some sort of solution for my problem, but I've found nothing . . .I don't even know what the problem is, other than to say that my internet is 'broken'. This is getting very frustrating for me, as I have no means whatsoever to connect to the internet using my laptop. I'm using a Windows machine right now, and I need to get this solved. I don't care if my machine is screwed. I just want to know what's going on so I can fix it asap. Please Help!! Thank you.

---

### Post by Inxsible on 2007-07-30
You need to give us a lot more information than the fact that your internet is "broken", if you need us to help you.

What exactly is the problem? Do you see any errors? If so, what are they?

What have you tried doing until now?

---

### Post by CheshireMac on 2007-07-30
> **Inxsible said:**
> You need to give us a lot more information than the fact that your internet is "broken", if you need us to help you.
 
What exactly is the problem? Do you see any errors? If so, what are they?
 
What have you tried doing until now?
Okay, here we go. 
I run on Edgy, with an HP nc8000 . . .I have an Intel 2200BG wireless card . . .there are no errors, but there is no connection. 
Power management, as well as the radio are off on ETH1, and there is an error (Input/Output) when I try to turn the power on . . .I don't know how to switch the radio. 
I've tried scanning for a connection, but to no avail, and that's about as far as I know how to take myself.

---

### Post by CheshireMac on 2007-07-30
So having said that, is there anything else that I'm able to do to figure out what's going on with my computer?
I don't even care about the solution. . . I need to find what the problem is first.

---

### Post by Inxsible on 2007-07-30
> **CheshireMac said:**
> So having said that, is there anything else that I'm able to do to figure out what's going on with my computer?
I don't even care about the solution. . . I need to find what the problem is first.
I am assuming, that the internet never worked. Have you tried installing ndiswrapper to see if your card works. Search the forums for ndiswrapper, and you will find a bunch of how-tos

Feisty has better support for wireless, so maybe upgrading to Feisty could be a solution.

---

### Post by CheshireMac on 2007-07-30
> **Inxsible said:**
> I am assuming, that the internet never worked. Have you tried installing ndiswrapper to see if your card works. Search the forums for ndiswrapper, and you will find a bunch of how-tos
 
Feisty has better support for wireless, so maybe upgrading to Feisty could be a solution.
I have had a connection before . . .sorry. That was vital to this problem, I think.
I do have ndiswrapper, and I've had both wired/wireless connections in the past. They have since ceased to work, and I apologize again for forgetting to mention that.

---

### Post by CheshireMac on 2007-07-30
Any thoughts on what's going on here? 
I looked up help on ndiswrapper, but all it says is that without an internet connection, I'm pretty screwed. I have ndiswrapper, but no connection, obviously. 
ARGH!!! This problem has plagued me for two weeks. I need to have it fixed so I can start working on my computer away from home. 
I'll follow anyone's instructions if they know what they're doing, and I'll answer any question I'm able to answer.

---

### Post by bukwirm on 2007-07-30
The Intel 2200 B/G Wireless card should work just fine without ndiswrapper - at least it does for me.

What is the output of:

lshw -C network
iwlist scan
iwconfig

---

### Post by CheshireMac on 2007-07-30
> **bukwirm said:**
> The Intel 2200 B/G Wireless card should work just fine without ndiswrapper - at least it does for me.
 
What is the output of:
 
lshw -C network
iwlist scan
iwconfig
 
The first is weird . . .it's like another menu . . .what am I looking for?
 
The second shows no scan results for Eth1, and the others don't support scanning.
 
The third shows all the connection options (Lo, Irda0, Eth0, Eth1, Sit0). Eth1 is my wireless.
The readout on Eth1 is :
radio off  ESSID: off/any
Mode:Managed  Channel:0  Access Point: Not-=Associated
Bit Rate: 0 Tx-Power=Off  Sensitivity= 8/0
Retry Limit:7  RTS thr: Off  Fragment: Off
Power Management:On
Link quality:0 Singnal level:0  Noise level: 0

---

### Post by CheshireMac on 2007-07-30
Okay . . . I'm still looking, but all I seem to find are recycled answers that do nothing for me except explain rhetoric and things I already know. 
I'm about to go insane here, and I haven't made ANY progress. If anyone can just take some time to walk me through this, I'd jump for joy. 
The only help I've been offered over the last week has been simple diagnostic checks, which have not helped me at all, since they only lead to people not responding after the read-out. 
I don't mean to sound agitated, but that's where I am right now.

---

### Post by CheshireMac on 2007-07-30
Okay, so I've run out of time on this computer, and I have to leave. I will be back tomorrow to spend another several hours trying to fix this problem. If anyone has any ideas between now and then, please let me know. 
I'd also be up for emailed solutions. Email me @ [EMAIL="macpublishing@gmail.com"]macpublishing@gmail.com[/EMAIL]
I'd love to get this issue out of the way so I can start using Ubuntu normally again. :) Thanks.

---

### Post by bukwirm on 2007-07-30
Your wireless card appears to be turned off - there should be a switch or a key combination that allows you to turn it on.

For the "lshw -C network" command, it should flicker though a couple of messages, then print your network devices.

You mentioned in an earlier post that you get an i/o error when you try to turn the wireless card on - what does that error message say?

Is your wired connection working?

Also, post the content of the file "/etc/network/interfaces".

---

### Post by ethan961 on 2007-07-30
I am having a similar problem with the same card.
```
sudo lshw -C network
``` gives
```
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:01:1f:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:40100000-40100fff irq:11

``` 
(ignoring my ethernet)
```
iwlist scan
``` produces
```
eth1      No scan results

```
(again ignoring ethernet)
and ```
iwconfig
``` gives
```
eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Network manager shows no wireless networks.
What do I need to do? :confused:


UPDATE: dmesg revealed that it has something to do with the firmware.
```
dmesg | grep ipw
[   32.256000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   32.256000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   32.256000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   33.188000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   33.212000] ipw2200: Firmware error detected.  Restarting.

```

---

### Post by CheshireMac on 2007-07-31
> **bukwirm said:**
> Your wireless card appears to be turned off - there should be a switch or a key combination that allows you to turn it on.
 
For the "lshw -C network" command, it should flicker though a couple of messages, then print your network devices.
 
You mentioned in an earlier post that you get an i/o error when you try to turn the wireless card on - what does that error message say?
 
Is your wired connection working?
 
Also, post the content of the file "/etc/network/interfaces".
 
I have no wired connection to speak of, and the error for the switch is an input/output error . . . 8B2C is mentioned in that .
The network file shows:
```

auto lo
iface lo inet loopback
 
 
auto eth2
iface eth2 inet dhcp
 
auto ath0
iface ath0 inet dhcp
 
auto wlan0
iface wlan0 inet dhcp
 
 
 
 
iface eth0 inet dhcp
```
I thought my wireless was supposed to be eth1, but it's not there at all . . . It used to function under that . . . also, someone had mentioned that my wireless wassupposed to be wlan0 or wlan1 . . .what's wrong here?

---

### Post by bukwirm on 2007-07-31
CheshireMac: It appears (from a little searching and an  [HP support forum]("http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=567021")) that the HP nc8000 has a non-standard wireless power switch. So, you could try a couple of things:
```
1. If you have Windows installed, turn the card on in Windows and leave it on
2. Try to find and install the firmware for the HP version of the wireless card
3. Try installing a different version of the firmware from the link given 
    below (probably won't work)
```

eth1 is the interface name that the Intel 2200BG driver uses - other drivers use different interface names.


Ethan961: Try installing new firmware, which can be found [here]("http://ipw2200.sourceforge.net/firmware.php").

---

### Post by CheshireMac on 2007-08-01
> Ethan961: Try installing new firmware, which can be found [here]("http://ipw2200.sourceforge.net/firmware.php").
Okay . . .so if I install the correct firmware, that would include the driver, and whatever else the card requires to function?

---

### Post by CheshireMac on 2007-08-01
Alright. I have HP support in a chat right now, although they seem to be rather useless . . .it seems that they only support Windows issues, but I'm hoping something will happen here . . .If something doesn't happen with them, am I lost or what? I've been troubleshooting for two weeks now, and to no avail. It almost seems like I should have just kept Windows and been naive about the simplicity.

---

### Post by CheshireMac on 2007-08-01
> **CheshireMac said:**
> Alright. I have HP support in a chat right now, although they seem to be rather useless . . .it seems that they only support Windows issues, but I'm hoping something will happen here . . .If something doesn't happen with them, am I lost or what? I've been troubleshooting for two weeks now, and to no avail. It almost seems like I should have just kept Windows and been naive about the simplicity.
Alright, so HP just totally left me hanging with the typical "We don't support that, so we think you suck" routine. It's rather unsettling, but they gave me the link for the Windows firmware . . . does anyone know if it would be supported in a different architechture?

---

### Post by bukwirm on 2007-08-01
Firmware is generally platform-independent, I think. What's the link they gave for the firmware?

By the way, what is the output of "dmesg | grep ipw2200"?

> **CheshireMac said:**
> Alright, so HP just totally left me hanging with the typical "We don't support that, so we think you suck" routine.
All too common, unfortunately.

---

### Post by ugm6hr on 2007-08-01
Not sure if this has anything to do with your problem - but it looks like the HP BIOS does some kind of check to see if the wifi is "HP verified".  Linux is supposed to be able to bypass this problem - but perhaps it hasn't?

[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=567021&admit=-682735245+1186006932910+28353475](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=567021&admit=-682735245+1186006932910+28353475)
Mark Wrightson post

---

### Post by anewguy on 2007-08-01
First of all, I don't have your wireless card, but have been through the same frustrations, as you will find MANY MANY others have with their wireless.  So, while frustrating, please tolerate my instructions and see what they do for you.  I have downloaded the service pack from HP for your laptop and the wireless you described.   Since I don't have your wireless card, please be sure it is "turned on" as others have mentioned, then try these instructions.  Bear with us - we've been there, we've "re-done everything from the very basics" a zillion times ourselves.  Sooooo:

(1) do the following in a terminal window:

ndiswrapper -l     and press enter   (that's a lower case "L")

If it returns any output, please do the following:

sudo ndiswrapper -r xxxxx     and press enter, where xxxxx is the name of a driver as shown in the output from the list command above

do this until nothing show from the list command

(2) Place the following 3 files on your desktop (they are the driver files you must already have if you are using ndiswrapper):

w22n50.sys
w22n51.INF
w22n51.sys

From what I see in the HP driver package, these are the files you need.

(3)  sudo ndiswrapper -i ~/Desktop/w22n51.INF  and press enter

If this gives an error, please report it here.

(4) sudo ndiswrapper -l  and press enter (lower case "L" again)

Does that show w22n50 or w22n51 as installed?

If so:

sudo modprobe ndiswrapper  and press enter

sudo depmod -a  and press enter

sudo ndiswrapper -m and press enter

Just for the heck of it, reboot Ubuntu.

Go to system/administration/network.  Check to see if the wireless is shown there and if it says "roamiing mode enabled" - you may have to click the box to enable it.  Then exit.

See if the wireless network you want to connect to shows now and see if you can connect to it.

BTW - I prefer to use network-manager-gnome myself (just a personal preference).  When you get wireless working you might want to install it.

Please post back the results of this and if you have any errors along the way.  If you need the 3 driver files I mentioned, let me know and I can try to email them to you.

Please post back - we're trying to help!:)


EDIT:  I also noticed on the HP site that there is a BIOS update for your PC dated June of this year.  Did you install that yet?

EDIT:  Looking in the .inf file it appears there might be some sort of power control for your wireless card as well.  I assume there was some software in Windows that managed the card and you were able to change your signal strength as well.  If so, you may want to boot into Windows and set your signal strength to maximum and see if that does anything for your moving to another room stuff.

---

### Post by CheshireMac on 2007-08-02
Hey folks. Good morning. I'm back at it again today, and I've noticed all the helpful thoughts from everyone. Thanks a lot, people. This is fantastic. 
Unfortunately, when I try to work through the ndiswrapper bit that "anewguy" discussed, it shows that the driver I found is invalid . . . I'm not entirely discouraged though, because I also have the firmware for the driver to deal with . . . if there is no firmware, the driver is useless right? So now I have this package to send . . .where?
 
Also, when I insert the CD to try ndiswrapper freshly, the CD doesn't prompt me to install any new packages . . .Should I just get rid of the older ndiswrapper and install the new one?

---

### Post by anewguy on 2007-08-02
Well, something I fooled around with after your latest post:  it turns out the LiveCD for Ubuntu 6.10 shows as containing software packages, but the 7.04 LiveCD does not.  Sorry!

Does the invalid driver show in ndiswrapper before you start the procedures I outlined, or after them?  What is the exact message?  I've had this happen in the past when I messed up the complete path/filename of the driver in ndiswrapper.  I would try "ndiswrapper -r xxxxxx" where "xxxxxx" is the name that shows as the invalid driver, and keep doing this until ndiswrapper returns nothing.  Then I would go back through the loading of the driver with ndiswrapper again, being very sure to get the path/filename correct.

As far as firmware, using ndiswrapper loads in the Windows version of the drivers for your card, so that should handle the "firmware" idea.   As an example,  there is a firmware cutter for the broadcom 43xx based cards.  It takes the place of ndiswrapper if you use it.  In your case, I believe you will have to use ndiswrapper.  I think that would take care of your firmware message, but I have never had that so I don't know.:)

---

### Post by bukwirm on 2007-08-09
Take a look at [this website]("http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/") - might be worth a try.

---

