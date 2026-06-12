---
title: "[SOLVED] AAARGH! Firmware update on MBP ruined my ubuntu installation - HELP!"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by phonky on 2007-10-21
I knew I shouldn't do it...but I did!

I bootet on OSX few days ago, and the OSX update manager announced
a firmware update for my macbook pro. I knew it could perhaps somehow
affect my ubuntu installation, but then I thought, it couldn't be too dangerous...

Well, now, when I try to boot into Ubuntu (I use rEFIt and grub), I get this horror message:

[    22.952909] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    23.365116] Kernel panic - not syncinc: IO-APIC + timer doesn't work! Boot with apic=debug and report, then try to boot with noapic option

And then stops booting.....

I added an entry to grubs menu.lst to with a noapic debug option, which boots, but with weird
effects on the screen (blurries, no network, bad responsiveness, no sound). Did it only once though.
Recovery mode boots, but I don't know what to do...

Has anyone an enlightening idea???
Would be enourmously grateful...

---

### Post by cyberdork33 on 2007-10-21
> **phonky said:**
> I knew I shouldn't do it...but I did!

I bootet on OSX few days ago, and the OSX update manager announced
a firmware update for my macbook pro. I knew it could perhaps somehow
affect my ubuntu installation, but then I thought, it couldn't be too dangerous...

Well, now, when I try to boot into Ubuntu (I use rEFIt and grub), I get this horror message:

[    22.952909] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    23.365116] Kernel panic - not syncinc: IO-APIC + timer doesn't work! Boot with apic=debug and report, then try to boot with noapic option

And then stops booting.....

I added an entry to grubs menu.lst to with a noapic debug option, which boots, but with weird
effects on the screen (blurries, no network, bad responsiveness, no sound). Did it only once though.
Recovery mode boots, but I don't know what to do...

Has anyone an enlightening idea???
Would be enourmously grateful...
Try resetting the SMC 
[http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

---

### Post by phonky on 2007-10-21
Ahemmm. sorry....

the reason for the problem was a totally different one.

As I am also using computers to make music, I installed the
ubuntustudio-audio package.

This installed a new (realtime- kernel 2.6.22-14-rt ) kernel in my system, which was
going to be booted by default. And this kernel seems didn't really
want to boot...

So the standard kernel works fine. Sorry for yelling in panic!

---

