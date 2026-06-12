---
title: "Problems recording DVD in Ubuntu feisty"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by dbrunod on 2007-05-30
Hi all,

I´m new here, and also newbie to linux. I´ve recently installed the Feist distribuiton, and after some working around, I already have most of my hardware working fine, including restricted hp scanner.

Anyway, my main issue is about recorgind DVDs in Ubuntu - specially converting from 9gb to 5gb. I´ve tried several applications, including k9copy, DVD95, DVDShrink for linux and so on. All of them, when i get about 90% of completition, display an error message. The problem is that it just says : Error...

On DVD RIp, I was able to extract the files to the HArd disk as .VOB, but the transcode asks for something like 14 hours to complete.

My machine is pretty fast - 2.8 1GBram, 350Gb harddisk. 

Can anyone please help me?
Regards,
Daniel

---

### Post by phatty420 on 2007-05-30
Try installing "wine" and use the windows dvdshrink3.2, the linux xdvdshrink is quite primitive and complicated, but the wine/dvdshrink.exe combination works, except you have to use k9copy to burn it.  so you create iso in dvdshrink and then burn with k9copy. I cant get the dvdecrypter to work on wine but if you can figure it out then dvdshrink can do the whole rip/burn process for you.

---

### Post by orb9220 on 2007-05-30
> Try installing "wine" and use the windows dvdshrink3.2,

Yep that and DVDecrypter in wine too.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

---

### Post by dbrunod on 2007-06-01
tahnks guys. I´m also in contact with the developer from DVD 95, and he ishelping me figure out the options under Linux. I will try DVDshrink and decripter, in the meantime.!

Best wishes!
Daniel

---

