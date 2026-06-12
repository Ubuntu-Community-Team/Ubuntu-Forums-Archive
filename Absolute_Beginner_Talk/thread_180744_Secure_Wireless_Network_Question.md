---
title: "Secure Wireless Network Question"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Chas on 2006-05-22
I am new but steadily learning. 
I just installed Ubuntu from a CD and did apt-get update and upgrade
on a Sony Vaio Z505RX with an Orinoco Classic Gold.
I also have a desktop with a Belkin wireless hub.
When I make my wireless network secure, 
I can't access it, so I must leave my network
open in order to have internet access.
I went to Network Settings, set the essid and wep key,
but the connection won't enable.
I've tried WEP64, WEP28, WPA, made sure I entered the
correct key in ascii and I don't know what else to do.
Can anyone point me to something simple to read?
Thank you.

---

### Post by ProjectGod on 2006-05-22
which release of ubuntu are you using?

can you ping the router device. 

is it dhcp configured or static ips?

does firefox time out?

are the wifi adapters flashing as though signals are being sent received?

---

### Post by Chas on 2006-05-22
Thanks for the questions.
I installed Breezy 5.10 and I updated it. 
If this is the IP to ping -- 192.168.1.1 -- I get no packets received.
The round Firefox icon just twirls and the page doesn't load.
One Orinoco light is on all the time,
the other blinks once when I call the page. 
I always use DHCP because I don't know what to do with Static IP.
I don't know if this iwconfig output helps you.
The first is with an open network,
the second is when I close it with WEP128 

eth1   IEEE 802.11-DS  ESSID:"DiBella"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:D4:A3:74
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/92  Signal level=-66 dBm  Noise level=-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

eth1   IEEE 802.11-DS  ESSID:"DiBella"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=107/153  Noise level=157/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

---

### Post by Chas on 2006-05-22
192.168.2.3
actually this might be the correct IP
and yes, it does ping.

---

### Post by ProjectGod on 2006-05-22
Chas, 

please check this tread regularly... people will surely help out. as for me i'm out! for the day! ;)

---

### Post by Chas on 2006-05-23
Logically, it seems I am doing everything right.  My connection is fine with an open network but when I secure it with a passphrase I can't get through.  I have reached a dead end with all my efforts.  I really do not want to leave my network open.  Any help would be appreciated.

---

### Post by DSn0wMan on 2006-05-23
For a temporary workaround you can just lock down your network by MAC address, until you get WEP or WPA figured out.

---

### Post by Chas on 2006-06-26
It turns out the Key type MUST be entered in Hexidecimal.  
Plain text ascii will not work.  I wonder why?

I have another strange problem related to gmail, but the problem only appears on this Ubuntu system.  While composing a letter in gmail, the cursor slows way down so that it takes 15 seconds for a sentence to type itself out.  I type a sentence, and need to wait until it types itself out.  This only happens in gmail, making it worthless to me.  Should I abandon gmail?  Is it not compatible with my system?  I have found gmail useful many ways.  Are there alternatives?  I am using Firefox.

Here is another issue I have been fighting with.  When the system boots up, it hangs on "installing hotplug subsystem" ... i figured out that a Cont-C in the first 5 seconds skips over the problem, but how do you really fix the problem?  I imagine there is a simple file to edit with sudo, but web research did not reveal a fix for me.

I am using Breezy - upgraded to Dapper but it won't not give me a GUI (on this Sony Vaio Z505RX 400mhz w/192 Mb).  After no luck with interent research, I reformated and reinstalled Breezy.  Got all the updates now here I am again.  Going round in circles.  Our LUG meets only once a month, and very little time to get much done.  No one else local to help.  I persist ....

---

### Post by DSn0wMan on 2006-06-27
1) Gmail slow typing thingy - the only time this happened to me, was when there was a keylogger on my comp.

2) Hotplug - cant help you on this one

3) GUI after upgrade dist. - You probably need to reconfigure xserver. I had the same problem. I think the command you type at the prompt is:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Chas on 2006-06-27
I suspect the keystoke lag issue is related to gmail rather than Ubuntu or Firefox, although I am tempted to try another browser.  For example, when I type this message in the Ubuntu forums text box, everything moves along fine.  The keystroke lag only happens with gmail, which employs some sort of script which saves the message as a draft as I write it.  Wish I could solve that issue ... and would like to hear if anyone else has experienced this.

Anyway, concerning upgrading to Dapper, I believe as I was troubleshooting I tried that dpkg command, but I may have had a space after dpkg and -reconfigure.  I gave up after a while and reinstalled Badger with a fresh format.  At the LUG meeting, one user kind of suggested it would be best to wait a while to upgrade to Dapper and let some of the more obvious bugs get worked out.  Seemed to make sense to me.  Is this true?  

Concerning the "hotplug subsystem" hangup issue, I thought that would be the easiest to solve.  I'll keep coming back to see if anyone has any ideas ...

Thanks for being there.  Don't know where else I would turn ...
Chas.

---

### Post by nalmeth on 2006-06-27
I've never seen that behavior in Ubuntu, and I use gmail alot. 
Sorry, I don't have a solution for you, just thought I'd let you know.

---

### Post by Chas on 2006-06-28
I believe this is gmail keystroke lag issue is somehow Ubuntu related.  I have no extensions loaded in Firefox besides English and am using the default theme.  When the keystrokes start to slow down, I can reboot Ubuntu, go back to gmail, and the keystroke speed returns to normal, but not for long.  I am not using any other programs but Firefox.  Could it be that this is a memory management issue, and if so, how can I free up more memory without rebooting each time the problem appears?

---

### Post by Apple 101 on 2006-06-28
I'm not sure, but with regards to your wireless LAN issue, have you tried using the WPA Gui (package name: wpa_gui)?  It is a GUI (obvious :) ) for configuring wpa_supplicant, and even detects your wireless LAN.

---

### Post by Chas on 2006-06-28
> have you tried using the WPA Gui
> (package name: wpa_gui)?

No.  I will take a look at it.  Thanks.

The "Starting Hotplug Subsystem" hangup is a problem I'd like to solve if anyone has any ideas how to diagnose this problem I would be glad to know.  Concerning, the gmail compose keystoke lag, the only solution is a reboot, which is certainly no solution, especially when I need to do it several times a day, and each time wait cautiously for the "Starting Hotplug Subsystem" and then hit Control-C ... 

I have a 400mhz Sony Vaio Z505RX
Mem:    191964k total,   186136k used,     5828k free,     8352k buffers
Swap:   361420k total,    30824k used,   330596k free,    47652k cached

I guess it is time to change the title of this thread.
Thanks again.

---

### Post by John.Gallogly on 2007-12-11
I get the same problem with ubuntu. I have verified that it is not due to system resources. And I wrote two emails where it lagged, wrote another and it no longer lagged. Sounds to me like it is an autodraft issue as well, as mentioned earlier.

---

