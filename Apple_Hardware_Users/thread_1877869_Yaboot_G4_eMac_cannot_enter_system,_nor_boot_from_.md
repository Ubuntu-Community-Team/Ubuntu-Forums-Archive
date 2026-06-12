---
title: "Yaboot: G4 eMac cannot enter system, nor boot from CDROM"
date: 2011-11-08
forum: Apple Hardware Users
---

### Post by Macbao on 2011-11-08
I post a thread for help in forum in China but cannot get any reply, it seems that few guys using ubuntu in PPC.

1. I tried to install 11.10 to my eMac G4, but failed at "scanning mirrors..."; so i download 11.04/10.10/10.04/openSUSE 11.1, and i succeeded in 11.04, and then i upgraded it to 11.10.

2. i install ubuntu to replace Mac OS X, that means there is only ubuntu in my eMac.

3. the Unity in 11.10 made me mad: i installed Ubuntu in order to make my old eMac usable, but 11.10 seemed to be slower than OS X with Unity interface.

4. so i installed openSUSE instead, but i found i could not boot from CDROM when startup. thanks for Google , i modify Yaboot.conf by adding "enablecdboot", to  boot from the openSUSE DVD, and installed it.

[/SIZE][SIZE=3][COLOR=Red]MY KEYBOARD IS BROKEN, SO I USE A PC KEYBOARD, AND I  DON'T KNOW WHETHER IT MATTERS OR NOT FOR FAILING TO BOOT FROM CD WHEN  HOLDING C FROM KEYBOARD WHEN STARTUP.[/COLOR][/SIZE]
[SIZE=3]
5. the OpenSUSE just doesn't support my Airport Extreme card and i don't know how to make it usable (the Ubuntu just supports everything well), i tried to change back to Ubuntu, using 10.04 LTS CD.

6. however, similar to previously installed Ubuntu, the openSUSE would not like to boot from CD when startup. and i found the yaboot.conf in SUSE boot, and tried to modify it, but when doing "ybin -v" in terminal it told me there was no "ybin".

7. i modified the path for boot in YaST, directing then to the Ubuntu Lived CD's Casper folder then reboot. Now i'm so sad to find my eMac boot with yaboot and then nothing happen, just staying with "boot: "

Would someone help to solve the problem?
should i enter sth after boot: to make it boot from CDROM?
as i told previously, i'm using a PC keyboard and my eMac won't boot from CD when holding C at startup before or after Chime.

Pls give me advice, thanks in advance...

---

### Post by rsavage on 2011-11-09
If you can get into openfirmware then you can boot the cd from there with

boot cd:,\\:tbxi

This post has all the links to the various documentation for ppc ubuntu [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)

I don't know anything about openSUSE, but if you want faster than unity then check out xubuntu or lubuntu.

---

### Post by Macbao on 2011-11-09
> **rsavage said:**
> If you can get into openfirmware then you can boot the cd from there with

boot cd:,\\:tbxi

This post has all the links to the various documentation for ppc ubuntu [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)

I don't know anything about openSUSE, but if you want faster than unity then check out xubuntu or lubuntu.

thanks a lot my friend.

Do you mean i type "boot cd:, \\:tbxi" after "boot:" show up?

---

### Post by rsavage on 2011-11-10
No openfirmware is different to that.  To restart the machine into openfirmware you have to hold down o and f and command and option while turning the machine on. I'm not sure if you'll be able to do it with your keyboard.  You will get an "ok:" prompt.  That is where you type what I gave you.
 
If you can't get into openfirmware then that is no problem either as we can do something from your "boot:" prompt which is the yaboot prompt.  I'll have to figure out the command you need and I haven't got time now, but you could work it out from the documentation I linked.
 
Have you also tried holding down option (alt) on restart to try and select the cd drive?

---

### Post by Macbao on 2011-11-10
> **rsavage said:**
> No openfirmware is different to that.  To restart the machine into openfirmware you have to hold down o and f and command and option while turning the machine on. I'm not sure if you'll be able to do it with your keyboard.  You will get an "ok:" prompt.  That is where you type what I gave you.
 
If you can't get into openfirmware then that is no problem either as we can do something from your "boot:" prompt which is the yaboot prompt.  I'll have to figure out the command you need and I haven't got time now, but you could work it out from the documentation I linked.
 
Have you also tried holding down option (alt) on restart to try and select the cd drive?

Thanks a lot sir...

However if i hold "ctrl+alt+o+f" or "c" or "alt" when startup with the PC keyborad, i will still get the "boot:" prompt and then cannot type anything into it.

if i don't touch at all the keyboard when startup, i can type sth after "boot:", wired, right?

Maybe the simplest way is to get a new keyboard but nowadays it's hard to find one...

---

### Post by rsavage on 2011-11-10
What is sth?

---

### Post by rsavage on 2011-11-10
To boot the 10.04 live cd you would type at the "boot:" prompt something like this I think (all one line):

/casper/powerpc/vmlinux initrd=/casper/powerpc/initrd initrd-size=1048576 file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ro --

If it doesn't work you may have to make the paths more openfirmware like with cd at the start. Let me know if it doesn't work and I'll look into it some more.  Hopefully you won't have to buy a new keyboard!

This is the relevant part of the yaboot.conf from the live cd:

image=/casper/powerpc/vmlinux
    label=live
    alias=live-powerpc
    initrd=/casper/powerpc/initrd
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --"
    initrd-size=1048576
    read-only

---

### Post by rsavage on 2011-11-10
Am I making this too complicated and just typing

live

would work????

---

### Post by Macbao on 2011-11-10
> **rsavage said:**
> What is sth?
  

ah, in college we use sth to refer to something

---

### Post by Macbao on 2011-11-11
> **rsavage said:**
> To boot the 10.04 live cd you would type at the "boot:" prompt something like this I think (all one line):

/casper/powerpc/vmlinux initrd=/casper/powerpc/initrd initrd-size=1048576 file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ro --

If it doesn't work you may have to make the paths more openfirmware like with cd at the start. Let me know if it doesn't work and I'll look into it some more.  Hopefully you won't have to buy a new keyboard!

This is the relevant part of the yaboot.conf from the live cd:

image=/casper/powerpc/vmlinux
    label=live
    alias=live-powerpc
    initrd=/casper/powerpc/initrd
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --"
    initrd-size=1048576
    read-only

my dear friend, thanks for all the job you've done.

however whether whatever i type, it just shows up "there is not such directory"

at last, i found the broken keyboard still function with "c" key, and use it to reboot from CD and i succeed installed 10.04....

:P

---

### Post by rsavage on 2011-11-11
> **Macbao said:**
> at last, i found the broken keyboard still function with "c" key, and use it to reboot from CD and i succeed installed 10.04....

Haha...yeah the low tech solution is always the best!  Glad to hear you got it working!

---

### Post by Macbao on 2011-11-11
> **rsavage said:**
> Haha...yeah the low tech solution is always the best!  Glad to hear you got it working!

i'm now trying to install a Xubuntu or Lubuntu on my eMac, learning your thread posted.

---

