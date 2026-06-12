---
title: "[SOLVED] Live CD building"
date: 2007-07-16
forum: Apple PPC Users
---

### Post by Keith Hedger on 2007-07-16
Hi guys need some help!
I'm trying to build a custom live cd for PPC I've been folowing this guide:
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)
but i'm stuck on the last bit, how to create the iso the instructions are:
sudo mkisofs \
    -o ubuntu-new.iso \
    -b isolinux/isolinux.bin \
    -c isolinux/boot.cat \
    -no-emul-boot \
    -boot-load-size 4 \
    -boot-info-table \
    -r \
    -V "Custom Ubuntu Live CD" \
    -cache-inodes  \
    -J \
    -l \
    ubuntu-livecd
but this apears to be for a pc based cd, options -b and -c dont seem to apply to a PPC system.
So basicly I need to know how to construct the iso from the folder  "ubuntu-livecd"
Any ideas or how-tos?

---

### Post by zach12 on 2007-07-16
you should try posting in Programming or Installation & Upgrades
you may get someone to help ther

---

### Post by linear on 2007-07-17
Once upon a time there were instructions in the wiki, [here]("https://help.ubuntu.com/community/LiveCDCustomization"). Someone has removed them.

Going back through the history of that page, I found:

On PowerPC, download [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://people.ubuntu.com/~cjwatson/hfs.map]("http://people.ubuntu.com/%7Ecjwatson/hfs.map"), then use the following command:  

[FONT=Courier New]  $ sudo mkisofs -r -V "Custom Ubuntu Live CD" \
            --netatalk -hfs -probe -map hfs.map \
            -chrp-boot -iso-level 2 -part -no-desktop \
            -hfs-bless extracted_cd/install \
            -hfs-volid Ubuntu/PowerPC_breezy \
            -o custom-breezy-live-powerpc.iso extracted_cd[/FONT]

---

### Post by Keith Hedger on 2007-07-17
Thanks !
Worked like a dream you are sure to go to heaven:):)
I've been searching for this for 2 days!

---

