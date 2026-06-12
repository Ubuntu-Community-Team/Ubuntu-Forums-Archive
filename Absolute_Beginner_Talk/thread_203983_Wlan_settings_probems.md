---
title: "Wlan settings probems"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-06-26
I'm new to Linux.

I've made up a "new" PC with my "old"  2Ghz Athlon and 1Mb ram.

I ran Ubuntu 5.10 live and Kubuntu 6.06 live, eventually getting connected to my WLAN and the internet but only by using the terminal to input the settings. My Belkin ralink card is recognised and I know the drivers come with Ubuntu/Kubuntu.

I decided to install Kubuntu 6.06 on the new HD. The wireless settings don't seem to be saved in the Network box. WEP keeps returning to ASCI.  Having to go into admin to configure the wireless card ra0 seems to lose the settings. I'm not sure how I should save the settings. I have to anyway go into Terminal to set the channel.

If I configure the wireless card from terminal it seems to work but I'm not sure how I would write a script to set up the wireless card.

Last night when eventually I got connected to the internet it was very slow. Sorry but my XP PC had no wireless problems. 

Suggestions?

---

### Post by AndyCooll on 2006-06-26
What settings were you entering into "Networking"? And perhaps you can give us a print of your /etc/network/interfaces file, this is where your network settings are kept

:cool:

---

### Post by Handssolow on 2006-06-26
Thanks Andy
Arriving home from work I was expecting to look for any replies on this forum, my normally stable XP machine came out in sympathy with a critical blue screen. I've done a system restore, sent messages to Bill's company, updated my video drivers, McAfee's AV, reconfigured Spamkiller etc. Finally a Reg Seeker clean seems to have got it sorted. Perhaps all caused by some Adobe updates.Oh happy days.

Back to Linux and Kubuntu. I've moved on to spent the last few hours tying to make some sense of were my WLAN problem(s) is(are). I've just got my Linux machine on the internet with Google. I searched for this site then my link goes. Wireless Assistant had shown between five stars then three, then crashes with a report of Signal 11 SIGSEGV. I've not rebooted but I can't get Wireless Assistant back.

20 minutes later

I'm wondering if I haven't got my IP addresses sorted and that I don't fully understand this area. At one stage my XP PC reported a wireless conflict on the toolbar. I thought this was all handled by the DHCP server in the router. How do I ensure I'm going for an Infrastructure not an Adhoc WLAN?

I went back to my Kubuntu PC, iwconfig shows no link, and now sudo iwconfig shows no encryption. 

I input the WEP key with 

sudo iwconfig ra0 key XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX

and for just a change I've tried inputting my routers IP

sudo /sbin/route add default gw 196.168.1.1 

I'm connected to the internet and things looked much faster than before, but returning to this XP PC it reports a wireless conflict.

So I'm losing WLAN settings for no apparent reason.
I've an IP conflict.
Network monitor has crashed.

Time for bed.

---

