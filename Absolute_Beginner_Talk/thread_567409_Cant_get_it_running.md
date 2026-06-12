---
title: "Cant get it running"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by matanlevy on 2007-10-04
Hi Everybody!

I downloaded the Ubunto 7.04 Cd ... i Burned it ..
Then i restarted my computer (Intel), the Ubunto screen came up 
I chose "insall or run from cd" (If i can recall right)
then it seemed to be loading.. took it long time though.. 
and when the orange indicator became  full my screen turned black and nothing happened..

I know my post isn't really clear so please ask me question so you could help me :)

thank you very much

---

### Post by overdrank on 2007-10-04
> **matanlevy said:**
> Hi Everybody!

I downloaded the Ubunto 7.04 Cd ... i Burned it ..
Then i restarted my computer (Intel), the Ubunto screen came up 
I chose "insall or run from cd" (If i can recall right)
then it seemed to be loading.. took it long time though.. 
and when the orange indicator became  full my screen turned black and nothing happened..

I know my post isn't really clear so please ask me question so you could help me :)

thank you very much

Hi and welcome, and could you give us some specs on your system, like cpu, memory, video card?
Also did you follow this "how to" to burn the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And you can verify the cd also because it could have been corrupted during the download
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by matanlevy on 2007-10-04
Thanks for the fast replay!

1. i did check if the download is ok.. and it came back fine :)
2. I burned it via Ashampoo 7  .. i think it should really matter.. (i did burn as image file)
3. Pentium 4 CPU 3.4 GHz 
    2GB of RAM
    2 maxtor 250GB hard disks
   RADEON X800 Series (Saphir)

4.  and when i try to use the "check the cd" option after rebooting with ubuntu cd inside 
 the same thing happened.. when the indicator was full the screen turned black.. and nothing happened untill i pressed the restart button..

---

### Post by overdrank on 2007-10-04
> **matanlevy said:**
> Thanks for the fast replay!

1. i did check if the download is ok.. and it came back fine :)
2. I burned it via Ashampoo 7  .. i think it should really matter.. (i did burn as image file)
3. Pentium 4 CPU 3.4 GHz 
    2GB of RAM
    2 maxtor 250GB hard disks
   RADEON X800 Series (Saphir)

4.  and when i try to use the "check the cd" option after rebooting with ubuntu cd inside 
 the same thing happened.. when the indicator was full the screen turned black.. and nothing happened untill i pressed the restart button..

Ok lets try this when you get to the screen that start/install ubuntu then press the F6 key and you can remove the quiet splash from the kernel line and then you will be able to see any errors.

---

### Post by matanlevy on 2007-10-04
I did as you told me but it didnt show any errors and it happened the same way as i described it before..

---

### Post by drsmaw on 2007-10-04
matanlevy,

Had a similar problem, but not exactly yours. In fact you got farther than I did when I first burned the image.

But I also remember burning at a lower write speed and it helped.  Try burning at 4x, it worked for me.

---

### Post by overdrank on 2007-10-04
> **matanlevy said:**
> I did as you told me but it didnt show any errors and it happened the same way as i described it before..

Hi you can try what drsmaw suggested. Also I have not run into this problem of installing but after the installation when trying to install the drivers is when the problem starts. You may also try adding (where you removed quiet splash) noapic and vga=771. Sorry I could not be of more help.
Edit try one more thing by using the alt. ctrl, F1 keys all at the same time when the screen goes black and see if this will bring you to the command prompt.

---

### Post by drsmaw on 2007-10-04
try these boot cheat codes:
 "vga=normal noapic noacpi pnpbios=off acpi=off noapm"
If you are successful, redo the codes again , knocking one off at a time.  This way you can narrow it down. 
It's worth a shot.

---

### Post by Tyke91 on 2007-10-04
sounds like xserver isn't configured correctly

if you can, boot into safe mode and type this into the command line

```
sudo dpkg-reconfigure xserver-xorg
```

follow the instructions to create a working xorg.conf file... then restart and see if it works. if it doesn't... ask here again :D

---

