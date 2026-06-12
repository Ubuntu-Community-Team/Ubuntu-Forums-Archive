---
title: "MacBook, Madwifi and Gutsy"
date: 2007-09-12
forum: Apple Intel Users
---

### Post by davidsiegel on 2007-09-12
I haven't had any success installing madwifi drivers on Gutsy Tribe 5. I did the usual download source, make, sudo make install, modprobe ath_pci, restart, repeat. Has anyone gotten madwifi to work on Gutsy? Any advice?

---

### Post by cyberdork33 on 2007-09-12
Did you blacklist the default module?
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

>  If you decide you absolutely need to compile madwifi from SVN, then you must **stop the linux-restricted-modules package from providing the madwifi module ath_hal, via its so called volatile module mechanism**. Do so by adding **ath_hal** to the list of **DISABLED_MODULES** in **/etc/default/linux-restricted-modules-common**.

---

### Post by davidsiegel on 2007-09-12
I tried blacklisting ath_hal but that didn't do the trick. lspci shows an Atheros network device with "name unknown." It will be a shame if wifi doesn't work out of the box on the Macbook in Gutsy---Macbooks are among the most popular notebooks.

---

### Post by cyberdork33 on 2007-09-12
> **davidsiegel said:**
> I tried blacklisting ath_hal but that didn't do the trick. lspci shows an Atheros network device with "name unknown." It will be a shame if wifi doesn't work out of the box on the Macbook in Gutsy---Macbooks are among the most popular notebooks.
It is probably a matter of getting the madwifi version that has macbook support into the repositories more than anything else.

It is "name unknown" just because the lspci application doesn't recognize the hardware ID... that doesn't mean you can't get it working.

so what level of "not working" are we at? Does it show in network manager? are the ath0 devices and such listed in ifconfig?

---

### Post by benanzo on 2007-09-12
You can update your PCI IDs by doing:
```
sudo update-pciids
```
while connected to the internet (ie via ethernet.)

---

### Post by Dale Cooper on 2007-09-13
I had to downgrade to SVN rev 2695 to have wifi working, hope it helps

---

### Post by davidsiegel on 2007-09-13
Ok, maybe I just need a different version of the source.

By "not working" I mean I get nothing in NetworkManager, nothing in my network preferences, nada.

---

### Post by kry10 on 2007-09-13
> **Dale Cooper said:**
> I had to downgrade to SVN rev 2695 to have wifi working, hope it helps

FYI, I was also having trouble with the latest SVN, but downgrading to 2695 works fine (at least on a public network - haven't tried WEP/WPA yet)

---

### Post by mikko.ohtamaa on 2007-09-15
> **davidsiegel said:**
> I haven't had any success installing madwifi drivers on Gutsy Tribe 5. I did the usual download source, make, sudo make install, modprobe ath_pci, restart, repeat. Has anyone gotten madwifi to work on Gutsy? Any advice?

I confirm an easy success. Just follow these instructions and compile/install Madwifi module  (trunk version).

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Hopefully Gutsy will have Macbook WLAN support out-of-the-box!

---

### Post by davidsiegel on 2007-09-15
Compiling from the latest SVN worked like a charm! Thanks.

---

### Post by bsantos on 2007-09-15
> **davidsiegel said:**
> Compiling from the latest SVN worked like a charm! Thanks.


Are you on a C2D?

I can't connect using nm-applet with latest svn and gutsy up to date, you're on gutsy too? *sigh*

EDIT: *sigh* After battling with madwifi for the last week, it works now. I'm using r2695 from svn, and did a 'make unload' which unloaded more modules I did by hand, if more people are having success with this svn revision maybe that was why it didn't worked here before. Did anyone tracked the possible problem with latest revisions?

The changelog is:

> ------------------------------------------------------------------------
r2708 | mentor | 2007-09-14 03:36:09 +0100 (Fri, 14 Sep 2007) | 2 lines

Assign values to named elements that actually exist in SNAP LLC header

------------------------------------------------------------------------
r2707 | mickflemm | 2007-09-12 10:14:06 +0100 (Wed, 12 Sep 2007) | 3 lines

 * Added new srevs
 * Only warn in case of a faulty EEPROM magic number

------------------------------------------------------------------------
r2706 | mickflemm | 2007-09-10 16:07:57 +0100 (Mon, 10 Sep 2007) | 5 lines

 * Add write capability to ath_info
 * Does not need driver to be loaded anymore
 * Added man page for ath_info
Thanx to Joerg Albert for his work !

------------------------------------------------------------------------
r2702 | mentor | 2007-09-03 00:56:54 +0100 (Mon, 03 Sep 2007) | 2 lines

Decapsulate packets using a DEC's OUI in SNAP packets. As per discussion on madwifi-devel, subject: "possible error when de-capsulating packets?"


---

### Post by davidsiegel on 2007-09-16
Yes, I am on C2D. I'm not sure why our cases differ.

---

