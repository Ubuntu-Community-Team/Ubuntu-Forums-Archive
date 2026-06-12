---
title: "WiFi stops working after some time, Ubuntu 18.04.3 LTS on MacBook Pro mid 2012"
date: 2019-10-30
forum: Apple Hardware Users
---

### Post by shevcha on 2019-10-30
[SIZE=3][FONT=arial]Hello,

I've finally decided to give Linux a try and installed Ubuntu 18.04.03 on my MacBook Pro, mid 2012 (dual-boot). So far I like it a lot apart from the fact that  I cannot get the Wifi to work properly. When I start Ubuntu it functions well for some time (usually for max 20 min) and then it stops. If I turn on and off the Wifi, it works again for several minutes and then it stops again. And so on.  My wireless card is **Broadcom [14e4:4331] (rev 02)**. It works without a problem under MacOS. 
So far I've tried what not:
- using the Broadcom driver supplied through *Software & Updates, Additional Drivers* tab
- everything suggested in this thread: [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
- disabling qos and hardware encryption in b43 module[/FONT][/SIZE] ([SIZE=3][COLOR=#000000][FONT=arial]echo "options b43 qos=0 nohwcrypt=1" | sudo tee /etc/modprobe.d/wireless.conf[/FONT][/COLOR][/SIZE])
- [SIZE=3]turning off Wifi power management
- setting "regdomain" in /etc/default/crda to my country code (BE)

I've already spent a few days trying to solve this problem, alas, to no avail. 
Currently I've gone back to using the driver supplied with Ubuntu ([SIZE=3][FONT=arial]Broadcom driver supplied through *Software & Updates, Additional Drivers* tab[/FONT][/SIZE]).
Any help or advice would be much appreciated.
[/SIZE]

---

### Post by wildmanne39 on 2019-10-30
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by wildmanne39 on 2019-10-30
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by Skaperen on 2019-10-30
does it stop even if you are busy using it or has it been idle for some time?  i do know that Windows is frequently communicating with Microsoft which could make the wifi look busy enough to stay running.  maybe Mac OSX does something like that, too (though if it does, i'm sure it would be communicating with Apple),  Ubuntu doesn't do that.  i had a like issue and set up a background ping to my own remote server.  that fixed my issue and now it stays up for days (i reboot before and after i upgrade so it's never up for more than a couple weeks).  or you could have one of those other listed issues.  but i would suggest trying a continuous light (once every 20 seconds) ping in a minimized terminal window and see if that changes things.  in my case i think it is an issue with how the AP i use is configured.

---

### Post by shevcha on 2019-10-30
Hi, Wildmanne, Here's the result I got after running the script: [https://pastebin.com/ity0gqwd](https://pastebin.com/ity0gqwd)

Hi, Skaperen, thanks for your reply. Yes, the Wifi stops even when I'm busy using it for some time - for example, I could open a few pages one after the other, and the first two might open and then the others not. Or it could stop in the middle of a Youtube video.
I am willing to try your suggestion with the ping but I'm quite new to this and I have no idea how to do it. Do I need to have my own server for this? Could you point me to some tutorial how to do it?

---

### Post by wildmanne39 on 2019-10-30
From your first post it looks like you have tried the b43 driver is that correct? It is the best driver for your card, I recommend re-installing it by doing:
```
sudo apt remove bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```

Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router. In your case the file says you have this many networks on the following channels:
```
3   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.28 GHz (Channel 56)
      2   APs on   Frequency:5.5 GHz (Channel 100)
```
So maybe you want to set your channel to 5 or 7, I imagine your connection is roaming from one network to the next causing you to get disconnected.

I would undo the following parameter:
>  - disabling qos and hardware encryption in b43 module (echo "options b43 qos=0 nohwcrypt=1" | sudo tee /etc/modprobe.d/wireless.conf)

Are you sure your country code it correct? the file says you are in Europe/Paris.

After you make these changes reboot the computer as well as the router and let us know if it helps.

---

### Post by shevcha on 2019-11-02
Hi Wildmanne,

Thanks a lot for you help. I tried everything you suggested, i.e. I  installed again the b43 driver and tried the different Wifi channels  suggested (1, 6, 11, 5 and 7). I could not change to WPA2-AES because my  router does not have this option, so I set it to WPA2-PSK. I also undid  the hardware encryption parameter. Regarding the country code, I'm in  Belgium, that's why I set it to BE. Don't know why it says Paris, I  think that when I was installing Ubuntu I might have chosen Paris for  the time zone, as it is the same for Belgium. 
 Unfortunately the problem still persists. However, while I was  tinkering with the Wifi settings in my router I noticed that my ISP  offers also Wifi in the 5G band with a different SSID. I've tried it and  so far, for two days and a half, it has been working without a problem.  I think I'll settle with that for the moment. At least I can use it at  home. If I have problems using Wifi while travelling, I guess I'll have  to use the MacOS installed on the same computer.
Thanks again for your help.

---

