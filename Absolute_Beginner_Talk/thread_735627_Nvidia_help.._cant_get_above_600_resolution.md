---
title: "Nvidia help.. cant get above 600 resolution"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by justinsn95 on 2008-03-25
I Have just install ubuntu and i am trying to get my nvidia GEforce 7600GS to work properly. I stuck the card in and plugged the monitor up to it and "enabled the closed drivers" or whatever but i cant seem to raise the resolution above the 600's, which needless to say makes everything huge. So much that it is nearly unusable. Can anyone tell me how to adjust it to normal size?

---

### Post by overdrank on 2008-03-25
> **justinsn95 said:**
> I Have just install ubuntu and i am trying to get my nvidia GEforce 7600GS to work properly. I stuck the card in and plugged the monitor up to it and "enabled the closed drivers" or whatever but i cant seem to raise the resolution above the 600's, which needless to say makes everything huge. So much that it is nearly unusable. Can anyone tell me how to adjust it to normal size?

Hi and you can try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the ctrl, alt, backspace keys. Then you may use the nvidia setting to adjust your resolution ```
gksudo nvidia-settings
```

---

### Post by justinsn95 on 2008-03-25
thanks a million man. but i have to ask.. do you just have that command line memorized or something? just curious i guess.

---

### Post by overdrank on 2008-03-25
> **justinsn95 said:**
> thanks a million man. but i have to ask.. do you just have that command line memorized or something? just curious i guess.

Yes I have posted and used it many times. I also have a text filed that I save all the useful commands. :)
Attached  If you like :KS

---

### Post by justinsn95 on 2008-03-26
cool thanks i downloaded that and put it in my documents.::guitar:

---

