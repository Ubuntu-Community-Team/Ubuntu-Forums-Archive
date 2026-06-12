---
title: "Help with wireless internet"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by AmazingJustin on 2007-07-15
Hello, I just installed Ubuntu on my Compaq Presario V2000 and have tried everything to get the wireless internet to work.  It just won't detect my Motorola router when I type in the name of the connection and the key.  I'm a Linux noob so I have no idea what to do!  Please help.

---

### Post by AmazingJustin on 2007-07-15
I don't mean to spam but I really need help.  I know next to nothing about computers and have been searching the internet for different solutions, none of them seem to work.

---

### Post by SoloSalsa on 2007-07-15
Do you have wired access, or can you not get on, by any means?

Start simple.  With a computer that *can* connect, disable the security.  Make a completely open access point.  Can you connect then?

---

### Post by 5-HT on 2007-07-15
To aid people in helping you, could you post 1) your wireless card model/manufacturer, 2) whether or not you have installed the appropriate driver for the card,  3) the method you're using to connect to the network (ie., networkmanager, manual config, etc...), and 4) as SoloSalsa mentioned, if you can connect to an unencrypted network.

If you have the proper driver for your card installed, as a quick fix I would recommend giving 'wifi-radar' a try. It's a GUI wireless network browser that can handle WEP/WPA{2} with ease. I know this could be seen as diverting the issue, but it may help you be able to use your network while you figure out what the current problem is.

cheers,

---

### Post by MyR on 2007-07-15
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by alzaf on 2007-07-15
I had recently bought a wireless router and had problems getting it working. As I went through so many tutorials/posts, I lost track of sys changes I had made so I decided to do a fresh install. Low and Behold after the fresh install the wireless worked fine. 

It might be helpful to do try a fresh install. I had an ethernet lead connecting wireless router to my laptop so best to do same thing as well.

---

### Post by AmazingJustin on 2007-07-15
I have a Broadcom 4318 card and I don't have the drivers for it.  I downloaded ndiswrapper but I'm having trouble starting it up.

---

### Post by rggavubt on 2007-07-15
> **AmazingJustin said:**
> I have a Broadcom 4318 card and I don't have the drivers for it.  I downloaded ndiswrapper but I'm having trouble starting it up.

Search for fwcutter in synaptic and install "bcm43xx-fwcutter".  This will install the firmware for you Broadcom WLAN card.  Card should lite up after install and then search for wireless connections.

---

### Post by AmazingJustin on 2007-07-15
> **rggavubt said:**
> Search for fwcutter in synaptic and install "bcm43xx-fwcutter".  This will install the firmware for you Broadcom WLAN card.  Card should lite up after install and then search for wireless connections.

I did that and it says I'm connected to my wireless network but I'm really not.  I can't access the internet still.  Any suggestions?

---

### Post by AmazingJustin on 2007-07-15
Also, it keeps asking for my network key over and over again.  I keep entering it and it still asks me.

---

### Post by MrMercutio on 2007-07-15
Which kind of protection do you use? If you use WEP you may have to select whether the key is supplied in HEX or ASCII. You should see a drop down list in the request (if you use WEP) where you can choose the format.

---

### Post by jimbob on 2007-07-15
Post the output from a terminal of:

   i[I][COLOR="Blue"]fconfig -a
   iwconfig[/COLOR][/I]
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by AmazingJustin on 2007-07-15
I got this:

eth1      Link encap:Ethernet  HWaddr 00:90:4B:F5:C1:6D  
          inet6 addr: fe80::290:4bff:fef5:c16d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:472 overruns:0 frame:0
          TX packets:820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:884 (884.0 b)  TX bytes:56552 (55.2 KiB)
          Interrupt:3 Base address:0x4000 

eth1:avah Link encap:Ethernet  HWaddr 00:90:4B:F5:C1:6D  
          inet addr:169.254.9.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1156 (1.1 KiB)  TX bytes:1156 (1.1 KiB)

and this:


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Motorola"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:A5:8A:BB:74   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level=-44 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:206  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by rggavubt on 2007-07-15
> **AmazingJustin said:**
> Also, it keeps asking for my network key over and over again.  I keep entering it and it still asks me.

I don't have Ubuntu running on my laptop..using PCLinuxOS... so I'm not sure what they are asking you.  Do you have it setup for WEP?  If so, make sure you check the correct WEP you are using...five or ten characters or whatever # you are using?  Then enter key characters.  Sometime it also asks you to enter a password to save entries?  I just reuse my root password.

---

### Post by AmazingJustin on 2007-07-15
> **rggavubt said:**
> I don't have Ubuntu running on my laptop..using PCLinuxOS... so I'm not sure what they are asking you.  Do you have it setup for WEP?  If so, make sure you check the correct WEP you are using...five or ten characters or whatever # you are using?  Then enter key characters.  Sometime it also asks you to enter a password to save entries?  I just reuse my root password.

I have it setup for WEP and I entered the password.  Every few minutes the network manager pops up asking for my password again.  It doesn't seem to have a "save password" button I can check or anything.

---

### Post by jimbob on 2007-07-15
Notice that you are only running 11Mb/s from your iwconfig output.  This is typical of the bcm43xx-fwcutter driver in Ubuntu.   If I was you I would do two things.

1)  get rid of bcm43xx-fwcutter and use ndiswrapper by following post #1 of this guide:  [I][COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318
[/COLOR][/I]
2)  get rid of Ubuntu's network manager and install Wicd (or Wifi-radar as suggested above).  They are much easier to set up and get your security working and you won't be troubled by those keyring passwords any more.  *[COLOR="Blue"]http://wicd.sourceforge.net/download.php[/COLOR]*
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by AmazingJustin on 2007-07-15
> **jimbob said:**
> Notice that you are only running 11Mb/s from your iwconfig output.  This is typical of the bcm43xx-fwcutter driver in Ubuntu.   If I was you I would do two things.

1)  get rid of bcm43xx-fwcutter and use ndiswrapper by following post #1 of this guide:  [I][COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318
[/COLOR][/I]
2)  get rid of Ubuntu's network manager and install Wicd (or Wifi-radar as suggested above).  They are much easier to set up and get your security working and you won't be troubled by those keyring passwords any more.  *[COLOR="Blue"]http://wicd.sourceforge.net/download.php[/COLOR]*
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

Alright I installed wicd now I can't connect to the internet even with a cable and I can't find the wicd network manager.

---

### Post by imdano on 2007-07-15
Remove network-manager and network-manager-gnome using Synaptic Package Manager (System->Administration). Just uncheck them and choose apply.

---

### Post by jimbob on 2007-07-15
I'm assuming you will save anything valuable  before you do this, right?

 You must download the *.deb package for wicd first.  Go to this URL and select the package wicd_1.3.1-all.deb and save it to disk in your home/<you> account.   *[COLOR="Blue"]http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=521838[/COLOR]*

From a terminal window enter *[COLOR="Blue"]sudo apt-get remove --purge network-manager[/COLOR]*
Then enter [I][COLOR="Blue"]sudo dpkg -i wicd_1.3.1-all.deb
[/COLOR][/I]

You should find Wicd under Applications->Internet.  Click and drag it to your desktop as an icon and you should be good to go.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by AmazingJustin on 2007-07-15
Yes, it works!  Thank you guys so much for your help!

---

### Post by imdano on 2007-07-15
Make sure you add the wicd tray to automatic start up.  Go to System->Preferences->Sessions and add a new entry called Wicd with the command "/opt/wicd/tray.py".

---

### Post by antonius1 on 2007-07-15
I am running a dell inspirion B130 with an intel(R) celeron (R) M Processor 1.40 GHz, I am using Kernel:  Linux 2.6.20-16 generic (i686) I don't know the type of wireless card or wireless router I am using.  I know they both worked when I was using windows but not now.  I followed the instructions for removing the network manager and installing .deb of wicd.  Still I am getting no love from my wireless card.  There is a difference btw. my wireless card and the guy who started this thread and the difference is that mine is internal but there is a light that comes on.   Unfortunately it's not lighting up.  Please I am having a bad day please help me to have a least one smlle today.

Also, all my room mates are running XP and all of their computers are working on our wireless network and me the cutting edge linux-ubuntu user have to sit in the dining room connected by a wire.

---

### Post by antonius1 on 2007-07-15
I Forgot to do something that is very important.  What did you forget Antonius. Oh turn on the wireless card. 
Done and Doner.
Thank you for all the help

---

