---
title: "Start up?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-06-04
Hi
When I start up from cold or restart etc, the grub menu appears without my xp choice (which is another story as I cannot get it back!) but also It gives me several ubuntu choices which all differ by a number only and they all seem to give me the same result, which is fine.
Do these "choices" refer to the number of times I may have updated or upgraded or is there another reason. I am slightly puzzled??

---

### Post by lamalex on 2007-06-04
they are different kernel versions, usually pick the top one or the one with the greatest number unless you're having problems

---

### Post by oilchangeguy on 2007-06-04
> **Benbow said:**
> Hi
When I start up from cold or restart etc, the grub menu appears without my xp choice (which is another story as I cannot get it back!) but also It gives me several ubuntu choices which all differ by a number only and they all seem to give me the same result, which is fine.
Do these "choices" refer to the number of times I may have updated or upgraded or is there another reason. I am slightly puzzled??

when you've done automatic updates, every once in a while a new kernel is included. that's what's showing up in the grub menu.

---

### Post by Benbow on 2007-06-04
aaaaahhhh! I see. Thanks for the very prompt answers. 
Final query - will this list continue to grow, or can I delete the earlier ones?

---

### Post by starcraft.man on 2007-06-04
> **Benbow said:**
> Hi
When I start up from cold or restart etc, the grub menu appears without my xp choice (which is another story as I cannot get it back!) but also It gives me several ubuntu choices which all differ by a number only and they all seem to give me the same result, which is fine.
Do these "choices" refer to the number of times I may have updated or upgraded or is there another reason. I am slightly puzzled??

The entries listed in GRUB at boot up are the Kernel versions you have installed. The top one is always the most recent. The second entry is usually always a recovery boot up for that particular kernel version. Usually its in your best interest to use the latest version, which is why it defaults to the top. In the rare case though, there has been unforeseen breakage with certain things, that is why the old kernel is left so you can boot that if you get problems with the newer version. Always boot to latest unless you have a reason not to. Oh and I forgot, memtest isn't important, its a simple ram diagnostic I think...

If you want a better explanation of what exactly the kernel is,[ here you go.]("http://en.wikipedia.org/wiki/Linux_kernel")

Oh and I'm not exactly sure what the problem with your XP entry is, can you elaborate? If its simply missing from GRUB this is a [good guide to editing the menu.]("http://users.bigpond.net.au/hermanzone/p15.htm"). It's advisable to understand it before editing the menu list. If its corrupt or otherwise damaged, maybe its not a simple fix...

Edit: You can remove them once there are too many, simply use Synaptic and search for the old kernel version you don't need.

Second edit: Why does it always seem I write too much? :p.

---

### Post by Dylnuge on 2007-06-04
There is a software somewhere called Start-Up Manager. You can use it to automaticly keep it so that only one Kernal shows (the latest one), in adddition to the Recovery option. If you don't, the list will continue to grow.

Explanations of the options:

1. Kernel-2.6.xx.xxx is your OS
2. Kernel-2.6.xx.xxx-recovery is a recovery mode for Ubuntu. It logs you on into a shell, no graphics, as root.
3. memtest86+. AFAIK, this only appears on Intel and AMD x86 installations. I have never used it, it seems like a startup test.
4. Other Operating Systems-Just what it says it is.

---

### Post by ncappel1 on 2007-06-04
Another document to read is from the feisty guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

---

