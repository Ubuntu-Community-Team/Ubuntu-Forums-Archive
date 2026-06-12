---
title: "[SOLVED] Dual Boot Startup Options"
date: 2008-03-19
forum: Apple Intel Users
---

### Post by Sweet Mercury on 2008-03-19
I recently installed a new, large HDD on my MacBook, with a fresh "from scratch" install of OSX. I partitioned off 15 GB of my hard disk, named it Ubuntu, and that was that. OSX formatted the smaller partition as HFS+ b default, but I can reformat it with GParted (Or the installer) no problem.

My question is, when I install Xubuntu to this partition, will it install GRUB to my machine? Considering the easy boot options on Macs it seems unnecessary and, ultimately, ugly.

Can I avoid GRUB and just use the Option boot to choose which partition I want to boot up like I do now with install CDs?

Thanks.

---

### Post by cyberdork33 on 2008-03-19
your live cd still has a bootloader... That is the initial menu you see..

to be more to the point, no. you need a bootloader to load the kernel. There are themes/skins for grub though to make it look better.

---

### Post by Sweet Mercury on 2008-03-19
> **cyberdork33 said:**
> your live cd still has a bootloader... That is the initial menu you see..

to be more to the point, no. you need a bootloader to load the kernel. There are themes/skins for grub though to make it look better.

Sorry, that's not quite clear to me.

Is the GRUB screen the bootloader?  Will it make my MacBook default to that as the primary boot up screen?

---

### Post by cyberdork33 on 2008-03-19
> **Sweet Mercury said:**
> Sorry, that's not quite clear to me.

Is the GRUB screen the bootloader?  Will it make my MacBook default to that as the primary boot up screen?Grub is a bootloader yes. I have no idea what you mean in your second question. Grub is the deafult bootloader for Ubuntu, and is required to load the Linux kernel. You do not use grub to load OS X or Windows (though it can do that too).

---

### Post by sooperhooper on 2008-03-19
Have you installed rEFIt, or something like it? That's what I use with my setup. I get the nice eye candy visual loader, giving me the choice between OS X and Linux. If choosing OS X, it just boots right up as usual; choosing Linux makes it go to the GRUB screen, which loads Linux. As cyberdork pointed out, you can dodge the ugly white-text-on-black bootloader screen, replacing it with something less bland, if that's your sort of thing; if you don't care how it looks, then you're set. GRUB will not interfere with how you boot OS X in any way whatsoever.

Do you also have a partition you intend to use for Windows? If not, you're good to go. If so, you just have to be careful to avoid a loop in your loader (where GRUB gets on your Windows partition, and choosing to boot Windows loads GRUB, and choosing Windows from the menu simply brings up the boot loader over and over again ad infinitum...) - if this is your plan, I'll let the more experience pros on here help you avoid that issue, as it's thwarted me enough times as it is.

---

### Post by Sweet Mercury on 2008-03-20
> **cyberdork33 said:**
> Grub is a bootloader yes. I have no idea what you mean in your second question. Grub is the deafult bootloader for Ubuntu, and is required to load the Linux kernel. You do not use grub to load OS X or Windows (though it can do that too).

I must be a true n00b here, I thought GRUB was the text screen that allowed me to choose which Linux Kernel to load, or I guess that's what a bootloader is. Just goes to show how piecemeal my knowledge is.

Let me be a bit more descriptive. When I had my Dell laptop, it came preloaded with XP. I turned it on and it went through the motions to boot up XP. When I installed Ubuntu, it partitioned the drive, and from then on when I booted the machine it would *first* show me the GRUB screen with a list of Kernels to load, and it also gave me the option to boot into Windows, not the default.

When I boot up my MacBook, I get a light grey screen, followed by an Apple logo, and then I'm in OSX. Now, if I holt the Option key when I turn the power on (or restart) I instead get a nice list of boot options, I can boot into OSX via the "Macintosh HD" partition, or from a CD (which is how I've been testing out Xubuntu), etc. I still want that, not some text screen. That's all. When I boot into OSX I want it to be the same as it is now.

I don't care if I get that GRUB screen after I choose the Ubuntu partition.

SooperHooper, I don't have a partition for Windows, nor do I plan on running Windows on this machine if I can avoid it. I'm not sure what rEFIt is? But it sounds interesting. You have a link to a software page or will it be available through apt when I install Xubuntu.

I think that, despite my confusion, you've all answered my question. Thanks for your patience.

---

### Post by cyberdork33 on 2008-03-20
Ok, you want rEFIt.

rEFIt basically is a nice boot menu that lets you choose between OSX and Ubuntu and is displayed on every boot (not just by holding Option). I thought you were saying that you wanted to use the Option-boot method... Either way, in a round-about way, we did answer your questions...

PS the text menu you see when booting Ubuntu is grub. I was suggesting that you can "theme" it so that it looks better than it does.

---

### Post by Sweet Mercury on 2008-03-20
> **cyberdork33 said:**
> Ok, you want rEFIt.

rEFIt basically is a nice boot menu that lets you choose between OSX and Ubuntu and is displayed on every boot (not just by holding Option). I thought you were saying that you wanted to use the Option-boot method... Either way, in a round-about way, we did answer your questions...

PS the text menu you see when booting Ubuntu is grub. I was suggesting that you can "theme" it so that it looks better than it does.

Alright, I actually do want to use the Option-boot way, so I'll skip rEFIt for now. I'll be installing Xubuntu to my drive today, I think.

Thanks. Can a mod mark this "resolved" then?

---

### Post by cyberdork33 on 2008-03-20
> **Sweet Mercury said:**
> Can a mod mark this "resolved" then? You can since you are the OP. The option is under Thread Tools at the top.

---

