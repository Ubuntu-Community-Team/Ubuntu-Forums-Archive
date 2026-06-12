---
title: "amd64 ATI driver woes"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by tokyo on 2006-06-11
i'm very new to linux, so be patient.

i wanted to give xgl a spin, so i read a bit and attempted to configure my card.  that took me here [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

i get down to the very last step, where you check to see if everything worked, and i receive this output from the terminal

> tokyo@laptop:~$ fglrxinfo
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18


any ideas here?

im using the 64 bit install of Ubuntu 6.06, and my card is an ATI Mobility Radeon 9600

any help would be appreciated, thank you in advance.

---

### Post by Packard on 2006-06-11
Hello,

you can try the following:

sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri

After that it worked for me. By the way, that is quoted from this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I hope that helps.

---

### Post by tokyo on 2006-06-11
i did a fresh reinstall of 6.06 and followed the guide at the link you provided, and it worked like a charm, thanks!

---

