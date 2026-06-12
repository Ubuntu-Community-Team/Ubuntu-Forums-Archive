---
title: "Help install Ubuntu on Mac book pro 3,1 mid 2007"
date: 2015-08-28
forum: Apple Hardware Users
---

### Post by joe178 on 2015-08-28
Hello, 

I am trying to reuse my old MacBook pro. As osx is not supported anymore,  I figured I'd try Ubuntu. I've spent hours on the forums and Ubuntu site to reach about 75% of the way I think. I'm not a programmer/developer etc. 

Current problem: I'm able to install Ubuntu (trusty tahr) from USB but upon rebooting immediately after install I get a purple screen of death. In order for me to be able to perform install,  from either trial version of Ubuntu or "install Ubuntu" I have to make the "nomodeset"  change in grub.  I don't know how to make the nomodeset change permanent on the install despite these instructions [http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

Full story
Initially tried to make a Bootable DVD,  wouldn't work. Used instructions on Ubuntu website and forums to make USB. Didn't think I'd need refit but installed anyway. Made Bootable USB. As I planned to remove osx, on boot, I held the option key,  booted from the orange efi USB icon to trial of Ubuntu. Originally had two error codes (i8042: No controller found AND ACPI PCC probe failed) Used nomodeset fix in grub on USB boot. Installed Ubuntu. (Yay!) Allowed Ubuntu to repartition my computer (probably a bad idea) After the first time I did this I no longer saw the option to boot into osx when holding option key during game boot process.   If I keep USB drive out, screen boots to gray,  then PSOD. If I hit esc key during boot loads to grub but can't do anything. I can type things,  but don't know what commands to type. 

I think I'm close... Any thoughts?  Thanks

---

### Post by asmodeus3 on 2015-08-30
So, what exactly are you doing in grub ?
I believe that, in order to  perform an installation you dont have to set a permanent nomodeset .

It isn't quite clear whether you are trying to reinstall ubuntu or trying to get past the purple screen.

---

### Post by joe178 on 2015-08-30
Thanks for taking the time to look at this post

I've installed Ubuntu, but it is not able to perform a  full restart immediately after I install - that's when I see PSOD.  If I hold esc on boot,  it loads grub but I don't know what to do at that stage. Hopefully that clears things up a bit

---

### Post by asmodeus3 on 2015-08-31
If you can get to grub, then you can edit it to boot with nomodeset. 
Look at the "*How to temporarily set kernel boot options on an installed OS" *section of the forum post you brought up. The steps are straightforward enough and
I think this should't be a problem to you.
This change is only temporal, so you have to make the it permanent from a terminal once you have managed to get past the purple screen and into a desktop.
Excuse me if I'm missing something obvious here.

---

### Post by joe178 on 2015-08-31
So, problem solved.

Earlier, when I went into grub from the boot screen all I saw was a prompt like grub>    - I would not see the prior boot menu where it had me select ubuntu to edit and place the nomodeset command in the linux/boot line

So, on one of my many reboots, when the screen would show gray, then black, then purple; instead of hitting the 'Esc' key as fast as I could hit it as soon as the machine booted up, I only hit it once when the screen changed from gray to black.  When I did that I obtained the full grub menu and was able to make the nomodeset change as previously described, load ubuntu and make the change permanent in terminal using the previously described method.

Thanks for your help!

---

