---
title: "MAC Filtering"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by all4als on 2007-05-19
I have searched the forums and believe I haven't found anything, because I don't know what I am looking to obtain. Here is my problem. I have a wireless linksys router that I have MAC enabled, and I cannot find a MAC address on Fiesty Fawn. I am looking at Ethernet Interface (eth0:avahi) and see a Hardware address. I have plugged that address into my MAC Filter table, but I still cannot connect.

I am really sorry that I am slow, but could someone offer a suggestion?

Signed, 
New to UBUNTU

---

### Post by ugm6hr on 2007-05-19
The hardware address is the MAC address.  The confusion may be that eth0 is your wired ethernet, rather than wireless MAC (they are hardware dependent, so each "network connector" is identified independently).  Easiest way to check is to:
right-click Network Manager -> Connection information
This will give the hardware address of the wireless card.

Otherwise, in a terminal:
ifconfig

And scroll through for HWaddr xx-xx-xx-xx-xx-xx (where "x" is a HEX digit)
This will also give the MAC address.  Again - look for the wireless MAC, which is usually wlan0, ath0, or something else other than eth0 (occasionally eth1).

As you have done - just put this into the MAC filtering of the router as "accepted connections" (or whatever), and it should work.  If it doesn't, then the problem is not with MAC filtering, but something else (which is possible).  

NB: If you have connected to the router from this PC before, then it should already be in the MAC accepted list, since the MAC is hardware dependent (i.e. it doesn't change from Windows to Ubuntu).

---

### Post by all4als on 2007-05-19
Thank you so much for the info. I have connected with this pc before. So I guess my next steps are what now? Am I just missing something in the forums that I shouldn't be?

---

### Post by all4als on 2007-05-23
Well because i am a noob, I decided to change my router config, and made it WPA Personal. I can connect to the web without doing anything using a wire. However, i still cannot get my wireless working putting in my passphrase. So off to the forums to do another search. Thank you so much for your help. Forums are awesome repositories for information.

---

### Post by reckless2k2 on 2007-05-23
Well there are 2 ethernet connections that you have: a wired and wireless. It sounds like you put the wired ethernet address in but not the wireless. ditch WPA and go back to MAC filtering only with a broadcasting SSID. Do the ifconfig and view both ethernet interfaces (your wired and wireless). make sure you put both addresses in your MAC filter. after that, reboot your ubuntu laptop and see if you can see your network and then connect to it. It should be that simple. once you've connected to the network then you know you're fine and then cloak the SSID. With the SSID cloak and MAC filtering enabled, you should be fine. 

If you are still unable to connect after the above mentioned steps, post your lspci results from the terminal. you may have a wireless hardware issue that requires a tweak.

---

### Post by all4als on 2007-05-23
Well I actually found a thread that suggested to download drivers for my wcard, and now it is working. However the speed is not as fast as wired, ie wired = 2.6 Mb and wireless 206b. So now I am a little confused. 

Anyway, what are the benefits to the MAC verse WPA? I looked at other forums, and George Ou (sp?) says MAC filtering is worthless. I thought MAC filtering was the way to go, but figured he knew more than I do. Anyway, I am up for suggestions.

---

### Post by reckless2k2 on 2007-05-23
Wired speed will always be faster than wireless. Signal traveling through the air will not be as strong as signal traveling through a confined cable. 

As far as MAC versus WPA. The best security is multi layered security. This would involve using a cloak SSID with a complex string, MAC filtering, and encryption of some sort using WEP or WPA. Using all, none, or a variation of some is up to you.

---

### Post by all4als on 2007-05-24
Thanks for your insight Reckless, I really do appreciate your time spent with me.

---

### Post by reckless2k2 on 2007-05-24
It's not a problem at all. With wireless access points all over the place in neighborhoods anymore, I personally don't see the need for "intense" security. Things like that make it so much more difficult especially when friends and family come over and might want to connect. As little as a cloaked SSID with a name other than the default will do many people fine anymore. This will avoid everyone in the neighborhood with Linksys routers with an open SSID set to the "linksys" default from jumping onto each other's network. Because wireless is so economical anymore, you will rarely catch hackers trying to exploit your network. Everyone has it and if your's is cloaked and the neighbors is open, which do you think they'd rather get on real fast to do anything? hahaha.

---

