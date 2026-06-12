---
title: "Wifi problems on a mac book pro"
date: 2016-02-05
forum: Apple Hardware Users
---

### Post by Nathan_Adamson on 2016-02-05
Hello,

I have recently installed Ubuntu 14.04 on my MacBook Pro 11 and I have managed to install firmware-b43-installer and get my wifi adapter to work and I can connect to networks but i cant seem to put the wifi adapter into monitor mode my output is below.

```

root@ubuntu:~# ifconfig wlan0 down
root@ubuntu:~# iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
root@ubuntu:~# ifconfig wlan0 up
root@ubuntu:~# 

```

My wireless card is below
```
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
```

Any help will be appreciated

---

### Post by este.el.paz on 2016-02-05
Nathan:

Did you use "additional drivers" to install the broadcom wifi driver??

e...

---

### Post by Nathan_Adamson on 2016-02-05
Hello,

After installing the 'firmware-b43-installer' package I then ran 'modprobe wl' and I was then able to connect to wireless networks but unable to put the wifi card into monitor mode.

Thanks

---

### Post by este.el.paz on 2016-02-05
> **Nathan_Adamson said:**
> Hello,

After installing the 'firmware-b43-installer' package I then ran 'modprobe wl' and I was then able to connect to wireless networks but unable to put the wifi card into monitor mode.

Thanks

"Monitor mode" . . . so I'm assuming that means to "use" the wifi to connect and/or stay connected??  So, perhaps it shouldn't matter if you use the console to install "b43" rather than additional drivers . . . but, another GUI step, if the wifi applet/network manager applet is showing in the toolbar upper right (I'm in my Xubuntu 14 system as I speak) . . . clicking on that applet should show drop down menu . . . .  Is "enable networking" and "enable wifi" . . . checked, to be "enabled"???

e...

---

### Post by darren32 on 2016-02-06
I think he means he wants to put it in monitor mode to use aircrack-ng ect. i.e (iwconfig wlan0 mode monitor)

---

### Post by este.el.paz on 2016-02-06
> **darren32 said:**
> I think he means he wants to put it in monitor mode to use aircrack-ng ect. i.e (iwconfig wlan0 mode monitor)

Ah, well knowing about that is beyond my paygrade . . . but the code provided in the first post may be illuminating . . . possibly "operation not supported" means just that; or it could be that something has to be added to provide that function . . . .  Searching Google for posts about "monitor mode" might be the fastest way to get the general idea of if it is possible . . . .

e.e.p.

---

### Post by Nathan_Adamson on 2016-02-06
I have done a lot of google searching and nothing that has really helped me, posting on the Ubuntu forum was my last option.

---

### Post by este.el.paz on 2016-02-06
> **Nathan_Adamson said:**
> I have done a lot of google searching and nothing that has really helped me, posting on the Ubuntu forum was my last option.

@Nathan:

Well, if literally nothing shows up in Google, that might be your answer . . . Google should show you the "universe" of answers and the forum related posts would possibly target those many answers into those appropriate for ubuntu related systems . . . .  But, there are **many** linux forums out there, also have you tried posting on Launchpad "Answers"???  Launchpad is where the bug reports are made but they also have a sub-forum providing (drumroll plz) . . . "answers" . . . .  Keep shopping your question around, eventually you will get someone who will tell you whether it is something you can do or not . . . .

Possibly removing any reference to the make of the computer and posting your question on the main forum as "How to get monitor mode via wifi?" may bring more and more accurate "answers" . . . ????  But, you didn't hear that from me . . . k?

e...

---

