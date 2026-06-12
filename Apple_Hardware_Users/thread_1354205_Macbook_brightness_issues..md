---
title: "Macbook brightness issues."
date: 2009-12-13
forum: Apple Hardware Users
---

### Post by jesuspoet on 2009-12-13
I can't figure out how to change the brightness settings on my Macbook. I've searched several forums, but haven't found anything at least simple enough for me to be able to set up on here. Do y'all know what I need to do?

---

### Post by miniyak on 2009-12-13
if you havn't all ready, right click on a panel and choose add to panel, then select the brightness applet

it should be the 3rd or 5th entry 

you should also have fn keyboard shortcuts that will turn the brightness down manually... but i dont know, ive never used a macbook

hope that helps

---

### Post by jesuspoet on 2009-12-13
> **miniyak said:**
> if you havn't all ready, right click on a panel and choose add to panel, then select the brightness applet

it should be the 3rd or 5th entry 

you should also have fn keyboard shortcuts that will turn the brightness down manually... but i dont know, ive never used a macbook

hope that helps

I appreciate the suggestion, but for some reason the applet is not working on my Macbook. Any other ideas?

---

### Post by Joeb454 on 2009-12-13
Thread moved to Apple Users :)

---

### Post by miniyak on 2009-12-13
hmm... odd, im not sure

but, the model of your macbook, the version of ubuntu your using and the type of install could all be important info for anybody stumbling across your thread whom has a similar issue.

---

### Post by Seq on 2009-12-13
If you've got a macbook with Intel graphics, this is a regression regarding it's behaviour. I've put a [bug in launchpad]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/388216"). It seems to be assigned to nobody.

Basically the intel X driver used to touch the hardware directly, including brightness, modesetting, etc. The 'proper' way to do this going forward is to move all hardware interactions to the kernel level. The intel driver has done this. Modesetting is done in-kernel now, and brightness is handled via ACPI or platform drivers (Most laptops use acpi for brightness as I understand it).

Unfortunately the macbook's backlight is not exposed via ACPI (not sure if this is an issue with apple's BIOS compatability, or if ACPI is handled separately). I've been meaning to look into writing a platform module for doing the backlight (since the actual backlight code exists already). Unfortunately I haven't gotten around to it yet.

---

### Post by Seq on 2009-12-13
Also, as a workaround you can install pommed and gpomme. The former is a system service, while the latter provides graphical feedback (you will need to set that up as a startup app in your session).

I've found it can cause some audio issues as it wrestles with pulse audio over volume levels.

---

### Post by _mario_ on 2009-12-14
> **Seq said:**
> 
I've been meaning to look into writing a platform module for doing the backlight (since the actual backlight code exists already). Unfortunately I haven't gotten around to it yet.

The older hal handler that memory-mapped the graphics adapter's registers to userland via /dev/mem has been deprecated and removed in recent hal versions. Please do not re-implement them.

Writing a platform module isn't necessary (and btw won't get accepted upstream). Despite its name the mbp_nvidia_bl driver can also support your machines, because it actually uses a firmware interface that is present on all machines since Apple switched to Intel processors. 

We only need to extend its device table. In order to do so, I need the output of:
```
sudo dmidecode --string system-product-name
```
and whether the machine incorporates an Intel or Nvidia chipset (mainboard chipset, not graphics!).

ciao,
Mario

---

### Post by Seq on 2009-12-14
> **_mario_ said:**
> The older hal handler that memory-mapped the graphics adapter's registers to userland via /dev/mem has been deprecated and removed in recent hal versions. Please do not re-implement them.

Writing a platform module isn't necessary (and btw won't get accepted upstream). Despite its name the mbp_nvidia_bl driver can also support your machines, because it actually uses a firmware interface that is present on all machines since Apple switched to Intel processors. 

I knew HAL was going away, and I knew there were other platform drivers (generally vendor-specific it seems -- asus and thinkpad drivers spring to mind). But I didn't check if they were upstream (or if they handled brightness).

The name really got me, this was neither a mbp or nvidia machine. Oh well, I should have looked closer I suppose.

> **_mario_ said:**
> We only need to extend its device table. In order to do so, I need the output of:
```
sudo dmidecode --string system-product-name
```
and whether the machine incorporates an Intel or Nvidia chipset (mainboard chipset, not graphics!).

ciao,
Mario

You can have that and the worlds easiest patch. Things are easy when somebody else has already done all the work. I'm using it right now, and it works great. Thanks!

```
sudo dmidecode --string system-product-name
MacBook3,1
```

The macbook1,1 and 2,1 both have intel 950 graphics that would also need to be fixed. I didn't include them in the patch since I can't immediately test either (though I could probably test a 1,1 next week).

---

### Post by _mario_ on 2009-12-15
> **Seq said:**
> 
You can have that and the worlds easiest patch. Things are easy when somebody else has already done all the work. I'm using it right now, and it works great. Thanks!

The macbook1,1 and 2,1 both have intel 950 graphics that would also need to be fixed. I didn't include them in the patch since I can't immediately test either (though I could probably test a 1,1 next week).

actually, you don't have to provide a patch, as it's a matter of seconds to update the device table. but it would be nice if you could test on a MacBook 1,1 or 2,1 sometime.

i merely didn't add those machines, because there were hal handlers available and it's getting quite confusing (for users) if we have several drivers/mechanisms all doing the same (or even interfering with each other). since the hal stuff has vanished, I added all older MacBook and MacBook Pro models to mbp_nvidia_bl (the Mactel-PPA version).

ciao,
Mario

---

### Post by Seq on 2009-12-15
> **_mario_ said:**
> actually, you don't have to provide a patch, as it's a matter of seconds to update the device table. I noticed. Makes me feel bad for putting up with pommed for a few weeks.

> **_mario_ said:**
> but it would be nice if you could test on a MacBook 1,1 or 2,1 sometime.I will hopefully this weekend. I've got a new laptop coming, which means my 3,1 will rotate to my wife, and her 1,1 will be sold. I'll try Ubuntu and mbp-nvidia-bl in the mean time.

It might be worthwhile to rename the package (or provide a second package with a dependancy on mbp-nvidia-bl-dkms) for those (like me) who didn't add it due to the name. Apple-backlight or something along those lines may be worthwhile.

> **_mario_ said:**
> i merely didn't add those machines, because there were hal handlers available and it's getting quite confusing (for users) if we have several drivers/mechanisms all doing the same (or even interfering with each other). since the hal stuff has vanished, I added all older MacBook and MacBook Pro models to mbp_nvidia_bl (the Mactel-PPA version).I believe in my case (3,1) it wasn't using the HAL handler, but the intel DDX driver. If I boot with KMS disabled, even though there is no HAL handler brightness would work fine.

---

### Post by _mario_ on 2009-12-15
> **Seq said:**
> 
I will hopefully this weekend. I've got a new laptop coming, which means my 3,1 will rotate to my wife, and her 1,1 will be sold. I'll try Ubuntu and mbp-nvidia-bl in the mean time.

thanks a lot.

> **Seq said:**
> 
It might be worthwhile to rename the package (or provide a second package with a dependancy on mbp-nvidia-bl-dkms) for those (like me) who didn't add it due to the name. Apple-backlight or something along those lines may be worthwhile.

you're right. i'll have a look at it at the weekend.

> **Seq said:**
> 
I believe in my case (3,1) it wasn't using the HAL handler, but the intel DDX driver.

what's the intel DDX driver? xorg or kernel? is it used by xrandr to adjust backlight?

> **Seq said:**
> 
If I boot with KMS disabled, even though there is no HAL handler brightness would work fine.

can you please run gnome-power-manager with debugging output (gnome-power-manager --verbose) to see which interface gets used when pressing the backlight keys.

and also provide the output of:
```

$ hal-find-by-capability --capability laptop_panel
$ lshal -u $(hal-find-by-capability --capability laptop_panel)

```

thanks & ciao,
Mario

---

### Post by sroecker on 2010-01-25
Hi,
I just fixed it this weekend, it is actually very easy and now works very smooth.
I wrote a bug report and a fix for my Macbook1,1.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/511965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/511965) 

To gain more info please run the following commands and add a comment.
(This is important because my manufacturer for example is Apple Computer, Inc. not Apple Inc.)

```

sudo dmidecode -s system-manufacturer
sudo dmidecode -s  system-product-name
lspci | grep VGA

```

---

### Post by linuxopjemac on 2010-02-09
A number of fixes were added to the mbp_nvidia_bl driver. See my post on this ([http://mac.linux.be/content/upcoming-kernel-updates-apple-products-update](http://mac.linux.be/content/upcoming-kernel-updates-apple-products-update))

---

