---
title: "ahha!! may have found a solution to offline package installation"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by jbs2212 on 2007-12-02
I believe i have found a solution with my problem of connecting my blackjack and tethering the internet connection in ubuntu
aside from typing in these commands:
hcitool scan
pand c- "cell phone mac address here" -d NAP
(after this my cell phone reads connected for a half second then disconnects! arrrrgh!)
then : dhclient bnep0
after typing that command it tells me "Permission denied"

i read that i might have to download additional bluetooth packages that didn't come with the live installation cd before it will work but of course i can only get on the internet through xp right now and not through ubuntu
here is the website that might offer a solution for me:
any feed back or sugestions?! please let me know if im on the right track!
[http://nonetdebs.homeip.net]("http://nonetdebs.homeip.net")

---

### Post by m0biu5 on 2007-12-04
> then : dhclient bnep0
after typing that command it tells me "Permission denied"

You should probably run dhclient as a privelaged user, ie:
```
sudo dhclient bnep0
```

---

