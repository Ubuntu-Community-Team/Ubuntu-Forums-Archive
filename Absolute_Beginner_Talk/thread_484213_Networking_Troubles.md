---
title: "Networking Troubles"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by kshane on 2007-06-25
Networking has not been a problem since switching over to Ubuntu.  This morning, however, my wife couldn't hit the net using her Windows (uugh!). Dual boot sys (Ubuntu/Vista).  Tech Support got it going, but when I logged onto Ubuntu, I had no internet.  While waiting I played around and think I screwed up my network settings some how.  Network Tools no longer shows my IP addy.  It shows IPv6, but not the normal one.  Nor does it show the physical address, just 0's..

Is there any way to reset the networking settings to the default settings?

Thanks in advance...

Kevin

---

### Post by daimaru on 2007-06-25
what does ifconfig give u in terminal?
whats your router address?

sorry cant say more without more info

---

### Post by gigaferz on 2007-06-27
at work, i noticed that after using xp, and then later booting to ubuntu  i have to enable and reconfigure eth0 again..

Then I go back to windows, i have to reenable the lan connection.

since we have to have a very specific media speed i have to use mii-tool to set the speed to 10mbs the I do a /etc/init.d/networking restart

and brings back the internet.

In the graphic mode after i enable the eth0 and change the speed I have to ctrl+alt+backspace,to restart the services.

I hope it could be of any use to you.

---

### Post by kshane on 2007-07-06
Thanks for the assist!

Kevin

---

