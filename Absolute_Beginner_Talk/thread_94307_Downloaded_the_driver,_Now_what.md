---
title: "Downloaded the driver, Now what???"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2005-11-23
hello guys, last week  I installed Ubuntu in my Laptop, so i'm really new.
i went to the drivers manufacturers website which has a number of drivers for ubuntu i386 which is the one i have, and  downloaded one of the many they had, (not really konwing if it is the correct one, i guess i'll try all of them until it works)
they all come with a .deb extention, my question si simple...
what do i do now??:confused:  how do i install the driver?:confused: 

I will apreciate a detailed intruction guide so that i can fallow....
thanks in advance:rolleyes:

---

### Post by tokyovigilante on 2005-11-23
In a terminal:

```
sudo dpkg -i <packagename>.deb
```

Best not to install drivers that your system doesn't have hardware for though, at best it'll bog your system down searching for nonexistent hardware, at worst you may experience instability and crashes.

You can find out what hardware you have using the commands

> lspci
lsusb 

for PCI and USB devices respectively. 

Is there any specific hardware you're struggling with?

---

### Post by poloman2 on 2005-11-23
Thank you, 
I Typed the command in the terminal, and it ran normally...
Then what I did was:
1) System>Network Settings
2) selected modem Connection and clicked on properties
3) Then i went to the MODEM tab and clicked on "Autodetect"

It took a few seconds and in the Modem port box apperared: /dev/modem

Does this mean that the modem was installed succesfully??
how do I perform anything like "Query Modem".??

if this this the modem was correctly installed then how do i dial the to connect to my ISP??

thanx....

---

### Post by tokyovigilante on 2005-11-23
Enable the universe and multiverse repositories in Synaptic, then install the gnome-ppp package. This will enable you to dial your ISP and connect, as well as probe the modem with AT commands.

---

### Post by towsonu2003 on 2005-11-24
another quicky way:

sudo wvdialconf /etc/wvdial.conf

if it finds your modem, you are ready to go :) this command will not dial though (you'll need to configure it first). 

man wvdial - for some more info. I use dial up and it's my favorite dialer (though not very sexy)... I'm guessing you want a more sexy one :p

---

