---
title: "Belkin F5D7050 won't work!"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-20
Hey guys, need a bit of help here.

Pretty new to Ubuntu, still don't understand all these commands, which is why most guides I use for this problem don't help much.

I used to use Belkin F5D7050 on Windows XP, then installed Ubuntu 6.10 to my computer as a dual boot, but on a single HD. The Belkin stick is installed and works fine on Windows, how can I get it to work on Ubuntu. Have had absolutely no progress so still at beginning. When I plug it in it doesn't respond. Would like, if possible, a step by step guide (or link to one) on getting this installed and running on Edgy, (I have the installation disc, it says the setup files can't be opened), and although I can type in the commands on Terminal, just giving me a list of what to type doesn't help as I am relatively new. A "walkthrough" would be handy.

Many Thanks,

Cams

---

### Post by ikg74 on 2007-03-20
I have the same Belkin wireless usb adapter and it works well with ubuntu 

Go to System > Administration > Networking

and a menu will open that will allow you to configure your wireless adapter

First of all you need to go to the DNS tab to add the DNS server address and then return to the Connections tab to setup the wireless connection that will be listed. Select Properties and enter your wireless and connection settings accordingly and when you're finished the device should be working properly for you and you'll see it listed as active.

---

### Post by NICU on 2007-03-20
Hi Camz,

I don't have this same adapter so I can't help with all the specific details, but you can find guides - [here]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver")

There are a few other threads on this subject and - [this one]("http://ubuntuforums.org/showthread.php?t=252465") - seems to be pretty helpful.  

Your first steps will be to determine which version of the Belkin F5D7050 you have, the 3000, 4000 or another version.  That determines which hardware chipset is used, and from there you can determine which driver you need.  Most wifi USB adapters I've seen have the version printed on the device itself.

---

### Post by camz on 2007-03-20
Also there is once problem, I can't connect to the internet from the computer with ubuntu. im using a different computer so i need a new method that doesnt involve connecting at all. i have the drivers for the adapter tht work with windows. could someone tell me what the "ndiswrapper" method does and how to do it. or just a way to get it working! please!

---

### Post by camz on 2007-03-20
Terminal says that "ndiswrapper" is not a valid command. Please help.

---

