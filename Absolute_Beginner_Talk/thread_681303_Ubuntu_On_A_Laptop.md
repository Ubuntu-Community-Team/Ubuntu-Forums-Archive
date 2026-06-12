---
title: "Ubuntu On A Laptop"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2008-01-28
Hey,

So i have my friends Vaio laptop and he wants to wipe windows and use Ubuntu. However, i seem to recall there was some setting one had to use, or else their laptops hard drive dies after a bit. What was the setting?

Or did i imagine that? Anyway, also how does one get a linksys ethernet card working on a laptop? I doubt it will work out of the box. the card is a Netgear WG511

Thanks a lot!

---

### Post by emarkd on 2008-01-28
I think you're referring to the read/write head parking issue that came up a while back.  That setting is turned off by default now so your friend has nothing to worry about on a new install.

---

### Post by Casual Fan on 2008-01-28
The hard drive problem was corrected in the most recent Linux kernel releases; just install Gutsy and update after install and it should be fine.

You'd be surprised how much hardware works right out of the box!

---

### Post by seventhc on 2008-01-28
I have 2 sony vaio's both with ubuntu, everything worked fine out of the box, but I don't have a netgear card, so I don't know if it will work right away or not.
Boot from the live cd and that will give you an idea of what will work as is.

---

### Post by roboxking on 2008-01-28
I recently put in a wireless card for Ubuntu on a desktop, and  I didn't even need to access the restricted drivers for it to work, it just worked!

---

### Post by crjackson on 2008-01-28
I have 2 laptops running ubuntu.  One Sony and One eMachines.  The Sony is supported 100% out of the box, the eMachines only needed the windows driver for the wireless card.

---

### Post by Amstell on 2008-01-28
I've had trouble running ubuntu on laptops so i ordered a dell with ubuntu.  Good luck though.

---

### Post by JoshuaRL on 2008-01-28
I had some trouble as well.  But mainly mine came from the fact that it was a couple years old and had an ATI card in it.  If it's even relatively new and doesn't have an older ATI card, you should be fine.  That and wireless are probably the only issues he may have.

---

### Post by crjackson on 2008-01-29
My eMachines has an ATI card and works fine.  I guess it just depends on what card you have.

---

### Post by thedrizz on 2008-02-05
well the laptop, only having 192 mb ram, cant run either Xubuntu or Ubuntu with any real success.
Is there a distro with lower requirements?

---

### Post by aysiu on 2008-02-05
> **thedrizz said:**
> well the laptop, only having 192 mb ram, cant run either Xubuntu or Ubuntu with any real success.
Is there a distro with lower requirements?
Fluxbuntu

---

### Post by emarkd on 2008-02-05
Maybe [Fluxbuntu]("http://fluxbuntu.org") if you want to keep it in the family.  There are other well-known distros for low-power system.  Puppy comes to mind, or DSL... Try [http://www.distrowatch.org](http://www.distrowatch.org) for more info.

---

### Post by Linux_Man on 2008-02-05
Try Puppy Linux [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1) It is small, there are others too, but Puppy seems to have the best hardware detection out of all of the ones Ive tried (smaller distros that is) however with most smaller distros such as Puppy, it takes a bit more work to get things configured and set up compared to Ubuntu or Mandriva.

---

### Post by thedrizz on 2008-02-05
oh and on a side note, it loads xubuntu, but after the bar fills the screen just turns blank

---

### Post by thedrizz on 2008-02-05
oh and can i run pidgen on Fluxbuntu?

---

### Post by Linux_Man on 2008-02-05
Yes, it will boot probobly many distros, however your better off with a lighter one then Xubuntu if you really want to do much with it, Wikipedia has a good list of some lighter distros [http://en.wikipedia.org/wiki/Mini_Linux](http://en.wikipedia.org/wiki/Mini_Linux)

---

### Post by Linux_Man on 2008-02-05
And to answer your newest question, yes you can run Pidgin on just about any Linux system however it may be called Gaim its old name on lighter distros.

---

### Post by thedrizz on 2008-02-05
how well does puppy linux read hardware?

because getting this damn wireless card to work seems like it will be a pain

---

### Post by Linux_Man on 2008-02-05
Puppy can detect some wireless cards that even Ubuntu 7.10 can't easily. However you don't have your nice NetworkManager applet to change networks and such, I cannot guarantee you that your card will be working however Puppy (at least with me) has had excellent compatibility even though it takes a bit more steps to get it working (don't worry there's a graphical program to handle it, it just is a bit less user-friendly then Gnome with NetworkManager)

---

### Post by thedrizz on 2008-02-05
any idea which network driver i need to load to enable the Netgear WG511?

---

### Post by Linux_Man on 2008-02-05
If you know what chipset it is it shouldn't be too hard, a quick search on Google says that it is Athros so you would need Madwifi for most distros however as the chipsets change while the name stays the same it might not be right.

---

### Post by thedrizz on 2008-02-05
er is puppy installable to the hard drive?

because i cannot get it to install itself

---

