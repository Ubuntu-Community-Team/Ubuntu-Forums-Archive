---
title: "Trouble Booting Feisty on PPC G4"
date: 2007-08-22
forum: Apple PPC Users
---

### Post by kerzon on 2007-08-22
Hi there,

I'm trying to get a dual-boot thing going on my 733mhz G4 PPC. I had this working with OpenSuse, but found that I like Ubuntu better. I have a second hard drive that I'd like to install it on and will then choose between the different OS's by holding down the Option key on startup. 

My problem is that I cannot get the Ubuntu Feisty CD to boot. I've tried holding down 'c' (could never get this to work on any Linux distro). When I hold down the Option key I get an nice CD icon with a little penguin, however when I select it and hit enter I get a GSOD (grey screen of death) and nothing happens. Does it matter that yaboot in the in the Install subdirectory?

Any advice is greatly appreciated. Am I better off ordering the free CDs? Is there a way to boot the CD in Open Firmware?

---

### Post by pxwpxw on 2007-08-22
From open firmware:
```

0> dir cd:,\
0> dir cd:,\install
0> boot cd:,\install\yaboot

```
works for a ubuntu704 alternate install cd just now.

---

### Post by kerzon on 2007-08-22
I'm able to do this (found out that my cd is ide1 in the device tree). However, I get the following error:

yaboot conf: damaged or corrupt filesystem, unable to open the config file.

The yaboot.conf file is just the one that came with the CD which I am booting from, so not sure what to do about that.

---

### Post by pxwpxw on 2007-08-22
What is the exact boot command you used?

---

### Post by kerzon on 2007-08-22
dir ide1:\
boot ide1:\install\yaboot

It definitely goes into yaboot (no grey screen). I get and option to press the TAB button to get a menu of bootable partitions, but none are to be found, I just get "boot:"

---

### Post by pxwpxw on 2007-08-22
> **kerzon said:**
> dir ide1:\
boot ide1:\install\yaboot

It definitely goes into yaboot (no grey screen). I get and option to press the TAB button to get a menu of bootable partitions, but none are to be found, I just get "boot:"

I assme that is a typo above, you left out a comma after the colons, it would not work if that was the actuall command you used. You are booting yaboot, so that is progress.

Then I assume that when you just hit enter you get the error reported above:
    "yaboot conf: damaged or corrupt filesystem, unable to open the config file".

That makes sense, but it means yaboot cant find  yaboot.conf  (hence no <tab> menu) - not that there is an error in yaboot.conf.

You should get a listing of the boot files (yaboot, yaboot.conf, ofboot, boot.msg) and their sizes/dates using dir
```

 dir ide1:,\install
### and if you do this it should complain that it "can dir a file" (which confirms it found it)
 dir ide1:,\install\yaboot

```

Would you recheck the above please, before we assume there is some sort of corruption in the CD, or look for other possibilities, such as the change from cd: to ide1:
Cant think of anything just now.

.

---

### Post by kerzon on 2007-08-23
Oops! Yes, I did neglect to include the comma. I am now typing this in a Firefox window from Ubuntu, Thanks so much for the help!

---

