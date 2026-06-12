---
title: "Can't boot Lucid netinstall image on Xserve G5"
date: 2010-05-25
forum: Apple Hardware Users
---

### Post by haggin@illinois.edu on 2010-05-25
Greetings, all. Apologies if there's another thread open on this; I searched and didn't find anything.

I'm an admin for a large (768-node) cluster of Apple Xserve G5s. We've been running Fedora, but we'd like to switch to an LTS release of Ubuntu for various reasons. I can boot the Lucid netinstall kernel (32- or 64-bit) with yaboot, which appears to correctly transfer the kernel and initrd, but when the kernel tries to unzip the initrd, it fails with "EOF while reading compressed data". I'm using the same yaboot binary we've been using for Fedora; the Fedora netboot image works a little differently but the file sizes are comparable.

I attempted the Karmic image to compare, and it boots, loads the initrd, and goes happily on its way, modulo an unrelated mistake of mine.

The relevant yaboot stanzas look like this:
```

image=ubuntu/vmlinux-64.karmic
    label=ubuntu-karmic-node
    initrd=ubuntu/initrd-karmic-64.gz
    initrd-size=18914
    root=/dev/ram
    append="syslog=172.22.61.22:514 netcfg/choose_interface=eth0 ks=http://172.22.61.24/kickstart/ubuntu-node.cfg --"
    read-only

image=ubuntu/vmlinux-64.lucid
    label=ubuntu-lucid-node
    initrd=ubuntu/initrd-lucid-64.gz
    initrd-size=23293
    root=/dev/ram
    append="syslog=172.22.61.22:514 netcfg/choose_interface=eth0 ks=http://172.22.61.24/kickstart/ubuntu-node.cfg --"
    read-only
```
Apart from our site changes (we're using the Kickstart support in d-i to smooth the transition), this is copied from the sample files on ports.ubuntu.com. Has anyone else seen similar problems?

---

### Post by haggin@illinois.edu on 2010-05-26
Hmm...after doing a firmware reset, I could boot Lucid correctly from the OF listener and it went on its merry way. A second attempt worked correctly when netbooting from the front panel.

Ignore this....

---

### Post by linuxopjemac on 2010-05-26
Can you tell me how you performed a so called "firmware reset" ?

---

