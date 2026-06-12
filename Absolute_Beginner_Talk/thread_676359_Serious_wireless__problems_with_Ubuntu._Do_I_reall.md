---
title: "Serious wireless  problems with Ubuntu. Do I really have to switch back to Windows?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by grainbarcelona on 2008-01-23
HI all, I'm having really problems to get a functioning wireless internet connection established with Ubuntu. Please give me a helping hand, I am pretty desperate after many weeks of trying. 

My problem?:
-- Each time at startup ,  I have to connect-reconnect at least 3 times with the 'manual network configuration', to get some internet connection going.
-- and even then, if and when I get in, iit is about as 3 times as slow Windows (I am on dual boot)

Can anyone help me?

My ISPCI specs:
 lspci -nn | grep Network
02:01.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=rt2500pci
driver=e100

Thanks for anyone who can help me out!

---

### Post by deltaprime on 2008-01-23
So i have two ideas that may help you.
1) try wireless assistant it is a program for fast and easy conection to a wireless ap.
2)try to manualy connect to your ap.

enter set up for your card
----------------------------
~# iwconfig [devicename ie eth1 or wlan0....] up
~# iwlist [devicename ie eth1 or wlan0....] scan
~# iwconfig [devicename ie eth1 or wlan0....] essid [type essid name of the ap you want to connect to here]
~# iwconfig 
----------------------------

the last command is for you to check if you are associated with the ap that you wanted to connect to


good luck keep me updated on your progress


DelTa

---

