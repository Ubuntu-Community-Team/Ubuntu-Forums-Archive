---
title: "Bluetooth no longer working"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by useResa on 2007-04-24
Since my upgrade to Feisty my mobile phone (SAMSUNG SGH-D900) can no longer connect to my laptop (DELL Latitude D620). It used to work flawlessly in Edgy.
What I used to do is go to *Applications --> Accessories --> Bluetooth File Sharing*, switch on bluetooth on my phone and I could transfer files between my laptop and my phone. Since the upgrade my phone cannot find my laptop anymore.

Here is some information on what I have tried so far.
Using *hcitool* I get the following results
```
rdrijsen@rdrijsen-laptop:~$ hcitool scan
Device is not available: No such device
rdrijsen@rdrijsen-laptop:~$ hcitool dev
Devices:
```Next I issued
```
rdrijsen@rdrijsen-laptop:~$ sudo hciconfig hci0 reset
```Then using *hcitool* again I get the following results
```
rdrijsen@rdrijsen-laptop:~$ hcitool scan
Scanning ...
        00:17:D5:A6:6A:E4       SGH-D900
rdrijsen@rdrijsen-laptop:~$ hcitool dev
Devices:
        hci0    00:16:41:8F:C3:58
```Using *sdptool* the result I get is
```
rdrijsen@rdrijsen-laptop:~$ sdptool browse 00:17:D5:A6:6A:E4
Browsing 00:17:D5:A6:6A:E4 ...
Service Name: WBTEXT
Service RecHandle: 0x10000
Service Class ID List:
  UUID 128: db1d8f12-95f3-402c-9b97-bc504c9a55c4
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x1cdb1d8f-1295-f340-2c9b-97bc504c9a55)
    Version: 0x0100

Service Name: Serial Port
Service RecHandle: 0x10001
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Profile Descriptor List:
  "Serial Port" (0x1101)
    Version: 0x0100

Service Name: Dial-up Networking
Service RecHandle: 0x10002
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Voice GW
Service RecHandle: 0x10003
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Voice GW
Service RecHandle: 0x10004
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0101

Service Name: Advanced audio source
Service RecHandle: 0x10005
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service RecHandle: 0x10006
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10007
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Object Push
Service RecHandle: 0x10008
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100
```Please also find below the content of */etc/bluetooth/rfcomm.conf*
```
rdrijsen@rdrijsen-laptop:~$ cat /etc/bluetooth/rfcomm.conf
#
# RFCOMM configuration file.
#

rfcomm0 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:17:D5:A6:6A:E4;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "SGH-D900";
}

rfcomm3{
       # Automatically bind the device at startup
       bind yes;
       # Bluetooth address of the device
       device 00:17:D5:A6:6A:E4;
       # RFCOMM channel for the connection
       channel 6;
       # Description of the connection
       comment "OBEX File Transfer"
}
```My questions are:
[LIST=1]
[*]Can anyone explain why I have to reset before any devices are found?
[*]Can anyone help me getting bluetooth working again?
[/LIST]
TIA.

---

### Post by azzoti on 2007-04-26
I've got a Dell Latitude D620 Core2 Duo and bluetooth file transfer is working in both directions you describe is working for my Nokia 6234. This is the first time I have tried it and I am impressed. (sorry). Feisty 7.04.  I blogged about my install here: [http://jroller.com/page/azzoti](http://jroller.com/page/azzoti)

---

### Post by lingnoi on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

I'm also getting this problem on my Samsung r55, after I upgraded it couldn't detect my built in bluetooth device anymore.

By typing lsusb it shows I have a USB Bluetooth device plugged in?

---

### Post by useResa on 2007-04-27
> **lingnoi said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375) 
I know, I posted the bug  :lolflag:


> **lingnoi said:**
> I'm also getting this problem on my Samsung r55, after I upgraded it couldn't detect my built in bluetooth device anymore.Are you the one who has also indicated that he has the same problem as described in the bug?
If not, someone else with a Samsung R55 is experiencing the same problem.

---

### Post by lingnoi on 2007-04-29
Yes its me. I wanted a link to the tracker for others in the forum.

---

### Post by useResa on 2007-05-01
> **lingnoi said:**
> Yes its me. I wanted a link to the tracker for others in the forum.Ok, clear.

In further search on how to get bluetooth working again, today I installed the package obexpushd.
This resulted in the fact that I do no longer have to issue the command "**sudo hciconfig hci0 reset**", but that my phone is immediately detected when using "**hcitool scan**".
However, I still can not transfer files from my phone to my laptop (it is not being detected)

---

### Post by monkster on 2007-05-03
I too am having this problem. Bluetooth syncing with a palm tungsten e2 worked fine with Edgy (although it was difficult to set up), now it is broken. I get a complaint about the sdp server, which I never got before:
```

:~$ sudo dund --nodetach --listen --persist --msdun call palm
dund[16665]: Bluetooth DUN daemon version 3.9
dund[16665]: Failed to connect to the local SDP server. No such file or directory(2)

```

Any pointers very much appreciated.

---

### Post by lingnoi on 2007-05-16
I am still having problems and there seems to be no way to fix it.

I can scan for Bluetooth devices but it is the only thing that seems to work. I also seems to detect my laptops internal Bluetooth as a USB Bluetooth dongle.

:(

---

### Post by useResa on 2007-05-16
> **lingnoi said:**
> I am still having problems and there seems to be no way to fix it.
:(I am experiencing the same. My laptop detects my phone (with some fiddling) but there is no way that I can get my phone to detect my laptop.
 
Furthermore I use to be able to get a listing of the "folders" on my phone and this I have not had working since the upgrade to Feisty.
 
Let's just hope that someone will pick up the bug and create a fix for it.

---

### Post by lingnoi on 2007-05-21
Its been a few weeks now and still no way to fix this.

Is it because I don't have a necessary package?

---

### Post by e_man_88 on 2007-05-27
I believe I have a similar problem. I have a Samsung D800, and I cannot send files from my phone to my hp dv5000 laptop which has bluetooth built-in. 

hcitool dev:
```
Devices:
        hci0    00:16:41:7D:59:99
```

hcitool scan:
```
Scanning ...
        00:17:D5:37:EB:56       D800

```

So it seems the computer can detect both its bluetooth and my phone. But when I try to send a file from my phone, the Samsung is unable to detect my computer.

Is there any solution to this?

---

### Post by blue_shift on 2007-05-27
Same experience with a k750i.

After scanning with hcittool, I found my phone, but BT Explorer (running on k750i) cannot find computer.

I can't speak for ubuntu, but I think kubuntu's implementation of bluetooth changed between edgy and feisty. Did your upgrade prompt for you to either overwrite or keep your bt config file?

Has anyone had this problem on a fresh install of feisty?

---

### Post by useResa on 2007-05-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **e_man_88 said:**
> Is there any solution to this?

> **blue_shift said:**
> Same experience with a k750i.
After scanning with hcittool, I found my phone, but BT Explorer (running on k750i) cannot find computer.


Would you both be so kind to also post your problems in the bug I have reported on this issue. TIA

---

### Post by blue_shift on 2007-05-27
> **useResa said:**
> 	Would you both be so kind to also post your problems in the bug I have reported on this issue. TIA

Done.

I can only assume there's a specific cause (ie not simply that fiesty can't do bluetooth) or this would have been caught earlier.

---

### Post by useResa on 2007-05-27
> **blue_shift said:**
> Done.Thank you

> **blue_shift said:**
>  I can only assume there's a specific cause (ie not simply that fiesty can't do bluetooth) or this would have been caught earlier.The strange thing I find is the fact that the desktops/laptops can see the phone but that the phones cannot find the boxes. As if it is hidden or so.

I just hope they will pick up the bug soon and that it gets sorted out.

---

### Post by e_man_88 on 2007-05-28
> **useResa said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375) [br].[/br] ----------------------------			
Would you both be so kind to also post your problems in the bug I have reported on this issue. TIA

Yup, I reported my problem in the bug. I also find it strange how the computer is able to detect the phone just fine, yet my phone can't see the computer. I hope this gets sorted out soon.

---

### Post by useResa on 2007-05-28
> **e_man_88 said:**
> Yup, I reported my problem in the bug.Thank you

> **e_man_88 said:**
> I also find it strange how the computer is able to detect the phone just fine, yet my phone can't see the computer. I hope this gets sorted out soon.**[COLOR=Lime]+1[/COLOR]**

---

### Post by blue_shift on 2007-05-29
[QUOTE=useResa]As if it is hidden or so.[/QUOTE]
Have you a laptop or anything else with bluetooth which can scan for indiscoverable machines on a bluetooth network? I know it can be done by some programmes, but nothing I can run from my 'phone, I don't think.

---

### Post by lingnoi on 2007-06-07
There seems to be a lot of people with this problem but no way to draw developer attention to fixing it.

I was looking at the next release and it doesn't look like any of the Bluetooth packages have changed so we are going to have the same problems in Gutsy too. :(

Is there anyway to get this flagged and looked at by someone higher up the food chain?

---

### Post by dirken on 2007-06-09
I am having almost the same problems. I can detect my phone from my laptop and I can find my laptop from my phone but letting the laptop make a connection to the phone doesn't work, I can let my phone make the connection and the pairing goes well but suddenly the phone starts to ask the computer a service list wich gives an error beacause apperantly there isn't one.

Any idea??

Greetz..
Dirken

---

### Post by dirken on 2007-06-09
It seems like i have made some progress.
Thanks to this tutorial: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
It made me connect to the phone, i had to enter a pin on the phone and the computer, then I had to try to connect again, my phone asked if it was ok to make a serial connection with my laptop, i said yes and then in my terminal came this message:
Can't open input device: No such file or directory (2)

I don't know what the hell that means but it should work!
Any help is welcome!

Greetz..
Dirken

---

### Post by dirken on 2007-06-09
Allright, even more progress :p
I can now send files from the phone to my laptop but not the other way. I got this working by opening the Bluetooth File Sharing app (Applications -> Accesoires) and then i try to get a new list service list. Everything went fine till then. But then tried to browse my laptop and didn't work. But could send image to laptop.

Now anyone on how to send form computer to phone? Cause that's what i really need :s

Greetz..
Dirken

---

### Post by useResa on 2007-06-10
> **dirken said:**
> Allright, even more progress :p
Congratulations!

> **dirken said:**
>  I can now send files from the phone to my laptop but not the other way. I got this working by opening the Bluetooth File Sharing app (Applications -> Accesoires) and then i try to get a new list service list. Everything went fine till then. But then tried to browse my laptop and didn't work. But could send image to laptop.
For some reason you seem not to have the same problem as we are having.
We use to have the same abilities as you but have lost this functionality when upgrading to Feisty  :(

> **dirken said:**
>  Now anyone on how to send form computer to phone? Cause that's what i really need :sI have never done this, but according to [this post]("http://ubuntuforums.org/showpost.php?p=1954248&postcount=3"), all you have to do is right mouse click the file and choose **sent to ...**

> **dirken said:**
> Greetz..
DirkenRegards, useResa

---

### Post by Marc O on 2007-06-13
Same problem here since a clean install of Kubuntu 7.04. I can send files to my phone but not vice versa (phone doesn't see my laptop). Been searching on the internet for several days now, but no luck yet in finding a solution.

---

### Post by dirken on 2007-06-13
I was having that problem to but not anymore because I changed the preferences of bluetooth in Gnome to Visible and connectable. Otherwise my phone couldn't find my pc.

Greetz..

---

### Post by useResa on 2007-06-13
> **dirken said:**
> I was having that problem to but not anymore because I changed the preferences of bluetooth in Gnome to Visible and connectable. Otherwise my phone couldn't find my pc.
Greetz..
Could you also indicate how you have changed the preferences so others can try your solution as well?
TIA

---

### Post by mindhaq on 2007-06-15
I also have problems with Bluetooth connecting to my phone (Nokia 6280) on Feisty. With hcitool I do find my phone, and the phone finds the computer. But I cannot make a connection. It all just times out, I am never asked for a pin.

I didn't upgrade from the previous Ubuntu, but I had it installed once, and I know I had this working with the same hardware. So obviously something broke...

---

### Post by useResa on 2007-06-15
> **mindhaq said:**
> With hcitool I do find my phone, and the phone finds the computer.I think you are one of the few who actually has a phone that finds the computer because most of us cannot achieve this.
 
Have you maybe also altered settings like dirken did?
> **dirken said:**
> I was having that problem to but not anymore because I changed the preferences of bluetooth in Gnome to Visible and connectable. Otherwise my phone couldn't find my pc.
 
If so, could you indicate how you did this?

---

### Post by dirken on 2007-06-15
> **useResa said:**
>  
Have you maybe also altered settings like dirken did?
If so, could you indicate how you did this?

Hi, the changes i made were alle done in Gnome, i just followed the ubuntu help page for installing Bluetooth ([https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)) and then i need to go to System -> Bluetooth Preferences. There you have to switch between 'other devices can connect' and 'visible and connectable for other devices'.
Afterwards, before i could send files to my phone or receive files from my phone i had to open the 'Bluetooth file sharing' program (displays a little blue icon in the notification area. You'll find this program in the menu applications -> accesoires.

This how i got it working, let me know if it helpe you guys!

---

### Post by mindhaq on 2007-06-15
> **useResa said:**
> I think you are one of the few who actually has a phone that finds the computer because most of us cannot achieve this.
 
Have you maybe also altered settings like dirken did?
 
If so, could you indicate how you did this?

I don't think I did anything besides what dirken did. But his post was useful, because I never started the Bluetooth file sharing program before. Now I was able to send a file from my phone to the computer.

Anything besides that I still don't get to work, like synching my contacts with evolution. It seems this is all still very experimental :(

---

### Post by Marc O on 2007-06-16
Looks like it is possible somehow to get it working under Gnome. However, I'm a Kubuntu (KDE) user, so I'm still confronted with the impossibility to get it done. I installed and started the "Bluetooth file sharing" utility but that didn't help either.

---

### Post by dirken on 2007-06-16
> **Marc O said:**
> Looks like it is possible somehow to get it working under Gnome. However, I'm a Kubuntu (KDE) user, so I'm still confronted with the impossibility to get it done.

I thaught KDE was much better for using bluetooth with, but anyway if you find a solution to get it working in KDE plz let me know, i'm thinking to change from Gnome to KDE :)

---

### Post by lingnoi on 2007-06-17
I am on Gnome but I don't see any options in the Bluetooth preferences...

---

### Post by useResa on 2007-06-18
> **lingnoi said:**
> I am on Gnome but I don't see any options in the Bluetooth preferences...Same here ... also none of the options as described are available for me. Could it be that other packages are installed?

---

### Post by magicrobotmonkey on 2007-07-02
I believe I have this same problem, I can scan and find my phone with hcitool scan, and then I can do ```
sudo hcitool cc XX:XX:XX:XX:XX && sudo hcitool auth XX:XX:XX:XX:XX
``` and I get a popup that says click here to open the pin diialogue and if i click there (the bt icon in the panel) really fast, the pin dialoge opens for a second but then closes really fast and the phone does not ask for a pin like it used to in edgy.

edit: Forgot to mention im also trying feisty to feisty connections with a variety of hardware, dell laptop with bt, mac mini with bt, and a generic broadcom dongle. All hardware appears to work fine until it comes to pairing time.

---

### Post by tnjed111 on 2007-08-11
Yup, same problem here. I never tried anything before Feisty but my BT is doing the exact same thing described here with my macbook pro.

---

### Post by useResa on 2007-08-13
In the [bug report]("https://bugs.launchpad.net/bugs/110375"), the following solution was suggested
> At one point, for no reason at all, the phone stops detecting my laptop.
The laptop can detect the phone and send files, but the phone CANNOT
detect the laptop.
 
Do: hciconfig -a
Look for "UP RUNNING" at the 3rd line
It shows exactly that on my feisty.
 
Do: sudo hciconfig hci0 piscan
Then it shows "UP RUNNING PSCAN ISCAN" and that's when the phone can see the computer again.
 
Hope it's relevant.
 
Please find below (also indicated in the bug report) the result when I tried it:
First I needed to do a sudo hciconfig hci0 reset.
Doing a hcitool scan shows that my phone is detected
 
```
 
0 rdrijsen@rdrijsen-laptop: ~
Sun Aug 12, 22:26 $ hcitool scan
Scanning ...
 
       00:17:D5:A6:6A:E4       SGH-D900

```
Next I did hciconfig -a
 
```
0 rdrijsen@rdrijsen-laptop: ~
Sun Aug 12, 22:26 $ hciconfig -a
hci0:   Type: USB
       BD Address: 00:16:41:8F:C3:58 ACL MTU: 384:8 SCO MTU: 64:8
       UP RUNNING
       RX bytes:374 acl:0 sco:0 events:14 errors:0
       TX bytes:51 acl:0 sco:0 commands:10 errors:0
       Features: 0xff 0xff 0x9f 0xfe 0x9b 0xf9 0x00 0x80
       Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
       Link policy:
       Link mode: SLAVE ACCEPT
       Name: 'Dell Wireless 350 Bluetooth Internal Car'
       Class: 0x000000
       Service Classes: Unspecified
       Device Class: Miscellaneous,
       HCI Ver: 2.0 (0x3) HCI Rev: 0x976 LMP Ver: 2.0 (0x3) LMP Subver: 0x976
       Manufacturer: Cambridge Silicon Radio (10)

```
Indeed UP RUNNING is indicated in the 3rd line.
So I did -- as suggested -- hciconfig hci0 piscan
The result of hciconfig -a indeed altered
 
```
0 rdrijsen@rdrijsen-laptop: ~
Sun Aug 12, 22:27 $ hciconfig -a
hci0:   Type: USB
       BD Address: 00:16:41:8F:C3:58 ACL MTU: 384:8 SCO MTU: 64:8
       UP RUNNING PSCAN ISCAN
       RX bytes:1295 acl:1 sco:0 events:34 errors:0
       TX bytes:132 acl:1 sco:0 commands:19 errors:0
       Features: 0xff 0xff 0x9f 0xfe 0x9b 0xf9 0x00 0x80
       Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
       Link policy:
       Link mode: SLAVE ACCEPT
       Name: 'Dell Wireless 350 Bluetooth Internal Car'
       Class: 0x000000
       Service Classes: Unspecified
       Device Class: Miscellaneous,
       HCI Ver: 2.0 (0x3) HCI Rev: 0x976 LMP Ver: 2.0 (0x3) LMP Subver: 0x976
       Manufacturer: Cambridge Silicon Radio (10)

```
However ... my phone still does NOT detect my laptop.
So for me this was no solution.
 
Has anyone else tried this solution? And if so, with what results?

---

### Post by Marc O on 2007-08-13
It doesn't work for me either, although it seems that my phone detects "something" (however it doesn't show my laptop name for instance) it didn't detect before. Unfortunately the transfer of a file results in an error.... :(

---

### Post by Marc O on 2007-08-30
For some reason it's working now. I activated the Bluetooth Filesharing app (which is actually the gnome-obex-server, and I was able to transfer a file from my pda-phone to my Kubuntu laptop...... I haven't done anything related to bluetooth last couple of weeks, so this is a real surprise to me. Let me know if anyone likes to see particular conf files or whatever.

---

### Post by useResa on 2007-08-31
Based on your post I have also tried this (Ubuntu and Gnome) and started the Bluetooth File Sharing (Applications --> Accessories --> Bluetooth File Sharing) application.
Unfortunately my phone still does not detect my laptop ](*,)
 
While in Edgy indeed it use to work like this ... start the application and my phone would detect my laptop. Next I could transfer files back and forward without any problems.
 
Furthermore I am still faced with the fact that I have to do
```
sudo hciconfig hci0 reset
```
before I get a result from
```
hcitool scan
```.
 
Find below a list of installed packages based on various search criteria
```
0 rdrijsen@rdrijsen-laptop: ~
Fri Aug 31, 12:43 $ dpkg --get-selections | grep bluez
bluez-cups                                      install
bluez-gnome                                     install
bluez-pin                                       install
bluez-utils                                     install
python-bluez                                    install
0 rdrijsen@rdrijsen-laptop: ~
Fri Aug 31, 12:43 $ dpkg --get-selections | grep bluetooth
bluetooth                                       install
gnome-bluetooth                                 install
libbluetooth2                                   install
libbluetooth2-dev                               install
0 rdrijsen@rdrijsen-laptop: ~
Fri Aug 31, 12:52 $ dpkg --get-selections | grep obex
cobex                                           install
gnome-vfs-obexftp                               install
libopenobex1                                    install
openobex-apps                                   install

```

---

### Post by useResa on 2007-09-02
In order to also show the versions that I have installed, I have installed apt-show-versions
```
sudo aptitude install apt-show-versions
```
Next I have done the same as in my previous post, except with the apt-show-versions command, please find below the result
```
0 rdrijsen@rdrijsen-laptop: ~
Sun Sep 02, 19:40 $ sudo apt-show-versions | grep bluez
python-bluez/feisty uptodate 0.9.1-1
bluez-cups/feisty uptodate 3.9-0ubuntu4
bluez-pin/feisty uptodate 0.30-2.1ubuntu3
bluez-gnome/feisty uptodate 0.6-1ubuntu3
bluez-utils/feisty uptodate 3.9-0ubuntu4
0 rdrijsen@rdrijsen-laptop: ~
Sun Sep 02, 19:41 $ sudo apt-show-versions | grep bluetooth
libbluetooth2-dev/feisty uptodate 3.9-0ubuntu1
gnome-bluetooth/feisty uptodate 0.8.0-0ubuntu4
libbluetooth2/feisty uptodate 3.9-0ubuntu1
bluetooth/feisty uptodate 3.9-0ubuntu4
0 rdrijsen@rdrijsen-laptop: ~
Sun Sep 02, 19:42 $ sudo apt-show-versions | grep obex
cobex/feisty uptodate 0.2.12-1
gnome-vfs-obexftp/feisty uptodate 0.2-0ubuntu1
libopenobex1/feisty uptodate 1.3-3
openobex-apps/feisty uptodate 1.3-3
```
Is this the same version and packages that are also installed for those people who have bluetooth working?

---

### Post by Marc O on 2007-09-03
```
root@marc-laptop:/home/marc# apt-show-versions | grep bluez
python-bluez/feisty uptodate 0.9.1-1
bluez-cups/feisty uptodate 3.9-0ubuntu4
bluez-pin/feisty uptodate 0.30-2.1ubuntu3
bluez-gnome/feisty uptodate 0.6-1ubuntu3
bluez-hcidump/feisty uptodate 1.33-0ubuntu1
bluez-utils/feisty uptodate 3.9-0ubuntu4
root@marc-laptop:/home/marc# apt-show-versions | grep bluetooth
gnome-bluetooth/feisty uptodate 0.8.0-0ubuntu4
libbluetooth2/feisty uptodate 3.9-0ubuntu1
kdebluetooth 0.99+1.0beta2-2+3v1ubuntu0 newer than version in archive
bluetooth/feisty uptodate 3.9-0ubuntu4
root@marc-laptop:/home/marc# apt-show-versions | grep obex
obexpushd/feisty uptodate 0.4+svn10-2
libopenobex1/feisty uptodate 1.3-3
qobex/feisty uptodate 0.99+1.0beta2-1ubuntu5
```

---

### Post by useResa on 2007-09-04
Except for the KDE application -- AFAIK -- I now have the same versions installed. However ... still no success. Please find results below
```
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 04, 09:59 $ apt-show-versions | grep bluez
python-bluez/feisty uptodate 0.9.1-1
bluez-cups/feisty uptodate 3.9-0ubuntu4
bluez-pin/feisty uptodate 0.30-2.1ubuntu3
bluez-gnome/feisty uptodate 0.6-1ubuntu3
bluez-hcidump/feisty uptodate 1.33-0ubuntu1
bluez-utils/feisty uptodate 3.9-0ubuntu4
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 04, 09:59 $ apt-show-versions | grep bluetooth
libbluetooth2-dev/feisty uptodate 3.9-0ubuntu1
gnome-bluetooth/feisty uptodate 0.8.0-0ubuntu4
libbluetooth2/feisty uptodate 3.9-0ubuntu1
bluetooth/feisty uptodate 3.9-0ubuntu4
0 rdrijsen@rdrijsen-laptop: ~
Tue Sep 04, 10:00 $ apt-show-versions | grep obex
obexpushd/feisty uptodate 0.4+svn10-2
cobex/feisty uptodate 0.2.12-1
gnome-vfs-obexftp/feisty uptodate 0.2-0ubuntu1
libopenobex1/feisty uptodate 1.3-3
openobex-apps/feisty uptodate 1.3-3
qobex/feisty uptodate 0.99+1.0beta2-1ubuntu5
```
Has anybody else been succesful in connecting from his/her phone to a laptop? And if so, was this also because the KDE application was installed?

Sure would like to get this working (again).

---

### Post by useResa on 2007-09-11
*** BUMP ***

Does everybody have Bluetooth working again on Feisty (like MarcO) and I am the only left with a non working Bluetooth on Feisty?
Or are there more of you still having the same issue?

---

### Post by lingnoi on 2007-09-11
No idea. I gave up trying after I realised everyone was more interested in Gutsy.

---

### Post by Marc O on 2007-09-12
I noticed I have a script running called:
"kbluetoothd.rea"

I'm not sure where it comes from but it could be your "missing key" here.

I also have the gnome-obex-server running in my system tray.

Good luck!

---

### Post by blue_shift on 2007-10-16
I've just got the official (k)ubuntu 7.10 release installed, and now I get no bluetooth errors at boot. Moreover, my bluetooth USB key* is not recognised at all.

*"Belkin Bluetooth USB adaptor"

Has anyone had any luck with Ubuntu 7.10 yet?

Any problems?

---

### Post by useResa on 2007-10-17
Okay ... 24 hours too early ;) ... I upgraded to Gutsy.
Unfortunately also in Gutsy my phone can still not detect my laptop.  :(

It seems that the upgrade will indeed not solve this issue.
It would have been nice if this would have been picked up.
Now since Edgy I am stuck with a laptop that cannot be detected by my phone ... maybe we have to wait for Hardy Heron to arrive.

---

### Post by blue_shift on 2007-10-18
> **useResa said:**
> Okay ... 24 hours too early ;)
Kubuntu does have other advantages, besides KDE :D

---

### Post by xeth_delta on 2007-10-31
I have finally managed to get my phone and laptop connected through bluetooth :D I followed the instructions for a workaround from this link: [http://wiki.bluez.org/wiki/FAQ#ImunabletofindmypcfromthemobileusingKubuntuEdgyFeisty]("http://wiki.bluez.org/wiki/FAQ#ImunabletofindmypcfromthemobileusingKubuntuEdgyFeisty").

I mention that I am using Kubuntu 7.04. Right now I can transferfiles both ways.

Xeth

---

### Post by useResa on 2007-11-05
Woohoo!! [This post]("http://ubuntuforums.org/showpost.php?p=3690860&postcount=6") put me on the track for [Blueman]("http://www.gnomefiles.org/app.php/blueman").
I have installed this package by downloading the DEB file from their download page. 
Guess what ... I can transfer files again from my phone to my laptop!! :)

Still have some minor issues to solve (like when going from my laptop to my phone the connection comes up and disconnects almost immediately again) but the biggest hurdle has been taken!!

---

### Post by useResa on 2008-06-04
Recently I have done a clean install of Hardy on my laptop (initially I upgraded).
Since then Bluetooth is working like it should (after setting the properties to my liking).

Glad to see this has been resolved.

---

