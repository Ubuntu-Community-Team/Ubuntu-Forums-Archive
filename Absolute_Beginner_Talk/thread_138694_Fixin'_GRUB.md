---
title: "Fixin' GRUB"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-02
I am trying to follow this tutorial: [http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33) My partitions look like this from the Ubuntu install window: *#1 Primary NTFS /media/hda1 #5 Logical NTFS /media/hda5 #6 Logical SWAP swap #3 Primary etx3 /media/hda3 #4 Primary (lightening bolt)* My question is: How should this command look so it reflects the specifics of my partition? *mount /dev/ide/host0/bus0/target0/lun0/part5 mounted* Thanks in advance.

---

### Post by mlind on 2006-03-02
If you can boot on your ubuntu, running "sudo update-grub" should ideally fix your
problems. If your GRUB is screwed and you can't boot into Ubuntu, see [this thead]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") instead.

Your linux /boot partition is probably /dev/hda3, grub will use assigment (hd0,2).
If / and /boot partitions are same it looks something like:

```

title           Ubuntu, kernel 2.6.15-16-386
root            (hd0,2)
kernel          /vmlinuz-2.6.15-16-386 root=/dev/hda3 ro
initrd          /initrd.img-2.6.15-16-386
boot

```

---

### Post by Cousindaddy on 2006-03-02
I'm typing this from Knoppix LIVE.  How can I execute *sudo update-grub* from here? BTW I tried installing another version of Ubuntu overtop of FreeBSD which didn't work...so consequently neither did the option of re-installing GRUB from the installation disk.
Also, XP repair doesn't work either...I ran a repair (FixMBR, Fixboot, & BootCFG)  and now it says NTLDR missing.  I think my HD is fried...(it smells a bit like KFC)...

---

### Post by mlind on 2006-03-02
update-grub won't do it if you're not booted on your current linux install.
try excecuting */sbin/grub-install* instead. It needs install device as
a parameter, which is usually the harddrive that's first boot device.
like /dev/hda.

If you went playing with XP's tools, I recovered partition once with
Fixboot (or was it FixMBR?). But those definetly work too. You will
lose your grub boot loader, so you need to boot into your ubuntu
using rescue mode.

You should have searched the forums before doing that, there's
about dozen threads about same problem.

---

### Post by Cousindaddy on 2006-03-02
I reinstalled FreeBSD.  Now BSD's bootloader lists DOS, Linux & FreeBSD as the options.  DOS and FreeBSD options work okay (XP & BSD boot when selected), but for some reason it won't boot to Ubuntu. I did some searching and found that BSD's bootloader can't be configured.  So, I don't really know what to do at this point.  If I do a re-install of Ubuntu I'm afraid I'll lose everything I have there.  I don't see another way to get GRUB back up and running.
I'm using Ubuntu Live right now...can I mount a /dev from here and fix things?

---

### Post by mlind on 2006-03-02
did you follow the link that's on my first post? It should describe how you recover
your install using ubuntu livecd.

---

### Post by mlind on 2006-03-02
especially look part which says "Preparing Your Working Environment"

---

