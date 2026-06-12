---
title: "Linksys USB Wireless Adapters"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Piney Woods on 2005-12-01
Hi Folks.  I consider myself a newbie to the linux community but I have tried out other distros such as Mepis, Fedora Core and Xandros.  I keep coming back to Kubuntu.  However, one problem always seems to arise when installing any distro: Wireless network support. I have a wireless network of 6 computers, a few of which are hard wired to my linksys wireless router.  One computer, which is in a different room than the router has a linksys usb wireless adapter that I would like to use with the desktop.  Linux always seems to have a problem detecting it.  I understand that wireless support in linux is iffy at best but I hope that support for more wireless cards are coming.

Anyway, to my question.  I have a linksys Wireless-B USB network adapter (WUSB11v4) connected to my desktop.  I have downloaded and installed the newest Kubuntu distro (5.10) and need to connect it to the internet.  I have read various things about ndiswrapper but have never used it.  I am re-aquiring a taste for the command line after not having done so since years ago in college learning ms-dos.

Can someone offer a step-by-step set of instructions on how I can install the wireless adapter?  I am hoping soon that the developer gurus will get together on this and make it easier for wireless cards to work right out of the box without so much bother.

Thanks,
PW

---

### Post by Lambert on 2005-12-01
There are few posts about the v4 and the ones I read sounded like the v4 caused problems with no success.

Looking at ndiswrapper though, they say it's supported.

[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) (line #18)

There is a link in my signature for using ndiswrapper. Pay close attention to what driver you're using (pull the one from the second link above)

If you have problems, come back and post any errors or give detail of what you've done and where you're stuck.

Please document what you do and post that back if you have success so others can benefit from this.

The ndiswrapper version I believe with breezy is 1.1 and I also believe ndiswrapper is up to 1.5 (correct me if I'm wrong anybody) If you can't get it to work with the breezy packaged ndiswrapper, you may have to search around how to compile the latest version to get this to work.

---

### Post by fuscia on 2005-12-01
i had a brutal time with my netgear adapter, even using ndiswrapper. i finally got it working with ndisgtk (you can get it from synaptic and i think you'll need ndiswrapper utilities with it).

---

### Post by Piney Woods on 2005-12-01
[QUOTE=Lambert]There are few posts about the v4 and the ones I read sounded like the v4 caused problems with no success.

Looking at ndiswrapper though, they say it's supported.

[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=281)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) (line #18)

There is a link in my signature for using ndiswrapper. Pay close attention to what driver you're using (pull the one from the second link above)

If you have problems, come back and post any errors or give detail of what you've done and where you're stuck.

Please document what you do and post that back if you have success so others can benefit from this.

The ndiswrapper version I believe with breezy is 1.1 and I also believe ndiswrapper is up to 1.5 (correct me if I'm wrong anybody) If you can't get it to work with the breezy packaged ndiswrapper, you may have to search around how to compile the latest version to get this to work.[/QUOTE]
Thanks for the info.  I've had to shut my pc down today because of a bad memory stick.  Having to wait until UPS delivers it in a few days before I can try this again.  Will let you know.

PW

---

