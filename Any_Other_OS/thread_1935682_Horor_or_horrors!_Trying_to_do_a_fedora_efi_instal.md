---
title: "Horor or horrors! Trying to do a fedora efi install..."
date: 2012-03-04
forum: Any Other OS
---

### Post by ClientAlive on 2012-03-04
Not getting any love on the fedora forum or the irc channel and not finding any clear cut information on how to do this. I've tried several methods, unsuccessfully and seem to keep running into a wall. I've read thier install guide from the first page throught to the end of section 10 as well as section 15 but the information seems to be incomplete or I'm just missing what I need to know.

Tried livecd-iso-to-disk. The option "--efi" gets me an error in the shell.

Tried making the minimal install media on a usb, followed section 3.3.1 instruction using dd. The usb boots but what I'm faced with is a "grub>" line which I don't know what to do with and I'm not seeing instructions on what to do from there or even if that's what is supposed to happen.

Can anyone, for the love of god and all that's good, please help?

Sorry to vent a little frustration here. I would sincerely appreciate some help if anyone can do it.

Thank you
Jake

---

### Post by cpatrick08 on 2012-03-04
you can make put the iso on a usb stick using unetbootin

---

### Post by r-senior on 2012-03-05
+1 for unetbootin

Use the [instructions](http://unetbootin.sourceforge.net/#other) for 'Installing other distributions' if you want to make a USB from the Fedora 16 ISO.

Making a Fedora live USB is harder than installing it! ;)

---

### Post by ClientAlive on 2012-03-05
> **cpatrick08 said:**
> you can make put the iso on a usb stick using unetbootin

> **r-senior said:**
> +1 for unetbootin

Use the [instructions](http://unetbootin.sourceforge.net/#other) for 'Installing other distributions' if you want to make a USB from the Fedora 16 ISO.

Making a Fedora live USB is harder than installing it! ;)



You know what's funny? I actually did that about 4 days ago and what I ended up with was an msdos partition table and some kind of funky mbr installation. Only about 2/3 of my disk space was being recognized but it was a working installation.

Right now, I mean like right this min, I'm working on another install (it'll take a while - one of my raid devices will take aprox another 7 hrs to complete). Perhaps I could share my plan because I'm not really sure if it will work or not.

Here's what I thought I would try:

1) Manually partition the 3 disks using gpt partition table, create my raids, create my lvm

2) Do a fedora install but when I get to that option, to select for it not to install a boot loader at all - hopefully it will do everything else except install a bootloader. (Apparently there actually is an option during the installation process to not install a bootloader).

3) Recompile the kernel, adding the patch for efi_stub

4) Manually move the kernel into the efi system partition and rename it accordingly

5) Add the boot entry to my firmware - how this is done I have no clue at the moment.

Hopefully upon reboot it would just fire right up but I'm not sure.

How does that seem? Are there any other things in a fedora linux system that need to know where the kernel is? Any config file/ files that need edited?

Alternatively, perhaps I could follow the same steps but where you see the word "kernel" replace that with the word "grub2" or the modified grub that fedora has. This could be a plan b for me.
---------------------

Edit:

Regarding this unetbootin thing (and efi vs mbr in general). Apparently, when it comes to a fedora install, you have to get the installer booted by efi as opposed to anything else. That's the only way to end up with an efi install. This has been the crux of my problem - getting it to boot that way. It's convoluted and complicated and I think fedora happens to be having a lot of problems with efi right now. Now, with the plan I outlined above, perhaps that will be a hack that will work for me and maybe even get me something really cool - efi_stub. I'd still like to get all the feedback I can on that idea though. There's just too much I don't know.

---

### Post by ClientAlive on 2012-03-06
Guess I'm on my damn own. Again.

---

