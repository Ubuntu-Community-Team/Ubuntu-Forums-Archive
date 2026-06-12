---
title: "How do I adjust LCD-colours?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Ba|der on 2006-10-28
In Windows the drivers for my integrated SIS-graphic card has an option for adjusting the colours. The default setting (for both Ubuntu and Windows) is very bad since I need to adjust the colours too see all info on web-pages (links, topics etc that often have a grey, low density colour. It does not help adjusting the light amount on the screen (which has keyboard shortcuts), so I need to adjust the three RGB colours by themself to get this correct. How do I accomplish this in Ubuntu?

---

### Post by handy on 2006-10-28
It is unusual that your LCD monitor doesn't have a *digital control menu* built into it?

My graphic's card driver supplies the abilities you need.  

I think that there is a solution for you too...

---

### Post by Ba|der on 2006-10-28
> **handy said:**
> It is unusual that your LCD monitor doesn't have a *digital control menu* built into it?

My graphic's card driver supplies the abilities you need.  

I think that there is a solution for you too...

It's a [desknote]("http://www.lostcircuits.com/motherboard/ecs_ibuddie/") from Elitegroup, an [iBuddie4 model: A928]("http://www.ecs.com.cn/ECSWeb/Products/ProductsDetail.aspx?MenuID=0&LanID=0&DetailID=224&DetailName=Specification") so the LCD is not an external monitor. How can I find the controlpanel for the driver in Ubuntu?

APPEND;
Btw: I've checked in BIOS and there is no colour-setup there, so it has do be done in the OS, like I do in Windows.

---

### Post by gn2 on 2006-10-28
Type "xgamma" in a terminal, this will tell you the value set currently.

To change the value, type "xgamma -gamma x.x" (without the quotes and where x.x is the value of the desired gamma)

For example my laptop is quite washed out at the standard gamma of 1.0, changing it to 0.7 gives better colour.

You can also change the colours individually -rgamma -ggamma -bgamma (red green blue)

More information by entering "man xgamma"

It is possible to permanently change screen gamma by editing xorg.conf

If you use Xubuntu there are sliders for adjusting gamma in the Display preferences in the Settings menu.

---

### Post by Ba|der on 2006-10-29
Thank you gn2. After reading your post I also searched for "gamma" on Ubuntu forum, and it seems there also possible to install a GUI for adjusting the RGB-colours (REF# [http://ubuntuforums.org/showthread.php?t=287271)](http://ubuntuforums.org/showthread.php?t=287271)). I'll play around with the settings a bit to find a good combination. :-)

---

