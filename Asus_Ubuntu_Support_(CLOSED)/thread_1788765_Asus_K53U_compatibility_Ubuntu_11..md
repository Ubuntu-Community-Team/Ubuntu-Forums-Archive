---
title: "Asus K53U compatibility Ubuntu 11.*"
date: 2011-06-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by hfinger on 2011-06-23
I am thinking of buying two Asus K53U laptops for my wife and me, one with Windows 7 and the other to be loaded exclusively with Ubuntu 11.*.

Has anybody used this model with Ubuntu 10.* or 11.*?  These new laptops are available very cheaply but I am concerned that this model does not appear at all on the list of certified or ready computers.  And a search for Ubuntu or Linux on the Asus site returns NOTHING for laptops!

Regards,
Hedley

---

### Post by hfinger on 2011-06-23
I am thinking of buying two Asus K53U laptops for my wife and me, one with Windows 7 and the other to be loaded exclusively with Ubuntu 11.*.

Has anybody used this model with Ubuntu 10.* or 11.*? These new laptops are available very cheaply but I am concerned that this model does not appear at all on the list of certified or ready computers. And a search for Ubuntu or Linux on the Asus site returns NOTHING for laptops!

Regards,
Hedley

---

### Post by sanderd17 on 2011-06-23
Asus only gives eeePCs with Linux, nothing else, but generally they work quite well.

I've also seen many problems with the certified hardware list. Some devices that are on it don't work and other that aren't on it work perfect. So I wouldn't trust that list.

I would suggest you just try it, and if it doesn't work, you can always return it.

---

### Post by s.fox on 2011-06-23
Please do not create duplicate threads. Thank you.

Threads Merged.

---

### Post by error1982 on 2011-06-24
> **hfinger said:**
> I am thinking of buying two Asus K53U laptops for my wife and me, one with Windows 7 and the other to be loaded exclusively with Ubuntu 11.*.

Has anybody used this model with Ubuntu 10.* or 11.*? These new laptops are available very cheaply but I am concerned that this model does not appear at all on the list of certified or ready computers. And a search for Ubuntu or Linux on the Asus site returns NOTHING for laptops!

Regards,
Hedley
hi man, what about ubuntu for asus k53u? i want insatll ubuntu 11.04 x64 to my laptop

---

### Post by cucisan on 2011-06-25
hi,

i just bought a asus a53sv which is the same as the k53sv.
nearly everything works out of the box, even gpu switching with bumblebee... (expect a bug where the fan turns on and never off when installing bumblebee)

things that don't currently work:
  volume keys
  touchpad gets detected as mouse (no multitouch, force elantech does not work here)
  fan goes fullspeed if using bumblebee (or acpi_call to disable nvidia card and use intel instead) - but saves a lot battery nevertheless


regards

---

### Post by cucisan on 2011-06-26
just posted my step2step howto here: [http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081)

got nearly everything working... :)

---

### Post by hfinger on 2011-06-27
Thanks guys.  I bought a Toshiba for myself and a Compaq for my wife.  The Toshiba will be getting Ubuntu, the Compaq will stay with Windows 7.

Regards,
Hedley

---

### Post by Charlie Gibbs on 2012-01-20
I Installed Ubuntu 10.10 on an ASUS K53U.  It came up OK, but the display resolution was stuck at 1024x768, which resulted in a distorted display as it was stretched to fill the laptop's 1366x768 screen.  Downloading the ASUS driver (ati-driver-installer-11-12-x86.x86_64.run) corrected this.

I've had problems with suspend and resume; I've sometimes had to do a complete power cycle to get it running again.  After downloading the 350MB of outstanding updates (I didn't do this during the initial installation), the laptop wouldn't boot at all.  I did a re-install, telling it to apply the updates during the installation procedure, installed the video driver, and so far everything is fine.  Wi-fi, sound, and card reader are all working.  I'm crossing my fingers and hoping everything stays up this time...

---

### Post by Peter LaValle on 2012-07-16
Why did you choose 10.10? Did you have any luck with this ... or 12.04?

Specifically:
 * did WiFi work?
 * did 3D acceleration work?

---

