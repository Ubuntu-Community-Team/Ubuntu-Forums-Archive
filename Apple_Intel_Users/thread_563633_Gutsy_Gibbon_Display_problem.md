---
title: "Gutsy Gibbon Display problem"
date: 2007-09-30
forum: Apple Intel Users
---

### Post by Black Mage on 2007-09-30
I just installed Gibbon on MacBook Pro, Santa Rose 15 Inch 2.2ghz. It installed fine but is having problem with monitor. It detects the Screen as Plug 'n' Play and the graphics card as a vesa-Generic VESA compliant card. I ran it like this, it didn't work. So I changed the graphics card to the NVIDIA 8 series and still didn't work.

A messge appears saying:

[ 67.960716] PCICannont Allocate resource region 5 of device 00000:00:1f.2
And the screen flickers and then go back to the setup. Any had this problem yet or know of a possible work around?

---

### Post by alephsmith on 2007-09-30
I can confirm this.

Even manually installing the binary driver from the official nvidia installer results in failsafe to VESA.

This is regression is recent, at about the same time nvidia-glx-new was upgraded to 100.14.19.

I was checking launchpad for any similar bugs and this might be similar [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146988](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146988)

I have since remove Ubuntu because this bug made my system almost unusable, so could you file a new bug?

---

### Post by Black Mage on 2007-09-30
Ok, sure thing.

Is there a work around for it?

---

