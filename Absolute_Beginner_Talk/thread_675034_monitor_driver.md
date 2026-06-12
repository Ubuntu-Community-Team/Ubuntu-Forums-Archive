---
title: "monitor driver?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-01-22
I have a samsung syncmaster 2220wm monitor I just got with this new computer. I don't see any drivers for it in ubuntu and it looks like its using the plug and play setting. is there something i can do to get a driver installed for this monitor?

---

### Post by Shazaam on 2008-01-22
I just looked at their site and it looks like they only have a driver for Windows. Ubuntu should detect and run the monitor properly. Is there a problem with your display?

---

### Post by Nutopia on 2008-01-22
Things seem a little fuzzy. I guess it's not really a big deal, but in terminal apps the text looks kind of "pixely"

---

### Post by Shazaam on 2008-01-22
Hmm. What video card do you have and have you tried the "Restricted Drivers Manager" yet?

---

### Post by Nutopia on 2008-01-22
128MB ATI Radeon HD 2400 PRO

I just went to restricted drivers and it said I didn't need any.

---

### Post by Shazaam on 2008-01-22
Well, you could install the driver from ATI/AMD here...

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

or use Synaptic to find drivers.

I would first search the forums here for any ATI video card posts to get a better answer as I have an nvidia card. Some have had great success but others have not. Research diligently before you commit to any action. You could also search the forums for any font tweaks others have posted if you are ok with your current desktop resolution settings.

---

### Post by OffAxis on 2008-01-22
> I just went to restricted drivers and it said I didn't need any.
True, you can run just fine with the open source driver, but if you think it's the cause of your problem you may want to try the Restricted Driver.

I'd be more concerned with the 'Plug and Play' setting on the monitor; this probably isn't the optimum.

 Look up the specs for your monitor and then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This command will let you reconfigure your xorg.conf file and add in your monitor specifics. It may help.

---

### Post by stchman on 2008-01-22
> **Nutopia said:**
> I have a samsung syncmaster 2220wm monitor I just got with this new computer. I don't see any drivers for it in ubuntu and it looks like its using the plug and play setting. is there something i can do to get a driver installed for this monitor?

Are you running the native 1680x1050 resolution?  If no then it will look fuzzy.  LCDs look their best when running the native res.

---

### Post by d13 on 2008-01-24
Hello, 

just have a similar problem. I have enough old NVIDIA mx 4000 videcard and NEC V721 monitor. Problem is, into 7.10 Gutsy, here is only 5xx series drivers, not 7xx, so monitor have only 72Hz frequency. One week ago on WinXP it was on 85Hz....
Clear, the Nec website have not linux driver for my monitor....

Please advice me ...

---

