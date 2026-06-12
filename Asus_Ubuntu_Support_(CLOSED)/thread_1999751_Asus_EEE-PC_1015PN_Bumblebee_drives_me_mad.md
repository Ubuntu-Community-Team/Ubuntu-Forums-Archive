---
title: "Asus EEE-PC 1015PN Bumblebee drives me mad"
date: 2012-06-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by gumbomumbo on 2012-06-08
Hey guys,

I have an Asus EEE-PC 1015PN with ubuntu here and for some reason, bumblebee just won't work, it's driving me mad.

Every single time after installing it, and trying to run something with optirun, I get:

[ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[Error]Could not connect to bumblebee daemon - is it running?


lspci | grep VGA
only gives me

03:00.0 VGA compatible controller: nVidia Corporation Device 0a6f (rev a2)


So my Intel-graphics aren't even recognized. When I restart, everything still runs on my nvidia card. Everything works when using Windows though, so there is no hardware error.

---

