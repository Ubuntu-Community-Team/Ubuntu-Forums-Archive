---
title: "Successful installation on a Mac Pro (kinda) + graphics issue"
date: 2007-03-12
forum: Apple Intel Users
---

### Post by .bashrc on 2007-03-12
Hey, I've been following progress on Ubuntu (Edgy 6.10) for use on a Mac Pro for some time now. Just wanted to post that I got it successfully running - quite easily, in fact. Ok, this is after sweating and more or less losing an entire 20 GB partition for a few months but whatever ....

I more or less used tips from various forums and the MacBook install wiki page for a general install. 

The major non-wiki tip I had to use was adding the 

irqpoll acpi=force 

modifiers to the install command (Pressing F6 at the initial install screen). This is only because I am using the Pioneer Drive ....

The killer step in that guide is installing the linux ver. of rEFIt just before the Ubuntu install and setting the partition tables BEFORE grub tries to install but AFTER the install begins its partition preparation. 

Ok, so I can probably deal without sound in Ubuntu (just running MATLAB), but the graphics problem is driving me nuts. (I'm finding information hard to find in the primary Mac Pro forum around here, so that's why I was hoping to pose it as a separate issue.)

I even tried installing the nVidia Drivers via apt-get, which looked successful but then screwed up X so hopelessly that all I get are alternating blue and black screens of error messages for X and that DVD drive problem.

Any suggestions as to what might be going wrong?

---

