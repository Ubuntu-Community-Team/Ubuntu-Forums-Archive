---
title: "prism2_usb on Dell Latitude"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by w.saoud on 2006-09-22
Dear All 
I Have A Dell Latitud Laptop And I Have A Eusso Wireless [[http://www.eusso.com/Models/Wireless/GL2411-MU/gl2411-mu.htm]](http://www.eusso.com/Models/Wireless/GL2411-MU/gl2411-mu.htm]), The Problem Is The Wireless Was Not Plugged When I Have Install My Ubuntu , So The Wireless Network Havn't Added And I Don't Have The Drive Of The Device For Ubuntu, I have it for Windows .

Does Any One Can Help Me And Tell Me How To Fix This Two Error I Have Contact The Company And I Have Ask Them To Send Me The Driver But What Is The Next >> After They Send Me The Drivers ?

Hope I Hear From You Soon Guys

Wajdi

---

### Post by ubuntu_demon on 2006-09-23
Hi,

Please provide us with :
-the modelnumber of your laptop
-the modelnumber of your wireless card
-the result of $lspci (in the terminal)
-the result of $lsusb (because you told me it's connected to usb)

Here's some information :
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

good luck!

---

### Post by w.saoud on 2006-09-23
**For The USB Wireless It's :**
7a01 Global Sun Technology, Inc. PRISM25 802.11B Adapter
**For The Laptop It's : **
Dell Latitud CPx
Model No : PPX
Latitudde C Family
Ref number : 99125

I Know It's an old one, but it's good for my age.

---

### Post by ubuntu_demon on 2006-09-23
The dutch dell site has "latitude CPx J" and "latitude CPx H". I don't see a "latitude CPx".

You have to google and search the Ubuntu wiki for your wireless card model.

Worst case scenario : 
choose a well supported wireless chip from
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

good luck !

---

### Post by w.saoud on 2006-09-23
**It's a USB Wireless I have Contact The Company And They Didn't Answer Yet.**

---

### Post by ubuntu_demon on 2006-09-23
> **w.saoud said:**
> **It's a USB Wireless I have Contact The Company And They Didn't Answer Yet.**
There are probably lots of usb wireless cards.

If this "Global Sun Technology, Inc. PRISM25 802.11B Adapter" works in windows then it's probably not a hardware failure.

You can try to contact the company who sold you this usb wireless card but probably they are only focused towards windows.

You probably have to search for this specific model on the wiki,forums and google.

You can get more information about your wireless card with :

$sudo lsusb -vv

please post the result of that command here

---

### Post by ubuntu_demon on 2006-09-23
also don't forget to try ndiswrapper on your windows driver(as a backup plan). And read the two wiki pages I posted.

---

### Post by ubuntu_demon on 2006-09-23
Here's information for your usb "card" :
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

Try this (if it doesn't work go then first read up on the wiki page I just gave):
$sudo aptitude install linux-wlan-ng
$sudo modprobe prism2_usb

Please post the result of :
$lsmod | grep prism2_usb

Here's the general guide to get wireless working (for WEP and open) :
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

Here's more general information :
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo)

---

### Post by w.saoud on 2006-09-23
[B]I have do step per step at : [https://help.ubuntu.com/community/Wi...ver/prism2_usb](https://help.ubuntu.com/community/Wi...ver/prism2_usb)

And Still Nothing Work, Please Help[/B]

---

### Post by ubuntu_demon on 2006-09-23
> **w.saoud said:**
> [B]I have do step per step at : [https://help.ubuntu.com/community/Wi...ver/prism2_usb](https://help.ubuntu.com/community/Wi...ver/prism2_usb)

And Still Nothing Work, Please Help[/B]
You have to say exactly what you did and exactly what the result was. "nothing work" doesn't provide useful information.

please provide all the information. Especially the result of :

$lsusb -vv (only the part of your wireless card)

$sudo modprobe prism2_usb
$lsmod | grep prism2_usb

I'm going to sleep now. I don't know when I will be able to help you again. But I will check back later. 

In the meantime please read the wiki pages I linked to. 

Here are some more useful pages :
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

good luck!!!

---

### Post by w.saoud on 2006-09-24
Sorry Guys But What The Hell Is This.
Can You Please Tell Me In What Linux Is Better ?
+ The Terminal Is Not Working , It Open And Then Closed , Why All This Happening ?

---

### Post by w.saoud on 2006-09-24
**Sorry For The Post 11 **

Let Me Tell You What I Have Do And What I Have Recived .

1. I Have Install "linux-wlan-ng" From The Ubuntu CD .
2. I Have Enter To : /etc/network/interfaces And Change The Delete EveryThing And Then I Have Past This Text :
> wireless_mode managed
wireless_enc on
wlan_ng_key0 [my wire mac]

3. I Have Unplug The USB And Plug In Again .
4. I Have Enter To The Network From The Administrator Menu

Notes : I Was Unable To Install Network Manager And I Was Reciving An Error Message .

Hope You Can Help Me .

---

### Post by ubuntu_demon on 2006-09-24
It can be quite hard to get your wireless working. Especially when you are new to Ubuntu. It also depends on the manufacuturer. A lot of them don't cooperate with the open source movement at all.

Please post the result of :

$sudo modprobe prism2_usb
$lsmod | grep prism2_usb

Now the prism2_usb "driver" is loaded if we are lucky. If it isn't loaded don't worry we'll solve it.

Also please set your wireless Acces Point to open and try to get that working first. 

Then delete everything from /etc/network/interfaces because you should try to set this up graphically first.

Try to get wireless working with an open / unencrypted connection. Here's more information about how to do this :
[https://help.ubuntu.com/community/WifiDocs/WirelessNetwork](https://help.ubuntu.com/community/WifiDocs/WirelessNetwork)
Here's the tool :
system -> administration -> networking 

If it doesn't work we need to make sure whether prism2_usb is properly loaded. And you can find some more information here : [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

But **DON'T TRY** to update the firmware. This can be risky. Especially because the wiki page says it's broken for Dapper.

If prism2_usb is properly loaded and you have read the prism2_usb wiki page and it still doesn't work then it's time to read the other wiki pages but don't follow breezy/hoary/warty specific instructions :

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

If open works then you should be able to configure wep graphically using :
[https://help.ubuntu.com/community/WifiDocs/WirelessNetwork](https://help.ubuntu.com/community/WifiDocs/WirelessNetwork)
system -> administration -> networking 

It's probably harder to get wpa working.

Use the links I provided for further reading if all of this doesn't work.

But first we should have the result of :
$sudo modprobe prism2_usb
$lsmod | grep prism2_usb

---

### Post by w.saoud on 2006-09-24
Ewwwwwwww , Bad Luck Is Every Where, I Have Lost My Wireless :( After A Elecricity Error, Please Give Me A Page Where I can find All Wireless Accepted By Ubuntu And If It Can Be Shiped To Lebanon.

---

### Post by ubuntu_demon on 2006-09-24
> **w.saoud said:**
> Ewwwwwwww , Bad Luck Is Every Where, I Have Lost My Wireless :( After A Elecricity Error, Please Give Me A Page Where I can find All Wireless Accepted By Ubuntu And If It Can Be Shiped To Lebanon.
Are you sure your wireless usb is fried ?
What exactly happened ?

---

### Post by w.saoud on 2006-09-24
The Elecicity In Lebanon Is 220 And I was Puting The Wireless In A PCM CIA , Unfortuntly , I Have Change The Elecirity Of My Room To 320 And The PCM CIA Adapter Was In The Electricity So I Have Smell A Burn , And When I Saw It It Was Burning [ The Adapter ]

I Will Check The Adapter And Then See If I Can Get New One , Or I Can Buy New Router That Will Cost Me 120 $, Do You Think The Router Should Work Correctly .

+ Do You Know Where To Download Software For Ubuntu, Like Dream Weaver And FireWorks .

As For My Age "14" Do You Think Ubuntu Is Good Or I Should Go To Kubuntu , I Have Some Sites And 2 Server And I Would Like To Connect To Them From My Leptop Using Ubuntu So What Should I Use Ubuntu Or k Ubuntu ?

---

### Post by w.saoud on 2006-09-24
+ Adding :

Do You Know Why The Terminal Is Not Working , When I Open It, It Close Automaticly .

---

### Post by ubuntu_demon on 2006-09-24
in case your wireless usb is fried and/or you need a new wireless card :

Here's a list of wireless cards :
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
The Free Software Foundation recommends these chipsets :
> Cards that use the Ralink 2500/RT2400 and Realtek RTL8180 chipsets work well with GNU/Linux.

I think it's best to find a card on this [wiki  page](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) with a Ralink 2500/RT2400 or Realtek RTL8180 chipset which works out of the box and is tested on Dapper (or Edgy).

(for people who are going to buy a new laptop : I'm going to buy a Intel Core Duo / Centrino laptop with ipw3945 wireless)

---

### Post by ubuntu_demon on 2006-09-24
> **w.saoud said:**
> + Adding :

Do You Know Why The Terminal Is Not Working , When I Open It, It Close Automaticly .
I don't know. You can post your .xsession-errors and we might be able to find out :

$gedit ~/.xsession-errors

---

### Post by w.saoud on 2006-09-24
[B]Thanks You For You Help :)

I'm Going To Buy New Dell Computer

By The Way Do You Know A Site Or Wiki Page Where I can Find All SSH Commands , So I Will Be Able To Restart Servers Remotly
[/B]

---

### Post by ubuntu_demon on 2006-09-24
> **w.saoud said:**
> The Elecicity In Lebanon Is 220 And I was Puting The Wireless In A PCM CIA , Unfortuntly , I Have Change The Elecirity Of My Room To 320 And The PCM CIA Adapter Was In The Electricity So I Have Smell A Burn , And When I Saw It It Was Burning [ The Adapter ]


You said you had an usb wireless card. I don't understand it anymore.

What about pcmcia ? Does your pcmcia card provide USB or something ?

> **w.saoud said:**
> 
I Will Check The Adapter And Then See If I Can Get New One , Or I Can Buy New Router That Will Cost Me 120 $, Do You Think The Router Should Work Correctly .


Did your wireless router get fried ?

AFAIK any wireless router that works with windows will also work with Ubuntu.

> **w.saoud said:**
> 
+ Do You Know Where To Download Software For Ubuntu, Like Dream Weaver And FireWorks .


AFAIK that particular software is windows only.

nvu is a nice program for website editting but there are also others.

You can install lots of free and open source software from :
add/remove in your "ubuntu menu". You can click on "unsupported software" to view a lot more available software. Here's some more information :
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

> **w.saoud said:**
> 
As For My Age "14" Do You Think Ubuntu Is Good Or I Should Go To Kubuntu , I Have Some Sites And 2 Server And I Would Like To Connect To Them From My Leptop Using Ubuntu So What Should I Use Ubuntu Or k Ubuntu ?

It's personal matter of taste. Personally I like Ubuntu (gnome) more. You can try the livecd of Kubuntu and see whether you like it.

---

### Post by ubuntu_demon on 2006-09-24
> **w.saoud said:**
> [B]Thanks You For You Help :)

I'm Going To Buy New Dell Computer

By The Way Do You Know A Site Or Wiki Page Where I can Find All SSH Commands , So I Will Be Able To Restart Servers Remotly
[/B]
Did your entire laptop get fried ?

I'm searching for a nice new laptop myself.

if ssh is running on your server you can just ssh to it like this :

$ssh username@serveradress

If the server is running linux then all linux commands should work. By the way : installing a Ubuntu Server isn't very hard.

to view more information about ssh :
$man ssh

---

### Post by w.saoud on 2006-09-29
Sorry I take time to reponse .

The Leptop That I'm using now work good and correctly, But i need something new :) only .

I will continue the post later , i wanna study :)

---

