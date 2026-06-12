---
title: "ipw2200 radio off Gutsy"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2008-01-27
I just did a fresh install of Gutsy, previously in Feisty my ipw2200 worked perfectly fine.

It seems like for some unknown reason the radio is off, and I can't turn it on.

$ dmesg | grep ipw
[  119.403636] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[  119.403640] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  119.403769] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  121.004359] ipw2200: Radio Frequency Kill Switch is On:
[  121.004469] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.

---

### Post by DSn0wMan on 2008-01-27
problem fixed. I had to go into the bios and set it to let an application turn it on and off rather then the fn+f2 key.

I wonder why this was not the case in feisty, or edgy, or dapper, or hory?

---

### Post by njborn on 2008-02-06
I've been trying to setup my wireless for the past few days, and finally stumbled across this post which actually worked! Thanks for the help

---

