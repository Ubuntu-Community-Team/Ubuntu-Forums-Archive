---
title: "Wireless Cardbus card trouble"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by harrythehat on 2007-09-25
Hello,
I am running Feisty on a Dell D-500. 

The computer came w/a built in Intel mini-PCI card (Centrino 2200BG).
This card was recognized by Feisty w/no problem. Works fine.

However, I wanted to run Aircrack-ng and Kismet and these are (apparently) not well supported on the Intel card so I ordered a ZyXEL G-102 v3 cardbus wireless card which I have installed. The light indicates that it is powered up.

I then installed the madwifi drivers.

All appeared to go well except that when I run: 

sudo lspci -nn 

The output recognizes the Intel Network controller, Pro/Wireless 2200BG just fine but....

the ZyXEL card is shown as: Network controller ZyDAS Technology Corp. UNKNOWN DEVICE.

Any ideas on how to get Feisty to recognize the ZyXEL card???

Thanks.
Harrythehat

---

