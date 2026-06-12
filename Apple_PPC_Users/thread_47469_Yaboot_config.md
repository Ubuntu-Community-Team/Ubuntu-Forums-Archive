---
title: "Yaboot config"
date: 2005-07-08
forum: Apple PPC Users
---

### Post by jcayo11 on 2005-07-08
I have just dual-booted ubuntu and OS X on an eMac.
Everything works just fine on both OSs.
Only question, how do I get OS X to be the default OS instead of ubuntu.

 ](*,)

---

### Post by arunsub on 2005-07-08
I don't know if this helps
[http://lists.debian.org/debian-user/2004/12/msg00122.html](http://lists.debian.org/debian-user/2004/12/msg00122.html)
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

---

### Post by arunsub on 2005-07-08
Here is the ubuntu one
[http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

---

### Post by Len on 2005-07-08
```
man yaboot
```
and
```
man yaboot.conf
```
should provide you with all the info you need. Don't underestimate the man pages...

---

### Post by DJ_Max on 2005-07-08
[QUOTE=arunsub]Here is the ubuntu one
[http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)[/QUOTE]
The PPC arch doesn't and can't use Grub, it uses Yaboot. Open your yaboot.conf and there make sure there's a line
```

defaultos=macosx

```

---

### Post by jcayo11 on 2005-07-09
](*,) 

Still not working.
I am really new to linux.

Here is my current yaboot.conf:

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda4
defaultos=macosx

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

Could use any help you guys can give.

---

### Post by ddevil on 2005-07-10
Hello jcayo 

Arter adding that in yaboot.cong (i mean, "defaultos=macosx"), you should simply write "ybin" in the command line and press enter in order that yaboot write the changes you did at "yaboot.conf"

I hope you understand my poor english  :-?

---

### Post by td5silver on 2005-07-10
[QUOTE=ddevil]Hello jcayo 

Arter adding that in yaboot.cong (i mean, "defaultos=macosx"), you should simply write "ybin" in the command line and press enter in order that yaboot write the changes you did at "yaboot.conf"

I hope you understand my poor english  :-?[/QUOTE]

Yeah, make sure you run ybin in a terminal window to register(?) your new config file. Then everything should work ok.

I just figured out ybin last nite, after 2 weeks of searching on the internet  :???:

---

### Post by jcayo11 on 2005-07-11
Thanks I will give that a try :)

---

### Post by jcayo11 on 2005-07-11
[QUOTE=ddevil]Hello jcayo 

Arter adding that in yaboot.cong (i mean, "defaultos=macosx"), you should simply write "ybin" in the command line and press enter in order that yaboot write the changes you did at "yaboot.conf"

I hope you understand my poor english  :-?[/QUOTE]

Thanks.

Everything is working great now.

 \\:D/

---

