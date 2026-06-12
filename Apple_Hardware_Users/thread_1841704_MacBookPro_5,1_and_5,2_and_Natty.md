---
title: "MacBookPro 5,1 and 5,2 and Natty"
date: 2011-09-09
forum: Apple Hardware Users
---

### Post by pollycat on 2011-09-09
Trying to install Natty on my MacBookPro 5,1 and 5,2 machines.

I can boot in to the LiveCD if I add the parameter:
nouveau.noaccel=1
before booting.

Once in the LiveCD, I can install Natty to the hard drive no problem.

However, when I then reboot from the hard drive, I get a purple Grub screen with the choice to boot in to Natty or OSX.

I choose Natty and then all I get is a black screen with a blinking cursor.

I've tried to edit the kernel parameters by pressing "e" on the Grub screen and adding: nouveau.noaccel=1 to the list of parameters there, but this trick doesn't work there.

I've hunted around on these forums and found advice to "downgrade" Grub, but I can't get this to work.

I've tried to follow the advice on the following page:
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)
but I simply can't understand it.

So... my question is...

Could someone provide me with a step-by-step idiot-proof way to boot up Natty on my MacBookPro 5,1 and 5,2 machines after I have it installed on the hard drive (i.e. how to get past the Grub entry and get beyond the black screen and flashing cursor)?

I would be very grateful for any assistance.  Thanks!

---

### Post by z.onichi on 2011-09-10
Hi, I think you would have to simply hold the option key at startup and select the mac os from the menu.

---

### Post by pollycat on 2011-09-10
Thanks for your response.

I'm not trying to boot in to OSX, I'm trying to boot the Natty installation.  I can get to the purple GRUB screen and choose Linux but then it doesn't boot, I just get a black screen with a flashing cursor.

When booting from the LiveCD, I can get around this by adding "nouveau.noaccel=1" to the boot parameters.  But I don't know how to get around this when booting from an installation on the hard drive, adding the same parameter to the GRUB entry doesn't work.

---

### Post by z.onichi on 2011-09-10
Oh ic,

Ur trying to actually boot the ubuntu.
I had this happen to me too, for some reason i wasn't ale to figure it out.

Even now, i do have a macbook, when my hd is hooked up internally, it boots fine. but when i try it from usb, i get the same issue u have, no clue why.

Yet it can boot on my hp pc from usb with no blinking cursor.


Somehow i have the feeling that after installing it, it's stalled at certain driver somewhere, and it just doesn't get past that.

If you can acces the terminal and somehow connect, try to fully update the ubuntu. it might get some hardware drivers incase they are missing, since it's a fresh install i assume.

good luck!

---

