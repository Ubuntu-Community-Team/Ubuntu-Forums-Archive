---
title: "Macbook Pro 5,3 - Ubuntu install won't boot"
date: 2014-02-10
forum: Apple Hardware Users
---

### Post by aradick2 on 2014-02-10
Hello everyone,

I am attempting to install Ubuntu 12.04.4 on my Macbook Pro 5,3.
I created a live usb using dd, but on my mac it boots to a grub screen giving the options "Try Ubuntu" or "Install Ubuntu" or "Check disk for errors." (Unlike in my PC where it just boots right up into a UI screen with just "try" or "install"). After selecting any of the three options the screen goes black and nothing happens.
I tried again, burning the image to a DVD and the same exact thing happened.

What do I need to change?

Thanks!

[Solution: boot with parameter nomodeset]

---

### Post by n5jyk on 2014-02-10
I think you have enough machine there to try the latest release. Since you have, or at least your computer shipped with, 4G of RAM or more you *might* find the 64bit version to be a better fit. You have the final say in that.  Give the Ubuntu 13.10 a try before giving up. If it will run on an Atom n270 (not a speedster however) it should do just fine on your MBP.

---

### Post by aradick2 on 2014-02-10
13.10 has the same issue.

After doing some research I believe it is related to the Nouveau driver and the nvidia 9600m gt card, but I can't figure out how to do it correctly.

Also: when booting in EFI mode I noticed that the CD gets an error "could not open efi fallback" or something similar (the message is too quick for me to read).
And, I am using the 64-bit :)

---

### Post by zircon_34 on 2014-02-11
Normally, the install will use as default the intel card if Im not mistaken, so this shouldnt be the problem. I tried to install the nvidia driver and then got a problem and couldnt boot anymore into Ubuntu and got the black screen...

Did you install reFind or reFit to boot into linux?

---

### Post by Quackers on 2014-02-11
Trying the nomodeset boot option may be an idea.

---

### Post by aradick2 on 2014-02-11
> **zircon_34 said:**
> Normally, the install will use as default the intel card if Im not mistaken, so this shouldnt be the problem. I tried to install the nvidia driver and then got a problem and couldnt boot anymore into Ubuntu and got the black screen...

Did you install reFind or reFit to boot into linux?

There is no intel card in my MBP, just two nvidia cards (9400m and 9600m gt).

Is rEFInd still necessary to install Ubuntu? It doesn't seem to be necessary for some other distros.

> **Quackers said:**
> Trying the nomodeset boot option may be an idea.

Aha! nomodeset works so far :) I will post/edit with results.

EDIT: It appears to hang after pressing continue on the second ("Preparing to install Ubuntu" with "For best results...:") page. The mouse spins as though it is loading but nothing happens and the DVD drive spins down. I don't have an ethernet cable plugged in - I can't atm but I will try later/tomorrow when I can.

EDIT2: Is it normal for there to be no GUI when booting with nomodeset into the "Try Ubuntu"?

EDIT3: Okay, so I tried everything (including plugging in the ethernet cable) and no dice. Apparently this is a documented bug separate from the initial one. ([http://ubuntuforums.org/showthread.php?t=1701390](http://ubuntuforums.org/showthread.php?t=1701390) and [http://askubuntu.com/questions/204771/ubuntu-12-10-installation-hangs-at-preparing-to-install-ubuntu](http://askubuntu.com/questions/204771/ubuntu-12-10-installation-hangs-at-preparing-to-install-ubuntu)) however, I do not know exactly how to fix/workaround it on a Mac.

For the time being, the problem outlined in the OP is SOLVED.

---

### Post by zircon_34 on 2014-02-12
> [COLOR=#000000]There is no intel card in my MBP, just two nvidia cards (9400m and 9600m gt)[/COLOR]
Ok, didn't know that this model has two nvidia cards. Mine has an intel that works fine, but could not yet install the drivers for nvidia unfortunately... so this is actually the main problem since you cannot even boot the live USB or DVD... My first guess is that you must find a way to load the driver for your default nvidia card in Grub2, but I dont know how to do that... some sudo nvidia current driver on the command line mode?


> [COLOR=#000000]Is rEFInd still necessary to install Ubuntu? It doesn't seem to be necessary for some other distros.[/COLOR]

Can u specify which distro pls?

I think its necessary to boot using OSX EFI mode but don't quote me on that (maybe somebody knows more about that?). At least it makes life easy ;) Have installed dual boot on two macs, one with Ubuntu 13.10 and the other XUbuntu, both work perfectly, and I even have a GPT partition table (no hybrid). Maybe if you install refind and boot your live USB from that it would work, but honestly I dont know. Its easy to install and deinstall refind so maybe its worth the shot or somebody can comment on that? In any case you may have a look at this [thread]("http://www.rodsbooks.com/ubuntu-efi/") if you want to know more. 

Last resort, I also had a similar problem with some distros, like Fedora or OpenSuse, that by the way think are also excellent, but it just loaded a black screen on my specific hardware, so I tried another distro (Ubuntu) and here I am today!

---

### Post by aradick2 on 2014-02-13
> **zircon_34 said:**
> Ok, didn't know that this model has two nvidia cards. Mine has an intel that works fine, but could not yet install the drivers for nvidia unfortunately... so this is actually the main problem since you cannot even boot the live USB or DVD... My first guess is that you must find a way to load the driver for your default nvidia card in Grub2, but I dont know how to do that... some sudo nvidia current driver on the command line mode?

nomodeset worked for me. -- I have a new problem now.

> Can u specify which distro pls?

Fedora at least. I was able to install it on my MBP without touching rEFInd or rEFIt.

> I think its necessary to boot using OSX EFI mode but don't quote me on that (maybe somebody knows more about that?). At least it makes life easy ;) Have installed dual boot on two macs, one with Ubuntu 13.10 and the other XUbuntu, both work perfectly, and I even have a GPT partition table (no hybrid). Maybe if you install refind and boot your live USB from that it would work, but honestly I dont know. Its easy to install and deinstall refind so maybe its worth the shot or somebody can comment on that? In any case you may have a look at this [thread]("http://www.rodsbooks.com/ubuntu-efi/") if you want to know more. 

Last resort, I also had a similar problem with some distros, like Fedora or OpenSuse, that by the way think are also excellent, but it just loaded a black screen on my specific hardware, so I tried another distro (Ubuntu) and here I am today!

Yeah but rEFInd is for the days before EFI support in the distros, at least to my understanding.

---

