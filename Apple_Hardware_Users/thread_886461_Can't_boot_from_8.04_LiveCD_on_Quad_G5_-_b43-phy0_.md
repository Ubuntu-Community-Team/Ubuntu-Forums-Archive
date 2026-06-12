---
title: "Can't boot from 8.04 LiveCD on Quad G5 - b43-phy0 errors"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by VirtualWolf on 2008-08-11
I'm trying to boot from the LiveCD, but it keeps getting stuck at the loading screen and spits out endless lines of these errors: 

```
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (4).
```

From my poking around Google it appears to be related to wireless, and I do have the AirPort Extreme/Bluetooth combo card installed. I don't particularly want to pull it out just to boot Ubuntu, and all the fixes and workarounds I've found seem to for x86 machines.

Any thoughts? Thanks!

---

### Post by Kevbert on 2008-08-11
It's saying you need the firmware drivers for your Broadcom based wireless card.  It's strange that you're having this problem as it normally only occurs in Intrepid (8.10, which doesn't come, at present, with many drivers) .  How old is the Live CD ?   It suggests it's from early July or earlier as the Broadcom drivers have been updated.

---

### Post by VirtualWolf on 2008-08-11
Oh, ok.

I downloaded it relatively recently, but it may well have been early July. I didn't realise it had been updated this soon. I'll download it again and test.

Cheers!

---

### Post by Kevbert on 2008-08-11
If you decide that you want to install the new CD on your PC and you still get the problem you can rectify the problem by using the method in my post [COLOR="Red"][here]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR].  Alternatively install the old CD and go to that page.

---

### Post by VirtualWolf on 2008-08-11
Ok, that didn't work. Same problem.

And I can't follow that post, because all I'm trying to do right now is just boot off the Live disc! I haven't even gotten to the point of installing yet. :(

---

### Post by Kevbert on 2008-08-11
Are you saying the new CD does work as it gives the same problem ?  If so, then that's a serious problem.

---

### Post by cyberdork33 on 2008-08-11
That error has been around. It should not affect the bootability of the system.

The b43 driver needs firmware loaded to work, that is what the error is complaining about, simply "sudo modprobe -r b43" and the messages will stop. You are likely at the login prompt, those messages just keep pushing things up! (IDK if the driver works in PPC Ubuntu anyway).

---

### Post by Kevbert on 2008-08-11
> **cyberdork33 said:**
> That error has been around. It should not affect the bootability of the system.

The b43 driver needs firmware loaded to work, that is what the error is complaining about, simply "sudo modprobe -r b43" and the messages will stop. You are likely at the login prompt, those messages just keep pushing things up! (IDK if the driver works in PPC Ubuntu anyway).

But the guy is only trying to boot up a Live CD, so surely sudo won't work.  I've seen this on Intrepid and until you fix the firmware the boot won't go any further.  Please comment. :confused::confused::confused:

---

### Post by cyberdork33 on 2008-08-11
> **Kevbert said:**
> But the guy is only trying to boot up a Live CD, so surely sudo won't work.  I've seen this on Intrepid and until you fix the firmware the boot won't go any further.  Please comment. :confused::confused::confused:sudo works on the livecd...

This might be the case on Intrepid, but I am pretty sure there isn't even an PowerPC release of Intrepid yet, so I am going to assume that is not what he is using. I used to get this situation on my Inspiron 5100 all the time with Hardy. It was very annoying. There has to be a way to prevent loading of the module from the bootline.

---

### Post by Kevbert on 2008-08-11
> **cyberdork33 said:**
> sudo works on the livecd...

This might be the case on Intrepid, but I am pretty sure there isn't even an PowerPC release of Intrepid yet, so I am going to assume that is not what he is using. I used to get this situation on my Inspiron 5100 all the time with Hardy. It was very annoying. There has to be a way to prevent loading of the module from the bootline.

No Intrepid is still in Alpha release.  This is the sort of problem that's liable to put people off using Ubuntu.

---

### Post by cyberdork33 on 2008-08-11
> **Kevbert said:**
> No Intrepid is still in Alpha release.  This is the sort of problem that's liable to put people off using Ubuntu.
Since it is Alpha.... 
all the more reason that there is likely not a PPC version yet (which I checked, there isn't) and why you shouldn't expect it to be working wonderfully yet.... but lets get back on topic shall we?

Virtualwolf, have you tried to login anyway? Have you checked if this issue is mentioned in the PowerPCFAQ?
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by VirtualWolf on 2008-08-11
I'm not seeing any login prompts, and I've tried hitting Return a few times, all that happens is I get a new blank line, heh.

And aye, I've checked the PPC FAQ, and there's no mention of it unfortunately.

---

### Post by stream303 on 2008-08-11
See if this has been fixed in the latest 8.04.1 respin:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

You may also want to try the "alternate" text-based installer - although I'm not sure that it would make any difference to the wireless issue stopping the install.  Worth a try especially with the 8.04.1 respin.

---

### Post by VirtualWolf on 2008-08-11
Aye, the disc was 8.04.1, I downloaded it afresh last night. I'll try with the alternate installer when I get home tonight. Not sure how much of a difference it'll make though, because it's crapping out during the initial text-based load process, it's not even getting to loading X. :)

---

### Post by cyberdork33 on 2008-08-11
does the alt install disc even try to startup wireless?

---

### Post by Kevbert on 2008-08-12
> **VirtualWolf said:**
> Aye, the disc was 8.04.1, I downloaded it afresh last night. I'll try with the alternate installer when I get home tonight. Not sure how much of a difference it'll make though, because it's crapping out during the initial text-based load process, it's not even getting to loading X. :)

Another option is to download good old [[COLOR="Red"]Gutsy Gibbon[/COLOR]]("http://releases.ubuntu.com/7.10/") 7.10.  It will give you the look and feel of Ubuntu without the wireless problem.  If you like it then you can install Hardy and we can sort out the problems from there.

---

