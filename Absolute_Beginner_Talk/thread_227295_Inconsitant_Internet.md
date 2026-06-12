---
title: "Inconsitant Internet???"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by undertakingyou on 2006-08-01
I am normally a Windows users and am your intermediate to advanced user there, I just installed Ubuntu last night after much frustration with MS and I can not get the internet to work.  I can download and install updates.... sometimes.  And I can get to the ubuntu website, most of the time.  And I can get into my DSL modem to configure it.  I can't seem to figure out how to get it to work.  Wether I use DHCP assignment or configure a static IP.  I can't figure it out.  Is there a firewall someplace that I can't find?  Any guidence would be very helpful

-------------------:!: 
Will Smith

---

### Post by s_h_a_d_o_w_s on 2006-08-01
Plug in you modem as you would you MS machine.

In terminal (weird Bcause dapper automatically connects, if the connection is set up at boot time.)

sudo pppoeconf

That should set you up.

---

### Post by undertakingyou on 2006-08-01
My ISP requires that the modem connect via PPPoA.  Will that kill it??

---

### Post by orb9220 on 2006-08-01
Did you search forums using  PPPoA for a search term?

---

### Post by undertakingyou on 2006-08-01
I haven't seen anything with a PPPoA search string, but I did find some tings about disabling IPv6 and editing certain files.  I don't know though, any help would still be good.

---

### Post by gils0040 on 2006-08-01
hey, this kinda sounds like a dns problem to me. are you by chance using an actiontec router? if so refer to this post [http://ubuntuforums.org/showthread.php?t=226947&highlight=internet+problem](http://ubuntuforums.org/showthread.php?t=226947&highlight=internet+problem)

---

### Post by undertakingyou on 2006-08-01
Holy goodness I am using an actiontec modem, I will have to get in there and try and change that.  Thanks a bunch I'll try it right when I get home.
---------------:rolleyes:
Will Smith--

LATER THAT DAY::::
Got home and sure enough, the wrong DNS.  Windows doesn't have a problem with it but a quick change and its good to go.  Thanks,
WS--

---

