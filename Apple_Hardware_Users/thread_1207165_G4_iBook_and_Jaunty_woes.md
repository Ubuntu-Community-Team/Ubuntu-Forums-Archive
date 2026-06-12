---
title: "G4 iBook and Jaunty woes"
date: 2009-07-07
forum: Apple Hardware Users
---

### Post by doulos05 on 2009-07-07
Ok, my wife and I are tired of putting up with our mac, we're gonna put Ubuntu on it. However, I need to know I can get wireless working on this laptop before I can proceed with the install (no wireless is a deal breaker, this laptop normally sits about as far from our router as is physically possible in our house). Here are the details:

iBook G4 w/ 12.1" screen
1.33 GHz
Broadcom 43xx (can't remember what the X's are and I'm unable to find it in my Mac ATM)
512 MB RAM
40 GB HDD

Network: Belkin 54g wireless w/ WPA and TSIK + AES encryption

When I boot to the live CD, running sudo lshw -C network tells me that it is disabled. I opened the Hardware Devices program and clicked the "Activate" button. It says it's activated, but lshw disagrees. At any rate, the Network Manager fails to detect my wireless network, and unfortunately none of my neighbors have wireless networks so I do not know if if I can detect non-secured wireless networks.

I tried manually entering the data into Network Manager and managed to crash it. On a related note, how do I restart Network Manager after it crashes and how do I right click with this touchpad? 

I am loathe to unsecure my network, as every time I do that, they bring my network to a halt (cheap cable internet isn't built to support 10 computers on the internet at once). I have a friend who (I believe) has an unsecured network, but before I try this there, I wanted to see if there was a simple solution (or even a complex solution) before I try an unsecured network.

---

### Post by doulos05 on 2009-07-09
Ok, I'm going to switch my wireless to WEP today at lunch and see if I can detect that. Can anybody tell me if I can do the firmware thing from the Live CD?

---

### Post by doulos05 on 2009-07-14
Just an update, in case someone else is encountering the same problem and fails to correctly read the FAQ page (like I did :oops:).
 
You cannot test the wireless card using the live CD because using the B43-fwcutter requires a restart. That is (pretty clearly, now that I look at it) stated on the FAQ page they link to in the sticky, but just in case there's confusion, there it is.
 
However, the B43-fwcutter worked great, and my wireless is up and running.

---

### Post by caalamus on 2009-07-16
I have a 500mhz 53 iBook.


I right click by pressing the eject button on my keyboard.


(strange huh?)


:]

---

### Post by DJKnut on 2009-07-18
What is the url for the FAQ page???  I'm just now trying to set up my mini G4, and can't get the wireless to work...  Dave

---

### Post by doulos05 on 2009-07-20
> **DJKnut said:**
> What is the url for the FAQ page??? I'm just now trying to set up my mini G4, and can't get the wireless to work... Dave
 There's a link to it in one of the 3 stickied threads on this forum. Note though, you can't test this from the live CD, you'll have to do the install before you test your wireless.

---

