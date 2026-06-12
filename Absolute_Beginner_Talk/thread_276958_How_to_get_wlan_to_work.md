---
title: "How to get wlan to work?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by 25an on 2006-10-13
Hi!

This is my first time using wlan with linux and i have no idea were to begin.
Do you have any advice?
As it is right now I cant get it to work.
I cant find the encryption settings in windows I have 
the encryption set to WPA-PSK(AES), how do i change this in ubuntu?
In the wireless settings there is only Key type?

Thanks for your help

---

### Post by 25an on 2006-10-15
ok I have managed to install knetwarmanager and managed to locate my wlan but i cant connect to it?
I think it has something to do with the encryption of the key but I am not sure.
Dose anyone have any ideas?

---

### Post by sleestak240 on 2006-10-15
If your access point is set to shared key you may have to set the authmode to 2.  Maybe try this in the terminal and see what happens:

sudo ifconfig wlan0 authmode 2
sudo iwconfig wlan0 essid "whatevetyoursis" enc "yourkey"
sudo dhclient wlan0

Don't include the quotes and set the interface (wlan0 in this case) to whatever yours is and report back.

---

### Post by ojasvi rajpal on 2006-10-15
Hi I am a newbee too.
Can u please be more specific what is the error message it throws or it just doesn't connects .I hope you r able to detect all the avialable networks. Wlan just worked just fine for me it automatically detcted and connected to wlan my key type is set to hexadecimel .Try using the same  May be that should help:-k

---

### Post by sleestak240 on 2006-10-15
I didn't even notice that you were using WPA so disregard my previous post...maybe you could try Wi-Fi Radar and see how it works out for you.  Should be available in Synaptic and will be installed in Applications > Internet.  There does appear to be some WPA settings in it, although I don't have any experience with them.

---

