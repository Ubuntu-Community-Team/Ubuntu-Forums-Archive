---
title: "I have Ubuntu and Vista.... I want Ubuntu and XP"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by c_olin on 2007-10-03
I bought an HP dv9000 which came with Vista (yuck...)... and I was told that if I dual booted with Vista and Ubuntu, I would be able to ditch Vista and do a clean install of XP without touching my Ubuntu/grub.

Can anyone point me in the right direction?

---

### Post by ryanVickers on 2007-10-03
XP is kind of random this way - sometimes it overwrites the GRUB (easy to fix - Super Grub Tool), and sometimes it doesn't.  If it doesn't, then just add a boot option for it in grub under linux  :)

1. Remove Vista
2. Install XP (all the while leaving ubuntu alone)
3. Re-create grub with Super Grub Tool (I think it's called)
That *should* do it! :)

---

### Post by jinx099 on 2007-10-03
> **ryanVickers said:**
> XP is kind of random this way - sometimes it overwrites the GRUB (easy to fix - Super Grub Tool), and sometimes it doesn't.  If it doesn't, then just add a boot option for it in grub under linux  :)

1. Remove Vista
2. Install XP (all the while leaving ubuntu alone)
3. Re-create grub with Super Grub Tool (I think it's called)
That *should* do it! :)

You can even repair grub with the ubuntu liveCD:  'sudo grub'

---

### Post by forrestcupp on 2007-10-03
> **jinx099 said:**
> You can even repair grub with the ubuntu liveCD:  'sudo grub'

That's how I did it.  I don't think you're going to get away with not having to repair grub.

---

### Post by FizzerJE on 2007-10-13
Hello

Very new to this forum was looking for a solution to an issue when I came across this thread.

I have JUST literally installed ubuntu on a DV9000 series (DV9590ea).

Currently I have Vista XP and Ubuntu triple booting. I used the Gutsy 7.10 build as I could not seem to load the 7.04 and get the livecd to run.

Used the guide on this excellent forum and it worked a treat.

The WiFi worked straight away no other drivers which quite surprised me. Excellent work by the people working on Ubuntu.

Here is a link to an excellent post with links to downloading all the drivers you need to install XP on a DV9000 series laptop.

[XP on 6500 / 9500 Series]("http://forum.notebookreview.com/showthread.php?t=140131")

Worked excellent for me BUT as HP has locked down the BIOS you can't turn SATA mode off Sooooo as their is no SATA support at boot on XP the only alternative is a USB floppy drive,

BUT the guide i linked you too shows you how to slipstream SATA support in XP using nLite,

Hope this helps.

---

