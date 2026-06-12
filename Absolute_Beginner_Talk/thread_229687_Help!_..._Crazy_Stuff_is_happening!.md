---
title: "Help! ... Crazy Stuff is happening!"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by ZaneV on 2006-08-04
Hi everyone,

This is question is probabley posted all over this forum and I have done some quick research on it but I can't find anything and I am in kind of a hurry, your help will be very much appreciated.

I have installed Ubuntu Brezy Badger on two systems so far... they were older systems and gave me no problems what so ever. Today I went to run the ubuntu installer disk on my new system (I have posted system specs bellow if it helps). The first ubuntu menu comes up but without the splash screen... I press enter... and it runs through what ever, then it asks for langauge and then country and then keyboard... everything like normal... and then it just sits on a blue screen with a white bar down the bottom which you can type stuff in. I then tried the live ubuntu Cd and it didn't get to the ubuntu desktop either.

Okay, so I thought fair enough... I will try a different linux distro called backtrack which I am also currently fiddling around with. I basicly did the same thing as ubuntu.

I have went into my bios and set the Plug and Play OS option to [YES] and checked out everything else. 

Has anyone encountered this problem before? Like I said I have tried it on older systems and it works fine and I also tried it on another newer system and it also worked fine. Help!

Thanks 

Zane

SYSTEM SPECS:

-Intel P4 3.4Ghz Processor
-512MB Ram
-120.0GB HDD SATA(I will be installing ubuntu on a 80.0GB HDD but that is beside the point)
-Asus Motherboard
-Nvidia Geforce 6200 Graphics card

Other Misc Stuff
-Running Windows XP Pro
-DVD/CD Burner

---

### Post by NeoGreen on 2006-08-04
Are your other computers running on Intel Chips?  There are different Ubuntu installs, one for Intel, and one for Athlon.

---

### Post by Engnome on 2006-08-04
Had this problem on two older computers.

One I got running by installing old breezy in server mode and then dist-upgrade to dapper.

The other by one by adding "install acpi=off noapic nolapic" (something like that anyway, try different options) after pressing escape in the boot menu.

You can also try and disable framebuffer.

Try pressing F4 - F9 at boot menu for more info.

---

### Post by ZaneV on 2006-08-05
I fiddled around with some setting and have found the basic problem now. When I change a setting (i.e acpi=off) or try installing via expert mode it always hangs on [Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'] when detecting hardware. 
When I try to install it just normally, like I said before it hangs on a blue screen with a white bar down the bottom after detecting hardware... I decided to leave it for a bit to see if it got past that and when I returned it had an error message saying that either the cd is not in the cd-rom drive. I have tried tried another ubuntu cd but the same thing happened.

Also the other computers I installed ubuntu on did have an intel processor.

Any more suggestions?

Thanks,

ZaneV

---

