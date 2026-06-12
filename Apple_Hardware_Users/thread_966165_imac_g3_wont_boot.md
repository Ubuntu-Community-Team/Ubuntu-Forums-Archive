---
title: "imac g3 wont boot"
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by chrisme52 on 2008-11-01
I've just installed Ubuntu 8.04.1 Ubuntu using the alternate PowerPC install cd. It installed and booted fine until > Loading please wait... appeared on the screen. After that the fan turned off, screen went black but the power light stayed on. The power buttons wouldn't turn the machine off and I had to unplug the power lead in the end.

I believe I installed with standard options.

Please help as this is the first time I've installed on a Mac.

Cheers

---

### Post by milkwood on 2008-11-01
If you are new to ubuntu,I much recommend you to install 6.06 dapper first of all
(if possible,Breezy 5.04 which is my nicest!).
Then why not upgrade to Hardy?
This way maybe rather better than install Hardy directly into your computer.
Then you maybe get the black screen problem.
If you get this problem.Just let me know.
I'm not very reliable though.
(Before you upgrade to hardy,make sure search this forum "upgrade" then you should find the way.)

---

### Post by Henry Higgins on 2008-11-01
Try booting into open firmware by typing "Linux video=ofonly" at the boot prompt.

If that doesn't help, there's a page of known issues with PowerPC [here]("https://wiki.ubuntu.com/PowerPCKnownIssues").

---

### Post by chrisme52 on 2008-11-01
> Linux video=ofonly
That booted fine but without gnome.

I also tried the known issues page but still getting nowhere

---

### Post by milkwood on 2008-11-02
I'm sorry,I might misunderstand your mention.
But you know,ubuntu no longer supports for PowerPc.
I think PowerPc version is sustained by anyone's favor or dedication or so.
In fact,I failed to install "hardy" from install CD.
But I have been used Ubuntu for about 2 or so years.
I know other means,for example,upgrade from dapper to hardy.
Your problem maybe hardware defection or install CD it's own.
If You want to install ubuntu,You just only should succeed installing ubuntu.
It's a only way for us.
But all of that was anyone's favor and dedication and philosophy in the first place,wasn't it.
Then why powerpc had been eliminated it's support?
But it's back and forth thing.
I pray good luck for you.

Thanks.

milkwood.

---

### Post by milkwood on 2008-11-02
I may be totally wrong.
You just check two things.
Try command "sudo nano /etc/yaboot.conf" in the terminal or by using Text Editor.
And Try "sudo nano /etc/X11/xorg.conf" as well(not need to add "").
And show me it's each result.

For example,

(yaboot.conf)
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

(xorg.conf)
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

and following.

---

### Post by stream303 on 2008-11-03
> **chrisme52 said:**
> Please help as this is the first time I've installed on a Mac.

Be sure to be patient - it can be done, but it might be best to rule out some variables out so you don't throw it through the window.  A G3 for a first-time install can try your patience. :)

Which model do you have?  How much memory is in it, and is the hard drive original, or a replacement that is larger than 128gb?  You may want to check the following to get some specs on your box:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

There is the possibility that you'll be hand-editing some files, maybe do manual repartitioning, etc.  Just want to let you know what you might be in for - but it can be done.  Be sure to see the old PPC message archives forum for some good hints too..

---

