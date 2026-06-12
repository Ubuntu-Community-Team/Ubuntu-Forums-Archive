---
title: "Desktop effects work only on Ubuntu 7.04 live cd...?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Grizzil on 2007-05-29
I am a new Linux user. When I try the Ubuntu 7.04  live cd the desktop effect work.
but after the installation I can't enable the desktop effects I get this error message
"Desktop effect could not be enable"
My Graphics card is a  Diamond S80 ATI Radeon 9200 SE
I try to get help from google but with no success...
any suggestion would be appreciate.

---

### Post by daimaru on 2007-05-30
b4 u follow numerous guides. i can only say that i never got desktop effects or beryl to work properly on a 9200SE card. anything above that works like a charm but somehow not that one. sry but if u want to try go here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
it says there that apprently the driver supports 9200 and below but i followed that guide and it didnt work for me . good luck

oh yeah just read in a few threads that the script envy or something @ [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) is suposed to install drivers automatically you could try that but as posted somewhere else then you have to reinstall your drivers everytime you upgrade your kernel.
best way is to get a cheap nvidia graphics card.

---

### Post by Grizzil on 2007-06-01
> **daimaru said:**
> b4 u follow numerous guides. i can only say that i never got desktop effects or beryl to work properly on a 9200SE card. anything above that works like a charm but somehow not that one. sry but if u want to try go here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
it says there that apprently the driver supports 9200 and below but i followed that guide and it didnt work for me . good luck

oh yeah just read in a few threads that the script envy or something @ [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) is suposed to install drivers automatically you could try that but as posted somewhere else then you have to reinstall your drivers everytime you upgrade your kernel.
best way is to get a cheap nvidia graphics card.

I try the guides but with no success   .I try activate the desktop effects with fedora 7 and it just work fine...

---

### Post by MrMatt2532 on 2007-06-01
Did you enable restricted drivers?

Those drivers don't allow you to use desktop effects with ATI cards.

---

### Post by brooksbp on 2007-06-01
Not only should you have your graphics card drivers installed, you need to enable 'Composite' in your xorg.conf.  Although, an error should pop up notifying you of that.

Also might want to try Beryl or Compiz if you can't get Desktop Effects to enable; provided your driver is working correctly.

---

### Post by Grizzil on 2007-06-01
I can't enable the restricted driver everytime I try a error message popop and told me I don't need them

---

### Post by MrMatt2532 on 2007-06-01
> **brooksbp said:**
> Not only should you have your graphics card drivers installed, you need to enable 'Composite' in your xorg.conf.  Although, an error should pop up notifying you of that.

Also might want to try Beryl or Compiz if you can't get Desktop Effects to enable; provided your driver is working correctly.

The ATI restricted drivers do not support composite. So if you are using these drivers, then you cannot use Desktop Effects.

---

