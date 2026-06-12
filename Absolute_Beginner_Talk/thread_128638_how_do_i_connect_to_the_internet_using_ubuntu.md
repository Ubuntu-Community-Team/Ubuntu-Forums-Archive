---
title: "how do i connect to the internet using ubuntu?"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by mhl12 on 2006-02-11
Hi, I've been playing around with the settings on Ubuntu but I can't seem to connect to the internet. I have a cable broadband connection. Normally it's connected directly through the ethernet on my desktop, but I want it to connect on my laptop (which has ubuntu installed) so I can install updates such as automatix and stuff. Can anyone help me out? Thanks.

---

### Post by alfonz on 2006-02-11
what type of laptop are you using, what type of connection, wireless or hardwired, it would be nice if you mention this it would be easier to help get it fixed.

---

### Post by mhl12 on 2006-02-11
I'm using a Toshiba Satellite M35x-S149

I wan't to directly connet through the ethernet so I guess it would hardwired.

Thanks for your help.

---

### Post by eriefisher on 2006-02-11
Plug it in and boot, it will probably just work. If not, it shouldn't take a whole lot to get it to work. Maybe just activate ethX.

eriefisher

---

### Post by gordong11 on 2006-02-11
I know for me it connected automatically. I just plugged my ethernet cable in, booted up, and it configured my connection for me. I dont know much, but I also know that in the beginning of the install, it configured it. did you have your internet plugged in when installing? that may be the iisue...I'm sure its an easy fix, but I dont know how.

---

### Post by mhl12 on 2006-02-12
no i did not have the cable plugged in when i installed ubuntu. Is that a problem? Is there a way to fix it or should i reinstall ubuntu?

---

### Post by mhl12 on 2006-02-12
ok i tried it again and it still doesnt work. In my network settings, I made sure that my ethernet connection (eth0) was active and under the configuration menu, i chose DHCP since I have cable. It took a while to connect but after it did, I still couldn't get onto any web pages. Any help would be great. thanks.

---

### Post by gordong11 on 2006-02-12
[QUOTE=mhl12]ok i tried it again and it still doesnt work. In my network settings, I made sure that my ethernet connection (eth0) was active and under the configuration menu, i chose DHCP since I have cable. It took a while to connect but after it did, I still couldn't get onto any web pages. Any help would be great. thanks.[/QUOTE]


I have cable too. You really shouldnt have to choose anything, should connect automatically.  Perhaps, your hardware has a built-in Firewall? it should work without issue. When you reinstalled, did your automatic network configuration take place? did it go by fast? both were yes for me. is your host name Ubuntu, or did u change it? maybe that has something, but i doubt it.  Did you right click on your connection, deactivate, then activate again? My settings:

DCHP
Default Gateway: Eth0
Host name: Ubuntu



Try unplugging your modem for a minute. Maybe thats the issue. otherwise I'm afraid I'm just not advanced myself, I'm new too...in fact I"m having issues playing DVD's I have burned in mpeg-2 format.

---

### Post by Peter76 on 2006-02-12
Did you get an ip address? post your output of ifconfig... Also in the dns tab of your networksettings, put in the ip of your modem/router

---

### Post by mhl12 on 2006-02-12
ok i finally got it to work after i called my isp. It turns out that I had to uplug my cable modem from the power outlet and wait for a minute and plug it back in and reboot my computer.

yay.. first post using ubuntu! :) thanks a lot for the help guys.

---

### Post by iraklirost on 2006-02-12
Hi, to all, I have a problem and it will be great if you will help me to solve these problem, I have modem “Conexant 56K AC-Link Modem” in my laptop , I install dial-up modem connetion.

---

### Post by gordong11 on 2006-02-12
[QUOTE=mhl12]ok i finally got it to work after i called my isp. It turns out that I had to uplug my cable modem from the power outlet and wait for a minute and plug it back in and reboot my computer.

yay.. first post using ubuntu! :) thanks a lot for the help guys.[/QUOTE]

Yes, congrats.  That happens to me to, tis why i suggested it. good luck

---

### Post by sniffass on 2006-02-12
i don't really have any idea but try running "sudo ppoeconf" from a terminal. And choosing the recommended settings. It's works with my ethernet modem connection. But maybe I'm barking up the wrong tree.

---

