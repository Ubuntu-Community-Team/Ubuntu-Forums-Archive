---
title: "Getting wifi going?"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by Sugoi48 on 2010-11-12
I just installed 10.04 64 bit. How do I get the wifi going?

---

### Post by paulinchen on 2010-11-13
I checked that for you ...

 > The  Broadcom driver was not installed by default on Lucid. You'll need the  STA one, goto "System->Administration->Hardware Drivers" and  enable it. If you prefer the command line, execute on the Terminal: ```
sudo apt-get install bcmwl-kernel-source
``` Then reboot the system and you're OK.[https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

There you can find anything for setting up Ubuntu for your Mac.

---

### Post by Sugoi48 on 2010-11-15
Thank you! :P

---

