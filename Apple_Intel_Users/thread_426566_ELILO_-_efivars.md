---
title: "ELILO - efivars"
date: 2007-04-28
forum: Apple Intel Users
---

### Post by benanzo on 2007-04-28
I am trying to get ELILO installed on my MacBook Core Duo.  I want to be able to tinker with the EFI boot stuff with efibootmgr but it says:
```
apt-install: Setting up efibootmgr (0.5.3-2ubuntu1)
apt-install: Setting up elilo (3.6-2ubuntu2)
elilo-installer: Couldn't load efivars module - is it statically linked?
```


```
ben@macbook:~$ sudo modprobe efivars
Password:
FATAL: Module efivars not found.
ben@macbook:~$
```

I'm running Feisty 2.6.20-15-generic

I might be wrong but according to [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381584](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381584) the efivars module was added to the 2.6.17 for i386.  Did it not get into Ubuntu or am I missing something?

---

### Post by Gen2ly on 2007-04-29
I've never heard of someone making Elilo work on a MacBook.  I think Elilo was primarily made for SPARC (I think!?) computers.

---

### Post by ronocdh on 2007-04-30
> **Dirk.R.Gently said:**
> I've never heard of someone making Elilo work on a MacBook.  I think Elilo was primarily made for SPARC (I think!?) computers.
It was my understanding that the E stood for EFI; meaning it was LILO built specially for computers with EFI rather than BIOS. Therefore it would be perfectly suited for the new Macs. I personally just use GRUB, though, because I'm lazy. =)

---

### Post by Chrisj303 on 2007-04-30
[http://en.wikipedia.org/wiki/Elilo](http://en.wikipedia.org/wiki/Elilo)

---

### Post by cabdouch on 2007-11-30
I know this is somewhat of an old thread, but I wanted to see if anyone else might have a clue about this.
I am developing an EFI BIOS and using Debian, Ubuntu, and Kubuntu to test with.

I am using elilo to load the initrd.img and vmlinux images. Linux is working almost flawlessly, but it isn't able to load efivars.

In fact during OS installs, should it attempt to modprobe efivars, the process hangs. I can switch to another tty and kill the process which allows the install to continue and finish.

If the OS is installed, then when I try to modprobe efivars I get a Segmentation Fault.

Linux is able to see the EFI System Table as I get a warning that it find version 2.00 and expected 1.00, but then it goes ahead and parses the EFI System table and properly finds the ACPI, SMBIOS, and MP table pointers and loads them properly.

When we boot, we pass the address of the EFI System Table to ELILO.
I believe that ELILO is suppose to pass the EFI System Table address to the boot kernel, which somehow gets to efivars.

But what I have discovered from dumping through the source code of efivars is that it hard codes where it accesses the EFI System Table.
At least it claims to hard code access the table from the comments.

I suspect this is due to someone along the line of booting Linux on an EFI platform dropping the ball and by the time efivars is loaded it doesn't get the EFI System Table address so all it could do was hard code the access based on the "Itanium" platform which was the only example for years.

I cannot find another example of someone having a x86 EFI BIOS which installs Linux without this error.

I too have an Apple MiniMAC, but since mine has the Legacy CSM portion of the BIOS, Linux and Windows install using the old Legacy method on it instead of EFI.
And it sounds like from the original post in this thread that if I did have an Apple BIOS without CSM such that Linux had to install using EFI Only that it would have the same problem.

I used to work at Dell and knew Matt Domsch back then whio is the author (and maintainer?) of efivars.

I am now seriously working on resolving this problem, but I suspect that Matt had to hard code the address (based on his comments) because the EFI System Table address doesn't propigate to the module and he had no other choice.

If this problem was solved, then Linux would work properly on an EFI-only BIOS based system.

---

### Post by volanin on 2007-11-30
> **cabdouch said:**
> I am now seriously working on resolving this problem, but I suspect that Matt had to hard code the address (based on his comments) because the EFI System Table address doesn't propigate to the module and he had no other choice.

If this problem was solved, then Linux would work properly on an EFI-only BIOS based system.

I am using kernel 2.6.23 from Fedora, and I believe this option exists in previous kernels as well:
There is an option in it to allow the kernel to receive variables from the EFI Boot Loader,
and it also explicitly names elilo in its documentation.

These EFI variables are made available through the /sys filesystem as well.
But even compiling this in, I could not get elilo to boot my Macbook (but I didn't try that hard anyway).
Is this what you're looking for?

Your post seemed more like an announcement than a request for help.
So, if there is anything we can help you with, don't bother to ask as well!
:)

---

### Post by cabdouch on 2007-12-03
It was kind of a list of how I understand this to work.

The main problem is that I cannot "modprobe efivars" or I get a hang in the process or a Segmentation Fault.

My MiniMAC has Legacy compatibility, so Linux installs like normal instead of the EFI method.

Does your system have the efivars module loaded?

If so, what kind/make of system is it and what BIOS do you have?

In clarifying this, we're making a BIOS for a standard Intel 945 based system. Although we think we are following the EFI Spec, Linux cannot load "efivars". This results in the inability for Linux to gain access to the EFI Variables and so it can't add an entry to the Boot List, it can't change the order of the Boot List, and it can't copy elilo.efi, elilo.conf, initrd.img, or vmlinuz to the EFI partition after installing the OS so that the next boot will boot to Linux.
I manually mount the EFI partition (which Linux does create during the install) and copy the boot files to the partition so EFI can boot Linux.
I am also getting a Time error with Linux trying to read the EFI Time, but I suspect that is related as well, though it might be a seperate issue.

Thanks.

---

### Post by oskarloko on 2008-01-03
I have done some advance on the question, but It's not totally solved

As you may see

[URL="http://ubuntuforums.org/showthread.php?p=4066721&posted=1"]http://ubuntuforums.org/showthread.php?p=4066721&posted=1
[/URL]

---

