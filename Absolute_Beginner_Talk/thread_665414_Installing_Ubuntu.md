---
title: "Installing Ubuntu"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by nosushi4you on 2008-01-12
My computer is 2.66GHz, 512 MB RAM, Pentum 4 running Windows XP. I have two graphics cards: a Radeon 7000 and an Intel 82865G Graphics controller. When I run the Ubuntu CD and press "Start or Install Ubuntu", it loads and then a screen comes up and says something about checking battery state. Then little window pops up and says Ubuntu can't detect my graphics cards. No matter how I configure them, or even if I press "Run in low graphics mode" it just goes back to the screen that says "Checking battery state..." along with a few other lines of text. What can I do to get Ubuntu to load? 


Also, how do I dual boot Windows with Ubuntu ? I'm having some trouble partitioning my hard drive. 

Thanks for all the help.

---

### Post by LaRoza on 2008-01-12
Maybe you could remove the card for the install. You can worry about the drivers for it later...

Dual boot with the guides available, [http://psychocats.net](http://psychocats.net)

---

### Post by nosushi4you on 2008-01-12
Which card should I uninstall?

---

### Post by nosushi4you on 2008-01-12
After looking at all the install guides, it seems that once I fix this problem, I should be able to get ubuntu up and running with no problem.

---

### Post by njparton on 2008-01-12
Disable the Intel 82865G Graphics controller in your motherboards bios and use the other one - you shouldn't run both.

---

### Post by nosushi4you on 2008-01-12
How do I disable the controller for that?

---

### Post by nosushi4you on 2008-01-12
I went into my BIOS and I didn't see any options for disabling a graphics card. Should I uninstall it from my Device Manager in Windows?

---

### Post by Waderider on 2008-01-12
This story has a mildly insane solution (that I opted for) but may help you.

My legacy PC has an MSI6198 mainboard and a ATI Rage Pro 128 graphics card. 7.10 won't even run as a live CD. Feisty will run as a live CD, but during install hangs when detecting hardware. 

By a process of elimination I removed the graphics card and installed 7.10 okay. However when I replaced the graphics card the system crashed on boot just after sign in. I was able to partially remedy this in safe mode by running some commands (sudo reconfig X or something similar) but in the end gave up as I couldn't get the card to work in anything other than a low screen resolution.

My solution? Edgy Eft installed straight away, then I updated the system through Feisty to Gutsy via update over the net. All works fine. What I couldn't work out the update process could.

Don't know if that helps but I feel better for sharing it:)

---

### Post by ayenack on 2008-01-12
If I were you I'd uninstall the ATI card by physically removing it from the system i.e. opening up the computers case and taking it out. Then try the install again and if all goes well you'll have to re-install the ATI card and drivers.

---

### Post by nosushi4you on 2008-01-12
I uninstalled my Intel card from the Windows device manager, but still no luck. Do you think the Edgy Eft install will work?

---

### Post by nosushi4you on 2008-01-12
Also, I need my Radeon 7000 for my Windows. I've had the Intel card disabled for quite some time now.

---

### Post by ayenack on 2008-01-12
> I uninstalled my Intel card from the Windows device manager, but still no luck. Do you think the Edgy Eft install will work?

It does not work like that sadly. You actually have to remove the ATI card to start with then re-install it in the computer. Make sure not to boot windows while the card is un-installedthen and when it's re-installed windows will not know any difference.

I'm not sure how experienced you are with computers/Linux but I would advise before you continue to do a lot of research on the net to get an understanding of the issues you may face and the differences between a Microsoft Windows OS and a GNU/Linux OS. If you can afford it I would get on Ebay and buy an secondhand or refurbished computer for £40/$85 and a KVM switch about £10/$22 and install Ubuntu on the Ebay machine and share your monitor/keyboard etc using the KVM switch. Look for one with nvidia graphics card and a least 512MB memory. 2GHz CPU is also preferable but a 1.5GHz should do the trick also.

As for Edgy Eft I don't know I've never tried this before.

---

### Post by dstew on 2008-01-12
The Ubuntu install CD might be having trouble processing interrupts. That might be why you got the "Battery low" signal. You might try to boot the LiveCD with the kernel parameters** noapic nolapic**. Press F6 at the initial menu to edit the kernel line. This will de-activate the programmable interrupt controller. You might get it to boot this way. Once it is installed, you can sort out your video card issues.

---

### Post by limac on 2008-01-12
you don't have to partition your hard drive to install ubuntu, while installing it asks you to resize the other partition and accordingly the size of the new patition is determined

---

### Post by njparton on 2008-01-12
Using device manager to uninstall your intel onboard graphics will have no effect in ubuntu!

Use your motherboard manual to see where to disable it in the BIOS.

It will be called something like VGA adapter, or onboard VGA, or onboard graphics or something like that. It's usually on the BIOS page called integrated components or something similar (with integrated in the title).

---

### Post by ayenack on 2008-01-12
> **njparton said:**
> Using device manager to uninstall your intel onboard graphics will have no effect in ubuntu!

Use your motherboard manual to see where to disable it in the BIOS.

It will be called something like VGA adapter, or onboard VGA, or onboard graphics or something like that. It's usually on the BIOS page called integrated components or something similar (with integrated in the title).

Apparently there's not an option in the BIOS or she/he can't find it to turn off the onboard graphics.

As you said if it's there (which I think it must be) it should be listed with other onboard devices such as sound & network so if those can be found in BIOS that should give an answer.

---

