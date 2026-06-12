---
title: "Ubuntu doesn't detect my wireless card"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by tseo on 2007-07-16
When I go to Administration/Network I see only Wired and Modem.
I just bought this laptop and I really don't know what to do.
How can I understand what is my card and how can I install it?

---

### Post by tseo on 2007-07-16
RTL-8185 IEEE 802.11a/b/g Wireless
So this is the card...

---

### Post by theDaveTheRave on 2007-07-16
tseo.

I've sent a post on another thread [here]("http://http://ubuntuforums.org/showthread.php?p=3030481#post3030481") have a look and follow the details for doing a <sudo lshw>

also do an  <iwconfig>, which should give a report similar to that below.


> 
davemyers@Aramis:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Mousquetaires"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:15:5D:43   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/94  Signal level=-37 dBm  Noise level=-91 dBm
          Rx invalid nwid:4731  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

davemyers@Aramis:~$ 


As always what are the details of the system you are using??

put this in as a search term on the forums, to see what it throws up?

I've only just got my DVD playback to work again.... due to using desktop effect breaking it!

you may find that you need to have the laptop hardwired into the net to get any updates, and these may solve the problem, they did with my atheros chip, and it suddenly just started working!

One word of warning, try not to play with the button that turns the wireless on and off in Windows, you can make it work in Linux, but I have had problems with mine and it has often prevented any connections at all if I have inadvertently pressed it -  don't ask me why though!

Good luck

Dave

---

### Post by theDaveTheRave on 2007-07-16
A quick search threw up this [thread]("http://http://ubuntuforums.org/showthread.php?t=416993&highlight=RTL-8185") for your wirless card.

The users there report same / similar problems and seem to have worked a solution.

Dave

---

