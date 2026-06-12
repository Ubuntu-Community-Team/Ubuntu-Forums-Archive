---
title: "Wireless Firmware Problems"
date: 2011-07-15
forum: Apple Hardware Users
---

### Post by r_joy on 2011-07-15
I'll admit I am unsure how to go about this. I just installed Ubuntu 11.4 over osx and I would like to keep it, but everything I read about installing B43 tells me a different thing and none of it seems to be working. I tried to install package from USB, but nada.

Any pushes in the general direction of wireless will win a linux convert in the making.

---

### Post by rsavage on 2011-07-15
Not sure about USB, but the command to get airport extreme (b43) working on ppc in natty is "sudo apt-get install firmware-b43-installer".  That will download it over an ethernet connection.  The old command that I used to use in lucid ("sudo apt-get install b43-fwcutter") didn't work.

---

