---
title: "Grubbing around in Grub2 and OS installations"
date: 2014-02-07
forum: Any Other OS
---

### Post by Don_Stahl on 2014-02-07
It's snowing and I'm NOT going out there! So I figure I'll play around with multi-boot and, along the way, probably learn something about configuring Grub2.

I have a laptop with two Ubuntu derivatives, Zorin and Elementary, installed. My vague plan is to remove Elementary. To do this, might I --

1. After booting to Zorin, use disk utility to reformat the partition where Elementary lives, and then
2. run [FONT=courier new]sudo grub-update[/FONT] to rebuild grub.cfg?

I'm assuming Grub2 will then look at the drive, find only one OS remaining, and update itself accordingly?

(I did look around the documentation a little bit, but didn't happen on a description of this particular operation.)

---

### Post by deadflowr on 2014-02-07
Seems like a plan, though run
```
sudo grub-install /dev/sda
```
first, or else there is the possiblity that the grub installed was the elementary os's grub, and running the update grub command for the zorin wouldn't do anything. And deleting the partition the grub is installed on would leave you without any grub installed.
run the above command from zorin. 
I assume you have one disk, so /dev/sda is typically it.

---

### Post by Don_Stahl on 2014-02-07
Yep! Good catch, and you're right all along. "Installation finished. No error reported."
 
Looks like Elementary is installed in an extended partition, and it created a swap partition there. I'll deal with that after [FONT=courier new]grub-update[/FONT].

Just playing around. If I have to re-install the OS from scratch it's no big thing on this laptop.

Thanks --

---

### Post by Don_Stahl on 2014-02-07
OK, all that succeeded and the laptop boots to Zorin. 

Now I'm going to try splitting the vacant 100 gb partition and installing Sabayon in one of the 50 gb halves. :P It's a Gentoo fork, and I believe it's happy with ext4...

---

### Post by Don_Stahl on 2014-02-07
Hosed! Sabayon install apparently succeeded, but when rebooting I get:

GRUB loading
loading
loading
loading

and so on.

Next step: boot from live CD and try sudo update-grub... ?

---

### Post by Don_Stahl on 2014-02-07
Nope to updating Grub from the live CD. Might have been able to do it somehow, but beyond my beginner's abilities. So, I reinstalled Zorin. Right now I'm updating the Sabayon installation, then I'll see if I can boot to Zorin as well. 

So, if Sabayon had not installed a bootloader -- one which didn't work -- then I could have booted to Zorin and run [FONT=courier new]sudo update-grub[/FONT] I guess. 

Well, next step for me -- as a terrible newbie -- is to edit /ect/grub.d/40-custom to change default boot entry?

---

