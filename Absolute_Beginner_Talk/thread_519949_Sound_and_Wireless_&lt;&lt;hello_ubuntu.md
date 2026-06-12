---
title: "Sound and Wireless &lt;&lt;hello ubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-07
Hello,
I've been trying to resolve a number of hardware based problems with ubuntu.  I currently have a dual-boot with windows xp, but would love to switch over to pure ubuntu (except for it's hardware/driver problems, love the gnu/linux/ubuntu os).

2 key things preventing that: sound and wireless.

Here are some threads I've started investing the sound issue:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121644](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121644)
[http://ubuntuforums.org/showthread.php?t=479912&highlight=no+sound+fiesty+fawn](http://ubuntuforums.org/showthread.php?t=479912&highlight=no+sound+fiesty+fawn)
[https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/8321](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/8321)

Anyone know if progress has been made on the sound issue with gateway mx3701?

2ndly, wireless:
how do I get wireless to work?  Do I need ndiswrapper, ro something? thnaks.

---

### Post by svega85 on 2007-08-07
i have the gateway mx3414 with the same issues. i feel your pain. tobad it's still broken

---

### Post by johntkucz on 2007-08-07
hehe, misery may love company, but I don't love misery!  broken may not be the best word -- "incompatible, unsupported drivers" might be the best choice.  However, I will NEVER by gateway hardware again, these things are pieces of crap!  the shitty keyboard has lost two keys!  Trinkpad, hp, dell, and apple make the best DURABLE hardware in my mind.  hardware durability has just become a major priority -- we're talking thick, heavy duty laptop keypads.  even the the ibooks are okay but powerbook pro even has too flimsy of a keyboard and main frame for me!

---

### Post by Rovdjur on 2007-08-07
> **johntkucz said:**
> 2ndly, wireless:
how do I get wireless to work?  Do I need ndiswrapper, ro something? thnaks.

Well a quick google told me that your wireless chipset is a Realtek RTL 8185L. Typing "lspci" into terminal can confirm this.

And the Hardware Support document for Ubuntu [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek") show that it does in fact work out of the box (in the previous Ubuntu releases, and it should work for Feisty as well (I assume you are using Feisty)).

Go to Terminal and type "iwconfig" and paste what comes up.

And is the wireless AP you are tryping to connect to have WEP or a WPA encryption? Try disabling the encryption to see if you can just connect at all.

---

### Post by golden11 on 2007-08-07
I also have an MX3414 laptop, dual booting with xp and fiesty fawn.  I have the exact same problems as well...the sound and wireless network is not working.  I haven't  tried fixing the sound, but here's what I have tried for the network issue.

I tried ndiswrapper using the following guide[I][COLOR="Blue"]
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")
[/COLOR][/I]
it ended up making my ubuntu freeze up during the boot process and the caps lock key kept blinking.  I did a reinstall since I am a newbie.

After that I found another post [COLOR="Blue"][I][http://ubuntuforums.org/showthread.php?t=370579]("http://ubuntuforums.org/showthread.php?t=370579")
[/I][/COLOR].  As Is mentioned in the the post, the driver files used were from Realtek's website.  That link is [COLOR="Blue"][I][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")
[/I][/COLOR]I chose the linux driver, of course.

Neither of the above options worked.  They both led me to the following error

[INDENT][INDENT][I]golden@golden-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device[/I][/INDENT][/INDENT]

For information purposes, here is the result of hwinfo.

[I][INDENT][INDENT]36: PCI 609.0: 0200 Ethernet controller
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8185
  Unique ID: bTKz.wyILY+jcc03
  Parent ID: 37TO._XJP+gD25h8
  SysFS ID: /devices/pci0000:00/0000:00:10.0/0000:06:09.0
  SysFS BusID: 0000:06:09.0
  Hardware Class: network
  Model: "Realtek Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8185 
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8185 
  Revision: 0x20
  I/O Ports: 0x6000-0x6fff (rw)
  Memory Range: 0xb3400000-0xb34001ff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v000010ECd00008185sv000010ECsd00008185bc02sc00i00"
  Driver Info #0:
    Driver Status: r818x is not active
    Driver Activation Cmd: "modprobe r818x"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)[/INDENT][/INDENT][/I]

---

### Post by golden11 on 2007-08-07
Here is my results from iwconfig, for comparison to johntkucz's.
[INDENT][INDENT]
golden@golden-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT][/INDENT]

Here is my results from lspci

[INDENT][INDENT]06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)[/INDENT][/INDENT]


I'm not trying to steal the spotlight, only help resolve the problem because our problem seems identical. 

*Note  I am using the 64 bit version of Ubuntu I believe.  uname - a results are as follows
[INDENT][INDENT]Linux golden-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux[/INDENT][/INDENT]

---

### Post by Rovdjur on 2007-08-07
> **golden11 said:**
> I also have an MX3414 laptop, dual booting with xp and fiesty fawn.  I have the exact same problems as well...the sound and wireless network is not working.  I haven't  tried fixing the sound, but here's what I have tried for the network issue.

I tried ndiswrapper using the following guide[I][COLOR="Blue"]
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")
[/COLOR][/I]
it ended up making my ubuntu freeze up during the boot process and the caps lock key kept blinking.  I did a reinstall since I am a newbie.

After that I found another post [COLOR="Blue"][I][http://ubuntuforums.org/showthread.php?t=370579]("http://ubuntuforums.org/showthread.php?t=370579")
[/I][/COLOR].  As Is mentioned in the the post, the driver files used were from Realtek's website.  That link is [COLOR="Blue"][I][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")
[/I][/COLOR]I chose the linux driver, of course.

Neither of the above options worked.  They both led me to the following error

[INDENT][INDENT][I]golden@golden-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device[/I][/INDENT][/INDENT]

For information purposes, here is the result of hwinfo.

[I][INDENT][INDENT]36: PCI 609.0: 0200 Ethernet controller
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8185
  Unique ID: bTKz.wyILY+jcc03
  Parent ID: 37TO._XJP+gD25h8
  SysFS ID: /devices/pci0000:00/0000:00:10.0/0000:06:09.0
  SysFS BusID: 0000:06:09.0
  Hardware Class: network
  Model: "Realtek Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8185 
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8185 
  Revision: 0x20
  I/O Ports: 0x6000-0x6fff (rw)
  Memory Range: 0xb3400000-0xb34001ff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v000010ECd00008185sv000010ECsd00008185bc02sc00i00"
  Driver Info #0:
    Driver Status: r818x is not active
    Driver Activation Cmd: "modprobe r818x"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)[/INDENT][/INDENT][/I]

I downloaded those drivers you linked to just to see what you were working with.

Did you trying following the instructions in the INSTALL file?

(For Ubuntu)
```
cd /path/to/realtekdriver/folder/rtl818x-0.1
gedit INSTALL
```

Or

 (For Kubuntu)
```
cd /path/to/realtekdriver/folder/rtl818x-0.1
kate INSTALL
```

---

### Post by golden11 on 2007-08-08
i satisfied the install instructions that you let me to, but when i got to

[INDENT][INDENT]tar xzf rtl8180-0.9.1.tar.gz
cd rtl8180-0.9.1
make[/INDENT][/INDENT]

I typed make and the contents of the directory disappeared. 

Getting to section 3.2 on module loading, I got stuck yet again

[INDENT][INDENT]sudo insmod ieee80211-r8180_crypt.ko
# you may or may not have to do this following step, Knoppix needs it
sudo insmod /usr/src/linux/lib/crc32.ko
# you will also need ARC4 support in kernel or by loading module

sudo insmod ieee80211_crypt_wep.ko
sudo insmod ieee80211-r8180.ko 
sudo insmod r8180.ko[/INDENT][/INDENT]

first of all, i was able to see that i don't have .ko files, i have .c files
and those .c files disappeared after make.

not sure what to do next, instruction are for knoppix

---

### Post by golden11 on 2007-08-08
I just tried booting with live CD with Ubuntu "Edgy Eft" 6.10 and it recognized i had a wireless device.
I just had to plug in the ssid and bam, it was working.  Something must have changed for the worse from 6.10 to 7.04  "Feisty Fawn"   I will say that Edgy seems a big more glitchy in other areas, but maybe that is due to the fact that i am running it from cd.

---

### Post by golden11 on 2007-08-08
ok so here's the deal.  The driver for the rlt8185 has been blacklisted.  For those of you were like me a coulple of days ago, it means the driver doesn't load at startup.  Like mentioned earlier, I have a MX3414 as well, and in fact the driver does allow me to get on the network.  Here's what I did to get it working, but before for that, know that it has been blacklisted because it has frozen certain computers in the boot process.  I recommend backing up your needed files in case of a necessary reinstall.  Unless there is a way to edit the blacklist in a console without booting...not sure though, but if someone knows the answer to that please tell me.  I've been messing with linux for only two days.

Go to the terminal window...............Applications > Accessories > Terminal

type in the following code:
```
[INDENT]gksu gedit /etc/modprobe.d/blacklist[/INDENT]
```

Scroll to the bottom of the list and you will see the following line
[INDENT]# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187[/INDENT]

Now, place a # in front of blacklist r818x to ignore that line.
Reboot

Go to System > Administration > Network and you should see a wireless connection
Double click the wireless connection and Roaming Mode should be enabled.  if so,you can close it out.  Now try to choose the wireless network you would like to connect to in the top right on the network tray icon (im sure that's not what u call it).   Choose your network and it should work. 

If that doesn't work, go back to the network setting and unclick the enable roaming mode box.  type in your ESSID ...in my case "linksys"  and type your WEP key in as the network password.  Haven't tried the secured network yet.  Post some results.

---

### Post by johntkucz on 2007-08-08
wow thanks a ton for the enormous amount of response quality! I'll check the posts and get back to you.

---

### Post by johntkucz on 2007-08-08
> **Rovdjur said:**
> Well a quick google told me that your wireless chipset is a Realtek RTL 8185L. Typing "lspci" into terminal can confirm this.

And the Hardware Support document for Ubuntu [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek") show that it does in fact work out of the box (in the previous Ubuntu releases, and it should work for Feisty as well (I assume you are using Feisty)).

Go to Terminal and type "iwconfig" and paste what comes up.

And is the wireless AP you are tryping to connect to have WEP or a WPA encryption? Try disabling the encryption to see if you can just connect at all.

Right now I'm just trying to set up being able to recieve any wireless signal at all in ubuntu.  The router I have has wpa2 encryption of something and I have it rigged to only accept MAC ids on the list, but i'll make it low-level security to first install it; first step is just picking up a signal.

In attempts to learn the commands that could potentially help me....
iwconfig == the wireless version of ifconfig.  it sets the wireless frequency and fetches stats from /etc/net/wireless.
[http://www.linuxcommand.org/man_pages/iwconfig8.html](http://www.linuxcommand.org/man_pages/iwconfig8.html)

lspci -- lists all the hardware PCI devices and all pci devices connected to them. you can get more information by including the various degress of verbosity (-v, -vv, -vvv) which, for more advanced users, provide more information on the PCI hardware network and locations and drivers on your computer.
[http://linux.die.net/man/8/lspci](http://linux.die.net/man/8/lspci)


I have to learn what commands I'm issuing to make sure I can repeat and understand a successful hack-fix!

---

### Post by johntkucz on 2007-08-08
> **golden11 said:**
> I also have an MX3414 laptop, dual booting with xp and fiesty fawn.  I have the exact same problems as well...the sound and wireless network is not working.  I haven't  tried fixing the sound, but here's what I have tried for the network issue.

I tried ndiswrapper using the following guide[I][COLOR="Blue"]
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")
[/COLOR][/I]
it ended up making my ubuntu freeze up during the boot process and the caps lock key kept blinking.  I did a reinstall since I am a newbie.

After that I found another post [COLOR="Blue"][I][http://ubuntuforums.org/showthread.php?t=370579]("http://ubuntuforums.org/showthread.php?t=370579")
[/I][/COLOR].  As Is mentioned in the the post, the driver files used were from Realtek's website.  That link is [COLOR="Blue"][I][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")
[/I][/COLOR]I chose the linux driver, of course.

Neither of the above options worked.  They both led me to the following error

[INDENT][INDENT][I]golden@golden-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device[/I][/INDENT][/INDENT]

For information purposes, here is the result of hwinfo.

[I][INDENT][INDENT]36: PCI 609.0: 0200 Ethernet controller
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8185
  Unique ID: bTKz.wyILY+jcc03
  Parent ID: 37TO._XJP+gD25h8
  SysFS ID: /devices/pci0000:00/0000:00:10.0/0000:06:09.0
  SysFS BusID: 0000:06:09.0
  Hardware Class: network
  Model: "Realtek Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8185 
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8185 
  Revision: 0x20
  I/O Ports: 0x6000-0x6fff (rw)
  Memory Range: 0xb3400000-0xb34001ff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v000010ECd00008185sv000010ECsd00008185bc02sc00i00"
  Driver Info #0:
    Driver Status: r818x is not active
    Driver Activation Cmd: "modprobe r818x"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (PCI bridge)[/INDENT][/INDENT][/I]

Hey golden,
Awesome! Finally I found a kindred linux hacker going through the same difficultis (with gateway) that I experience, simultaneously! I'll keep this thread posted with new findings.  Sincerely appreciate your input, man.  I've put a lot of time into the sound.  Maybe I'll have some luck with the wireless.

Note: about installing new drivers, key system software (like ndis, etc.) a lot of people said somethings worked before "upgrading".  I just want to be careful that, in installing wireless, I don't, for example, lose my ability to "boot" or something!

---

### Post by johntkucz on 2007-08-08
> **golden11 said:**
> Here is my results from iwconfig, for comparison to johntkucz's.
[INDENT][INDENT]
golden@golden-laptop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT][/INDENT]

Here is my results from lspci

[INDENT][INDENT]06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)[/INDENT][/INDENT]


I'm not trying to steal the spotlight, only help resolve the problem because our problem seems identical. 

*Note  I am using the 64 bit version of Ubuntu I believe.  uname - a results are as follows
[INDENT][INDENT]Linux golden-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux[/INDENT][/INDENT]

It looks like Ravdjur was right, and your post confirms it: our wireless chipset (hardware) sounds like 8185.  That will be essential in getting it to work.

---

### Post by johntkucz on 2007-08-08
Wireless links:


[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) -- debian linux (not ubuntu, but still potentially helpful)
[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283) (targets the same router I'm using -- wrt54g -- useful for later stages of problem resolution -- after ubuntu can first pick up a signal)
[http://ubuntuforums.org/archive/index.php/t-191776.html](http://ubuntuforums.org/archive/index.php/t-191776.html) -- realtek 8185 references
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5376](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5376)

---

### Post by golden11 on 2007-08-08
I just did a fresh install and tried to do what I did earlier....and it doesn't work.   Somewhere along the line, something I did worked, but I can't seem to pinpoint the exact process to success.  It's bugging me like crazy to know that it worked and I can't re-create the awesomeness of walking around on browsing the net.  Earlier I noticed that I had better succes on actually seeing the wireless networks around me in the Network Manager applet in the top right of the panel.  anybody else have any luck?

*****************************************
EDIT:
              I got in to working consistently with Ubuntu 6.10 (Edgy Eft).  
[INDENT]Step 1 fresh install
Step 2 make sure your connected to the internet via a cable not wireless
Step 3 Right click Network Manger icon in top right and click remove from panel.
Step 4, go to System > Administration > Networking. Select &#8220;Wireless Connection&#8221; and click 
[INDENT]Properties. Un-check &#8220;Enable this connection&#8221;.  Click OK then Close.[/INDENT]
Step 5 Go to Applications > Add/Remove. Search for Network Manager. Check Network Manager 
[INDENT]and click OK. Click Apply when asked &#8220;Apply the following changes?&#8221;. When completed, click Close.[/INDENT]
Step 6 Restart computer
Step 7 Left click the new network manager icon and select your wireless network.  Mine 
[INDENT]connected and after a reboot to check, it automatically connected again after[/INDENT]
[INDENT]next restart.  Signal strength says 30% but I know its more.  I think its faster than its saying.[/INDENT]

My network is unsecure at the moment, so I'll post the results of that test.
Finally, walking and browsing the net...

Try this in Feisty Fawn someone... I don't feel like another install at the moment.



[/INDENT]

---

