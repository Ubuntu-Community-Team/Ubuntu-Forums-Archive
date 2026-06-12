---
title: "Can I replace my old Linux with Ubuntu?"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by amrust on 2005-07-13
Hello everyone. This is my 1st post!  \\:D/ 

I tried the Ubuntu Live CD, and I absolutely loved it! It detected everything flawlessly, from what I recall. I have a few questions, before I possibly install Ubuntu permanently on my IBM Thinkad R50 laptop... (yay!)

Currently, I have a Windows XP Pro and Fedora Core 4 *dual boot* setup (GRUB), on the same 40GB physical disk, partitioned 20GB for Windows XP, and the other 20GB for Linux. I want to delete all the Linux partitions, but keep Windows XP partition safe, so I can boot from it, and use it to download anything I may need while reinstalling any Linux stuff.

I would consider trying a Ubuntu full install, on the other (non-Windows) portion of my laptop HDD. My questions:

1. Is it possible to delete the Linux partitions completely, and leave Windows XP partition bootable from the HDD, like before I installed Fedora? Would deleting Linux (and thus, GRUB) make Windows XP partition unable to boot? 

2. I'd like to dual boot Windows XP and Ubuntu, if possible? Does Ubuntu "play nice" in a dual boot environment with Windows XP Pro? 

3. How do I safely delete my old Linux OS, and still be able to boot Windows XP in the meantime, until I get Ubuntu up and running?

I'm relatively new to Linux, but eager to learn. Please help me out, if you have the time. Thanks in advance, and I look forward to joining the Ubuntu family!

---

### Post by flak9 on 2005-07-13
Hello fellow Hoosier.  You should be able to boot off the install cd for ubuntu and when you get to the partitioning part, just install over your linux partitions that you already have.  I would reformat the linux partitions.  It should boot just like it used to!

---

### Post by aysiu on 2005-07-13
It's a lot easier than you think. Pick manual partition setup. Since it's all prepartitioned, all you do is select your FC4 partition as the one you want to reformat as ext3 filesystem with a / mount point (/ for root). Then, make sure you install Grub on the MBR. Ubuntu will most likely recognize your Windows partition for dual boot.

Then, you're all set.

---

### Post by Seti on 2005-07-13
You should be able to delete the linux partitions and still be able to boot windows, given GRUB is installed in the MBR. So you should be OK. Just use GRUB as you normally would to start windows.

Once you are ready for Ubuntu, install it to any free space you have left over from the deleted linux partitions, and reinstall GRUB, again to MBR. Ubuntu will pick up the windows partition and add it as a booting option to the menu.

---

### Post by amrust on 2005-07-13
Hey, responses already! Very Cool! I am encouraged by this. :)

If I still need to use GRUB to boot Windows, will it remove the entries for the 2 Fedora kernel boot options, leaving me with only one option, Windows XP Pro? At least until I get Ubuntu installed, that is?

And is there any problem with using GRUB from a Fedora install, to boot my system? Or will Ubuntu's GRUB replace it completely, once I get it installed on the HDD?

Sorry for being redundant, if I am. I just want to be careful and not screw things up so I can still use Windows, until I finish my transition, LOL.

---

### Post by aysiu on 2005-07-13
> You should be able to delete the linux partitions and still be able to boot windows, given GRUB is installed in the MBR. So you should be OK. Just use GRUB as you normally would to start windows. I don't know that this is true. Grub is installed on the MBR, but the Grub config files all reside on the FC4 partition (/boot/grub/menu.lst, for example). I wouldn't delete FC4 before installing Ubuntu.

> And is there any problem with using GRUB from a Fedora install, to boot my system? Or will Ubuntu's GRUB replace it completely, once I get it installed on the HDD? Ubuntu's Grub will and *should* replace it. It's a lot cleaner that way, trust me.

---

### Post by amrust on 2005-07-13
OK, I installed Ubuntu, and it lists Windows XP in "other operating systems" in GRUB, but when I try to select Windows, it gives a blue screen with "unmountable boot volume"

Any way to fix, or would I be better off just completely wiping entire disk, reinstalling Windows XP, then reinstalling Ubuntu?

*Edit: maybe since my question has changed, I better go to the appropriate thread for follow-up discussion. This appears to be a Dual-Boot/GRUB issue, now. I had to delete the Linux partitions. But good news is, I was able to get XP booting again with fixmbr. I'll try reinstalling Ubuntu again, see what happens. *

---

### Post by Nimefurahi on 2005-07-13
And how did your reinstallation of Ubuntu go this morning? Can you dual-boot XP Pro & Ubuntu?

By the way, welcome to the Ubuntu community! This is your home and we are your family.

Nimefurahi

---

### Post by Umbra on 2005-07-14
> OK, I installed Ubuntu, and it lists Windows XP in "other operating systems" in GRUB, but when I try to select Windows, it gives a blue screen with "unmountable boot volume" 

Stranges thing.
When you installed Ubuntu, did you formated your FC4 partition?

Give us more info, you start your pc, then grub boot menu appears and you select WinXP PRO, then it happens what you describe above, isn't it?

If you choose Ubuntu everything is ok?

---

### Post by amrust on 2005-07-14
Yes! Thank you!

What I did to get it to work, in a nutshell:

*0. Upgraded BIOS on Laptop
1. Deleted all partitions on HDD
2. Installed Windows XP Pro
3. Did basic XP setup and configure
4. Installed Ubuntu 5.04
5. GRUB installed to MBR
6. Success!!

Note step #0... I think that may have been the key. Anway, so far my Ubuntu and XP are coexisting, and things are fine on each OS. I upgraded a few packages with Synaptic, and installed and configured Firestarter firewall. 

I'm having a few minor issues using Ubuntu. I can't get Firefox to "Install missing plugins" with the button at the top of the browser page, it downloads the Flash plugin, but then reports "Failed". But that's probably a just software (or learning curve) issue with Firefox, and I've searched through the forums here looking for solutions. I see a lot of threads on it, but none of the suggestions listed worked for me. I'll try to do some more digging, maybe on the Mozilla forums (I used to be a moderator there). If anyone has any ideas on how to properly install plugins, feel free to post or PM me.

But I have my Fedora replaced with Ubuntu, things are good. I love this OS, and if I can get the Firefox issue resolved, and figure out how to add a Launcher button for Mozilla, I'll probably switch to Ubuntu for my main OS. I'm glad to be a part of the community here! Thank you to everyone, for making me feel welcome. :)

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=amrust] If anyone has any ideas on how to properly install plugins, feel free to post or PM me.
[/QUOTE]

In synaptic.

---

### Post by amrust on 2005-07-14
Yeah, I found [This link in the Starter Guide](http://ubuntuguide.org/#jre) . Instead of sudo apt-get, I can probably just search Synaptic for the packages, and install them that way.

I still wish the internal Firefox method of adding plugins from inside the browser worked for me. Then again, once the missing extensions are installed, that little button at the top of the browser will no longer taunt me, LOL.

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=amrust]
I still wish the internal Firefox method of adding plugins from inside the browser worked for me.[/QUOTE]

Unfortunatly lack of something like an exe in Linux make things like that difficult.

---

### Post by amrust on 2005-07-14
You know what? I just realized that's what was happening, while eating my lunch... how silly of me. It was right in front of my face the whole time! ](*,) 

Ok, thanks for the reality check... At least everyone is getting to know me, and to see how haphazard I am, LOL. I've extended this poor thread beyond what it was supposed to be about, so I'll move other questions to the appropriate threads.  :p

---

