---
title: "Help with T60 wireless"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by patrickk on 2007-05-04
Hey there

I just installed ubuntu tonight on my lenovo t60 and am having a bit of trouble with the wireless.  I installed and started using ubuntu with a wired connection, and just recently tried removing my wired connection to get a taste of the wireless abilities.  Unfortunately, I got nothing.  I installed this over an old redhat that i had become tiresome of, and absolutely LOVE ubuntu so far (such an improvement over RH), but wireless is an essential with my job and i was hoping to get some help from you guys.

I am working with a lenovo t60 with an intel pro/wireless 3945 A/B/G card.  I have a dual boot setup so i can go into XP every now and then, and the wireless works fine in windows.  The wired connection works in ubuntu, and the wireless can see available networks, it just cannot connect to them.  I am attempting to connect to a completely open, non-encrypted wireless-g network.

One side note..when ubuntu fired up, it asked me if i wanted to enable a restricted driver "Atheros Hardware Access Layer"...I enabled that along with the restricted driver for the ATI card and rebooted, still no luck.

Can anyone offer some advice?  Thanks a ton i really appreciate it.

---

### Post by dergringo on 2007-05-04
Hi

Would you please open a terminal and enter "iwconfig"? Then copy-paste the output here.


Regards

Philipp

---

### Post by patrickk on 2007-05-04
patrick@patrick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:73508  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.


i cant get it to do this without formatting, but the obvious reason isnt in the nasty part...i have no wireless extensions?

arg...can anyone help me?

---

### Post by dergringo on 2007-05-04
Well, this doesn't look too bad ;)

So what's the problem?
If you don't know how to connect to a wireless lan then try to click on the small monitors icon at the gnome panel.


Philipp

---

### Post by patrickk on 2007-05-04
Well, I dont claim to be a linux expert at all...but when i ran iwconfig up above, i was connected via a wired connection...why is information about a wired connection coming through ath0?

So i tried to connect to the wireless network i was talking about above, and i ran iwconfig again and got this:

patrick@patrick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"WFUguest"  Nickname:""
          Mode:Managed  Frequency:5.28 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-67 dBm  Noise level=-98 dBm
          Rx invalid nwid:322  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.


so now its showing a wireless connection to WFUguest, which is the network im attempting to connect to, as being connecting with  a bit rate and all...yet I can't actually use it.

any ideas?

---

### Post by patrickk on 2007-05-04
anyone??

---

