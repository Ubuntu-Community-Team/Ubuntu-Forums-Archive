---
title: "WPC11 V4, oft recommended install not working"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-13
I've been collecting web pages on how to install my wifi since I ordered it. So last night I armed myself with all this collective wisdom to install the card. Yeah, well, that ain't working out so well. 

Here are the ugly facts:
Linksys WPC11 v4 with Realtek chipset, machiine sees the card ( I think I used lshw to verify )
I downloaded the P driver off the Realtek site, installed it into  /home/user/wpc11. 

Commands are:
cd /home/bt/wpc11

sudo ndiswrapper -i NET8180.INF

sudo ndiswrapper -l (this then says the driver is loaded, but an invalid driver)

So I read that soometimes you should delete and reinstall. 
So I try sudo ndiswrapper -e net8180.inf
I get net8180.inf is not installed.

hmmm, okay, then I'l just reinstall.
sudo ndiswrapper -i net8180.inf
output advises driver is installed
sudo ndiswrapper -l
yep, you guessed it, invalid driver

Can any of my new large brained friends help get me started down a new rabbit trail, because I rinsed and repeated this process until about 6 hours ago.

---

### Post by bt224 on 2006-05-13
good news, when I took .INF off the -e command, it uninstalled the driver.

I reinstalled and it shows driver and hardware present

More to follow

---

