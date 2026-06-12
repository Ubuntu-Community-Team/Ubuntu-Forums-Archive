---
title: "New Web page: EFI-Booting Ubuntu on a Mac"
date: 2011-01-19
forum: Apple Hardware Users
---

### Post by srs5694 on 2011-01-19
I've mentioned in the past that I've been working on documenting a procedure to get Ubuntu booting on a Mac without using a hybrid MBR or BIOS emulation mode. I've finally got the Web page up:

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

Comments are of course welcome.

---

### Post by pafufta503 on 2011-01-22
interesting.  i was running 9.10 for a little while on my mac pro 1,1.  things were going great until i upgraded to 10.04.  linux would boot to a blinking cursor.  i feel pretty positive that ubuntu's installer is not correctly configured for most mac computers.  this is an issue that really needs to be addressed, as i had stopped using linux all together over my issues with booting.  it also seems a little odd that ubuntu doesn't offer an EFI option that works without heavy configuration.

luckily i've bought this sys76 laptop, so i can live my linuxy dreams again.  i'm going to read through this for a bit and consider putting linux back on my mac.  thanks for doing all that research and writing this up, i'm sure it'll help a lot of mac folks out (just look at the apple section of this forum, seems like every other thread has to do with grub).

---

### Post by linuxopjemac on 2011-01-22
Great I will add a link to your site on mac.linux.be. Thanks for your work.
Edit: [this is the page]("http://mac.linux.be/content/apple-intel-wiki").

---

### Post by srs5694 on 2011-01-22
FWIW, I've just successfully installed Fedora 14 using EFI mode in a VirtualBox session. That gives me more experience with Linux EFI installation. It worked, but required far too many manual interventions that would stump most newbies. The Fedora installer included a native EFI boot on the CD, but it wasn't configured to allow direct booting from the CD! (Copying one file out of an image file on the CD and creating a new CD image fixed that.) For some reason the installation stopped after installing the bare minimum of packages, declared itself done, and rebooted. That forced me to manually install the rest of the packages. The boot loader was a modified GRUB legacy that worked, but it wasn't configured to run automatically, so I had to select it manually from the EFI menus each time. Then I had video problems -- but those were partly due to the framebuffer support in VirtualBox.

I mention all this just to expand on your point about Ubuntu's EFI support being weak, pafufta503; it seems that Fedora's got problems on that score, too, although they're very different from Ubuntu's problems. As motherboard manufacturers are starting to transition to EFI, this will have to change -- and soon!

Thanks for the link, linuxopjemac. It looks like a nice site you've got there. I'll add a link back when I revise my own page.

---

### Post by pafufta503 on 2011-01-22
i just thought of something, most new apple computers have 64 bit processors.  oddly enough the 1st gen mac pro's run in a hybrid 32/64 bit mode, while newer generations run a 64 bit kernel.  most 32 bit cpu apple computers are at least 3-4 years old now right?

---

### Post by srs5694 on 2011-01-22
Yes, something like that. My own Mac Mini was built in 2006 or so, IIRC. It's got a 32-bit CPU and 32-bit EFI. That certainly affects things, since most or all non-Apple EFIs on x86-class computers are for x86-64 and use 64-bit EFIs.

Further complicating matters, Apple uses a variant of EFI version 1.1, whereas most or all PCs with EFIs use UEFI 2.0.

Broadly speaking, the tools exist in Linux to handle both 32- and 64-bit EFIs, as well as all versions of EFI/UEFI, and I was able to get Ubuntu working with the 32-bit EFI in my Mac. Still, a hypothetical properly-written installer would need to be able to handle both types of EFI, and ideally the 32-bit version of this hypothetical installer should work with both 32- and 64-bit EFIs (and CPUs), which is trickier under EFI than under BIOS.

For a platform that was supposed to clear away the gunk of BIOS, EFI has already accumulated a lot of complications.

---

