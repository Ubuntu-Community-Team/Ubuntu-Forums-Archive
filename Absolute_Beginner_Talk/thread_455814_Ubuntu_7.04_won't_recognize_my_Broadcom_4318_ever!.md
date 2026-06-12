---
title: "Ubuntu 7.04 won't recognize my Broadcom 4318 ever!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by seungki on 2007-05-27
Yes, I've done everything I could.  I'm serious.  I looked at all the help guides, tutorials, etc.  My friend even told me my computer is whacked.  I have a HP Pavilion dv5000 series, dualbooting with Ubuntu Linux 7.04 Feisty Fawn with Windows XP SP2 on a 1gig ram, 90gig hdd, amd turion 64 system.

Since I followed some of the tutorials, I have also installed ndiswrapper and all.


This is the chat log between him and me.  It will providde most of the information you need.

[http://pastebin.ca/513198](http://pastebin.ca/513198)

If you need me to do a terminal to whatever more information you may need (if you're too lazy to read that pastebin), then please ask and I'll do what I can to give you the information you need.

Thanks for helping this newb out!

---

### Post by mengfei on 2007-05-27
Ooh, Broadcoms are a pain.

Is wireless absolutely essential? My wireless doesn't work perfectly either, so I opted to just live with ethernet, meaning I run down two flights of stairs everytime I want to use the Internet.

Also, I suspect that the network-manager that is now default in Feisty may be the culprit of my issues on my laptop wireless. It could be the same for you. You may or may not want to try using an older version of Ubuntu, such as Edgy or Dapper.

---

### Post by seungki on 2007-05-27
> **mengfei said:**
> Ooh, Broadcoms are a pain.

Is wireless absolutely essential? My wireless doesn't work perfectly either, so I opted to just live with ethernet, meaning I run down two flights of stairs everytime I want to use the Internet.

Also, I suspect that the network-manager that is now default in Feisty may be the culprit of my issues on my laptop wireless. It could be the same for you. You may or may not want to try using an older version of Ubuntu, such as Edgy or Dapper.


*sigh*  I'll check what kind of responses I get, and I will decide then I suppose.

---

### Post by solarwind on 2007-05-27
Hmm... This is weird. I'll try to look something up...

---

### Post by seungki on 2007-05-27
Gah this is so hard :(

---

### Post by solarwind on 2007-05-27
Post the full output of the following:

ndiswrapper -l

sudo ifconfig

lsmod

lspci

Remember to use code tags when posting ouput...

---

### Post by taco_truck on 2007-05-27
This thread worked for me:

[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by seungki on 2007-05-27
> **solarwind said:**
> Post the full output of the following:

ndiswrapper -l

sudo ifconfig

lsmod

lspci

Remember to use code tags when posting ouput...

```

(00&#49884; 24&#48516; 47&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: ndiswrapper -l

(00&#49884; 24&#48516; 48&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: type that

(00&#49884; 25&#48516; 30&#52488;) Seungki: k

(00&#49884; 25&#48516; 48&#52488;) Seungki: Installed ndis drivers:
bcmwl5          driver present, hardware present 

```

```


(00&#49884; 27&#48516; 43&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: type this

(00&#49884; 27&#48516; 48&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: sudo ifconfig

(00&#49884; 27&#48516; 59&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: im sure e're getting close to solving this

(00&#49884; 28&#48516; 23&#52488;) Seungki: eth0      Link encap:Ethernet  HWaddr 00:0F:B0:C4:F0:9D  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fec4:f09d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33456260 (31.9 MiB)  TX bytes:3414401 (3.2 MiB)
          Interrupt:21 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)



```

```
You have my lsmod, solarwind.
```

```

(00&#49884; 35&#48516; 46&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: lspci

(00&#49884; 35&#48516; 48&#52488;) [    &#348; &#1060; &#321; Å &#1071; &#1064; &#8747; &#330; &#272;    ]: tellme output

(00&#49884; 36&#48516; 17&#52488;) Unable to send message: The message is too large.

(00&#49884; 36&#48516; 20&#52488;) Seungki: er..

(00&#49884; 36&#48516; 38&#52488;) Seungki: http://rafb.net/p/HmbisN67.html


```


@taco_truck:  I don't have ubuntu edgy.  I have Feisty Fawn and I don't know if that works or not.  I will try it though, thanks.

---

### Post by jrmwvu04 on 2007-05-27
I will also refer you to this howto: (it does work on Feisty)

[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

However, before you get started with that you should take a few steps to try to clean up failed attempts. 

1. uninstall the current windows driver ndiswrapper has loaded
```
sudo ndiswrapper -r bcmwl5
```

2. remove ndiswrapper from the modules
```
sudo rmmod ndiswrapper
```

3. if you installed ndiswrapper from the Feisty repositories, ok. otherwise you might want to do that before continuing. that version worked better for me.

At this point you should be able to start at the Edgy howto post. I definitely recommend using the driver linked in the howto. There are other methods of getting the bcm4318 up and running, I hear, but this method was easiest for me. After you get through the howto, I personally recommend getting the "wifi-radar" package from the repos, especially if you're going to be using encryption. It's pretty straight forward if you have all the information about the wifi network you're using. Hope this helps. If it doesn't work or you need more specifics, just ask.

---

### Post by seungki on 2007-05-27
> **jrmwvu04 said:**
> I will also refer you to this howto: (it does work on Feisty)

[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

However, before you get started with that you should take a few steps to try to clean up failed attempts. 

1. uninstall the current windows driver ndiswrapper has loaded
```
sudo ndiswrapper -r bcmwl5
```

2. remove ndiswrapper from the modules
```
sudo rmmod ndiswrapper
```

3. if you installed ndiswrapper from the Feisty repositories, ok. otherwise you might want to do that before continuing. that version worked better for me.

At this point you should be able to start at the Edgy howto post. I definitely recommend using the driver linked in the howto. There are other methods of getting the bcm4318 up and running, I hear, but this method was easiest for me. After you get through the howto, I personally recommend getting the "wifi-radar" package from the repos, especially if you're going to be using encryption. It's pretty straight forward if you have all the information about the wifi network you're using. Hope this helps. If it doesn't work or you need more specifics, just ask.


Thanks I'll post my results when I reboot on Linux.

---

### Post by solarwind on 2007-05-27
You might also want to look into blacklisting some old modules or something...

---

### Post by seungki on 2007-05-27
> 
If hardware not found and you are sure you followed the howto you have a different card and this howto will not work.


From the howto.  I did everything and it say that the driver is invalid, but why?  I do have that driver.  :(

---

### Post by jrmwvu04 on 2007-05-28
> You might also want to look into blacklisting some old modules or something...

That's covered in the howto.

> From the howto. I did everything and it say that the driver is invalid, but why? I do have that driver. 

Well.. are you definitely sure you have a 4318 card? Is it a Broadcom brand card or an off brand using the bcm4318 chipset? Maybe if it is, you could find drivers that are a better match? I don't know what to tell you for sure because it worked for me two different times (once with the card in the Aspire 5050 it came in and once transplanted into an Inspiron 5100). What's the exact output of the "ndiswrapper -l" command?

Edit: I might also add that if it's not too much of a hassle, you may have better results if you follow that howto from a fresh install of Ubuntu. I find that at times when you tinker with things too much you get a lot of unwanted residual problems.

---

### Post by jargoman on 2007-05-29
I have the same computer as you and I'm using wireless right now. I just wrote a how to on the broadcom.
I have a dv5216ca. That's a sub model of the dv5000 series. You can check your service tag sticker on the bottom of your computer but I think all the dv5000 series have the same chip.

if you run
$ lspci | grep Broadcom

you'll get:
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

This is the how to I just thew up 5 minutes ago. 
[http://freeshells.ch/~jargoman/ndiswrapper.html](http://freeshells.ch/~jargoman/ndiswrapper.html)

The drivers and everything you need are provided there and this works on my computer every time. I bet you it will work. Just be sure that everytime you want to connect that you press your wireless on/off button a few times every time you reboot. This is a known bug in ndiswrapper. I have to do it everytime but once I connect I find it more reliable than windows. (it's the same driver). 

Once on a sabayon system I also would have to run
$ sudo rmmod ndiswrapper
$ sudo rmmod bcm43xx
$ sudo modprobe ndiswrapper 
every time I rebooted because although I edited my blacklist file bcm43xx was still loading. You can check this with
$ lsmod | grep bcm43xx 
This should show nothing if the module isn't loaded.

please follow up with whether or not it worked I'd like to know. I'm sure it will.

---

### Post by jargoman on 2007-05-29
I'll be adding more how to's to that site. They will all relate to the computers I have. For now the dv5000 and the one broadcom how to.

---

### Post by Eagle 101 on 2007-05-29
Um, its not working for me, I'm doing a brand new xubuntu install, nothing has changed other then following your instructions. No wireless card light (yes I'm using broadcom 4318.) I'm also using v7.04 of xubuntu.

Just a note your directions say:

[FONT=Comic Sans MS][I][FONT=New Times Roman]$ cd ~/Desktop/ndiswrapper
$ sudo make uninstall
$ make

[/FONT][/I][FONT=New Times Roman]i[/FONT][FONT=New Times Roman]t should say

[/FONT][/FONT][I][FONT=Comic Sans MS][FONT=New Times Roman]$ cd ~/Desktop/ndiswrapper-1.42
$ sudo make uninstall
$ make[/FONT][/FONT][/I]


if that is not the case then your files are off. I'll paste in my lspci output in case that helps. 

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

Thanks for any help you can give

---

### Post by Josey on 2007-05-29
First remove ndiswrapper
```
sudo apt-get remove ndiswrapper
```
then install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot & enjoy wireless

---

### Post by Eagle 101 on 2007-05-29
Err... how do I install that? Sorry! (and thanks for the help)

---

### Post by Eagle 101 on 2007-05-29
Well I'm going to report to note that the above tutorial does not work. But [this]("http://ubuntuforums.org/showthread.php?t=197102") does. Though the instructions do note the requirement for a new install of ubuntu. Thanks for the help, and hopefully this will be useful to the original poster of this thread.

---

### Post by Josey on 2007-05-29
I have broadcom 4318 and it works perfect for me.

---

### Post by jargoman on 2007-05-29
Eagle 101:
 Thank you for pointing the error on my site. It's now fixed. That's good because I want people to be able to copy and paste.

 I looked at your lspci output. You do have the same card as me. Infact I believe you may have the same computer. The hp dv5000. You should note that sometimes these broadcom cards get stuck in "monitor mode". They should be in "managed mode". I noticed this when I messed around with backtrack 2. When you use a program like kismet or airsnort they put the card in monitor mode and they get "stuck". 
What I mean by stuck is that the ndiswrapper driver doesn't support changing the mode. The patched bcm43xx driver can. I have never patched the driver but I know that backtrack 2 comes default with the patched driver. All the patch does is add suport for changing to and from monitor mode.

You have to boot into windows and it will switch to monitor mode automatically.

This is the result of "$ iwconfig" on my computer using the ndiswrapper with the wlan0 alias.

wlan0     IEEE 802.11g  ESSID:"spike"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:A3:2F:0B:E2   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:770  Invalid misc:21458   Missed beacon:0

If the part that says mode is different then you have to change it with
$ sudo  iwconfig wlan0 mode managed
$ sudo ifconfig eth1 up

Like I said though your card might be stuck in a mode that ndiswrapper can't get out of. You need to use windows or backtrack 2. 

As a side note by default your card is detected as eth1 (sometimes eth0 but not usually) my how to adds an wlan0 alias. You can exchange this step
   
 $ sudo gedit /etc/modprobe.d/ndiswrapper

with

$ sudo gedit /etc/modules
Then just add the word "ndiswrapper" to the bottom of the list of modules you want to load.

I didn't include this step because I figured people want their card to read as wlan0 not eth1

I will be adding a trouble shooting page to the site as well.

---

### Post by Eagle 101 on 2007-05-30
Did you notice me pointing to another tutorial that works very well... perhaps you can look at that. That tutorial worked for me the first time around with minimal fuss, just download one thing, and run it, and it works.

The other tutorial can be found at  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102).
*Also a second note, following the above tutorial means that you don't have to turn the wireless card on and then off. I just now noticed that, it works every time on start up the way that you would expect it to. 

If after looking at that tutorial you think yours is good as well,  I would suggest adding contact data to your website for notification of errors. 

Another idea would be to submit your tutorial to the ubuntu forums. There is a section for HowTos, this would be very useful for those seeking help as they can ask questions in the forum part of the HowTo. Just an idea.

Cheers, and thanks for trying to help :).

-- edit --
Also in case this helps you out, follows is my iwconfig, perhaps it will help you in working with your tutorial. Please do remember I did not use your tutorial (I tried but had problems), but the other one that I linked to. I don't know if booting into windows would help or not (you are assuming that those you are helping are indeed dual booting with windows), so you might want to check out and see how and why this tutorial was able to bypass that requirement. Cheers! :)

eth1   IEEE 802.11g  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:5C:3D:44:11   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jargoman on 2007-05-31
Thank you for your output and input, lol. I was wondering what driver you are using ndiswrapper or linux native bcm43xx. I went with ndiswrapper because at the time bcm43xx only had 11mb/s max bit rate. 

plus this error in my log all the time:
/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:03.0' with ...

I noticed that yours works fine. If that's the case I'll post that specific bcm43xx driver to my site as an alternative. 

If your unsure what driver you have installed then try these commands

$ ls /lib/firware/bcm43xx*                                      (I'm not sure, that's the directory on gentoo)

$ lsmod | grep bcm43xx                                         
 
if you get nothing for both than your using ndiswrapper

thank you,

---

### Post by Eagle 101 on 2007-05-31
Ok, trying what you have stated: the first command did not work, and the second one gave nothing. So I ran sudo find / | grep bcm4318 the output I will add on to the end of this post.

Also I have configured xubuntu on a second computer, also with broadcom 4318, again I tried your tutorial first. I'm sorry to report that it failed again. The other tutorial worked, again. I don't know what is not working with the two, but I suggest that you have a read over the second tutorial. I would also suggest that if you continue to have your own tutorial, to at the very least put a link to the second tutorial, in case yours does not work. To be honest I think that your tutorial would be better off on the ubuntu forums in the howto sections, simply because of the increased chance that others can help, and report on if it is working. Again at the very least to help other folks should your tutorial fail, I would leave a link to the ubuntu howto I gave you in prior posts. That seems to work every time. Cheers! and let me know fi there is anything I can do to help you figure out why your script is not working. (please note that I ran it through **first thing after installing xubuntu, on two different computers, it failed both times**. Hope I can help you figure out what exactly went wrong. :) 

Output from find /:

/usr/local/apache2/bin$ sudo find / | grep bcm43xx
Password:
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/pci.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/dma.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/dma
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/dma/and
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/dma/and/pio
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/dma/and/pio/mode.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211/pio.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/mac80211.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/dma.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/dma
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/dma/and
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/dma/and/pio
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/dma/and/pio/mode.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/bcm43xx/pio.h
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/bcm43xx
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/bcm43xx/Kconfig
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/bcm43xx/Makefile
/usr/src/linux-headers-2.6.20-16/drivers/net/wireless/bcm43xx
/usr/src/linux-headers-2.6.20-16/drivers/net/wireless/bcm43xx/Kconfig
/usr/src/linux-headers-2.6.20-16/drivers/net/wireless/bcm43xx/Makefile
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/pci.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/dma.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/dma
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/dma/and
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/dma/and/pio
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/dma/and/pio/mode.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211/pio.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/mac80211.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/dma.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/dma
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/dma/and
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/dma/and/pio
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/dma/and/pio/mode.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/bcm43xx/pio.h
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/bcm43xx
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/bcm43xx/Kconfig
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/bcm43xx/Makefile
/usr/src/linux-headers-2.6.20-15/drivers/net/wireless/bcm43xx
/usr/src/linux-headers-2.6.20-15/drivers/net/wireless/bcm43xx/Kconfig
/usr/src/linux-headers-2.6.20-15/drivers/net/wireless/bcm43xx/Makefile
/usr/share/doc/bcm43xx-firmware
/usr/share/doc/bcm43xx-firmware/copyright
/usr/share/doc/bcm43xx-firmware/changelog.Debian.gz
/media/hda1/Program Files/mIRC/logs/freenode/##bcm43xx.20070314.log
/media/hda1/Program Files/mIRC/logs/freenode/#bcm43xx-wireless.20070314.log
/media/hda1/Program Files/mIRC/logs/freenode/#bcm43xx.20070314.log
/media/hda1/SWSetup/WLAN/bcm43xx.cat
/media/hda1/SWSetup/WLAN/bcm43xxa.cat
/var/lib/dpkg/info/bcm43xx-firmware.list
/var/lib/dpkg/info/bcm43xx-firmware.preinst
/var/lib/dpkg/info/bcm43xx-firmware.postinst
/var/lib/dpkg/info/bcm43xx-firmware.md5sums
/lib/firmware/bcm43xx_initval02.fw
/lib/firmware/bcm43xx_initval09.fw
/lib/firmware/bcm43xx_pcm5.fw
/lib/firmware/bcm43xx_pcm4.fw
/lib/firmware/bcm43xx_microcode2.fw
/lib/firmware/bcm43xx_initval04.fw
/lib/firmware/bcm43xx_microcode5.fw
/lib/firmware/bcm43xx_microcode4.fw
/lib/firmware/bcm43xx_initval07.fw
/lib/firmware/bcm43xx_initval08.fw
/lib/firmware/bcm43xx_initval05.fw
^[[5~/lib/firmware/bcm43xx_initval01.fw
/lib/firmware/bcm43xx_initval06.fw
/lib/firmware/bcm43xx_initval03.fw
/lib/firmware/bcm43xx_initval10.fw
^[[5~/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/bcm43xx
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx
/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx
/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

---

### Post by GabrielDunn on 2007-05-31
I had the same issues and I gave up.  I dual boot and use wireless in xp and feisty for everything else.  I'm just crossing my fingers for dell to release their own distro to solve my problem for me.

---

### Post by bmartin on 2007-05-31
I have the same chipset and I got it working. It worked with the firmware and the ndiswrapper method, but it was very flaky with the firmware. Here's [my solution]("http://ubuntuforums.org/showthread.php?t=457371"). It's a work-in-progress, but it's worked twice so far.

---

### Post by MrObvious on 2007-05-31
I just run the bcm43xx driver and it runs fine. The only problem (which I'm stil researching) is that I can't get a full 54 meg connection. Do the following code and you should be good:

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe bcm43xx
```
That should get you up and going. Just make sure you remove all instances of ndiswrapper.

Edit: I'm running a BCM4318.

---

### Post by bmartin on 2007-05-31
> **MrObvious said:**
> I just run the bcm43xx driver and it runs fine. The only problem (which I'm stil researching) is that I can't get a full 54 meg connection. Do the following code and you should be good:

```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe bcm43xx
```
That should get you up and going. Just make sure you remove all instances of ndiswrapper.

Edit: I'm running a BCM4318.
The commands you have listed install the bcm43xx module, which only works for *some* Broadcom chipset (e.g., not mine). You'll never get 54Mbps w/ them because they only support 11Mbps. To get 54Mbps, use ndiswrapper. Many people also have flaky connections when using the bcm43xx module.

I'm running a BCM4318 and it's flaky w/ bcm43xx.

---

### Post by jargoman on 2007-06-01
**[COLOR="Red"]UPDATE[/COLOR]** I find out that my how to wasn't working because of a recent Ubuntu kernel update. I made the necessary changes and it now works.

[http://freeshells.ch/~jargoman/](http://freeshells.ch/~jargoman/)

If it doesn't it's because your card is stuck in monitor mode. Bcm43xx driver should be loaded then run
$ sudo iwconfig eth1mode managed

or replace eth1 with wlan0 depends what your card registers as

 Even though it's slow and low range bcm43xx has the abillity to go in and out of monitor mode. Used by wep cracking programs. ndiswrapper can't be used for wep cracking as far as I know. bcm43xx driver is easy to install as well.

$  sudo apt-get install bcm43xx-fwcutter
select yes when the screen comes up and your done

just make sure it's not still blacklisted if you want it to load at boot. Though both ndis and bcm can be installed at once only one driver should be loaded at a time

$ sudo blacklist /etc/modprobe.d/blacklist

change: 
blacklist bcm43xx
to:
# blacklist bcm43xx

and add a # infront the word ndiswrapper in
sudo gedit /etc/modules

or 

sudo gedit /etc/modprobe.d/ndiswrapper
# infront of all entries

switch between the two drivers by removing and loading the respective modules
$ sudo rmmod ndiswrapper
$ sudo modprobe bcm43xx

If you want ndiswrapper to load at boot you remove the # you placed in front of the configuration commands above. This will be added to the site as well soon enough. I also will link to other how to's. For now i need sleep. I have telecommunication courses I'm taking as well, overworked!

---

### Post by Eagle 101 on 2007-06-01
I still say you need a contact e-mail on that site.  Also I'd suggest a link to the other working script, as it does not require you to turn the card on and off. (yes it reaches 54mb/s as well.) :)

Also would it be useful for me to write up a bash script that does these commads for you?

Cheers! :)

---

### Post by jargoman on 2007-06-02
Since I updated my site the need to turn the card on and off has been fixed.

I'll add an email link as well. I will also add various links to other sites or at least to the one site that worked.

---

