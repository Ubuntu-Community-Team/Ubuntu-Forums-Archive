---
title: "nvidia card wiki page"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by chadmichael on 2006-03-15
I have a couple of questions about some concepts and terms referred to on the wiki page that describes how to set up an NVidia graphics card.

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)


1)  It calls this the nvidia binary driver.  Is this the proprietary driver provided by nvidia?  If not where did it come from?

2)  The page has you install "linux-restricted-modules-386" -- what is this?

Chad

---

### Post by mlind on 2006-03-15
restricted modules are kernel modules that have more restrictive licence, they're not
GPL stuff. 

These modules enable kernel support. In addition you need nvidia-glx package, so that X is able to use your driver too.

---

### Post by chadmichael on 2006-03-15
So, these restricted modules do what?  The package that the wiki mentions sounds like a huge glob of modules, rather than a specific one.  I assume the one I need is just something to communicate with the nvidia driver?

---

### Post by mlind on 2006-03-15
package info says
```

Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

```

so yes, you're right. It's a glob of modules, but you really don't lose anything
if you install this package. These modules are not loaded by default.
This is just the way Ubuntu provides Nvidia's kernel modules, packaged
in one big restrictive modules package.

You can always get the kernel source, nvidia's binary package and compile modules yourself!

I guess it's less hassle for the devs to rollup these on one .deb package, dunno.

---

