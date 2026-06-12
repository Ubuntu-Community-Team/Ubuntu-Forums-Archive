---
title: "MP-BIOS: 8254 timer not connected to IO-APIC"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Moyers on 2007-01-11
Hi everyone. I have used ubuntu before on my old desktop and recently it died so I took the oppurtunity to buy a new Dell Innspiron 1501.
 I went to try out Ubuntu 6.06 on this using the live cd to make sure it works and was greeted with the error listed in the title whenever I select anything on the menu, then the screen goes black and disk activity haults. I have tried entering safe graphics mode but this did not help either.
 I tried getting help from the nice people on your freenode channel but they were not able to help either. We were able to narrow it down to that it may be a problem with my graphics card (ATI RADEON Xpress1150 with 256mb) because supposedly ATI support in Ubuntu is problematic. I don't know if Ubuntu will work on my AMD Sempron Mobile either because I have always used Intel.
AM I out of luck or is there anything I could try to get ubuntu working because I love Ubuntu on my desktop and would hope I can get it running again on here.

---

### Post by Moyers on 2007-01-11
Bump

---

### Post by Moyers on 2007-01-11
BumP

---

### Post by Moyers on 2007-01-11
BuMp Come on I can't be the only one with this problem...

---

### Post by qamelian on 2007-01-11
> **Moyers said:**
> BuMp Come on I can't be the only one with this problem...

I get this message on Feisty, but not on earlier versions. I also get it on all versions of Fedora Core since 4. However, it doesn't interfere with booting or using my laptop. Is it possible that this message is just a read herring and the problem might be something else?

---

### Post by Moyers on 2007-01-11
I am not sure. I have relatively low experience in this period of setup and everyone has said it has to be my ati card because it is relatively new. I don't know if I should try out edgy for the purpos of it possibly having the driver. 
What do you guys think I could do because I **MAYBE** could make it to April for the newest Ubuntu, but what are the chances that they actually put the driver for my video card in there even though it is relatively common? What should I try?

---

### Post by Moyers on 2007-01-12
Bump

---

### Post by arielK on 2007-01-14
Although I see this same message everytime I boot-up, I had no issues installing both Ubuntu 06.06 and SimplyMepis 6.0 on my newly home assembled AMD64 Athlon X2 5200+ and Asus Mobo.  Both distros boot-up and run smoothly.  As someone else suggested, you might be on the wrong trail in thinking that this message is related to your other issues.

---

### Post by Squish on 2007-01-15
I have this same problem that I am trying to solve as well. I made a thread in the installing section of the forum, and am too waiting for a reply.
FYI, I did a teeny bit of research, and I thing that the IO-APIC is associated strictly with intel processors, which makes me think my solution is in the fact that I am using the basic ubuntu install, and not the AMD 64 bit specific one... otherwise, i am still wondering...

---

### Post by jjalocha on 2007-04-02
Nope, not strictly an issue with Intel processors, since [my notebook]("http://ubuntuforums.org/showthread.php?t=367898") runs on a Mobile AMD Sempron 3500+, just like the parent poster.

When I try to install Ubuntu Feisty I get the following message just after the initial installation menu (after which it stalls):

```

[  111.237638] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

```

I didn't experience any such thing earlier with Ubuntu Edgy.

Anyone knows what to do?

---

### Post by undertakingyou on 2007-04-03
I get a similar error.  I didn't notice it in dapper, or in edgy kubuntu.  But, I did notice it in Feisty.  I can get it going still even with that message so I don't worry about it.  I only get it on the laptop and that has such strange buggy hardware it is a mirical that anything, even windows, will run on it.

---

### Post by DemaSRV on 2007-04-14
Has this been resolved yet?  I have a 7950GT with an AMD X2 4200+

---

### Post by mid_night gypsy on 2007-04-14
I had this boot error too. You should fine alot of info googling that error,But this is what I did to fix it.
In a terminal:
```
sudo gedit /boot/grub/menu.lst
```
Find the lines....# defoptions ,# altoptions=and add acpi_skip_timer_override...Here is a example from mine.
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi_skip_timer_override
```
Now we need to tell grub(boot manager) to use this new boot option. In a terminal type:
```
sudo update-grub
```
One last thing to finsh it up reboot, I hope this helps,gypsy
P.S. You also could use "noapic" without the quotes,instead of acpi_skip_timer_override

---

### Post by ashmew2 on 2007-12-10
Well i have Edgy 32 Bit installed on an A M D X2 3800+ and i was having the same bug after installing Edgy....Whenever i selected the Edgy Kernel at the boot screen , it gave me this error...
What i did was , i entered the recovery mode and then i was 

root@hostmachine#:

All i did was i typed in "gdm" and pressed Enter...
And Boom! The graphical interface loaded up and its running as great as ever.....If this worked for me , I'm pretty sure it will work for everyone else...Please verify this..

---

### Post by arvinoids on 2007-12-10
I have the same problem on my setup with Gutsy and AMD64 4000+ and nForce MoBo. Gutsy suggests that I add *'noapic'* to the kernel arguments, and I did. Now it works. But the thing is, is there a fix for this other than disabling apic? I worry that there are other effects for disabling apic.

---

### Post by Pgi947 on 2007-12-17
Getting this error everytime I boot up gutsy...Very curious what it means, having major audio issues with gutsy....

---

### Post by coolbrook on 2007-12-17
I see this error every time I boot but it doesn't affect my use of Gutsy.  I should mention that my hardware didn't like a fresh install of Gutsy and didn't want to do the same for Feisty after it initially worked well.  My current machine is built from a fresh install of Edgy, installed all updates, upgraded to Feisty, installed all updates, and upgraded to Gutsy.

---

