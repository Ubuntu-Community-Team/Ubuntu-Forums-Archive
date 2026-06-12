---
title: "Help with wireless setup"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Deguello on 2007-03-05
Good morning...

I have installed Ubuntu Feisty Herd with Wubi so I can dual boot. It is on my Acer Aspire 5601 AWLMi. 

This notebook has the Intel 3945ABG wireless built in.

Everything works except this wireless setup.

I have tried several different methods for getting it installed to include installing ndiswrapper 1.38 but I am unable to get it to work.

Is there a more simpified way to get this working? Can someone point me to the right place or post to fix this. I am afraid I have mired myself to the point that I am lost. 

My wireless shows up in the hardware, but I do not get the wireless section in the Network.

Thanks for your help.

---

### Post by martbuang on 2007-03-06
To start with I had similar problems but the following worked for me. I have a Toshiba A60 laptop with a Linksys WPC-11 version 4 PCMCIA wireless adapter running Ubuntu 6.10. Ubuntu recognized my adapter on install and I didn't have to set it up. 

First check that Ubuntu can see your wireless adapter. In Terminal enter the command *iwconfig*. You should get something like this;

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b linked  ESSID:"FUNKNET"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0F:B5:7A:F8:1E   
          Bit Rate=11 Mb/s   
          Retry: on   Fragment thr: off
          Power Management: off
          Link Quality:34/100  Signal level:-54 dBm  Noise level:-190 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/I]

If so you can now setup wireless networking. You will need to install *network-manager-gnome*, once installed reboot and network manager should work on start up. It will scan for available networks and present you with a list ( make sure you enable SSID broadcast on your access point!), select your network. If an encryption key is required it will prompt you for it and it will ask you to set up a password for access to the network. You should now be able to access your wireless network. 

Martin.

---

### Post by tjod on 2007-04-04
I have the Aspire 5601 as well. I use WICD for the wireless:

[http://compwiz18.blackhole.cx/wicd/wb/]("http://compwiz18.blackhole.cx/wicd/wb/")


> **Deguello said:**
> Good morning...

I have installed Ubuntu Feisty Herd with Wubi so I can dual boot. It is on my Acer Aspire 5601 AWLMi. 

This notebook has the Intel 3945ABG wireless built in.

Everything works except this wireless setup.

I have tried several different methods for getting it installed to include installing ndiswrapper 1.38 but I am unable to get it to work.

Is there a more simpified way to get this working? Can someone point me to the right place or post to fix this. I am afraid I have mired myself to the point that I am lost. 

My wireless shows up in the hardware, but I do not get the wireless section in the Network.

Thanks for your help.

---

