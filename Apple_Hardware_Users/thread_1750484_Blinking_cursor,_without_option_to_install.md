---
title: "Blinking cursor, without option to install"
date: 2011-05-05
forum: Apple Hardware Users
---

### Post by philipolson on 2011-05-05
I have a MacBookPro5,2 with WinXP and Mac 10.6.7 installed. I created a new partition, and installed refit. I burned Ubuntu 11.04 32bit, rebooted, held 'c' and it started the boot process via the CD. It makes it to a brief Ubuntu image but changes the the blinking cursor and doesn't change. I see no menus and have no options except to be sad and reboot.

How should I proceed debugging this? Simply running Ubuntu via 'LiveCD' would be nice, as would being able to install Ubuntu. Should I try an alternative version of Ubuntu? All advice welcome.

---

### Post by Silmathoron on 2011-05-05
Did you try the mac version ?
You should try both ubuntu-11.04-alternate-amd64+mac.iso and ubuntu-11.04-desktop-amd64+mac.iso
Here : [http://cdimage.ubuntu.com/releases/natty/release/](http://cdimage.ubuntu.com/releases/natty/release/)

---

### Post by philipolson on 2011-05-05
I tried the standard version. Also, I got it to work (I think) or at least Mac+Linux+Win are all installed and I'm booted into Ubuntu as I write this.

A few pre-install notes:
1. Trying the Mac specific version is probably wise, and ideally it'd be clearer within the instructions
2. Pressing F6 (Fn+F6) is required when the initial Ubuntu screen pops up. This prevents the blinking cursor. I'm sure other Fn variations would work too, but it must be quickly done. This then allows the install.
3. The F6->nomodeset option must be chosen (read this, didn't try other options, but fails without).

And after install:
4. I must add "nouveau.niaccel=1" to the linux bootup command, which is currently typed by hand at bootup

So that's where I ended up, hope that helps someone. If I run into problems then I'll try a Mac variant of Ubuntu.

---

