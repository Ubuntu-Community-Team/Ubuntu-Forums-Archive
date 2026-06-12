---
title: "Screen Resolution Acer 3680-2682"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by robskicks on 2007-12-09
I'm a newbie to Ubuntu, so you're going to have to walk me through this...

I have Acer Aspire 3680-2682... I changed the OS to Ubuntu after vista crapped out... My biggest concern is my screen resolution just does not look right. It is supposed to be 1200x800 but it seems the biggest option I have is 1024x768. This pulls my screen so that all pictures are kinda wide, etc.

How can I get my screen to look right?

I tried searching the forums but I don't know much about changing the code, so I'll need step by step instructions on how to do this. Any help I get is greatly appreciated.

---

### Post by Crashmaxx on 2007-12-09
Do you know what graphics card you have? Have you went into System>Administration>Restricted Drivers Manager and enabled your graphics drivers there? You may just need to install the proprietary drivers and reboot.

---

### Post by meborc on 2007-12-09
there is a great wiki-page about resolutions here [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

if you want a quick fix though, then write this down (don't do it, write it and then do it as the first command will take the X away from you ;))

1. ctrl+alt+F2
2. log in using your user name and password (the password will be invisible, just type it and hit enter)
3. type: "sudo /etc/init.d/gdm stop" +enter, it will ask for password... insert it and enter
4. type: "sudo dpkg-reconfigure xserver-xorg" enter
5. follow the questions, choose the default answers when not sure (use tab and arrow keys to move around, space to select many objects etc)
6. the important part is when the screen resolution is asked, choose the ones you want to use, use space key to select them
7. after all is finished type "sudo /etc/init.d/gdm start" +enter

good luck :)

---

### Post by robskicks on 2007-12-09
> **Crashmaxx said:**
> Do you know what graphics card you have? Have you went into System>Administration>Restricted Drivers Manager and enabled your graphics drivers there? You may just need to install the proprietary drivers and reboot.

I just checked my restricted drivers, "Firmware foe Broadcom 43xx chipset" was the only thing there and it said it was not in use. I enabled it, restarted and the screen is still the same. :/ but thanks for your speeedy reply :)

---

### Post by Crashmaxx on 2007-12-09
That is your wireless card, probably didn't hurt to enable the drivers for it.

Go under System>Administration>Screens and Graphics and tell us what it say under the Graphics Card tab. Then we can tell you what driver to select.

meborc's instructions should work, but they aren't very noob friendly and I wouldn't start with that.

---

### Post by robskicks on 2007-12-09
> **meborc said:**
> there is a great wiki-page about resolutions here [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

if you want a quick fix though, then write this down (don't do it, write it and then do it as the first command will take the X away from you ;))

1. ctrl+alt+F2
2. log in using your user name and password (the password will be invisible, just type it and hit enter)
3. type: "sudo /etc/init.d/gdm stop" +enter, it will ask for password... insert it and enter
4. type: "sudo dpkg-reconfigure xserver-xorg" enter
5. follow the questions, choose the default answers when not sure (use tab and arrow keys to move around, space to select many objects etc)
6. the important part is when the screen resolution is asked, choose the ones you want to use, use space key to select them
7. after all is finished type "sudo /etc/init.d/gdm start" +enter

good luck :)

I tried it but after #3 it said no such directory...

---

### Post by robskicks on 2007-12-09
My graphics card is: Intel 945*****

---

### Post by robskicks on 2007-12-09
It also says i810 Intel Integrated in drivers

---

### Post by Crashmaxx on 2007-12-09
Change the driver to "intel" then you should have more resolution options.

---

### Post by robskicks on 2007-12-09
I did this, but when I open "screen and graphics" again it is changed back to i810

---

### Post by Crashmaxx on 2007-12-09
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e)
That link explains the problem and the solutions. Follow that until you get to where it says "Use 915resolution with the older i810 driver" and reboot. If that didn't work, then continue the instructions.

---

### Post by meborc on 2007-12-09
> **robskicks said:**
> I tried it but after #3 it said no such directory...
be sure about the spaces in that command:```
**sudo /etc/init.d/gdm stop**
```

---

### Post by robskicks on 2007-12-09
> **Crashmaxx said:**
> [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e)
That link explains the problem and the solutions. Follow that until you get to where it says "Use 915resolution with the older i810 driver" and reboot. If that didn't work, then continue the instructions.

Thanks for the link but I simply don't understand how to do this...

---

### Post by robskicks on 2007-12-09
> **meborc said:**
> be sure about the spaces in that command:```
**sudo /etc/init.d/gdm stop**
```

Ok ill give it another go...

---

### Post by robskicks on 2007-12-09
Butters . Finally Got It! Thanks Alot To Everyone Who Replied!

---

### Post by meborc on 2007-12-09
> **robskicks said:**
> Butters . Finally Got It! Thanks Alot To Everyone Who Replied!

no problem man :) and remember, help is only a tear-drop away!

---

