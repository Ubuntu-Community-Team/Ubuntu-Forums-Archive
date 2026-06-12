---
title: "Enterprise wireless flakey, latest broadcom driver seems to fix."
date: 2011-10-06
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2011-10-06
I have been battling wireless disconnects on our campus enterprise WPA2 network ever since putting ubuntu on my 5,2 MPB.  The laptop has a BCM432b chipset.

As far as I can tell the problem was that the client could not decide which access point to roam to, would get confused bouncing from ap to ap and finally just drop the connection.  I tried every community driver, ndiswrapper, wicd, etc but nothing helped.

For the longest time I just used wired network while on campus, but my job demands that sometimes I work in a location where wireless is my only option. As a last ditch effort I found the broadcom release of the wl driver 5.100.82.38 which I downloaded and compiled.

Happily this has solved my issues. The client still roams a lot from AP to AP, even if the laptop is stationary, but it doesn't seem to get so out of whack that the connection drops altogether.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

so for those of you with problems on your enterprise wireless, you might want to give this a shot.

-J

---

