---
title: "Asus N56vm Fn Keys doesn't seems to work"
date: 2012-05-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by diogojg on 2012-05-25
Hi guys! 
I have a problem working with the Fn hotkeys on my brand new laptop Asus. I cannot change my volume, screen brightness, keyboard back light and other minor functions.
I have tested many possible solutions, but without any sucess.
This model of asus is brand new, but i believe that is a solution over there.
Thank you!

I aprecciate some help! :)

---

### Post by diogojg on 2012-05-26
I think it might be something about the nvidia driver which i dont have installed because i've tried several times and nvidia-settings do not detect nvidia driver in use... I need some help over here...

---

### Post by gordintoronto on 2012-05-26
Have a look at this:
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

I doubt very much that the nvidia driver have anything to do with the failure of the volume control keys. What keyboard did you specify when you installed Ubuntu?

---

### Post by diogojg on 2012-05-26
I've tried bumblebee, but when i have it installed i dont have the nvidia-settings. Whean i dont have it installed and try to install nvidia driver manually from the official website, nvidia-settings dont recognize the driver and give some error message about the xorg.conf. I just dont know what to do about that. The keyboard leyout i selected in ubuntu installation was the standard portuguese keyboard. BTW: I have a keyboard shortcut alt+F3 that isnt working, and in previous versions of linux worked perfectly.

---

### Post by gordintoronto on 2012-05-27
Is it really a Portugese keyboard? I suggest you try setting the keyboard to English US.

---

### Post by diogojg on 2012-05-28
Of course it is. I'm portuguese and i bought the laptop in Portugal.

---

### Post by gordintoronto on 2012-05-28
Neither of those guarantee that it's a Portugese keyboard.

---

### Post by diogojg on 2012-05-29
Anyway, i've tried both, but nothing happened. :/ Maybe the new kernel 3.4 supports my keyboard.

---

### Post by adroitster on 2012-06-01
Hey diogojg!

I am planning to buy an Asus laptop with almost the same configure but being sold with a different name here in the US. Would you please tell me that apart from Nvidia settings and function keys what else isn't working ? Like sound from speakers and headphones , mic , webcam, HDMI and touchpad ? Are those working fine. I would really appreciate it.

---

### Post by diogojg on 2012-06-01
> **adroitster said:**
> Hey diogojg!

I am planning to buy an Asus laptop with almost the same configure but being sold with a different name here in the US. Would you please tell me that apart from Nvidia settings and function keys what else isn't working ? Like sound from speakers and headphones , mic , webcam, HDMI and touchpad ? Are those working fine. I would really appreciate it.

Hey! I'll try to be helpfull. About the graphics if You install bumblebee, which is very simple, Ubuntu will running with intel graphic card, unless you use the command 'optirun' to run an app exclusively. Sound from speakers, headphones , mic , webcam, and touch pad are working great. Except the external subwoofer that came with this laptop. I have no experience with the hdmi output. The major problem to me is fn keys, without that I don't have the backlight on keyboard.

---

### Post by adroitster on 2012-06-02
> **diogojg said:**
> Hey! I'll try to be helpfull. About the graphics if You install bumblebee, which is very simple, Ubuntu will running with intel graphic card, unless you use the command 'optirun' to run an app exclusively. Sound from speakers, headphones , mic , webcam, and touch pad are working great. Except the external subwoofer that came with this laptop. I have no experience with the hdmi output. The major problem to me is fn keys, without that I don't have the backlight on keyboard.

Hey diogojg !

Thanks for your reply. I think I might just end up buying this laptop sometime this month. I believe sooner or later someone might find a fix for the function keys. 

Also did you post this question on askubuntu.com [http://askubuntu.com/questions/144961/windows-dont-boot-after-ubuntu-installation/144985#144985](http://askubuntu.com/questions/144961/windows-dont-boot-after-ubuntu-installation/144985#144985) ? If yes, then I have answered it.

---

### Post by woozy on 2012-06-12
@diogojg hi there! I'm also from Portugal, and I'm considering buying that model. Have you managed to fix the fn keys issue? All the rest works fine? Sleeping, etc?

Thank you

---

### Post by iip on 2012-07-28
The same problem with my new ASUS N46VM, all fn keys are not work, sub woofer also not working, I have tried acpi4asus, but no luck.

:(

---

### Post by capricornday on 2012-08-05
> **iip said:**
> The same problem with my new ASUS N46VM, all fn keys are not work, sub woofer also not working, I have tried acpi4asus, but no luck.

:(

Hi IIP , i think Fn+F2 and Fn+F7 works, but not with the Wifi led indicator :( .  
I have a n46vm too, disappointed with fn keys.. :)

regards

---

### Post by iip on 2012-08-05
> **capricornday said:**
> Hi IIP , i think Fn+F2 and Fn+F7 works, but not with the Wifi led indicator :( .  
I have a n46vm too, disappointed with fn keys.. :)

regards

Yes, you right, fn+f2 and fn+f7 are works.

---

### Post by Jomenvisst on 2012-08-16
Here's the solution to most of your problems.
[http://askubuntu.com/questions/166261/keyboard-backlight-not-working-on-an-asus-n56v](http://askubuntu.com/questions/166261/keyboard-backlight-not-working-on-an-asus-n56v).

---

### Post by diogojg on 2012-08-20
> **Jomenvisst said:**
> Here's the solution to most of your problems.
[http://askubuntu.com/questions/166261/keyboard-backlight-not-working-on-an-asus-n56v](http://askubuntu.com/questions/166261/keyboard-backlight-not-working-on-an-asus-n56v).

Actually, it did solve almost all of my problems! :) 
But the Ethernet solution is not working on kernel 3.5, works only on 3.2 version. And the f5 f6 buttons are not working, still, all other buttons are working perfectly.
Do you have any solutions for these non solved problems?

---

### Post by Jomenvisst on 2012-09-01
> **diogojg said:**
> Actually, it did solve almost all of my problems! :) 
But the Ethernet solution is not working on kernel 3.5, works only on 3.2 version. And the f5 f6 buttons are not working, still, all other buttons are working perfectly.
Do you have any solutions for these non solved problems?
Nope no idea. Just wait for updates.

---

### Post by fishbulb1022 on 2012-10-09
Hello,

I'm looking at buying the same computer, and I was wondering if anyone had tried this with quantal? If so, did any of the updates fix anything? If not, even with the troubles, would you recommend this laptop?

I'd really appreciate your feedback as my old laptop just died and I really need to replace it soon.

Thanks,

Chris

---

### Post by zezadas on 2012-10-16
Boas ja resolveste o teu stress? tambem tenho uns problemas parecidos com o meu k55vm, eu consegui meter algumas teclas a funcionar com o acpi4asus, mas a luz de fundo nao funca... se quiseres manda me uma pm, para discutir umas ideias...

---

### Post by brunomicas on 2012-11-18
Hi,

In my Asus K55VJ-SX098H don't work too FN + F5 or F6 (to adjust bright).

By the way, don't save bright.

When i restart pc, screen off, or when i change to energy or battery mode change bright again to minimum.

Only if i set maximum bright is save, always 100% bright.

(I'm portuguese too)

---

