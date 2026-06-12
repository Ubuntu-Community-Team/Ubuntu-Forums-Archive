---
title: "Standby problem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-05-09
I've had this problem since I've been using Ubuntu. Every time I click standby on the shutdown menu, or on the keyboard, my system goes into standby. When I try to bring it back, however, I see my BIOS pop up, then my system freezes with either a bunch of squareish smiley-faces, or a bunch of diagnal lines. I can only get out of the freeze by performing a hard shutdown.

 How can a go into standby without being plagues by the square smiley-faces of death?

---

### Post by Martin on 2007-05-09
I guess you're using a laptop. Not that it should make too much difference. When you say standby - do you mean suspend or hibernate. In my recent experience under Feisty, suspend works much better than hibernate - which doesn't work at all. Using hibernate on my system leads to what you describe, suspend on the other hand works well unless I have an external USB drive connected.

---

### Post by misfitpierce on 2007-05-09
Also do you have video card drivers updated and bios somewhat up to date? They maybe help on recovery.... But also alot have been having this problem.

---

### Post by ZeroWing on 2007-05-09
> **misfitpierce said:**
> Also do you have video card drivers updated and bios somewhat up to date? They maybe help on recovery.... But also alot have been having this problem.

 Yes, I've got an Up-to-date video card driver. I'm not sure how to somewhat update my BIOS, though.

 And by going into standby I mean suspending. It's a laptop. An HP. Don't know that BIOS version, since I haven't rebooted in a long time. :)

---

### Post by Martin on 2007-05-09
You may have done this already - but do a targetted search on your laptop type and probs with suspend. Maybe someones had a similar problem and has a solution.

---

### Post by kornelix on 2007-05-10
I have a desktop system with an Intel D975XBX motherboard 
and nVidia graphics card. I have gotten suspend/resume to
work for the first time with Ubuntu 7.04. 

There seems to be no documentation on how to do this
(except for some outdated stuff that does not work).
After searching around and trying various things, I
got the following combination to work:

file  /etc/default/acpi-support

    ACPI_SLEEP=true        
    ACPI_SLEEP_MODE=standby
    MODULES="agpgart"        
    SAVE_VBE_STATE=false        
    POST_VIDEO=false        
    USE_DPMS=false        


file  /etc/X11/xorg.conf            

   Section "Device"
       Driver        "nvidia"
       ...
       Option      "NvAGP"  "1"
   EndSection
   

This black magic works for me, and hopefully for some
other folks out there in Ubuntu land. I will watch this
space in hopes someone more informed will elucidate more.

I have another PC with an MSI motherboard that worked
on the first try with default everything.

---

### Post by LollYouSuckZor on 2007-05-10
> **ZeroWing said:**
> I've had this problem since I've been using Ubuntu. Every time I click standby on the shutdown menu, or on the keyboard, my system goes into standby. When I try to bring it back, however, I see my BIOS pop up, then my system freezes with either a bunch of squareish smiley-faces, or a bunch of diagnal lines. I can only get out of the freeze by performing a hard shutdown.

 How can a go into standby without being plagues by the square smiley-faces of death?

[IMG]http://www.dailyhaha.com/_pics/crazy_finger_grandma.jpg[/IMG]

---

### Post by n2stc on 2008-01-01
> **kornelix said:**
> I have a desktop system with an Intel D975XBX motherboard 
and nVidia graphics card. I have gotten suspend/resume to
work for the first time with Ubuntu 7.04. 

There seems to be no documentation on how to do this
(except for some outdated stuff that does not work).
After searching around and trying various things, I
got the following combination to work:

file  /etc/default/acpi-support

    ACPI_SLEEP=true        
    ACPI_SLEEP_MODE=standby

    POST_VIDEO=false        
 

f

This black magic works for me, and hopefully for some
other folks out there in Ubuntu land. I will watch this
space in hopes someone more informed will elucidate more.

I have another PC with an MSI motherboard that worked
on the first try with default everything.

Above seems to work for me. THANKS!

Stan:):)

---

