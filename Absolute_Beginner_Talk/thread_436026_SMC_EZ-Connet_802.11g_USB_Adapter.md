---
title: "SMC EZ-Connet 802.11g USB Adapter"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by aspri on 2007-05-07
Hi all,

I've just installed Ubuntu 6.06 today and got it installed successfully. The only device that didn't work is the SMC EZ-Connect 802.11g USB adapter. It has been detected by Ubuntu (apparently) as it shows up in the Device Manager. However, it didn't seem to work.

I googled the problem online (I'm very new to Linux btw) but got no success. I initially tried to configure the wi-fi using the network settings GUI. I entered the ESSID and WEP key (in hex) and left everything else in default. That didn't work so I went to terminal and tried a few things.

First off, I tried iwconfig and got the following reply.

lo     no wireless extensions

etho0     IEEE802.11b EESSID:"2wireXXX"
              Mode: Auto   Channel=6   Access Point: Invalid
              Sensitivity-0/200
              Link Quality:0   Signal level:0   Noise level:0
              Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
              Tx excessive retries:0   Invalid misc:0   Missed beacon:0

sit0   no wireless extensions

I noticed that it says 802.11b instead of g. How do I change that? Also, the channel was originally wrong and I set it to 6 using the iwconfig command. Here's another error I found but I think it's related to the b and g issue. Here's what I get when I type "sudo iwconfig eth0 key XXXXXXXXXX":-

Error for wireless request "Set Encode" (8B2A) :
   SET failed on device eth0; unknown error 524

Does anyone have any clues? Thanks for your help!

---

### Post by aspri on 2007-05-08
Er...anyone got an idea how I can proceed on this? This is exasperating. I'm currently using 6.06 and am downloading Fiesty to see if it gets around the problem. I hope I don't have to boot up my Windows XP again...:(

---

