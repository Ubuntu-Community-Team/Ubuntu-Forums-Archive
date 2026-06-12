---
title: "mactel-boot"
date: 2015-12-12
forum: Apple Hardware Users
---

### Post by drew37 on 2015-12-12
I've been trying to follow this: [http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot-short-version/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot-short-version/)

I've got to the point of adding the ppa:detly/mactel-utils repo in Ubuntu MATE 15.04. However, after running sudo apt-get update, it is unable to find the mactel-boot package. It appears there isn't a repo yet for Wiley, only Trusty. Am I up a river until this gets updated? Or is there a way to pull this from the Trusty repo?

---

### Post by drew37 on 2015-12-12
Ah, I also see from this [site]("http://glandium.org/blog/?p=2830") I can grab the source [here]("http://www.codon.org.uk/~mjg59/mactel-boot") and compile it as so.

Grab the [mactel-boot source code]("http://www.codon.org.uk/%7Emjg59/mactel-boot/mactel-boot-0.9.tar.bz2"), unpack and build it:
[INDENT]# wget [http://www.codon.org.uk/~mjg59/mactel-boot/mactel-boot-0.9.tar.bz2](http://www.codon.org.uk/~mjg59/mactel-boot/mactel-boot-0.9.tar.bz2)
# tar -jxf mactel-boot-0.9.tar.bz2
# cd mactel-boot-0.9
# make PRODUCTVERSION=Debian

I presume I would change Debian to Ubuntu?
[/INDENT]

---

### Post by drew37 on 2015-12-12
Got it! 

Ran make PRODUCTVERSION=UBUNTU

Then 'sudo cp hfs-bless /usr/sbin'

And finally the 'sudo hfs-bless "/boot/efi/EFI/$(lsb_release -ds)/System/Library/CoreServices/boot.efi"'

When rebooting I was prompted with the glashing question mark folder, but if you force reboot and hold option, Ubuntu presents itself. You can then hold the ctrl key and click the circular arrow to let the system know to always boot into Ubuntu.

---

