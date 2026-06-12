---
title: "Upgrade problems"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by sidamo on 2007-01-15
Sorry if this is the wrong place to post this, but I am new to Ubuntu/Linux and need some help.

I was using Dapper for almost two months on an older HP computer without any problems. I decided to upgrade to Edgy and did a clean install from a CD. The install went fine, but now I have no video after reboot. I get the GRUB screen,  (dual boot with XP) but no video after that. Does anyone know what might be wrong? I can boot into recovery mode, but have no idea what to do from there. Any help would be appreciated.

Thanks.

---

### Post by yager on 2007-01-15
I am assuming that you do have the prompt to login in correct?

If so, log in and execute the following command.  This will rebuild the xorg.conf file and should address your graphics initialization issues.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

