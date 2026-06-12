---
title: "How to install ndiswrapper?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Wowl on 2007-02-21
I have a Linksys WPC54g network card and need to install ndiswrapper. The linux computer has no ethernet ports so i can only transfer files from USb drive. I downloaded ndiswrapper1.37.tar.gz and did the extract (tar .....) so it created a folder in my home directory.

I then did make distclean and make, then did CD to get to the root
and make install but got many errors and when I tried ndiswrapper -i driver.inf it sasy "ndiswrapper command not found"

Any ideas please?

---

### Post by Bachstelze on 2007-02-21
Everything you need is [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

Good luck ;)

---

### Post by tgalati4 on 2007-02-21
I assume that you used:  **sudo make install**
Then**locate ndiswrapper**
You should find files in roughly the same places:
 user@ubuntu:~$ locate ndiswrapper
/var/cache/apt/archives/ndiswrapper-utils_1.8-0ubuntu2_i386.deb
/var/lib/dpkg/info/ndiswrapper-utils.postinst
/var/lib/dpkg/info/ndiswrapper-utils.list
/var/lib/dpkg/info/ndiswrapper-utils.md5sums
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper
/etc/ndiswrapper/mrv8000c
/etc/ndiswrapper/mrv8000c/11AB:1FAA.5.conf
/etc/ndiswrapper/mrv8000c/mrv8000c.sys
/etc/ndiswrapper/mrv8000c/11AB:1FAB.5.conf
/etc/ndiswrapper/mrv8000c/mrv8000c.inf
/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/sbin/ndiswrapper-buginfo
/usr/sbin/ndiswrapper
/usr/share/doc/ndiswrapper-utils
/usr/share/doc/ndiswrapper-utils/README.Debian
/usr/share/doc/ndiswrapper-utils/README
/usr/share/doc/ndiswrapper-utils/AUTHORS
/usr/share/doc/ndiswrapper-utils/changelog.gz
/usr/share/doc/ndiswrapper-utils/copyright
/usr/share/doc/ndiswrapper-utils/changelog.Debian.gz
/usr/share/man/man8/ndiswrapper.8.gz

The main ndiswrapper program resides in /usr/sbin/ndiswrapper
To run it you need:  **sudo /usr/sbin/ndiswrapper -i yourdriverfile.inf**

It's always a pain to get wireless working without a wired network.  No simple way around that.

Good luck,
Terry

---

### Post by teaker1s on 2007-02-21
sounds like [COLOR="Red"]build-essential[/COLOR] missing.

your easiest way is the alternate.iso and add it as a source

---

### Post by aysiu on 2007-02-21
*ndiswrapper* is on the installation CD.

Type these commands in the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by teaker1s on 2007-02-21
but as far as i'm aware [COLOR="Red"]network-manager-gnome[/COLOR] is only on alternate.iso

---

### Post by maniacmusician on 2007-02-21
download the ndiswrapper-common and ndiswrapper-utils  packages from  [http://package.ubuntu.com](http://package.ubuntu.com)  Put them on your usb drive, and away you go.

---

### Post by aysiu on 2007-02-21
> **maniacmusician said:**
> download the ndiswrapper-common and ndiswrapper-utils  packages from  [http://package.ubuntu.com](http://package.ubuntu.com)  Put them on your usb drive, and away you go.
But *ndiswrapper-utils* is on the installation CD already, which can be added as repository. It's on both CDs--Desktop CD and Alternate CD.

---

### Post by maniacmusician on 2007-02-21
isn't ndiswrapper-common necessary as well? I thought it was. If not, then yeah, CD is easier.

---

### Post by aysiu on 2007-02-21
> **maniacmusician said:**
> isn't ndiswrapper-common necessary as well? I thought it was. If not, then yeah, CD is easier.
*ndiswrapper-utils* depends on *ndiswrapper-utils-1.1*, which in turn depends on *ndiswrapper-common*, so I'm assuming they'd include the dependencies as well.

---

### Post by Wowl on 2007-02-21
Thanks, I'm fairly new to do so if I download the alternateiso should that inclde the GUI to help and make it easier to set it all up for networking?

Thanks atgain (much appreciated)

---

### Post by aysiu on 2007-02-21
> **Wowl said:**
> Thanks, I'm fairly new to do so if I download the alternateiso should that inclde the GUI to help and make it easier to set it all up for networking?

Thanks atgain (much appreciated)
*ndiswrapper-utils* is also on the Desktop CD.

You don't have to download the Alternate CD ISO!

---

### Post by teaker1s on 2007-02-21
[COLOR="Red"]gksudo synaptic[/COLOR]
hit edit tab
click on ADD-CDrom
follow prompt and hit reload tab

select search tab
search name and description
type ndiswrapper
search

tick the ndiswrapper related boxes and apply

---

### Post by Wowl on 2007-02-22
Thanks, that worked, so can I just jump to installing drivers? (which step) or do I need to do cab extract?

---

### Post by teaker1s on 2007-02-22
okay you should now be able to install the driver, I'll have a look and find out what it is called

---

