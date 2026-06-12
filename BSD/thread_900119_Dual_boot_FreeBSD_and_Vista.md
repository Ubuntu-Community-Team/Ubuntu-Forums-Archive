---
title: "Dual boot FreeBSD and Vista"
date: 2008-08-25
forum: BSD
---

### Post by PurposeOfReason on 2008-08-25
Currently I have arch and vista installed but will be trading arch for bsd soon. As I understand it, freebsd can be installed without a bootloader. If so, can I install it next to vista, go into it right after the install and then run grub-install, storing grub in freebsd and then easily dual boot the two?

---

### Post by Bachstelze on 2008-08-25
> **PurposeOfReason said:**
> Currently I have arch and vista installed but will be trading arch for bsd soon. As I understand it, freebsd can be installed without a bootloader. If so, can I install it next to vista, go into it right after the install and then run grub-install, storing grub in freebsd and then easily dual boot the two?

Yes, you can install GRUB in FreeBSD. I don't know hos simple it is, though, so it might be better sticking with the default FBSD bootloader.

---

### Post by mips on 2008-08-25
The easiest way is to use GAG. It is graphical, simple and it works!

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
[http://en.wikipedia.org/wiki/GAG_(boot_loader](http://en.wikipedia.org/wiki/GAG_(boot_loader))

---

### Post by Bachstelze on 2008-08-25
> **mips said:**
> The easiest way is to use GAG. It is graphical, simple and it works!

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
[http://en.wikipedia.org/wiki/GAG_(boot_loader](http://en.wikipedia.org/wiki/GAG_(boot_loader))

I beg your pardon but how is it easier to install an additionnal bootloader than to just use the one that ships with the OS?

---

### Post by mips on 2008-08-25
> **HymnToLife said:**
> I beg your pardon but how is it easier to install an additionnal bootloader than to just use the one that ships with the OS?

No need to screw around with a menu.lst file when adding or removing an os.

I will leave it up to the OP to decided what he prefers though.

Have a nice day.

---

### Post by theonlyrealperson on 2008-08-25
> **HymnToLife said:**
> I beg your pardon but how is it easier to install an additionnal bootloader than to just use the one that ships with the OS?

I think GAG is a better option as well, but I use both Grub (on the root partition) and GAG on the MBR. Saves me from worrying about adding items to grub or lilo, etc.

If I overwrite the MBR accidently, I pop in the GAG disk and instantly have it all back. 

Works for me.

---

### Post by PurposeOfReason on 2008-08-29
Started to tackle this today and am done. There is no amd64 nvidia driver. Maybe in a few months I'll try again.

---

### Post by Lifedeath on 2008-09-05
> **PurposeOfReason said:**
> Started to tackle this today and am done. There is no amd64 nvidia driver. Maybe in a few months I'll try again.

Bummer, I was hoping to give FreeBSD a go but now I'm not so sure if there isn't a 64-bit Nvidia driver available.

Also, I don't mean to derail your thread but I was just wondering what your reasons were for wanting to switch to FreeBSD from Arch?

---

### Post by PurposeOfReason on 2008-09-05
> **Lifedeath said:**
> Bummer, I was hoping to give FreeBSD a go but now I'm not so sure if there isn't a 64-bit Nvidia driver available.

Also, I don't mean to derail your thread but I was just wondering what your reasons were for wanting to switch to FreeBSD from Arch?
EXP. That's it. :KS

---

### Post by Lifedeath on 2008-09-05
> **PurposeOfReason said:**
> EXP. That's it. :KS

As good a reason as any! :)

---

### Post by theonlyrealperson on 2008-09-05
> **PurposeOfReason said:**
> Started to tackle this today and am done. There is no amd64 nvidia driver. Maybe in a few months I'll try again.

You may have to wait a little longer for AMD64 Nvidia drivers. Nvidia claims that there is a bug in FreeBSD's AMD64 kernel that doesn't allow for their driver. It's been that way all the way through FreeBSD 6.2 at least. I really, really want a 64 bit driver, but I think we're in for a long wait.

Funny, I run Arch 64 bit, FreeBSD 32 bit, and Vista 32 bit all on the same machine. They all play nice with GAG on the bootloader. The only one that needs a little more help is Arch, which needs grub on the root partition.

---

