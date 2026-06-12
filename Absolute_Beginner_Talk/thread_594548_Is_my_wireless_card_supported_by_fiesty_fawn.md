---
title: "Is my wireless card supported by fiesty fawn?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-10-28
Hello,

i have finally decided to go all ubuntu :)

ill remove my win xp installation and make my entire system ubuntu, 

now the only problem is that i dont know if ubuntu will support my wireless card.

i use a wireless card to connect to my router, the card is D-Link AirPlus G DWL-G630

is it supported 

where can i find out?

---

### Post by stomponthis on 2007-10-28
Check out this doco....
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by forestpixie on 2007-10-28
[this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") is the list of wireless cards - dwl-g630 is on there 3 times - different chip sets - Atheros works the others have problems - check out the wireless [forum]("http://ubuntuforums.org/forumdisplay.php?f=136")

I'd be inclined to go dual boot until you've got the card working :)

hope that's of help to you - can't help unfortunately with the card itself I haven't opened that can of worms

---

### Post by Rinzwind on 2007-10-28
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28dlink%29](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28dlink%29)

Answer: yes, but with comments.

See the link for the comments.

---

### Post by faraz_k86 on 2007-10-28
i dont understand the comments, wat shud i do ?

---

### Post by derred on 2007-10-28
Why not just test it in the Live CD? It's what it's there for...
Boot from the Installer CD (not the alternate) and you will get a fully functional Ubuntu system that does not touch your hard disk. See if your card is detected and if you can connect to a wireless network or two.

PS I recommend giving Gutsy a try unless you really really need feisty, It's the latest version and it's waaaay cool + WiFi support is only getting better

---

### Post by faraz_k86 on 2007-10-28
thx a lot.

thats an excellent idea.

ill try that now and get back here with an update.


i wanted to order gusty gibbon but on the homepage it was written that this is still in the beta stage, i think that means in the test stage.

or am i wrong??

---

### Post by derred on 2007-10-28
It's no longer in beta; that was before the 18th of October. You can simply download it if you don't want to wait. Also I've used it throughout the beta and it was extremely stable so don't worry so much about using beta software, just don't put it on mission critical machines.

---

### Post by faraz_k86 on 2007-10-28
ok i just used live cd, it picked up my wireless card and recognized it, but i cant connect to the internet. i bilieve it has to do something with the settings.

im attaching a screenshot of my settings in winxp, where shud i enter these settings in ubuntu.

so far i used automatic configuration and entered the DNS and alternate DNS in the DNS tab of ubuntu.

@derred

i see in you sig yu mention " USE LINUX! Because a 486 is a terrible thing to waste."

i dont thnk a 486 can support ubuntu, which OS or linux can run a 486

---

### Post by faraz_k86 on 2007-10-28
bump

---

### Post by derred on 2007-10-28
Is your network set up to use the wep of wpa encryption?
If it's using WEP then there are different kinds of WEP encryption 64/120k and also they can be hex asci or passphrase. Use these in yours setup under Ubuntu and see which one works.

As for the 486 version of Linux: No, Ubuntu can't run on a 486 but there are a lot of linux distros made for older computers. My favorites are Damned Small Linux and DeLi Linux, but you could also install a customized Slackware from what I understand. Don't expect great performance, and without 16-24 mb of ram don't expect graphics ether.

---

### Post by faraz_k86 on 2007-10-28
i dont use any encryption neither wep nor wpa.


 thx

---

### Post by faraz_k86 on 2007-10-28
and another bump :(

---

### Post by faraz_k86 on 2007-10-28
im really sorry guys but ill have to do another bump. :(

if someone can only help me with my internet i'll start installation of ubuntu

---

### Post by derred on 2007-10-28
It's me again :P

1. You should really really really use encryption
2. Could you post the result of the command ifconfig before and after connecting to the network.

If 2 is unclear just:
 start the terminal program by pressing Alt+F2 and writing 'gnome-terminal' without quotes
 a black window will appear
 in that window you will get some text like: john@his-computer:~$
 enter 'ifconfig' here, again without the quotes
 tell us what it says
 connect to the network and repeat

---

### Post by faraz_k86 on 2007-10-28
i live in an area where no one , besides me even knows what wlan stands for :) so im not that efficient on applying encryption, call me lazy :)


ok ill have to load up ubuntu using the live cd again, so ill be offline, once i get the result of ifconfig i'll post it here, so wait for me :)  i wont be more than 5 min :)

---

### Post by faraz_k86 on 2007-10-28
ok i am attaching the results of the ifconfig.

ill also add it here.

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F3:86:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4612 (4.5 KiB)  TX bytes:4612 (4.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:19:5B:79:9B:49  
          inet6 addr: fe80::219:5bff:fe79:9b49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:1 dropped:1 overruns:0 carrier:0
          collisions:4 txqueuelen:1000 
          RX bytes:409637 (400.0 KiB)  TX bytes:2848 (2.7 KiB)
          Interrupt:16 

```

---

