---
title: "Getting wireless internet on MacBook Pro 6,2"
date: 2010-11-18
forum: Apple Hardware Users
---

### Post by Ekirä on 2010-11-18
I just installed Ubuntu 10.04 alongside Mac OS X 10.6.3 and I'm unable to get internet in Ubuntu, it doesn't recognize my connection at all. 

When I go to System->Administration->Hardware Drivers it's unable to find any drivers. 

Help? Is my Pro just too new to run Ubuntu?

---

### Post by lael on 2010-11-18
Checkout [https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)
> IconsPage/restricted.png The Broadcom driver was not installed by default on Lucid. You'll need the STA one, goto "System->Administration->Hardware Drivers" and enable it. If you prefer the command line, execute on the Terminal:

sudo apt-get install bcmwl-kernel-source

Then reboot the system and you're OK. The driver seems to handle all situations fine - disable power management in case you experience unexpected connection loss (doesn't seem to be necessary although):

sudo iwconfig eth1 power off

Also checkout the page for 10.10

[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)

---

### Post by Ekirä on 2010-11-18
> **lael said:**
> Checkout [https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)


Also checkout the page for 10.10

[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)

Yes, I did try both the command in Terminal and trying to find drivers but it couldn't find any. Maybe I'll just install 10.10 as from the page you linked to it seems like the wireless works better.

---

