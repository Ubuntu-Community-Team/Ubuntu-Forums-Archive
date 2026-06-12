---
title: "Bios and battery"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by sir4taye on 2008-02-18
Model: Presario f700 (f730us)
Processor: amd64 tk-55 1.6Ghz
Wireless Card: Broadcom 4311 mini-pci
Graphics Card: nVidia GeForce 6100 (64Mb shared mem)
Gutsy 7.10
Boot Parameters: noapic nolapic

My battery is no longer used as a power source for my notebook. I cannot start from battery and if I unplug while using it dies. This is constant through all three (xp/vista/ubuntu) distro's I have installed on my notebook. This power problem happened after I finally got my wireless working with ndiswrapper. I'm worried about my warranty with ubuntu installed and whether or not linux modifies bios as a normal install proceedure? Thanks.

PS. I will abandon completely M$ as soon as I finish this term of school.

---

### Post by paultag on 2008-02-18
Ubuntu does not modify the BIOS. Check some simple things: does the battery still hold a charge?  Does the battery charge with the power supply in?

And as far as I know, Ubuntu voids the manufacturer's warranty about as much as a text file will. You are all set.

Cheers,
Tag

---

### Post by seventhc on 2008-02-18
what's the output of this command
```
acpi
```
Do this when the battery is in, even if your still plugged in.
you can also do
```
acpi -V
```

---

### Post by sir4taye on 2008-02-18
thank you. I was running on some fear when I posted this morning, thank you for helping me. I ran the codes in terminal and this is the out put:

acpi
    Battery 1: charged, 98%, rate information unavailable.

acpi -V
    Battery 1: charged, 98%, rate information unavailable.
    Thermal 1: ok, 32.0 degrees C
 AC Adapter 1: on-line

Get back to me if you can help me further.

I took a linux class last term after using ubuntu for 6 months or so, and was not as impressed with fedora 6. Why can't they use Ubuntu? I also just got an Ubuntu bible, but have yet to crack it because these forums are so helpful. 
Putting terminal commands and processes in simple step by step for us noobs is very encouraging. As I learn, I will do the same (I already have with the ndiswrapper settup for broadcom 4311).

---

### Post by paultag on 2008-02-18
> 
Battery 1: charged, 98%, **rate information unavailable.**


Humm. It looks like a busted battery to me, anyone else have thoughts on this?

Cheers,
Tag

---

### Post by seventhc on 2008-02-18
when I run acpi I get
```

 Battery 1: charging, 95%, 00:00:11 until charged

``` so maybe it is your battery.

---

### Post by seventhc on 2008-02-18
I was actually surprised that it even showed you as having a battery.
I didn't expect it to see it if it's broken.

---

### Post by Joshgray on 2008-02-18
Hope someone can help me with a similar problem. My Lenovo Z61t all of a sudden cannot run off battery. The battery will not charge and when AC power is disconnected the laptop turns off. 

acpi -V gives:
Thermal 1: ok, 44.0 degrees C
Thermal 2: ok, 41.0 degrees C
AC Adapter 1: on-line

acpi -s gives:
Battery 1: slot empty

Of course, there is a battery in slot 1. 

Power Manager shows the battery always at 0% charge.

This laptop is really very new and everything was working great until this happened. I have no idea what changed to cause it either. I am a newbie so I don't attempt changing many system things.

I am running Gutsy Gibbon with KDE for windows.

Thanks for the help.

EDIT: giving acpi command returns nothing, but it takes a long time to do that

Josh

---

### Post by igknighted on 2008-02-18
Forget what linux sees... this happens in the BIOS.  I would suggest (if you can live without your laptop for a few weeks... I know I couldn't) taking the laptop back to where you bought it for service.  If you complain enough, since it is under warranty (or should be... thats a recent model), you might be able to get a loaner for the meantime.

---

### Post by Joshgray on 2008-02-18
This laptop was bought for me by my department which refuses to even hear the word linux. If I bring it to them they will 'fix' it by reimaging XP back onto it. Which would probably fix the battery issue, but not much help to me otherwise.

The only power options in BIOS setup is something about balanced or unbalanced CPU something or the other. Nothing to help with this.

Everything was working great with Ubuntu until I closed the lid to hibernate one day, a few hours later I have this issue. I had zero problems with the battery before.

Why wouldn't the battery in the bay be 'seen' by ubuntu?

---

### Post by JoshuaRL on 2008-02-18
Well, I hate to say it but maybe you should let them do whatever it takes to fix it.

But just make sure you use [Remastersys](http://www.remastersys.klikit.org/) beforehand, plus back up all your important info so you can reinstall how you want it.

---

### Post by paultag on 2008-02-18
> **Joshgray said:**
> 
Why wouldn't the battery in the bay be 'seen' by ubuntu?

It my not be seen. Again, check the BIOS for info on the battery.
this could be as simple as the flash memory in the battery ( yes they have some ) returning bogus info. I have ran into this once before, however I have never seen it on a Linux Box.

My feeling is that if this problem is across all of the OS'es on his multi-boot box, then this is a hardware issue.

I would check by borrowing a friend's battery, and testing to see if it will run off of that. I doubt severely that Ubuntu wrote anything to the BIOS, most of the time the BIOS is locked into Read Only, or completely not accessible to the OS ( pre ACPI, I think ).

Give another battery a try, and if that fails, I think it must be a MoBo issue, but it can't hurt to try to reinstall Microsoft. *shudder*

Cheers,
Paul

---

### Post by paultag on 2008-02-18
> **Joshgray said:**
> Hope someone can help me with a similar problem. My Lenovo Z61t all of a sudden cannot run off battery. The battery will not charge and when AC power is disconnected the laptop turns off. 

acpi -V gives:
Thermal 1: ok, 44.0 degrees C
Thermal 2: ok, 41.0 degrees C
AC Adapter 1: on-line

acpi -s gives:
Battery 1: slot empty

Of course, there is a battery in slot 1. 

Power Manager shows the battery always at 0% charge.

This laptop is really very new and everything was working great until this happened. I have no idea what changed to cause it either. I am a newbie so I don't attempt changing many system things.

I am running Gutsy Gibbon with KDE for windows.

Thanks for the help.

EDIT: giving acpi command returns nothing, but it takes a long time to do that

Josh

My old laptop got this issue, The MoBo stoped sending power to the Batt, and thus never charged it. I think you are SOL on this buddy, sorry :(

Cheers.
Tag

---

### Post by Joshgray on 2008-02-18
EDITED: questions answered while I typed a long whining post

Thanks guys, I will try another battery and then install Windows if it doesn't work... ouch.

---

### Post by paultag on 2008-02-18
> **Joshgray said:**
> This is amazing, several folks have this problem and the solution from the Ubuntu lovers and developers is to... install Windows? Sorry, just frustrated... shutting down and restarting the computer everytime I want to move to the other room is a real pain. I have always received such great help on these forums, I'm surprised that no one has a clue about this one. 

How would my BIOS get messed up? Anyway to restore it to working settings? There are very few options available in the BIOS setup.

Why is there is the battery no longer recognized as being in the slot, but it displays in power manager as being 0% charged?

Wouldn't this be an acpi problem?

Thanks for being so helpful to a frustrated n00bert

josh

Josh,
I understand your frustration, and I share it. Your BIOS might be fine, and this is not a Linux issue with your laptop, this is a different issue. Your battery reads 0% whereas the other reads as about 90%. Read my post on your issue, I think that it is a MoBo or Battery issue, not Ubuntu or BIOS.

Cheers,
Tag

---

### Post by Joshgray on 2008-02-18
I apologize again for whining like a child. This forum has been nothing but incredibly helpful, courteous and prompt.

Thanks guys and keep up all the great work.

Josh

---

### Post by seventhc on 2008-02-18
I would also try booting from the live cd and see if that works. If Ubuntu was using it before and then it stopped...maybe something got changed so using the live cd would help determine that. I am sure if XP would see it, then so would ubuntu. I think think it's most likely a hardware failure. But If the live cd can see and use it, at least now we know it is a setting somewhere.

---

### Post by Joshgray on 2008-02-18
Thx seventhc, I will add that to the list of things to try tomorrow (liveCD in my office)

Josh

---

### Post by JoshuaRL on 2008-02-18
My suggestion wasn't so much "install Windows" as it is to let the IS department do whatever they want to fix your laptop.  If you use remastersys to backup your system then you can reinstall even if they decide to reinstall Windows.

---

### Post by paultag on 2008-02-18
i'm not going to push this anymore, but I would strongly suggest taking a look at the Battery. 

It is not unheard of to have the electronics governing the battery (the flash banks that hold info such as the mfg'r etc) to break. This would account for the failure across all OS'es, as well as the odd ACPI reading.

I would check this by looking at the battery information from the BIOS. You eliminate all points of failure that you can. Instead of ACPI --> /proc/ --> kernel --> hardware level, you check BIOS --> hardware level. If your BIOS can not read basic info such as mfg'r, or the fields come up blank or changed, I would look into your battery.

Cheers,
Tag

---

### Post by sir4taye on 2008-02-19
OK, my guess is that his batteries broken and that I have internal hardware issues. Reimaging back to windows won't fix a dead battery. 
Am I wrong? 
And, should circuit city help me due to compaqs warranty? 4 months?

---

### Post by paultag on 2008-02-19
> 
OK, my guess is that his batteries broken and that I have internal hardware issues.

I would try to find a matching battery, and see if it really is a Battery Issue. I am about 90% sure this is it.

> 
Reimaging back to windows won't fix a dead battery.
Am I wrong?

Nope. Windows wont do anything.

> 
And, should circuit city help me due to compaqs warranty? 4 months?

Ask and see if they can fix it under warranty. If they give you any BS about Linux voiding warranty, ask too see where it breaches the contract: they can not dictate what goes on to your had drive.

---

### Post by JoshuaRL on 2008-02-19
> **paultag said:**
> Ask and see if they can fix it under warranty. If they give you any BS about Linux voiding warranty, ask too see where it breaches the contract: they can not dictate what goes on to your had drive.

Nice.

And true to boot.

---

### Post by MikeSz on 2008-02-19
In my experience, if there is a harware fault then the software that is installed, be it XP, Linux or whatever else, then it wont make any difference.  If your battery has gone, then no one can blame you for the software you have installed as it is likeley to have made no difference at all - its not the kind of component that would have been affected

---

### Post by paultag on 2008-02-19
> **MikeSz said:**
> In my experience, if there is a harware fault then the software that is installed, be it XP, Linux or whatever else, then it wont make any difference.  If your battery has gone, then no one can blame you for the software you have installed as it is likeley to have made no difference at all - its not the kind of component that would have been affected

Agreed.

---

