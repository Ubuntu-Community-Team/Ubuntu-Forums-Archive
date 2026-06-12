---
title: "Linux has failed to install again!"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-10-10
I've tried linux 3 times, and countless live cd's.
This time knowing that if I installed it to my hard drive and dual booted it would go wrong (as usual) so I decided to use Wubi and try Ubuntu studio.
I have the same problem as I did with Ubuntu 7.04.
X doesn't support my ATI Radeon Xpress 200M Graphics Card, now can anyone give me a step by step guide on how to fix this problem?
I have read that editing the xorg.config file can fix it but first how do I do this and what do I edit?
(BTW im a linux n00b)

Thanks a lot
Sam

---

### Post by Martje_001 on 2007-10-10
Press CTRL+ALT+F1 and install the drivers via the terminal.

---

### Post by Terl on 2007-10-10
What exactly is happening?  You say "go wrong" but not really sure how to help without more info.  Do you get error messages?  Does it even boot?

---

### Post by 900donuts on 2007-10-10
patience young grasshopper with amd open sourcing their ati drivers its only a matter of time till your graphics card is supported in the mean time ask your self these questions
do i have a spare video card?
dose the motherboard have a integrated video card?
do i have a spare computer? after all linux is great at reviving old hardware
could i exchange it(the card or spare computer) for one that is supported at a establishment specializing in computer parts?

---

### Post by SamTyson92 on 2007-10-10
> **Terl said:**
> What exactly is happening?  You say "go wrong" but not really sure how to help without more info.  Do you get error messages?  Does it even boot?

Its a bug that makes X server unable to work which they couldn't fix before the release.
I cannot boot into it no.

---

### Post by SamTyson92 on 2007-10-10
> **900donuts said:**
> patience young grasshopper with amd open sourcing their ati drivers its only a matter of time till your graphics card is supported in the mean time ask your self these questions
do i have a spare video card?
dose the motherboard have a integrated video card?
do i have a spare computer? after all linux is great at reviving old hardware
could i exchange it(the card or spare computer) for one that is supported at a establishment specializing in computer parts?

I have no spare video card.
The mothboard has an intergrated video card (its a laptop)
I do not have a space computer
And no I cannot exchange the graphics card out of a laptop seeing as it's near impossible.

---

### Post by jingo811 on 2007-10-10
> **SamTyson92 said:**
> I've tried linux 3 times, and countless live cd's.
This time knowing that if I installed it to my hard drive and dual booted it would go wrong (as usual) so I decided to use Wubi and try Ubuntu studio.
I have the same problem as I did with Ubuntu 7.04.

Sam

Step away from Wubi and Ubuntu studio and put your hands over your head :) why complicate things even further with 3rd party stuff.
I'm thinking that you have downloaded the wrong ISO cd

[LIST]
[*]Live Desktop CD
[*]Alternate CD
[*]Server CD
[/LIST]

or chosen the wrong Architecture for the download

[LIST]
[*]i386
[*]amd64
[/LIST]

or that you haven't burnt the CD like Ubuntu officially recommends
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)

==============================================================

> **SamTyson92 said:**
> 
X doesn't support my ATI Radeon Xpress 200M Graphics Card, now can anyone give me a step by step guide on how to fix this problem?
I have read that editing the xorg.config file can fix it but first how do I do this and what do I edit?
(BTW im a linux n00b)

Thanks a lot


When you Boot with the Ubuntu LiveCD in order to install Linux choose
**Start Ubuntu in safe graphics mode**
If that wasn't your issue then here's how to mess with the xorg.conf file.


_Applications> Accessories> **Terminal**_
copy and paste the commands that follows the $ sign into terminal.  You probably have to be root to do these things!

[COLOR="Sienna"][SIZE="4"]0.[/SIZE][/COLOR]
$ **cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

[COLOR="Sienna"][SIZE="4"]1.[/SIZE][/COLOR]
$ **nano /etc/X11/xorg.conf**

[COLOR="Sienna"][SIZE="4"]2.[/SIZE][/COLOR]
In Nano editor
**Ctrl+w** ,  
[COLOR="Sienna"]
[SIZE="4"]3.[/SIZE][/COLOR]
type in this when it asks for Search:
**section "device"**
press ENTER.

[COLOR="Sienna"][SIZE="4"]4.[/SIZE][/COLOR]
Then you should see something like this replace value for Driver into "vesa" instead of "ati".
**"vesa"**

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
```

[COLOR="Sienna"][SIZE="4"]5.[/SIZE][/COLOR]
**Ctrl+x**, and save your change.

[COLOR="Sienna"][SIZE="4"]6.[/SIZE][/COLOR]
Then reboot
**sudo shutdown -r now**

See what happens.

---

### Post by Bliepo32 on 2007-10-10
[Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by floke on 2007-10-10
I have a laptop with an integrated ATI Radeon 200M express and it works fine - compiz fusion and all - with no special hacking.

So lets start from the beginning.

What's your PC (make and specs)? And what do you want to do - dual boot?
And which version(s) of ubuntu have you tried to install? And how did you do it - and what happened?

As much info as poss would be good.

---

### Post by SamTyson92 on 2007-10-24
> **floke said:**
> I have a laptop with an integrated ATI Radeon 200M express and it works fine - compiz fusion and all - with no special hacking.

So lets start from the beginning.

What's your PC (make and specs)? And what do you want to do - dual boot?
And which version(s) of ubuntu have you tried to install? And how did you do it - and what happened?

As much info as poss would be good.

My laptop is a Toshiba Satellite A110-162
1.46 GHz Intel Celeron M410 CPU
512MB RAM
DVD/RW
55 GB Hard Drive
400 GB External Hard Drive

I have tried 6.04, 6.10 and 7.04 and I don't want this install to go wrong like the other 3 did.
I did it by installing by the Live cd, and creating a partition to dual boot with XP.

---

### Post by floke on 2007-10-25
First off - make sure you have done ALL of these...

(1) Download the i383 (or x86) architecture (ie NOT AMD64 or anything else!)
(2) Burn at slowest speed possible
(3) Make sure your PC is set to boot from the CD (you might have to set this in your bios)
(4) Verify the burn - select verify CD option  from the menu

Then...

(1) Does the LiveCD run ok as a liveCD?
- if not - what is (not) happening - do you get any error messages?
(2) Does 7.10 work as a liveCD?

If so - what is the problem with installing? What happens when you try to install?
(and make sure you defrag XP FIRST!!)

- you might be better off with the alternative installer (I don't trust the live partitioner at all) - but let's see - we'll know more once we have info on the above.

---

### Post by SamTyson92 on 2007-10-25
> **floke said:**
> First off - make sure you have done ALL of these...

(1) Download the i383 (or x86) architecture (ie NOT AMD64 or anything else!)
(2) Burn at slowest speed possible
(3) Make sure your PC is set to boot from the CD (you might have to set this in your bios)
(4) Verify the burn - select verify CD option  from the menu

Then...

(1) Does the LiveCD run ok as a liveCD?
- if not - what is (not) happening - do you get any error messages?
(2) Does 7.10 work as a liveCD?

If so - what is the problem with installing? What happens when you try to install?
(and make sure you defrag XP FIRST!!)

- you might be better off with the alternative installer (I don't trust the live partitioner at all) - but let's see - we'll know more once we have info on the above.


I've already done all that and the live cd is fine its when I install it, it goes fine until it reboots and then it gives an error message about a problem with the X desktop stuff but 7.10 is said to have a built in feature that will stop it from happening and load to the normal dekstop so it might just work.

I'll try installing it tomorrow with the tips from the thread and post my results,

---

