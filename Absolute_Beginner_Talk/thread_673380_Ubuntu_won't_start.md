---
title: "Ubuntu won't start"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by GBee on 2008-01-20
I get past the grub loader (dual boot with Vista), the Ubuntu start up screen appears, but it then goes to the computer name, and it says login, this appears as a black screen with white text, i can type my username and password in, and it then is like terminal?

help 7.10 is the first time i've stuck with Ubuntu and thought that it's finally getting there as a useable alternative to the big M!

---

### Post by Ub1476 on 2008-01-20
Do you get any errors if you type into the terminal (after you have logged in)

```
startx
```

---

### Post by Ebuntor on 2008-01-20
> **GBee said:**
> I get past the grub loader (dual boot with Vista), the Ubuntu start up screen appears, but it then goes to the computer name, and it says login, this appears as a black screen with white text, i can type my username and password in, and it then is like terminal?

help 7.10 is the first time i've stuck with Ubuntu and thought that it's finally getting there as a useable alternative to the big M!

Sounds like the X-Server isn't properly configured. 

After you typed your username and password try this command.

```
 sudo dpkg-reconfigure xserver-xorg
```
It will allow you to configure the X Server. When in doubt simply the default settings are best, press enter for the next dialog. 

After you finished all the dialogs, reboot.

Hope that helps. :)

---

### Post by Ebuntor on 2008-01-20
> **Ub1476 said:**
> Do you get any errors if you type into the terminal (after you have logged in)

```
startx
```

Please correct me if I'm wrong but won't that start X as root? Besides I think that isn't a fix, just a workaround.

---

### Post by GBee on 2008-01-20
Ub1476

thanks, error said something about missing 'fglrx'? I have an ati graphics card, i got an error before i shut down about my card driver being missing? is this related?

---

### Post by GBee on 2008-01-20
Ebuntor - thanks, worked a treat, back in, and my sincere thanks, is there anything i need to know about what i did to get back in, xserver settings that i should change back etc?

---

### Post by Ebuntor on 2008-01-20
> **GBee said:**
> Ebuntor - thanks, worked a treat, back in, and my sincere thanks, is there anything i need to know about what i did to get back in, xserver settings that i should change back etc?

You're welcome, glad it worked. :)

No, the settings have now been permanently changed and if everything keeps working as it should you'd never have to change anything again. Hope that answers your question.

---

