---
title: "Macbook Pro 3,1 Support 11.10"
date: 2011-11-07
forum: Apple Hardware Users
---

### Post by Accophox on 2011-11-07
Wondering if anybody has any experience with how the 3,1 models (Mid 2007) support 11.10? I know the support base says it's supported up to 10.10, but I'm not willing to tread into unfamiliar waters (as I'd like the newest release), considering I've decided to single boot just Ubuntu. :)

And I'd like to only have to do it once, as much as I know it's probably wishful thinking...

---

### Post by yugnip on 2011-11-07
Oh let us know how it goes in Oneiric. 

I have a 3,1 I want to upgrade as well. Unfortunately my dvd drive isn't functioning, and am unable to boot from usb (even tried efi-grub to no avail, although it works on a 5,1 machine), otherwise I would let you know how mine went.

You might want to keep a small mac partition. It makes things much easier if there are any firmware upgrades, or if you use a basestation router or something.

---

### Post by recezone on 2011-11-08
> **Accophox said:**
> Wondering if anybody has any experience with how the 3,1 models (Mid 2007) support 11.10? I know the support base says it's supported up to 10.10, but I'm not willing to tread into unfamiliar waters (as I'd like the newest release), considering I've decided to single boot just Ubuntu. :)

And I'd like to only have to do it once, as much as I know it's probably wishful thinking...


It's working fine for me.  Only problem i'm running into now is getting the fan to go above 2000rpms.  I've added mactels ppa and still can't seem to get applesmc or macfanctld installed. I keep getting unable to locate packages. that aside,  it's fine.

---

### Post by Rankun on 2011-11-09
I had the same problem on my MacBook Pro (late 2009 model) which was caused by the upstart-udev-bridge process eating up 100% of my CPU power, thus making the fan run at full speed for the whole time. Check [FONT=Courier New]top[/FONT] and see if it's the same for you.

If yes, try [FONT=Courier New]sudo stop upstart-udev-bridge[/FONT] ... that fixed it for me. Fan is quiet now and my machine doesn't heat up like a frying pan.

---

