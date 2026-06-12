---
title: "sagem fast 800 and how to connect"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by cotiK on 2007-04-25
ok everybody im curretly one step from installing. I have a SAGEM FAST 800 dsl modem. What should  i do to connect to the internt? i searched older posts but cant understand them. Please give me SIMPLE and exact steps (goto there open that write that) if you can. Im the noobiest one could be

---

### Post by mikeyphi on 2007-04-26
Is this guide any help?
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by stuntgp2000 on 2007-04-27
==================


[SIZE="5"]**UPDATED:**[/SIZE] look [here]("http://ubuntuforums.org/showpost.php?p=4402171&postcount=32"). You will find how to use Sagem Fast 800 in both modes PPPoA & PPPoE.


==================

Hi,
Here is what I did to get Sagem Fast 800 running on a clean Ubuntu 7.04 & Ubuntu 7.10 with PPPoA.

first, download Sagem Firmware from [here]("http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz")

It's preferable to unplug the modem

assuming you have downloaded that firmware and put it on your Ubuntu Desktop, run these commands from Terminal (found on Application Menu => Accessories => Terminal)

These lines will copy extracted binary firmware files to firmware directory
```

cp ~/Desktop/ueagle-data-1.1.tar.gz /tmp && cd /tmp
tar -zxvf ueagle-data-1.1.tar.gz
sudo mkdir /lib/firmware/ueagle-atm
cd ueagle-data-1.1/
sudo cp -a * /lib/firmware/ueagle-atm/

```
**[COLOR=Red]Important Note[/COLOR]**: the quotation mark when copy/pasted from the below script is not the same as the one we need. The cause is related to how some forum boards handle some special characters, in our case the quotation mark. So, WRITE THE QUOTATION MARK MANUALLY.


now, we have to create a file that will be used to get Sagem connect to your ISP.
from Terminal, do
```
sudo gedit /etc/ppp/peers/ueagle-atm
```then put these lines into the text editor that have appeared on the screen
```

user "login@ISP"
plugin pppoatm.so 8.35
noipdefault
usepeerdns
defaultroute
persist
noauth

```you have to replace   login@ISP  with your real login@ISP   ,and   8.35  with your ISP VPI.VCI


Now, it's time to create a file that will contain our login@ISP and Password. from Terminal do:
```
sudo gedit /etc/ppp/chap-secrets
```when text editor shows up, copy this line at the end of that file
```
"login@ISP" * "password" *
```again, replace    "login@ISP"  with your real ISP login  and replace  "password" with your real password. quotes must be retained.


It's time to test if we have succeeded to get our modem up and running.
Plug the modem, and from Terminal do:
```

sudo modprobe pppoatm
sudo modprobe ueagle_atm


#wait a few seconds before running the next line to see if both modem led become green.

pppd call ueagle-atm


#if both led become green and you have run the above line and got this message "Plugin pppoatm.so loaded." then it's probably that you have successfully connected to the Internet. To verify run the following command and you receive details about your ppp modem interface.

ifconfig ppp0

```
if you got your modem running, then if you wish you can make your modem dial and redial automatically by following these further steps.

from Terminal, do this 
```
sudo gedit /usr/bin/adsl
```this will show up the text editor again.
now copy/paste these into it.
```

#!/bin/bash
pppd call ueagle-atm

```save the file, close text editor, return to Terminal and run this to make the file executable.
```
sudo chmod +x /usr/bin/adsl
```then, we have to move it to a init.d directory to get it running at different stages of our Ubuntu Linux.
from Terminal, do this
```
sudo mv /usr/bin/adsl /etc/init.d
```well, we are almost done, 
run this for Terminal to add its entry to different startup stages.
```
sudo update-rc.d adsl start 50 2 3 4 5 . stop 50 6 0 .
```Note, the dots are not put into that line there by mistake, they are required.

Well, that's all you should have Internet running all day and should redial automatically without intervention from you part. However, if you want to drop the connexion, just run ```
poff
``` or ```
sudo poff
```  from Terminal, or if you want to dial manually run   ```
pppd call ueagle-atm
```
I hope that was helpful.

for French speaking people [here]("http://libreinfo.wordpress.com/2007/04/22/connexion-a-internet-en-utilisant-sagem-fast-800-usb-modem-ubuntu-704-feisty-fawn/") is the same thing in French

---

### Post by cotiK on 2007-04-28
> **stuntgp2000 said:**
> 
you have to replace   login@ISP  with your real login@ISP   ,and   8.35  with your ISP VPI.VCI

What is the VPI.VCI??

Also, is there  a way to (dis)connect to the internet using a graphical interface?

Thanks a lot (really, you dont imagine how much)

---

### Post by stuntgp2000 on 2007-04-28
Hi,

Concerning VPI.VCI [here]("http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL") is a list of Countries/ISPs/Connexion Type/VPI.VCI values. look into that list for your country, then your ISP and its VPI.VCI required values to connect using DSL.


A Graphical Interface way to (dis)connect to the Internet is simple.
Let's begin with Connect. Right click on the desktop then choose Create Launcher, a dialog box will appear on which you fill the name i.e Connect, then on command field write ```
pppd call ueagle-atm
``` then validate that dialog box and a shortcut will appear on the desktop which you can double click to connect to the Internet.

To disconnect, do the same as above, right click on the desktop, choose Create a Launcher, fill the name field with Disconnect, and fill command field with  ```
gksu poff
``` afterwards, you will see a shortcut on the desktop named Disconnect, double click on it to disconnect from the Internet. it will ask you for your password in order to drop the line.

I hope that was helpful. see you soon :)

---

### Post by stuntgp2000 on 2007-04-28
Hi again,

Well you are from Greece, and your country uses the same values as Morocco, so you don't have to change you VPI.VCI. it's 8.35

see you soon :)

---

### Post by cotiK on 2007-04-28
> **stuntgp2000 said:**
> Hi again,

Well you are from Greece, and your country uses the same values as Morocco, so you don't have to change you VPI.VCI. it's 8.35

see you soon :)

yeah!

---

### Post by cotiK on 2007-04-28
> **stuntgp2000 said:**
> Hi,
Here is what I did to get Sagem Fast 800 running on a clean Ubuntu 7.04 with PPPoA.

first, download Sagem Firmware from [here]("http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz")

It's preferable to unplug the modem

assuming you have downloaded that firmware and put it on your Ubuntu Desktop, run these commands from Terminal (found on Application Menu => Accessories => Terminal)

These lines will copy extracted binary firmware files to firmware directory
```

cp ~Desktop/ueagle-data-1.1.tar.gz /tmp && cd /tmp
tar -zxvf ueagle-data-1.1.tar.gz
sudo mkdir /lib/firmware/ueagle-atm
cd ueagle-data-1.1/
sudo cp -a * /lib/firmware/ueagle-atm/

```


now, we have to create a file that will be used to get Sagem connect to your ISP.
from Terminal, do
```
sudo gedit /etc/ppp/peers/ueagle-atm
```
then put these lines into the text editor that have appeared on the screen
```

user “login@ISP”
plugin pppoatm.so 8.35
noipdefault
usepeerdns
defaultroute
persist
noauth

```

you have to replace   login@ISP  with your real login@ISP   ,and   8.35  with your ISP VPI.VCI


Now, it's time to create a file that will contain our login@ISP and Password. from Terminal do:
```
sudo gedit /etc/ppp/chap-secrets
```
when text editor shows up, copy this line into that file
```
"login@ISP" * "password" *
```
again, replace    "login@ISP"  with your real ISP login  and replace  "password" with your real password. quotes must be retained.


It's time to test if we have succeeded to get our modem up and running.
Plug the modem, and from Terminal do:
```

sudo modprobe pppoatm
sudo modprobe pppoatm ueagle_atm


#wait a few seconds before running the next line to see if both modem led become green.

pppd call ueagle-atm


#if both led become green and you have run the above line and got this message "Plugin pppoatm.so loaded." then it's probably that you have successfully connected to the Internet. To verify run the following command and you receive details about your ppp modem interface.

ifconfig ppp0

```


if you got your modem running, then if you wish you can make your modem dial and redial automatically by following these further steps.

from Terminal, do this 
```
sudo gedit /usr/bin/adsl
```
this will show up the text editor again.
now copy/paste these into it.
```

#!/bin/bash
pppd call ueagle-atm

```
save the file, close text editor, return to Terminal and run this to make the file executable.
```
sudo chmod +x /usr/bin/adsl
```
then, we have to move it to a init.d directory to get it running at different stages of our Ubuntu Linux.
from Terminal, do this
```
sudo mv /usr/bin/adsl /etc/init.d
```
well, we are almost done, 
run this for Terminal to add its entry to different startup stages.
```
sudo update-rc.d adsl start 50 2 3 4 5 . stop 50 6 0 .
```
Note, the dots are not put into that line there by mistake, they are required.

Well, that's all you should have Internet running all day and should redial automatically without intervention from you part. However, if you want to drop the connexion, just run ```
poff
``` or ```
sudo poff
```  from Terminal, or if you want to dial manually run   ```
pppd call ueagle-atm
```


I hope that was helpful.

for French speaking people [here]("http://libreinfo.wordpress.com/2007/04/22/connexion-a-internet-en-utilisant-sagem-fast-800-usb-modem-ubuntu-704-feisty-fawn/") is the same thing in French
i did what you said and got both green lights running. But no conection whatsoever. I thnik that the proflem might be with the "secrets file". Idont know where exactly to put my codes in the file

---

### Post by casaoui on 2007-05-02
Hi,

I did all the step you mentioned above, but could not get to Internet after even if the ifconfig command shows that I am connected to the Web.

Is there any other steps / configuration that I must do to tell Ubuntu to connect to Internet using my dsl modem?

Thanks a lot for your valuable help.

Regards,
Karim

---

### Post by zeusalmighty on 2007-05-06
Well, I've been trying the same thing and indeed, it doesn't connect. The thing is, I don't think it's the secrets file, the Greece Sagem F@st 800 modem needs some extra firmware to be installed, the file is called "ueagle-atm-1.3.tar.gz". When you extract this, all you need to run is

> $ sudo make
$ sudo make install

in the directory you extracted. As for the "secrets" file, you just need to add the following line:

> "username@provider" * "password" *

pretty much anywhere. username@provider is ofcourse your full username your provider gave you (the one you use in windows at the dial-up screen you need to fill in).

Now, the problem is using the "make" command. I get an error using this, probably because my build-essential or linux-headers files are not the correct versions. I know that this worked in Dapper, i just can't get it to work in Feisty. Anyone for more heads-up?

---

### Post by stuntgp2000 on 2007-05-06
Hi, Sorry for the delay but I didn't receive any notification by email from this thread when you replied.

well, first of all, I can confirm that Ubuntu 7.04 from a CLEAN INSTALL DOES NOT NEED  ueagle-atm-1.3.tar.gz while it was necessary on both Ubuntu 6.10 & 6.06. Which means you don't need to compile anything for Ubuntu 7.04 to get connected  to the Internet. However, this may vary if your ISP uses PPPoE instead of PPPoA.

I will post at the end of this  post a why to get Ubuntu 6.10 & 6.06 to  connect to the Internet ;)


@cotiK
if you suspect that the problem is with chap-secrets then it's time to create another file named pap-secrets which may be need if your ISP use PAP to authenticates instead of CHAP.

form Terminal do this
```

sudo gedit /etc/ppp/pap-secrets

```
at the end of that file add your login and password, like  "cotik@greecom" * "102030" *
> "login@ISP" * "password" *
Note: quotes "" are required.
I hope that helped ;)


@casaoui
Your issue may be due to the fact that you have another network device configured as the default gateway.

From Terminal you can run **route** to see the default route. if everything is ok you should get a result like this
```

Destination     Passerelle      Genmask                 Indic   Metric     Ref     Use   Iface
adsl-1-31-192-8   *              255.255.255.255    UH      0            0        0       ppp0
10.0.0.0              *              255.255.255.0        U        0            0        0       eth0
link-local            *              255.255.0.0            U        1000      0        0       eth0
default               *              0.0.0.0                   U        0            0        0      ppp0

```
the last line which begin with default is the one we need, and as you see it points to ppp0 which is my Sagem F@ast 800 modem.

But, if default doesn't point to ppp0 and you are sure that ppp0 is activated when you checked using ifconfig then run this from Terminal
```

pppd call ueagle-atm
sudo route del default 
sudo route add default ppp0

```
well, you are done try to ping to google.com from Terminal.
```
ping google.com
```
then check your browser to see you are able to browse the Internet.
If everything went ok, then you may add a script that will do this for you or remove the gateway you have set.

here is the script you need to create, from Terminal do
```

sudo gedit /etc/ppp/ip-up.d/000defaultroute

```
then put this on it.
```

#! /bin/sh
set -e
/sbin/route add default ppp0

```
now, we make it executable by doing this
```

sudo chmod +x /etc/ppp/ip-up.d/000defaultroute

```
Ok, that's will do the trick for you ;)


@zeusalmighty
for build-essential & linux-headers packages they are available on Ubuntu CD.
P.S: Ubuntu 7.04 installs linux-headers by default


@To compile ueagle-atm-1.3.tar.gz for Ubuntu 6.10 & 6.06 by hand here are the steps.
first, download ueagle-atm form [here]("http://eagle-usb.org/ueagle-atm/ueagle-atm-1.3.tar.gz") and copy it into your home directory.
second, Insert Ubuntu CD into your CD/DVD driver, and open Terminal

run this to get your Ubuntu Kernel version number
> uname -r
now, suppose I got this result    2.6.17-11-generic

To remove  eagle-usb module which conflicts with ueagle-atm do this,
> sudo modprobe -r eagle-usb

now, we will remove eagle-usb module file, you should replace  Ubuntu_Kernel_version_number with what you got from uname -r
> 
sudo rm /lib/modules/Ubuntu_Kernel_version_number/kernel/drivers/usb/net/eagle/eagle-usb.ko
sudo rm /lib/modules/2.6.17-11-generic/kernel/drivers/usb/atm/usbatm.ko


It may be preferable to reboot your Ubuntu machine before you continue. but it's not obligatory.

now, it's time to install essential packages that will help us compile ueagle-atm from source.
note: replace  linux-headers-2.6.15-26  with the result you got from uname -r  for example, if you got  2.6.20-15-generic  then headers packages should be named  linux-headers-2.6.20-15  or  linux-headers-2.6.20-15-386
> 
sudo apt-get install  gcc  make  build-essential  linux-headers-2.6.20-15

After, you got those packages installed successfully don't forget to  UNPLUG  your Sagem Modem.

now, I suppose you have copied ueagle-atm into your home directory. form terminal do this
> 
cp ueagle-atm-1.3.tar.gz /tmp && cd /tmp
tar -zxvf ueagle-atm-1.3.tar.gz
cd ueagle-atm-1.3/
sudo make
sudo make install


that's all, ueagle-atm module is compiled. you may continue the rest of this guide [here ]("http://ubuntuforums.org/showpost.php?p=2548455&postcount=3")

Hope that was helpful. and don't forget to contact me by email to resolve any issue that may arise ;)

see you soon

---

### Post by zeusalmighty on 2007-05-07
Well, it turns out I had already installed all the packages you told me to, and even though I re-installed them later, the make command failed. So, I took the noobie route and re-installed Feisty ;)

I used your guide and it worked like a charm, only thing is, when I "ifconfig" I get a "Local Loopback" instead of a "Point to Point Protocoll". I also think my pap, chap and ueagle-atm configuration files have been configured correctly. This maybe an issue with my provider (even though my connection works fine in my windows boot??). I'd really appreciate any further ideas you may have, and GREATLY appreciate your feedback!

---

### Post by stuntgp2000 on 2007-05-07
Hi, 

@zeusalmighty

I am happy to hear that you got your Internet connection up & running :)

and I have no further information about your last issue since I am a Linux newbie too ;)

However, I may provide you with two things that may help.

first, the output of ifconfig on my ubuntu 7.04 machine
```

$ ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:0B:6A:36:BC:89  
          inet adr:10.0.0.1  Bcast:10.0.0.255  Masque:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:18 Adresse de base:0xe800 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:76 erreurs:0 :0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:5868 (5.7 KiB) Octets transmis:5868 (5.7 KiB)

ppp0      Lien encap:Protocole Point-à-Point  
          inet adr:81.192.120.126  P-t-P:81.192.120.1  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          Packets reçus:852 erreurs:0 :0 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3 
          Octets reçus:475907 (464.7 KiB) Octets transmis:211053 (206.1 KiB)


```

second, if you wish your dsl modem to have an explicit network interface that you may turn on/off using  
```

sudo ifdown ppp0
#or 
sudo ifup ppp0

```

then here is the trick, open terminal and edit a file called **interfaces** found in **/etc/network/**, this file simply has your network interfaces configuration.

Note 1: this may interfere with NetworkManager,which come by default on Ubuntu 7.04, if you mess with your local network adapters configuration if you have any.

Note 2: I found it somehow not reliable on Ubuntu 6.10, I think it didn't redial if I lost the connection, but I may be wrong since I was doing a lot of things concerning optimizing dsl speed :)

anyway, from terminal run this
```

sudo gedit /etc/network/interfaces 

```

then add this to the end of the file
```

auto ppp0
iface ppp0 inet ppp
provider ueagle-atm

```

that's all, now it's time to test if it's working.
```

sudo poff
sudo /etc/init.d/networking restart

```

now try  **ifconfig ppp0** and try to navigate. if things went wrong then open  interface file again and remove the lines you have just added and restart your network using **sudo /etc/init.d/networking restart**

I hope that helped, and remember I am at your service sir ;)

Berdai Mohammed

---

### Post by zeusalmighty on 2007-05-07
Well, what I actually meant was, my internet connection is NOT working! This time though, everything seems to be operating without errors as opposed to the gibberish I was getting with pon ueagle-atm BEFORE the re-install. I'm going to try it again later on, and also try the stuff you wrote earlier. Thanks a bunch!

---

### Post by ferahl on 2007-05-07
hi, i followed stuntgp2000 guide on the first page (2nd post)

i now have internet connection, and this is confirmed because i successfully pinged a few domains

HOWEVER i cant browse the net or connect to chat messengers etc

pls help!

---

### Post by zeusalmighty on 2007-05-08
Well, I redid the driver install and redid the info files, and guess what? IT WORKED! Thanks a bunch again, i'm going to try the other stuff you wrote about now.

---

### Post by stuntgp2000 on 2007-05-09
Hi,

@zeusalmighty
I'm happy you got your modem running ;)


@ferahl
I find that a little weird! usually if you pinged successfully, it means you could reach the Internet. are you sure you didn't install a firewall or anything else, or you have already another network interface set as default route !?
anyway, try to follow my answer to @casaoui issue **[here]("http://ubuntuforums.org/showpost.php?p=2605615&postcount=11")** 

See you soon ;)

---

### Post by Arwen on 2007-06-24
Hello everyone!
I typed "ifconfig ppp0" and got sth like "device not found".Both LEDs are on,I would appreciate if anyone told me what to do to procede,I've done all the previous steps too many times and still have the same error.
Thanx 4 n e response :-)


the error is:   "ppp0:error fetching interface information: Device not found"

---

### Post by mi.the.little on 2007-06-24
This is the same problem I'm having, after following exactly the guide on the first page.
Can someone please help??

---

### Post by stuntgp2000 on 2007-06-24
Well, there is one little problem, the **quote mark "** when copied from some code tags and pasted directly on the text editor gedit, becomes an inclined **quote mark  like this “**. So please, pay attention to it and try to verify all the code that has quotes such as your login@ISP and password and when you find these inclined quotes just try to replace it with the normal found on your keyboard.

---

### Post by mi.the.little on 2007-06-25
I checked the quote marks, its not that. When I do modprobe pppoatm and modprobe ueagle_atm, nothing happens. Ligtsh do not turn greeen, however, when I unplug and then plug the modem again, both lights turn green immediately! As mentioned earlier on ifconfig ppp0 I get "error: fetching from interface: device not found"  sth like that. :( :(
Any ideas? :(

---

### Post by Arwen on 2007-06-25
Do I have to install kernel sources or linux headers or sth like that before beginning the installation?I've tried with all sorts of quote marks,if it were so I would get errors or undefined or unkown declarations..Is it a problem that it's annex B(I have ISDN line)?

---

### Post by stuntgp2000 on 2007-06-25
It's weird because I have revised many times all the step I have mentioned in posts.

Just to clear things up, my guide applies to a **CLEAN UBUNTU 7.04 i386 INSTALL** and therefore nothing is required except what I mentioned.

However, if you are upgrading from Ubuntu 6.10, you have to make sure to remove eagle-usb ( a former driver for Sagem 800) or to black list it before you follow my howto.

To black list the former driver that's included within the previous version do this from Terminal:

```

sudo modprobe -r eagle-usb

sudo gedit /etc/modprobe.conf


```

then put this line in the text edito that has just appeared

```

blacklist eagle-usb

```

So to sum up things, my how to is for sagem fast 800, PPPoA mode, in a clean install of Ubuntu 7.04 i386.

I don't forget I would be very happy to help anyone who did get his modem working.

By the why, I would like from those who got their modem running to post, thanks in advance.

---

### Post by Arwen on 2007-06-25
When I did sudo modprobe -r eagle-usb it gave me FATAL as I don't have this module installed(thank god,cause I could have messed things with all those unsuccessful previous efforts)
It's a clean ubuntu 7.04 installation though..

---

### Post by mi.the.little on 2007-06-26
Well, it seems Arwen that we have the same problem. I have ISDN line too, thus my Sagem is not F@st 800, but F@st 840 E4 - designed for ISDN line. My guess is that yours is too. I tried everything and the modem doesn't seem to respond to any of commands that I give.
My final solution is not the efficient one, but I hope it will work - I called my ISP and I'm going to exchange my Sagem F@st 840, for the modem with Ethernet interface. If you have that option too, with your ISP, I strongly suggest - everydody says that it saves a lot of nervs :)

---

### Post by ::Reksio:: on 2007-08-17
Well, It seems that istalling the firmware is essential.. :/ Without the formware it doesn't work.. :/ So how to install the firmware under Ubuntu 7.04..? :> Any ideas..?

---

### Post by stuntgp2000 on 2007-08-18
Hi,

Please follow the steps I mentioned [at the beginning of this thread. Post #3]("http://ubuntuforums.org/showpost.php?p=2548455&postcount=3")

Regards,

---

### Post by coltrane on 2008-02-22
Will this guide still work with ubuntu 7.10?

---

### Post by stuntgp2000 on 2008-02-22
> **coltrane said:**
> Will this guide still work with ubuntu 7.10?

Yes, It does work with Ubuntu 7.10. I will update this howto as soon as it becomes incompatible with any future Ubuntu release.

---

### Post by coltrane on 2008-02-23
Thanks for your reply and help. :)

---

### Post by coltrane on 2008-02-24
Sorry, but nothing in this guide has worked for me. I'm installing it for a friends computer.
ppp0 never seems to be listed and the set route default commands do not exist in gutsy.
The modem has all green lights on though and otherwise appears to be connected.

---

### Post by stuntgp2000 on 2008-02-25
Hi,

**Please be patient and read this carefully !**

I have received a lot of emails in which they told me that they couldn't get the modem working. Then I have checked and found that this forum changes some symbols like the quotation mark in the scripts I wrote in the previous posts which makes them ineffective.

To make things easier I have written two scripts to do things automatically. One for PPPoA and the other for PPPoE DSL connectivity mode.


**Explaining things for both PPPoA & PPPoE, here is what you should do :**

Before you proceed, you should know that :
* You have to download some packages first.
* You have to **adjust** the script (either the one for PPPoA or PPPoE found below)  to your ISP's configuration. The script is well commented and should be easy to setup. Precisely, all you need to adapt is  the login, password & VPI/VCI configuration. if you are unsure about your VPI & VCI configuration, go [here]("http://faq.eagle-usb.org/wakka.php?wiki=ListConfigADSL") and see your ISP's VPI & VCI parameters.
* It's compatible with Ubuntu 7.04, 7.10 and 8.04.

These two scripts will :
* Extract and put the required firmware in the right place.
* Setup you box to connect & reconnect automatically.
* Set your modem as the default route.



**Instructions for PPPoA mode:**

You have to :
* Download the firmware from [here]("http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz") and put it into your home directory.
* Download the script named install_sagem_800_pppoa.sh below and put it into your home directory.
* Then you run it (from Terminal) with: ** sudo  bash ~/install_sagem_800_pppoa.sh**
* Reboot your PC and hopefully your DSL should be working now.



**Instructions for PPPoE mode:**

You have to :
* Download the firmware from [here]("http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz") and put it into your home directory.
* Download these two packages **libatm1** and **br2684ctl** :. 
[INDENT]- If you are using Ubuntu 7.04 (Feisty) get libatm1 from [**here**]("http://packages.ubuntu.com/feisty/i386/libatm1/download") and br2684ctl from [**here**]("http://packages.ubuntu.com/feisty/i386/br2684ctl/download").
- If you are using Ubuntu 7.10 (Gutsy) get libatm1 from [**here**]("http://packages.ubuntu.com/gutsy/i386/libatm1/download") and br2684ctl from [**here**]("http://packages.ubuntu.com/gutsy/i386/br2684ctl/download").
- If you are using Ubuntu 8.04 (Hardy) get libatm1 from [**here**]("http://packages.ubuntu.com/hardy/i386/libatm1/download") and br2684ctl from [**here**]("http://packages.ubuntu.com/hardy/i386/br2684ctl/download").
- If you are using any later version from Ubuntu go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and look for libatm1 & br2684ctl accordingly with your version.[/INDENT]
* Put the packages you have just downloaded into your home directory, then open Terminal and do: **sudo dpkg -i *.deb**
* Download the script named install_sagem_800_pppoe.sh below and put it into your home directory.
* Then you run it (from Terminal) with: ** sudo  bash ~/install_sagem_800_pppoe.sh**
* Reboot your PC and hopefully your DSL should be working now.




**Instructions if you want to uninstall the modem:**
* Download the script named uninstall_sagem_800.sh below and put it into your home directory.
* Then you run it (from Terminal) with: ** sudo  bash ~/uninstall_sagem_800.sh**



I hope this one will be the definitive post for people who wants to use their Sagem Fast 800 modem under Ubuntu & Debian derivatives for both PPPoA & PPPoE DSL mode ;-)


Please do not hesitate to contact me if you have any questions. I will be glad to help you. ;-)


**[COLOR="Red"]Last time updated : [/COLOR]**

**18 April 2008 :**
- Introduced the uninstaller script just like Jadd wanted :-)

**29 March 2008 :**
- Fixed a bug in both scripts related to the way Ubuntu handles "sh" scripts. @cclofton Thanks for the feedback.
- In this post: I updated how to run the scripts from Terminal. please look above.

**17 March 2008 :**
- Fixed a bug related to making ppp the default route in both scripts.
- Made both scripts under GPLv3.
- Added all the features Jadd asked for.
- Made both script more resilient to DSL connection dropping.
- Both scripts give feedback.
- PPPoE script try to be ACID compliant. The script won't proceed if it's not sure to successfully complete the installation.

**13 March 2008**
- Updated the script for PPPoA : install_sagem_800_pppoa.sh
- Introduced the script for PPPoE: install_sagem_800_pppoe.sh
.

---

### Post by Jadd on 2008-03-15
I tried the pppoe script with a friends Sagem 800 USB modem, and it worked! Thanks for that!
I do have suggestions though:
- make the script check it's running as root before attempting to do it's stuff.
- make the script verify that LOGIN, PASSWORD, VPI and VCI have been edited.
- make sure that those two debian packages have been installed.

I do have a problem though. Yesterday I installed the Sagem 800 driver with this script on a clean Gutsy Gibbon, and everything worked fine. I left it downloading 102MB of important 'security updates'. My friend has just phoned me to tell me that the Internet doesn't work anymore. It still works on Windows. So I think the updates must have caused that. Am I right?
I left everything in the home directory so I am going to tell him to run
sudo ./install_sagem_800_pppoe.sh
again. Hope this works.

---

### Post by stuntgp2000 on 2008-03-17
> **Jadd said:**
> I tried the pppoe script with a friends Sagem 800 USB modem, and it worked! Thanks for that!
I do have suggestions though:
- make the script check it's running as root before attempting to do it's stuff.
- make the script verify that LOGIN, PASSWORD, VPI and VCI have been edited.
- make sure that those two debian packages have been installed.

I do have a problem though. Yesterday I installed the Sagem 800 driver with this script on a clean Gutsy Gibbon, and everything worked fine. I left it downloading 102MB of important 'security updates'. My friend has just phoned me to tell me that the Internet doesn't work anymore. It still works on Windows. So I think the updates must have caused that. Am I right?
I left everything in the home directory so I am going to tell him to run
sudo ./install_sagem_800_pppoe.sh
again. Hope this works.

Thank for reporting that it worked for you.

I found your suggestions to be useful. In fact, I had already thought about such functionalities but since I am a beginner too I tried to avoid implementing them. However, I do really want these two scripts to be useful for people with different level of experience which requires for me to make things even better and easier. I have to thank you again for pushing me to find out how to implement what you suggested.

I will soon update those scripts. ;-)

Concerning the issue your friend had with it. I've got the same issue here but in my case I have just switched to ADSL2 / TV-DSL so I thought that maybe it's the cause. The good news is that I have mostly identified the issue and I am already trying to fix it. So I will update my post soon.

Thanks for cooperating. For those who used or will use those scripts please report back any problem you have found or at least report back that it worked for you. Thanks in advance. :-)

---

### Post by Jadd on 2008-03-20
You're welcome.
I asked my friend to simply run the script again and it fixed the problem. So looks like there's some update somewhere that broke something.

---

### Post by lifeisalongwhile on 2008-03-23
Any hope on Allied Telesyn AT-AR206?

Reply me soon

Thanks in advance.

---

### Post by cclofton on 2008-03-28
@ stuntgp2000
I appreciate how much work you've done, and obviously it worked for some...but not for me. I've been trying to get this damn modem to work all night. It's really disheartening. It seems insane that I can repartition a hard drive and install an entire operating in less than ten minutes, yet it then takes over 7 hours to try to get a modem to work. It is insane. Perhaps this is just a one off, but if all future hardware installations are going to be like this, I'm giving up on linux for a few more years.

Anyway, my problem, for what it's worth, is that the script comes up with the following 
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
[: 155: ==: unexpected operator
[: 155: ==: unexpected operator
the script can't complete the configuration of the network interfaces file, perhaps it was modified manually or misconfigured.

Well, it certainly wasn't modified, because that's the second time I've done a clean install (7.10) and done NOTHING in linux except run those scripts (and edit them first, yes). 

This is really really frustrating. I thought I'd found the solution when I found this thread, as you've clearly done a great job writing all the scripts, and it was a welcome relief to have something automated rather than having to manually retype dozens of lines into the terminal, as I had to do with other "solutions". 

And yet....it still doesn't work.

Really, really not happy right now. A whole evening wasted, 8 reinstalls (since I know nothing about linux, so I don't know what settings change when running other people's terminal commands), and yet still no success. I'm thinking of just going out and buying a wireless router tomorrow to get around the whole problem, but then I wonder how many problems I'm going to have trying to set THAT up, and if my money will be wasted.

Seriously - ubuntu people, if you're listening - amazing job done on the software, but if you're planning to conquer the windows market you need to make harware installation as painless as it is in windows (and I've never considered it painless until now). I see no reason why linux drivers that are freely available on the internet cannot come in the install (and no, they're not in 8.04 - I tried that too). Maybe there's licensing laws or something, I don't know, but I doubt it very much. Why would Sagem care about their drivers being distributed when they're freely available from the website? 

Or if you really can't distribute them in ubuntu, at least make some kind of installer package to help the process along. Coming to it cold is a nightmare for someone used to exe's and dll's.

Anyway, I've gone on long enough. If you have any advice to offer, I'd love to hear it, else I'm going back to windows. I've got work to do!

Cheers

---

### Post by stuntgp2000 on 2008-03-29
@ cclofton
Thanks for reporting the issues you found. I've fixed those issues in my post above. It's was a mistake for me not to do enough testing before releasing those scripts. Lesson learned.

The firmware is not allowed to be redistributed, so it can't be included in GNU/Linux Distributions. Even Windows does not recognize that modem, it's only by using the driver from Sagem's site or by using a CD provided by your ISP that makes it work. Unfortunately, some hardware (less than 10%) still gives headaches in order to work. But Hey!!, we should look at the big picture, the value we get from GNU/Linux. Personally, I made I commitment to support GNU/Linux or Free Software by all means, and no matter what it takes I will not go back to the proprietary software which sometimes makes things easier but at the cost of pushing me to be depend, ignorant, and to license every bit of usage.

@Everyone
Please don't hesitate to report your feedback, I do address every feedback very quickly. Thanks in advance.

---

### Post by cclofton on 2008-03-30
Well, I haven't run the new version of the scripts, because I did the sensible thing and bought a router yesterday. Worked straight away with ubuntu - not a single problem. And now..........I'm converted! Once I got a connection to the internet, everything flowed smoothly. Sure, there's still a few issues, but I'm so happy with ubuntu I'm also converting my laptop. Wonderful wonderful software, and thanks to everyone for all the support and help. Sorry if I was grouchy before!

Ubuntu people - I love you all

---

### Post by johnc1970 on 2008-04-03
I've been having a few probs with my Sagem F@st 800 E2T on Feisty.  I've mostly followed the procedure in this post and have the following:

[FONT="Courier New"][COLOR="Blue"]johnc@johnc-machine:~$ ifconfig ppp0[/COLOR]
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:80.my.fixed.IP  P-t-P:212.87.77.54  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:186 (186.0 b)  TX bytes:112 (112.0 b)[/FONT]


[FONT="Courier New"][COLOR="blue"]johnc@johnc-machine:~$ route[/COLOR]
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.87.77.54    *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         80.my.fixed.IP    0.0.0.0         UG    0      0        0 eth0[/FONT]

My DNS servers are correct in resolv.conf

I can ping 212.87.77.54, but can't ping anything else.

I suspect my routeing table above might be at fault, but I'm not sure.  Perhaps default should use ppp0 instead of eth0, or the Gateway for default should be 212.87.77.54.  I'm at work at the moment and won't be trying again till this evening, but any help would be greatly appreciated.  

Thanks,
John

---

### Post by stuntgp2000 on 2008-04-03
@Johnc1970

Yes, I think the route is the cause.

To set it up manually type in into Terminal : 
```
sudo route del default
sudo route add default ppp0
```

Did you use one of the scripts above or have you set up things manually ?

---

### Post by johnc1970 on 2008-04-03
That worked a treat.  I now have broadband!

My routeing table is now:

[FONT="Courier New"][COLOR="Blue"]johnc@johnc-machine:~$ route[/COLOR]
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
redback-lb-bgp. *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
[COLOR="Blue"]johnc@johnc-machine:~$ [/COLOR][/FONT]


I hadn't followed the script exactly as I'd started at the start of the thread rather than the end.  I ran into into problems but didn't want to go as far as reinstalling so had tried tinkering.

Many thanks!

---

### Post by Jadd on 2008-04-18
Hey Stuntgp, believe it or not, my friend moved house, and now he doesn't need the USB modem anymore. Anyways, for some reason Ubuntu doesn't recognise the new ethernet card, and so I'm wondering whether the installed USB modem driver is intefering. Could you write an uninstall script? Thanks.

---

### Post by stuntgp2000 on 2008-04-18
@Jadd
It's done. I have introduced the uninstaller script ;-)

---

### Post by Grizli on 2008-05-22
Try this:

```
http://www.ubudsl.com/en/download.php
```

It works!:guitar:

---

### Post by kumo99 on 2008-06-30
I followed both the step by step tutorial and the Ubudsl package, yet it didn't work until now that I realized that the firefox goes in offline mode by default! when I disable that option I connect to the internet without problems..:D

Thank you all for the help

---

