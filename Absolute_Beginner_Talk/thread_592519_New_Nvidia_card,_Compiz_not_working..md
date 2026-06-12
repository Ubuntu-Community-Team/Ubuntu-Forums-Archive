---
title: "New Nvidia card, Compiz not working."
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-10-26
1) Swapped out old ATI card for new Nvidia 7600 GT. 
2) Turned on computer, went to restricted manager, downloaded and installed driver. 
3) Restarted, go to Appearance and effects:  "The composite extension is not available."
4) Uninstalled then reinstalled restricted driver -- same thing. 


What do I do to make Compiz work?

Thanks.

---

### Post by mikeyphi on 2007-10-26
Check under Screens & Graphics that the nvidia driver is used.
Try this guide: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by aberadam on 2007-10-26
Yes, it says it's using the nVidia driver.  

I don't really want to install anything, I'd rather use the default one and add plugins.  It should work by default. 

As far as I know I already have Compiz Fusion, it came with Gutsy, downloading again will no doubt mess things up.

---

### Post by aberadam on 2007-10-26
A weird thing is that when I first booted Gutsy there were no restricted drivers installed -- then basic compiz worked.  At that point it was using the graphics chip on the motherboard and the basic compiz fusion effects worked (wobbly windows, etc).  When I installed the ATI drivers it all stopped working, as expected, but I thought with the Nvidia drivers it'd be back up again.

---

### Post by MegaJim on 2007-10-26
Just try doing

```
sudo apt-get install compiz
``` to check it actually is installed first

---

### Post by aberadam on 2007-10-26
Yep MegaJim, just ran that and it's installed. 

Still saying 'composite extension not available'.

---

