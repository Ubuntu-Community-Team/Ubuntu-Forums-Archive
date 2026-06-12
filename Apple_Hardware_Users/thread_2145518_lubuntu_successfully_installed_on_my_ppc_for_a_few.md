---
title: "lubuntu successfully installed on my ppc for a few days... now won't boot"
date: 2013-05-15
forum: Apple Hardware Users
---

### Post by Strat1290 on 2013-05-15
hello, I recently installed Lubuntu 13.04 on my ppc eMac.  it was working great for a few days and really breathed some life into my old machine which I need to use over the next few months.

now, the computer won't boot up and has the 'fixing recursive fault, reboot is needed' error.  I have searched and only can find info about encountering this when first installing from a disk, not for after its been succesfully installed.  I did encounter this when I installed it initially and was able to use the parameters 'live video=radeonfb:1024x768-32@60 snd-powermac.blacklist=yes' and it installed just fine.

I don't know if it was because some updates were downloaded last night... but Lubuntu is already installed.  I've tried entering the same parameters in yaboot but it does not recognize them... any help is greatly appreciated!  I was really impressed with lubuntu and need to get it working again!  I was going to reinstall the OS, but I can't even open the disk drive without the computer booted up...

thanks in advance 
Dan

---

### Post by ajgreeny on 2013-05-15
I am not running 13.04 so I do not know what updates there may have been recently, but I suggest you try booting to a previous kernel, if you have one, from the grub menu, though as it is a mac, I am not even sure if grub is used, and have no knowledge of yaboot.

---

### Post by Strat1290 on 2013-05-15
thanks for your reply, Aj.  I'm a complete noob when it comes to both ubuntu and mac.  could you tell me how to go about booting from a previous kernel?

---

### Post by ajgreeny on 2013-05-15
I'll try but I know so very little about the mac version of ubuntu, and as I said, I'm not even certain if it uses grub; what is yaboot; perhaps a version of grub bootloader used by macs?

Anyway, try holding Shift down when you press the power button on the computer, and you may see a menu with more than one apparent version of ubuntu, plus other "Recovery" modes of ubuntu.  Try using cursor keys to move down to an earlier kernel (not recovery mode) to see if that will boot.  If it does, we can go from there for a hopefully permanent answer.

---

### Post by michiganmac on 2013-05-17
> **Strat1290 said:**
> hello, I recently installed Lubuntu 13.04 on my ppc eMac.  it was working great for a few days and really breathed some life into my old machine which I need to use over the next few months.

now, the computer won't boot up and has the 'fixing recursive fault, reboot is needed' error.  I have searched and only can find info about encountering this when first installing from a disk, not for after its been succesfully installed.  I did encounter this when I installed it initially and was able to use the parameters 'live video=radeonfb:1024x768-32@60 snd-powermac.blacklist=yes' and it installed just fine.

I don't know if it was because some updates were downloaded last night... but Lubuntu is already installed.  I've tried entering the same parameters in yaboot but it does not recognize them... any help is greatly appreciated!  I was really impressed with lubuntu and need to get it working again!  I was going to reinstall the OS, but I can't even open the disk drive without the computer booted up...

thanks in advance 
Dan

When typing boot parameters for an already installed system, you need to substitute "Linux" where you originally used the word "live". Try this at the second boot prompt:

Linux video=radeonfb:1024x768-32@60 snd-powermac.blacklist=yes

Use a capital "L" in the word Linux. The boot screen goes by pretty quick, so type that first "L" right after you see the prompt. Then, you can take your time typing the rest of the parameters.

If this works for you, report back and I can (hopefully) show you how to make the fix permanent. Good luck!

---

### Post by str8bs on 2013-05-17
ajgreeny's suggestion is worth a try as well. PPC uses yaboot which differs a little. Quickly press the tab key when you see the boot: prompt. You should see the options you have and one should have "old" in the name. Type exactly what the option has on the screen to try booting that option.

This is the first I've seen someone report this problem showing up after updates. preventing snd-powermac from loading seems to workaround for most. Some have reported differences between warm and cold boots. Could you try:
At the boot: prompt
Linux single snd-powermac.blacklist=yes
If that gets you to a prompt,
shutdown -r now
Press enter at the boot: prompt to boot normally and see if you still get the error.

---

### Post by Strat1290 on 2013-05-19
Thanks, everyone, for the help.  This did work... and you're right capital 'L'.  For some reason I don't have to enter the "video..." portion, only the "snd..."  Kind of strange.  Sometimes this is not required, sometimes it is. Now if I can just figure out how to get Flash player to work...

---

### Post by michiganmac on 2013-05-19
> **Strat1290 said:**
> Thanks, everyone, for the help.  This did work... and you're right capital 'L'.  For some reason I don't have to enter the "video..." portion, only the "snd..."  Kind of strange.  Sometimes this is not required, sometimes it is. Now if I can just figure out how to get Flash player to work...

Glad to hear you got it working!

There's no linux version of Flash for the PowerPC. There are some add-ons to Firefox for downloading Youtube videos in mp4, but no Flash.

---

