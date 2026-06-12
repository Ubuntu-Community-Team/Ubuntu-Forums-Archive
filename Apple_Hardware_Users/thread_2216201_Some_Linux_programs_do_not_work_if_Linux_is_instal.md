---
title: "Some Linux programs do not work if Linux is installed on a Macbook Pro?"
date: 2014-04-10
forum: Apple Hardware Users
---

### Post by will32 on 2014-04-10
Hi,

I am trying to install the Linux x86 version of Sonnet software on the Ubuntu 12.04.4 partition on my Macbook Pro 8.1.  However, the installation fails during one step when it tries to unzip a file.  I contacted Sonnet technical support, and they replied with this:

"We don’t support the underlying Mac architecture at the hardware level, even if you are running linux on a Mac. We just don’t build the software for the Mac platform. We recommend to Mac users that want to use Sonnet to create a linux virtual machine in Virtual Box."

I tried searching around to see if this makes sense, but I haven't found any information about why Linux on a Mac would be unable to run certain Linux programs because of the "underlying Mac architecture."  Does this restriction make sense?  Thanks for the help!

-Will

---

### Post by Double.J on 2014-04-10
Hi there!

Welcome to the forums!

is this sonnet the thunderbolt storage people? Cause they definitely make devices for mac. Which device are you downloading software for? Whilst macs are now x86 and basically just pc's in many ways, i suppose it is possible that their inplimentation of thunderbolt may restrict some thunderbolt accessories?

just a thought

jj

---

### Post by bapoumba on 2014-04-10
Moved to Apple Users.

---

### Post by will32 on 2014-04-10
Hi JJ,

Thanks; I'm pretty new to Ubuntu.  This is E&M simulation software; it shouldn't be using anything very hardware-specific.  They have Windows versions and Linux versions; I am wondering why the Linux version would specifically be for Linux on a PC partition. as opposed to Linux on a Macbook Pro partition.

-Will

---

### Post by Double.J on 2014-04-10
Hi there,

I went to their support pages to see if I could help shed some light for you!

could you confirm whether this is the software in question?

If so I have downloaded their used manual for linux and noticed two key points. 

Firstly that they only officially support red hat enterprise linux, and suse linux enterprise. This probably means that when you run the installer script in the downloaded folder, ubuntu does not have the package managed and libraries it is looking for.

secondly, the minimum hardware requirements in the link i put up are way beyond that of a macbook pro. These are serious workstation requirements which is why I said double check I got it right!

Jj

---

### Post by will32 on 2014-04-11
Hi JJ,

I didn't see a link in your post - this is the software I'm talking about: [http://www.sonnetsoftware.com](http://www.sonnetsoftware.com)

They only officially support Red Hat and Suse, true, but on the downloads page they actually have three versions: Windows version, Red Hat and Suse version, and "other Linux" version for x86.  I've been trying to install the "other Linux" version.

I checked the system requirements on this page ([http://www.sonnetsoftware.com/products/sonnet-suites/requirements-redhat.html](http://www.sonnetsoftware.com/products/sonnet-suites/requirements-redhat.html)) and although I have the hardware requirements, I actaully don't have all the software requirements.  So that might be it.  I'm still a little puzzled by the claim that the "underlying Mac architecture" is to blame though - if that is indeed the case, then installing no amount of extra packages/libraries would make it work.  I'd really like to know if that claim makes any sense - if indeed Linux on a Mac is any different from Linux on a PC in terms of the programs that it can possibly run.

Thanks,
Will

---

### Post by Double.J on 2014-04-11
Hi sorry, the link i meant to add is just at the bottom of your page, [link]("http://www.sonnetsoftware.com/products/sonnet-suites/requirements-hardware.html"). Although it looks like these are just recommended optimum.

it may be worth attempting an install on centos. It's binary compatible and has now become part of the red hat family. Going forward, they will be offering fedora style spins of rhel, but have currently cloned up to rhel 6.5

As for the hardware, no. Not that I can see. I've used linux on mac for years and, sure back in the ppc days you needed whole other software (ubuntu ppc) to run and you had to have special repositories and such, but since macs went intel, I've only ever had a few proprietary driver issues. (Thunderbolt ethernet adapter comes to mind), and the obvious efi work around.
 
They really do use PC laptop hardware. If there are requirements that specific, then it would affect many pc OEM machines too. In fact based on their recommended hardware, the current mac pro would mac sense. I would seek clarity on this if I were you, make sure they were not quoting from the ppc days? Or even find out which specific components are not supported?

keep us up to date! 

jj

---

