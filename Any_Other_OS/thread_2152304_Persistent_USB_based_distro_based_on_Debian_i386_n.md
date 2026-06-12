---
title: "Persistent USB based distro based on Debian i386 non-pae"
date: 2013-06-07
forum: Any Other OS
---

### Post by mips on 2013-06-07
I'm looking for a Debian based distro that I can install to a USB stick that will allow me to install new packages and save any configs or personal files just like on a normal desktop install.

It must be able to boot on any** i386 non-pae cpu** and up. 

I don't wanna jump through any hoops to make an distro that was not designed to do this fit the bill. I saw Neptune (from the ZevenOS) guys which looks like what I want except it's only x86-64 from what I gather. A forensics/penetrating distro would be great, does kali linux meet these requirements?

---

### Post by ajgreeny on 2013-06-07
Try Bodhi 2.3.0, based on ubuntu so debian once removed, if you see what I mean.

It uses the E17 DE/WM, which is very different from most of the *ubuntu family OSs, and may take a bit of getting used to, but can be made to look gorgeous, and can use all the packages in ubuntu repos.  It can also manage well with persistence when the USB is made using the ubuntu startup-disk-creator.

Try it for a while and you may find that with its minimal ram usage on your old machine that it is just the ticket.

See [http://jeffhoogland.blogspot.co.uk/2013/03/bodhi-linux-230-released.html](http://jeffhoogland.blogspot.co.uk/2013/03/bodhi-linux-230-released.html)

---

### Post by 2F4U on 2013-06-07
Probably not exactly what you are looking for, since it is dedicated to older machines and meant to be especially lightweight: antiX.

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

It is based on Debian Testing

---

### Post by kiyop on 2013-06-08
> **mips said:**
> I'm looking for a Debian based distro that I can install to a USB stick that will allow me to install new packages and save any configs or personal files just like on a normal desktop install.

It must be able to boot on any** i386 non-pae cpu** and up.

How about installing debian to a partition in an USB stick similarly as to a partition in an internal HDD using netinst (without using squashfs filesystem)?
But, debian (after version 3.1) [does not support mere]("http://www.debian.org/releases/stable/i386/ch02s01.html.en#idp5574912") [80386]("https://en.wikipedia.org/wiki/Intel_80386") but supports [i486 (80486)]("https://en.wikipedia.org/wiki/I486") or later.
Do you use 80386? Or i486 and later?
And if you use Wheezy, [you should use 486 kernel](http://www.debian.org/releases/wheezy/i386/release-notes.en) rather than 686-pae as you may know.

---

### Post by mips on 2013-06-13
C'mon, I need some more replies please.

---

### Post by Cheesemill on 2013-06-13
> **mips said:**
> A forensics/penetrating distro would be great, does kali linux meet these requirements?

Although they don't provide a download it's easy enough to create your own Kali non-PAE image by following the instructions on their site...
[http://docs.kali.org/live-build/live-build-a-custom-kali-iso](http://docs.kali.org/live-build/live-build-a-custom-kali-iso) 

CrunchBang have a non-PAE version available for download...
[http://crunchbang.org/download](http://crunchbang.org/download)

I've actually just made a custom image myself of #! built on top of Kali instead of Debian, I made a 64-bit version but it would be easy enough to create a non-PAE version.
[http://ubuntuforums.org/showthread.php?t=2150410&p=12688499&viewfull=1#post12688499](http://ubuntuforums.org/showthread.php?t=2150410&p=12688499&viewfull=1#post12688499)

---

### Post by mips on 2013-06-14
Cheesemill, but will they install to a USB stick like a normal hard drive, can I install apps afterwards, save stuff to /home etc?

---

### Post by Cheesemill on 2013-06-14
As far as I  know ***any*** linux distro can be installed to a USB stick in the same way that it can be installed to a hard drive.

---

### Post by mips on 2013-06-14
> **Cheesemill said:**
> As far as I  know ***any*** linux distro can be installed to a USB stick in the same way that it can be installed to a hard drive.

Was not aware of that, I recall it being an issue back in the day but that was a long time ago. Will have to try out thx.

---

### Post by sudodus on 2013-06-14
> **Cheesemill said:**
> As far as I  know ***any*** linux distro can be installed to a USB stick in the same way that it can be installed to a hard drive.
+1
It will be easier if you remove or inactivate the internal drive, so that you only have the source drive (CD/DVD/USB) and the target drive. If you have the internal drive connected, the installer will probably want to ***install the bootloader*** to that drive instead of the USB drive. In Ubuntu desktop you select 'Something else' and in many text mode installers (Ubuntu alternative installers) it is called 'Manual partitioning' which I think is a better name. I think this is the only tricky thing, otherwise it is pretty straight-forward.

Maybe you can install Debian itself, or LMDE or Knoppix. But Knoppix is intended to run live or persistent live, and you should download updated isos instead of updating/upgrading. Knoppix is very good at recognizing hardware, also old hardware.

*Edit*: Avoid proprietary drivers, if you want true portability. Be prepared to use boot options (via the grub menu) for some computers.

---

### Post by mips on 2013-06-14
> **sudodus said:**
> +1
Maybe you can install Debian itself, or LMDE or Knoppix. But Knoppix is intended to run live or persistent live, and you should download updated isos instead of updating/upgrading. Knoppix is very good at recognizing hardware, also old hardware.

*Edit*: Avoid proprietary drivers, if you want true portability. Be prepared to use boot options (via the grub menu) for some computers.


Thing is I want a Debian 7 (Wheezy) distro on a flash stick I can boot on any PC I plug it into. I would also like to install new packages should the need arise. Cheesemill's setup intrigues me as that would be an ideal setup as mix between #! & Kali. We all know debian does not get many updates so that would be cool.

Agreed, something like vesa fb would be ideal as it should work on all systems.

---

