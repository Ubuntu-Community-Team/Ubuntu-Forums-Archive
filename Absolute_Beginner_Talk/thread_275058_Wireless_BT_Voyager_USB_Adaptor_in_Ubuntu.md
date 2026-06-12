---
title: "Wireless BT Voyager USB Adaptor in Ubuntu"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by ubunovice88 on 2006-10-10
Hello, new here.

I'm looking for some advice on wireless in Ubuntu. I have a BT Voyager 1055 USB Wireless Adaptor which I'd like to use in Ubuntu. I was told by someone to download ndiswrapper, which I now have (On Windows partition), but I have no idea what to do with this file.

ndiswrapper-1.25.tar.gz

I get the idea from the net that .gz is a Linux compressed file?

Thanks, ubunovice88

---

### Post by dmizer on 2006-10-10
what you've downloaded is a programs compressed source code.  when you unpack it, you'll have to compile it (turn the code into something linux can understand).

if you have no internet connection at all on your ubuntu box right now, you're going to have quite an adventure trying to install ndiswrapper from source.

to do that, you'll need a whole range of programs installed on your system that is only available when connected to the internet.  sure, you can download these seperately and install them individually, but you're looking at a seriously lengthy hair pulling project.

also, this will not garantee that your card will work after you're done.  so you could spend weeks in what we like to call "dependency hell", resolve everything, only to find out that all your effort was in vain.

i suggest doing the following:

take a look at the output of
```
lspci
```
find your network adapter and it will give you more information (specifically chipset).

then look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and see if you can find a card with the same chipset.  then use the directions given there.

frankly, i think your best bet (if you have no other way to connect to the internet) is to look at the above link, and find another adapter that works without configuration.

---

### Post by ukripper on 2007-02-02
If someone could tell me the way HowTo extract .exe, it would perhaps push this issue towards the resolution.

I have already tried cabextract with no luck and also unzip doesn't work. Tried internet but no avail.

Is there any other way to extract exe or inf from exe? OR if someone could tell me the .inf needed for bt voyager 1055 or the required chipset?

extracting exe seems to be the tough one , I assume, even for the ubuntu community but I have faith in everyone here:) .

---

### Post by helliewm on 2007-02-02
I tried this the other day I downloaded the drivers from Voyager 1055 USB Adaper CD that BT send you. I could find the INF file either. I gave up and neither could get my Belkin F5D7011 Network card working either. In the end Bigken from this forum kindly sent me a compatible Linkssys card in post.

Could you keep me posted on the outcome to this?

Helen

---

### Post by ukripper on 2007-02-02
> **helliewm said:**
> I tried this the other day I downloaded the drivers from Voyager 1055 USB Adaper CD that BT send you. I could find the INF file either. I gave up and neither could get my Belkin F5D7011 Network card working either. In the end Bigken from this forum kindly sent me a compatible Linkssys card in post.

Could you keep me posted on the outcome to this?

Helen




Sure Helen, I really want this problem to get resolved not just for me but for our masses ( our ubuntu family) that is why I am not going to give up and get a new network card, I already have resolved similiar problem with my other laptop which had bcm4318 pcmcia card and now working fine. 

please could you tell me the full name of that linksys compatible driver probably that could resolve this mystery and I think only piece is remaining to fit the whole puzzle that is .inf

Thanks.
Ash

---

### Post by aberry5555 on 2007-02-02
There's one easy way to get the drivers out, if you still have a windows box lying around somwhere stick it on there, and once it's unpacked raid the "temp" directory for the files you want, or try and install it on wine, then just copy the files out of the driver repository in the windows folder you create.

---

### Post by helliewm on 2007-02-02
Actually may be I did not clearly explain Ken sent me a spare new Network Card that is compatible with Ubuntu. Hence I had to give up on  BT Voyager USB adpater and the Belkin card as desparately needed WIFI.  I never did manage to resolve the issues as I just could find the INF file for the BT Voyager 1055 USB Adapter.

I am afraid I gave up and am using the new Network Card Ken sent me. I would love to hear the outcome  to see if you can get it working.

Helen

---

### Post by ukripper on 2007-02-02
> **aberry5555 said:**
> There's one easy way to get the drivers out, if you still have a windows box lying around somwhere stick it on there, and once it's unpacked raid the "temp" directory for the files you want, or try and install it on wine, then just copy the files out of the driver repository in the windows folder you create.

Thanks for reply aberry.:KS 
I have tried using universal extracter which does the very similiar operation looking into temp while .exe is running but to my surprise this particular exe whoever created is very cleverly put together which keeps no track records in temp therefore it runs directly through cd without caching in temp so I reckon this option is also comes under exclusion list for 1055.

---

### Post by ukripper on 2007-02-02
> **helliewm said:**
> Actually may be I did not clearly explain Ken sent me a spare new Network Card that is compatible with Ubuntu. Hence I had to give up on  BT Voyager USB adpater and the Belkin card as desparately needed WIFI.  I never did manage to resolve the issues as I just could find the INF file for the BT Voyager 1055 USB Adapter.

I am afraid I gave up and am using the new Network Card Ken sent me. I would love to hear the outcome  to see if you can get it working.

Helen

Helen sorry I misunderstood your post in a hurry. I am also really looking forward for this issue to make another HowTo for our growing community. 

And I know somewhere someone has the answer for exe extraction, can't be that hard. I believe in ubuntu community forever.

:)

---

### Post by ukripper on 2007-02-05
Some how I have managed to find the name of inf and sys files  used for BT voyager 1055, it is called AegisP.inf and AegisP.sys However, I could only get hold of AegisP.inf but still I need AegisP.sys file. 

Any suggestions friends?:confused: 

Thanks.
Ash

---

### Post by tyres on 2007-02-13
Hi guys,

I came across this thread while looking for information on getting the BT 1055 USB adapter working under Ubuntu Edgy 6.10. There doesn't seem to be much information out there about it, but I thought you might like to know that I can report success! I've now got a BT 1055 working properly under Ubuntu Edgy.

I'd previously got a Belkin USB 54G working under Ubuntu, so armed with that experience I thought I'd give the BT 1055 a go, as I had 2 (!) of them lying about, apparently useless for me as they seemed not be operable under Ubuntu.

The key to getting these things to work in my (fairly brief) experience is to know what brand the chipset is inside the adapter. What company's name is on the outside doesn't matter so much. I tried to discover what was inside the BT 1055 by software means, but could only get some indication that it was a Broadcom chip. So I took the plunge and physically opened the adapter to see what was inside! That was quite easy (opening it) as it happens, the two sides just clip together, so it's easy to pull them apart :-)

It turns out it's a Broadcom 4320 chip inside. I then went to the NDISWrapper homepage. There's a list there of adapters that people have had some success in installing under Linux (see 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)),
and I looked for people who had installed adapters with a Broadcom 4320 chipset, of which there are a number. One stood out, as he mentioned the drivers I knew I had on the BT 1055 installtion disk (bcmrndis.inf, copy RNDISMPK.sys & usb8023k.sys). 

So I followed his instructions. It's a bit geeky, as you have to create a hardware configuration file under /etc/udev, but if you follow what he says, and then follow the usual procedure to run a driver with ndiswrapper, it works! I was gobsmacked when the light came on on my BT 1055 :-))) I had to reboot before the adapterr associated with my BTHomeHub router, but then it was off and running.

Anyway, the guy's posting on the NDISWrapper adapter list is number 50, search for 'Gladier' (his name I think).

Good luck.

Colin

---

### Post by ukripper on 2007-02-14
Great news! the good thing is I know my chipset drivers on my disk as I had to rip the temp files in windows xp to find just the name in a hex file and that was bcmrndis so probably I assume it is bcmrndis.sys and bcmrndis.inf which i need. But there is a problem as i couldn't find any drivers for bcmrndis. 


Guys another good news after long struggle, last week i have found  BT voyager adapter is similiar to Belkin F5D7051 (USB 2.0 Adaptor 802.11g 125Mbps) and using the same drivers as i have extracted it and found all the bcmrndis files needed to wrap with ndiswrapper to make it work and today I am going to try it as I go home and will post the results. Looks like it is time for HowTo after tests are done.

---

### Post by ukripper on 2007-02-14
Found some more detail for bcm4320 from ndiswrapper website:

Card: Belkin F5D7051 (USB 2.0 Adaptor 802.11g 125Mbps) 
Chipset: BCM4320 
usbid: 050d:7051 
Driver: Used hidden driver's from installation CD - bcrndis.inf - installation via commandline - configuration via controlcenter. 
Other: Tested on Mandriva 2006 Free - ndiswrapper 1.13 
Other: Tested on Mandriva LE 2005 - ndiswrapper 1.34 
Other: Keyboard freezes on hotpluging. 



Proving the theory.
Should theoratically work with BT voyager 1055 but still pratical has to be done which i would conduct today.

---

### Post by tyres on 2007-02-15
Hi,

Like I said in my last post, I managed to get the Belkin 54G adapter working under Ubuntu.
However, mine is a 7050, not a 7051, and the chipset is Ralink, so it uses the rt73 driver.

Fortunately I discovered that there is a native Linux rt73 driver. You have to download the 
source code and compile it, but that's not too difficult, and obviously it's better having 
something that works natively with Linux, rather than via ndiswrapper.

If you want to try the BT 1055 thing, I could probably mail you the drivers (they're pretty 
small), although I'm surprised they aren't on your installation disk. You won't find a 
bcnrndis.sys driver file, maybe that's what your problem was? The files you need are 
bcmrndis.inf, rndismpk.sys and usb8023k.sys. See if you've got those someplace.

Cheers,

Colin

---

### Post by ukripper on 2007-02-16
> **tyres said:**
> Hi,

Like I said in my last post, I managed to get the Belkin 54G adapter working under Ubuntu.
However, mine is a 7050, not a 7051, and the chipset is Ralink, so it uses the rt73 driver.

Fortunately I discovered that there is a native Linux rt73 driver. You have to download the 
source code and compile it, but that's not too difficult, and obviously it's better having 
something that works natively with Linux, rather than via ndiswrapper.

If you want to try the BT 1055 thing, I could probably mail you the drivers (they're pretty 
small), although I'm surprised they aren't on your installation disk. You won't find a 
bcnrndis.sys driver file, maybe that's what your problem was? The files you need are 
bcmrndis.inf, rndismpk.sys and usb8023k.sys. See if you've got those someplace.

Cheers,

Colin

Nice work mate. Have you tried BT voyager 1055 with the same drivers. Do they work? As I dint get a chance to test the drivers i have downloaded. Would you be so kind to send the drivers those work for 1055, would save me some hassle. do 7050 drivers work for bt 1055 also?

Cheers mate.

---

### Post by johnnyxf on 2007-02-20
greetings.

i am brand new to ubuntu [today, v6.10] and like ukripper am trying to get an internet connection through a bt voyager 1055.

i have installed ndiswrapper from the live cd - apparently correctly: it is responding - and attempted to install the drivers - bcmrn.inf, RNDISMPK.sys, usb8023k.sys - following the instructions in th ubuntu documentation project, ie. sudo ndiswrapper -i ~/Desktop/bcmrn.inf.

however ndiswrapper -l gives: bcmrndis invalid driver, and the wireless widget is definitely not working.

tyres: in post #14 you mention native a linux driver rt73, which is available from opensource.bureau-cornavin.com. did you mean that this will work for the voyager 1055? 

can anyone help me out, please? thanks.

learning process proceeds:
i have:
- installed driver bcmrndis.inf with ndiswrapper
- copied usb8023k.sys & rndismpk.sys to /etc/ndiswrapper/bcmrndis/
- created hardware configuration file  /etc/udev/rules.d/99-custom.rules [see post #11]
- ndiswrapper -l now gives bcmrndis driver present, hardware present [yay]

however, sudo modprobe ndiswrapper now returns Invalid argument error.

update.
went back to square one.
- reintalled ndiswrapper
- installed driver bcmrndis.inf with ndiswrapper
- copied usb8023k.sys & rndismpk.sys and also usb8023.sys & rndismp.sys to /etc/ndiswrapper/bcmrndis/. 
- created hardware configuration file  /etc/udev/rules.d/99-custom.rules [see post #11]
- ndiswrapper -l gives bcmrndis driver present, hardware present
- sudo modprobe ndiswrapper and sudo ndiswrapper -m now work
- reboot

but the wireless adapter is still inactive, and no wireless connection is recognised by the system.
i have checked the widget on another machine, and the usb socket itself - both are fine

examination with lshw shows the device, but i note that there is no driver mentioned in the configuration line. does this mean that there is in fact no driver associated with the adapter, despite ndiswrapper claiming otherwise?

any help much appreciated. thanks.

---

### Post by campbellj on 2007-02-25
I found aegisP.sys in WINDOWS\system32. 

:guitar:

---

### Post by tyres on 2007-02-26
Hi Johnny,

I replied to another thread you were in about this subject, but in case you don't read that I'll repeat here. I think the problem is, as you surmise in the other thread, your /etc/udev/99-custom.rules script. I changed 2 things in the script that Gladier had in his posting on the ndiswrapper site. When I opened the BT1055 adapter to see what chip was inside, I noted down everything that was on the chip, and that included the Vendor and Product ids. Those weren't the same as the ones Gladier quoted, so I figured I should change those to what I had  seen on the chip in my adapter. It worked, so I guess I didn't do anything wrong at any rate.

That might be the key to your problem. I suggest you substitute the values for 'idProduct' and 'idVendor' that i've got in my 99-custom.rules script, and see if that works for you.

Here's my 99-custom.rules script;

#START**
BUS=="usb",
SYSFS{idProduct}=="0715", 
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**


Good luck,

Colin

PS. No the Ralink rt73 driver I used to get a Belkin USB 54G adapter working will not work for the BT1055, it's a different chipset altogether.
I just mentioned it because ukripper mentioned trying a Belkin adapter.

C

---

### Post by overproof on 2008-02-03
Hi
I had a voyager 1055 doing nothing, so when I read this post I thought I ll give it a go, but I have the same problem the voyager 1055 is not recognised.
 
This is what I've done so far:
-installed driver bcmrndis.inf with ndiswrapper
-copied usb8023k.sys & rndismpk.sys and also usb8023.sys & rndismp.sys to /etc/ndiswrapper/bcmrndis/
-made a file called "99-custom.rules" and typed in it:
#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**
-then put this file in:   /etc/udev/rules.d/

Any more help will be appreciated. thanks

---

### Post by ukripper on 2008-05-05
> **overproof said:**
> Hi
I had a voyager 1055 doing nothing, so when I read this post I thought I ll give it a go, but I have the same problem the voyager 1055 is not recognised.
 
This is what I've done so far:
-installed driver bcmrndis.inf with ndiswrapper
-copied usb8023k.sys & rndismpk.sys and also usb8023.sys & rndismp.sys to /etc/ndiswrapper/bcmrndis/
-made a file called "99-custom.rules" and typed in it:
#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**
-then put this file in:   /etc/udev/rules.d/

Any more help will be appreciated. thanks
Finally after 2 years I have successfully made my BT voyager 1055 working under ubuntu Hardy. Right now i am typing using my new voyager 1055 in ubuntu:-)

I would like to share with my fellow ubuntu mates how I have achieved this:-

Step 1 - Dowloaded and installed latest Bt voyager drivers from BT's website on my windows box. Once installed I went into program files/BT VOYAGER/ folder and copied all over to my ubuntu box.

Step 2 - Make sure your Voyager 1055 device is connected to your ubuntu box. Installed latest ndiswrapper-1.9 from hardy's repos.


Step -3 - In terminal &#8211; type following once you are in folder where you copied the BT voyager files to.
```
sudo ndiswrapper -i bcmrndis.inf
```
don't worry if you get invalid error. just carry on!

Step -4 - Run ```
ndiswrapper -l
```, it is 'ell' not one

Step -5 - copy files over ```
sudo cp -v  usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/
```

Step -6 - Run again ```
ndiswrapper -l
``` and then ```
sudo modprobe ndiswrapper
```

Step -7 - create new file - ```
sudo gedit /etc/udev/rules.d/99-custom.rules
```

Step -8 - copy paste the following:
#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**


then save and exit



Unplug your adapter and plug it back. Everything works hopefully for you as well. 

configure your wireless using network manager and then off you go.


I have never felt so much relieved resolving this, like a quest for me. :guitar:

---

