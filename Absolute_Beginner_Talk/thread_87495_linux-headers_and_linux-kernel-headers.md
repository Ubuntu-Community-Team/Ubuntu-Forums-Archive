---
title: "linux-headers and linux-kernel-headers?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by victorche on 2005-11-08
Please, someone explain here... Waht is the difference between those two files?
I am talking about these two:
/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb

They are not installed by default... What are they for?
And if I install this one:
/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
Should I upgrade it to 686, as I do with linux-image and linux-restricted-modules?

So, simple questions... I hope to get some simple answers also ;)

---

### Post by az on 2005-11-08
If you need the full source for the linux kernel, install linux-tree - it will give you a full patched and configured linux source tree.

Use the linux-source package if you do not want the defaut config or you need to play around with patches.

Do not use the full source to make modules.  Use the linux-headers package.  You do not need the full source for most kernel modules.  It is much less messier to just use the headers.  Everythig will be set up so that the source for the module will use the linux-headers directory as if it were the full source.  The headers are on the install cd.

linux-kernel-headers are just the libc headers.  They are specific to the linux kernel, but not specific to the running kernel version.

If you are running the 686 kernel, install the corresponding 686 linux-headers package.  The same goes for other arches.

---

### Post by victorche on 2005-11-08
[QUOTE=azz]If you need the full source for the linux kernel, install linux-tree - it will give you a full patched and configured linux source tree.

Use the linux-source package if you do not want the defaut config or you need to play around with patches.

Do not use the full source to make modules.  Use the linux-headers package.  You do not need the full source for most kernel modules.  It is much less messier to just use the headers.  Everythig will be set up so that the source for the module will use the linux-headers directory as if it were the full source.  The headers are on the install cd.

linux-kernel-headers are just the libc headers.  They are specific to the linux kernel, but not specific to the running kernel version.

If you are running the 686 kernel, install the corresponding 686 linux-headers package.  The same goes for other arches.[/QUOTE]
So... I can install the linux-kernel-headers_2.6.11.2 from the CD, no matter that they are not 2.6.12-9? I don't see a different architecture for them... Like i386, i686 I mean.
And if I run linux-image for i686, I shouldn't use this one from the disk:
linux-headers-2.6.12-9-386
Just because it is like the linux-image and the linux-restricted-modules... It is for i386
So I have to update it via apt-get to 686 like I did with image and modules?
Is this correct?

---

### Post by Kyral on 2005-11-08
Source code is Arch independant. What makes a binary dependant on Arch is when its compiled. So you can use any linux-headers pack from the x86 series (386, 686, K7) you want. You could prolly also use AMD64 and PPC (Look at Kernel.org, only one sourceball for everything)

---

### Post by az on 2005-11-08
[QUOTE=victorche]So... I can install the linux-kernel-headers_2.6.11.2 from the CD, no matter that they are not 2.6.12-9? I don't see a different architecture for them... Like i386, i686 I mean.
And if I run linux-image for i686, I shouldn't use this one from the disk:
linux-headers-2.6.12-9-386
Just because it is like the linux-image and the linux-restricted-modules... It is for i386
So I have to update it via apt-get to 686 like I did with image and modules?
Is this correct?[/QUOTE]
That is correct.  linux-kernel-headers should match your libc6 version and linux-headers should match your linux-image version.

---

