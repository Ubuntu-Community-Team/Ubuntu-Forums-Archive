---
title: "Kubuntu wont boot on imac 266 :("
date: 2007-08-29
forum: Apple PPC Users
---

### Post by Bong_Master_Darky on 2007-08-29
yo peeps i decided to try kubuntu today on my old imac 266mhz, the problem is the bloody cd doesnt  work i put it in tha mac and hold c when booting but nothing happens it just loads osx, i aslo have an older version of ubuntu which is pressed from the ubuntu people and that one wont boot either what could be up with my mac i tired resetting the pram stuff but no luck, also when i go into OF my screen doesnt come on it stays off i have to plug in a external monitor wtf is up with that 

any help will be great thanks for ya time 

bong master darky:)

---

### Post by ajgreeny on 2007-08-29
Is this a 266Mhz processor with a similarly low MB ram figure?  You need at least 256 MB for Ubuntu or Kubuntu to boot as the live CD, and preferably more if you want to install them and get them running at a sensible speed.

---

### Post by Bong_Master_Darky on 2007-08-29
yeah its a 266mhz purple imac it has 128mb ram at the moment but im unsure which sort to buy to upgrade it whats is reconmened i have looked on ebay but still unsure is there any other linux distabutions that would run on this old dust collector 

bong master D

---

### Post by Bong_Master_Darky on 2007-08-30
will this ram work in my imac
[http://cgi.ebay.co.uk/256MB-PC100-133-SODIMM-SDRAM-LAPTOP-MEMORY-144PIN-IBM_W0QQitemZ160151949189QQihZ006QQcategoryZ31575QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/256MB-PC100-133-SODIMM-SDRAM-LAPTOP-MEMORY-144PIN-IBM_W0QQitemZ160151949189QQihZ006QQcategoryZ31575QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)


thanks

---

### Post by ajgreeny on 2007-08-30
Sorry, no idea about mac hardware.

---

### Post by linear on 2007-08-30
Assuming this is the correct model here: [http://lowendmac.com/imacs/imac-c.shtml](http://lowendmac.com/imacs/imac-c.shtml), your memory specs should be:

> RAM: 32 MB, expandable to 384 MB using SO-DIMM SDRAM (3.3V, unbuffered, 64-bit, 144-pin, 100 MHz or faster, 10ns) in two DIMM sockets (256 MB on top, 128 MB on bottom), top DIMM socket accepts 2" DIMM, bottom socket takes 1.5" DIMM
* The exact amount a Rev. A-D iMac can be upgraded varies from unit to unit. We have field reports of some models accepting 256 MB modules in both memory socket and reaching 512 MB - and other reports of early iMacs that won't work at all with 256 MB modules. There appears to be no way to know in advance whether a particular iMac will work with a certain sized memory module.

---

### Post by pxwpxw on 2007-08-31
> **Bong_Master_Darky said:**
> yo peeps i decided to try kubuntu today on my old imac 266mhz, the problem is the bloody cd doesnt  work i put it in tha mac and hold c when booting but nothing happens it just loads osx, i aslo have an older version of ubuntu which is pressed from the ubuntu people and that one wont boot either what could be up with my mac i tired resetting the pram stuff but no luck, also when i go into OF my screen doesnt come on it stays off i have to plug in a external monitor wtf is up with that 

any help will be great thanks for ya time 

bong master darky:)

As well as the memory (good advice above) here are some things to do with your non-booting and the OF wanting the external screen, which seem to be separate problems.

1. Booting:

 Confirm you have a PPC CD, and not an iso image file. You should see the folders/files from macosx, including /install/yaboot (the i386 CD hae an /isolinux folder). Or try it on another mac.

If you have a readable ppc cd it may be bootable from openfirmware, even if it wont boot normally using the C key.

Your cdrom drive may have the alias "cd" or "ide0" or similar ( I don't have an imacg3 to check).
See what aliases you have, the list below should give a clue.
```

 devalias
 devalias cd

```
If it is cd
```

0> boot cd:,\install\yaboot
 # or
0> boot cd:,\\:tbxi
 # or to list files from OF
0> dir cd:,\ 

```
 
2. OF wants another screen.
(this can cause problems when the cd boots but the initial stages cant find the screen)

if Command-Option-P-R (zap pram) dose not fix the OF screen
```

0> printenv output-device
## this is usually "screen"
0> setenv output-device screen
## will try that
## if there is a second video card, you may need to remove it for some initial install stages.
0> devalias screen
## will show th full path for screen, if is exists

``` 

3. If your cd drive cant read the live CD, consider just installing to the internal hard drive, from an Alternate install CD .iso image on HD, or from the network.

See **section 4 and 5 of the Alternate install guide** **hd-media **and **Netboot install images** for explanation.

==============

---

