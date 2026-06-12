---
title: "Wireless not showing up?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Kzav on 2007-08-19
Hello,

i've just installed Ubuntu in dual boot on my laptop, but i cannot connect to the internet. My network connection doesn't find my wireless network, and i can't find any application/installer/whatever to find my network. I don't know how to configure it. Is there anything in the system that finds all the networks in range? I guess so, but then my wireless card is not working now. that might be the problem. :confused:

How can i get connected? I have Toshiba laptop, using an Intel PRO/Wireless 2200BG Network Connection card.

I am totally new at Linux/Ubuntu, so bear with me. I hope you guys can help me find what the problem is.

thanks in advance

---

### Post by Happy_Man on 2007-08-19
Try here: [http://www.student.dtu.dk/~s971652/ipw2200.shtml](http://www.student.dtu.dk/~s971652/ipw2200.shtml)

---

### Post by Kzav on 2007-08-19
ok thanks, this helps, but i do not have an acer laptop, but a toshiba one, it probably makes a difference, right?

how do i get that corret file then?


EDIT: from what i can understand, i need to download a driver for it to work , right? If i download [Intel Pro/Wireless 2200BG]("Intel Pro/Wireless 2200BG"), can it work or is there something more required?

---

### Post by HermanAB on 2007-08-19
The 2200 software is for the little Arm processor inside the WiFi adaptor, not for your laptop.  What your laptop has to do, is download it at the opportune time to the WiFi device.

'Hope that explains it a bit.

Cheers,

Herman

---

### Post by Aishiko on 2007-08-19
> **Kzav said:**
> ok thanks, this helps, but i do not have an acer laptop, but a toshiba one, it probably makes a difference, right?

how do i get that corret file then?


EDIT: from what i can understand, i need to download a driver for it to work , right? If i download [Intel Pro/Wireless 2200BG]("Intel Pro/Wireless 2200BG"), can it work or is there something more required?
well, no it doesn't matter, I could have that same wireless adapter in any laptop or computer the thing is you need the drivers for it the OS just goes OK this driver belongs to this device in this case the wireless adapter.

Hope that helps.

---

### Post by Kzav on 2007-08-20
ok, i still cannot connect, that whole tutorial doesn't really work with me, i don't know why. I downloaded a file acerhk-0.5.34.tgz and tried those commands in the terminal, but it doesn't work, i get alot of faults back, that the dir's don't work and that the files aren't found.

any other ideas?

---

### Post by Aishiko on 2007-08-20
share the error messages the more technincal ones  here would be able to help you better that way.

---

### Post by Kzav on 2007-08-21
this is what i get; im connected through a wire now, sitting next to my modem:


$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i guess that my wireless card is not recognised...

---

### Post by mistergq on 2007-08-21
I have an almost one year old Gateway laptop.  I had to follow these instructions to get my wireless card to work:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

