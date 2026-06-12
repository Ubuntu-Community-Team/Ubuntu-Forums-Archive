---
title: "Okay, now I'm having another problem (Feisty Fawn, 7.04) - Loading Hardware Freeze"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by esocyn on 2008-02-14
I've just finished installing Feisty on my dad's laptop (Presario F730US). Now that I've done so, I can't boot into Ubuntu all the way. It freezes on "Loading Hardware Drivers".

Has this happened to anyone else? Any help?

Thanks.

---

### Post by jan quark on 2008-02-14
what are your specs?

graphic? memory and so on

---

### Post by esocyn on 2008-02-14
Processor: AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55; 1.8GHz
  	
Display: 15.4" WXGA High-Definition BrightView Widescreen display
  	
Memory: 1024MB DDR2 SDRAM
  	
Maximum memory expansion: 2048MB
  	
Graphics: Nvidia GeForce Go 6100 (UMA) with up to 288MB total available graphics memory
  	
Primary CD/DVD drive: LightScribe Super Multi DVD+/-R/RW with Double Layer Support
  	
Hard disk drive(s): 120GB (5400RPM) SATA Hard Drive

[http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=storefronts&landing=rts_notebook&category=rts_notebook&orderflow=1&a1=Brand&v1=Compaq&product_code=GR967UA%23ABA&catLevel=2](http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=storefronts&landing=rts_notebook&category=rts_notebook&orderflow=1&a1=Brand&v1=Compaq&product_code=GR967UA%23ABA&catLevel=2)

---

### Post by esocyn on 2008-02-14
Bump

---

### Post by stevejesus on 2008-02-14
I know this won't solve your problems but...  why is it that you installed Feisty?

---

### Post by agurk on 2008-02-14
Try removing any connected peripherials, such as usb sticks, mouse, external displays.
Have you tried selecting recovery mode in the boot menu?

---

### Post by esocyn on 2008-02-14
> **stevejesus said:**
> I know this won't solve your problems but...  why is it that you installed Feisty?

I've read that Gutsy is difficult with HP/Compaq laptops, so I wanted to run Feisty first to see how well *it* performs on the computer before I upgraded it.

---

### Post by esocyn on 2008-02-14
> **agurk said:**
> Try removing any connected peripherials, such as usb sticks, mouse, external displays.

I didn't have any peripherials connected to the laptop at any time.

> Have you tried selecting recovery mode in the boot menu?

Yes. That's where I know it's getting stuck.

And, actually, I tried it at some point last night and it booted up all the way through, but afterwards a black screen just popped up. Since then, it's gone back to just freezing at "Loading Hardware".

---

### Post by dhruva023 on 2008-02-14
i think, try gusty.

it works better on my computer then Feisty.

---

### Post by agurk on 2008-02-14
Guessing it's kernel driver related, I'd try experimenting with kernel boot parameters. For example adding the acpi=off parameter.

---

### Post by esocyn on 2008-02-15
> **agurk said:**
> Guessing it's kernel driver related, I'd try experimenting with kernel boot parameters. For example adding the acpi=off parameter.

Sorry for the (probably stupid) question, but how would you mess with the kernel boot parameters when it won't boot into the OS?

---

### Post by agurk on 2008-02-15
No worries, there are no stupid questions. [Here](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)'s a guide that should explain the procedure.

---

### Post by esocyn on 2008-02-15
Cool, thank you. I found a boot order that worked. However, it's opened up a different can of worms.

When I try to edit the menu.lst file, it won't let me. It says I don't have the permission to do so and only opens the file as "Read Only". Any solutions? I couldn't find anything in search.

ETA: NVM, I found it.

---

### Post by ZanexGt on 2008-02-17
[THIS](http://ubuntuforums.org/showthread.php?t=643195&highlight=f730us) thread should answer your questions. You need to edit the boot strings to boot into Gutsy/Feisty properly. Good luck.

---

