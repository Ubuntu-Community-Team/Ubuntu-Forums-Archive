---
title: "How do I install a video card?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Adjutant on 2006-06-22
Hi, I'm very new to the whole Linux world and now that I've gotten through a bunch of problems trying to install it, I want to install my video onto my PC.

See, I had to remove my video card from my computer because Ubuntu wasn't loading. Now that I have loaded Ubuntu, I want to know how to install it.

I'm not sure how to go about this.

Do I install the hardware first? Or do I download drivers? Do I have to set Ubuntu to the new card? I have no idea. It was pretty hard to do it in Windows because I had to disable the onboard graphics in order to use the new card. I would like some help. I searched around the forums and couldn't find any post that would help me with this specifically. You know, like the really noob questions.

Thanks.

---

### Post by johnc4510 on 2006-06-22
First thing is to let us know what kind of card it is.

---

### Post by Adjutant on 2006-06-22
Right. It's an nvidia GeForce 6200

---

### Post by bruce89 on 2006-06-22
You put the card in first, then worry about the drivers. (I think).  After you install it, and boot up, X probably won't start so do what johnc4510 says below:

---

### Post by johnc4510 on 2006-06-22
To install the correct drivers:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

---

### Post by Adjutant on 2006-06-22
ok, i installed the card, tried to start up ubuntu again and ubuntu just isn't taking it. it's getting stuck again at "Loading hardware drives..."

Am I supposed to do something before I install the card to avoid this?

---

### Post by johnc4510 on 2006-06-22
Installing the card and then installing the driver and configuring has always worked for me, so I'm not sure what the problem is. 
You could try taking the card out then boot and install the nvidia driver without the config enable. Then shut the computer down and install the card. Boot and when X fails, run the config enable. I'm really not sure if that will work or not, but I don't know what else to tell you to try.

---

### Post by Adjutant on 2006-06-22
Doesn't work.....

Ubuntu hates my 6200? :(

I tried installing the drivers first, then putting the card in, then starting it up again, but I get the same problem, it freezes at "Loading hardware drives..."

This sucks... maybe I need to do something besides install the nvidia drivers to get it to work maybe?

---

### Post by johnc4510 on 2006-06-22
See if the linux-restricted-modules that correspond to your kernel are installed, they need to be to support nvidia cards.

---

### Post by Adjutant on 2006-06-22
Alright, so how do I check that? This is my first time on linux, so I don't know how to check or look for most of these things...

EDIT: ok i went thru that synaptics program, and i have installed for 386, as opposed to the 686 that i currently have installed. installing the new things (for the lack of a better word; noob, haha), see if that works

---

### Post by bruce89 on 2006-06-22
[QUOTE=Adjutant]Alright, so how do I check that? This is my first time on linux, so I don't know how to check or look for most of these things...[/QUOTE]
Assuming you can get to the text display, ```
 apt-cache policy linux-restricted-modules-`uname -r`
``` will give the installation status of the restricted modules.
**Edit : I didn't realise that you got to GNOME.**

---

### Post by johnc4510 on 2006-06-22
Okay, go to Synaptic: 
System>Administration>Synaptic Package Manager
Scroll down in the window to:
linux-restricted-modules and see if any are being shown as installed.(the box to the left of it will show green if any are installed)
If none are installed, look just above it at the: linux image and compare the version numbers to choose the correct restricted module.
An example would be this:
linux-image-2.6.15-25-386
So for the restricted module, you would choose:
linux-restricted-module-2.6.15-25-386
See how the numbers correspond?

---

### Post by Adjutant on 2006-06-22
I have mixed stuff installe.

Like i have image and modules for 15-23 for 386 and 686

and also image and modules for 15-25 for 386 and 686

Do I uninstall the image and modules that I don't need and just leave one set? Maybe they're conflicting?

Also, now when I try with the video card, it says "fail" and then it freezes as opposed to just freezing without saying anything, I think I'm making some progress here.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Adjutant]Do I uninstall the image and modules that I don't need and just leave one set? Maybe they're conflicting?[/QUOTE]
You might as well, you'll save 100MB of space, just make sure you are not currently running the one you are about to remove.

---

### Post by johnc4510 on 2006-06-22
You can do that, but they shouldn't conflict as the system will use the last install and configured kernel. What about the restricted image, were any installed? If not, install the one for the 15-25 686 kernel. That's the newest kernel you have installed.

---

### Post by az on 2006-06-22
[QUOTE=Adjutant]
See, I had to remove my video card from my computer because Ubuntu wasn't loading. Now that I have loaded Ubuntu, I want to know how to install it.
[/QUOTE]
It worked with another operating system?

It may be that the hardware does not work with your motherboard without tweaking.  

Linux is not a PnP OS.  Check your bios to see if pnp is dissabled.  If it is enabled, dissable it.  You may also have to allocate the IRQ to a different number.

---

### Post by Adjutant on 2006-06-22
All the correct images and modules were installed already. Now I've removed all the unecessary files and reinstalled the nvidia glx.

Unfortunately nothing happened.... Now it doesn't even say "fail" anymore, just freezes. :(

All the corresponding files are installed. I made sure I didn't remove any good files, checked about 3 times.

[QUOTE=azz]It worked with another operating system?

It may be that the hardware does not work with your motherboard without tweaking.  

Linux is not a PnP OS.  Check your bios to see if pnp is dissabled.  If it is enabled, dissable it.  You may also have to allocate the IRQ to a different number.[/QUOTE]

Yes, it did work with Windows XP when I had it installed, ill try that, thanks

---

### Post by Adjutant on 2006-06-22
Ok, this is what happened now.

I put my card back into my computer.

Then I went to BIOS to check the Video Configuration, it was set to Auto, so I changed it to the intel on-board graphics.

I was able to load Ubuntu now, even tho I still had my video card inside. I then went to the Terminal and put this in: ```
sudo nvidia-glx-config enable
```

Ok, so now I should be able to use my video card, right? Ok, then I went back to BIOS and changed the vid config again so that it would load up my video card. But no, that didn't do anything.... still getting frozen up at the much dreaded "Loading hardware drivers..."

So now I can't use my video card, nor my on-board graphics because I enabled nvidia-glx-config.

Can anyone tell me a command so that I can enable my on-board graphics now? I don't know how to revert back....

---

### Post by az on 2006-06-22
[QUOTE=Adjutant]Can anyone tell me a command so that I can enable my on-board graphics now? I don't know how to revert back....[/QUOTE]
Re-enable the onboard graphics, boot into recovery mode and type

dpkg-reconfigure -phigh xserver-xorg

and that will config things properly.

Before you do that, try adjusting other bios settings, in regards to onboard devices or your added video card.  This is not a driver issue this is a hardware conflict.  The kernel cannot handle the hardware.  If this were a video driver issue, you would be booting into the command line.

---

