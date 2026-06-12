---
title: "Grub Error 17 after upgrade"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by vavroom on 2007-04-12
I did the updates pushed by Ubuntu 6.10 today.  I unfortunately didn't note what the updates were (and not sure how to find it, I assume it's logged somewhere, don't know where).

Upon booting back up, I got Grub fine, but suddenly had several choices that weren't there before (as if I had attempted to install or reinstall Ubuntu).

I selected one (though got the same response on all).  And got Error 17, cannot mount partition.

I went and edited the /root through Grub, from (hd0,4) to (hd0,5), and I was able to boot up.  But before I booted up, I saw several lines that I don't usualy see at boot up, and even received a command prompt.  I typed "exist" and it booted up without a problem!

Once in Ubuntu, I loaded a terminal and ran cat /boot/grub/menu.lst with the following result (default option not showing):
```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

This confirms that somehow, it's wanting to boot from (hd0,4).  Which, from memory, is what I've been using all along.

Then I had a look at  cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=45ED-E8CD /data vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda9 -- converted during upgrade to edgy
UUID=45F0-24C8 /documents vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=45E8-9775 /fujitsu vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=32e4bffd-3f67-4849-b530-8251ff659735 /home ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=3D4F-15F0 /ibm vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=FC80B5AB80B56CB0 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda8 -- converted during upgrade to edgy
UUID=f6998423-8618-4103-8976-0fce718c2f3e none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Which shows me there's no hda4, or am I reading this wrong???

I *think* I have a mess on my hands, but I don't understand how it got messed up, much less how to fix it properly.

Any assistance would be greatly appreciated.

Oh! I should point out, i'm dual booting into XP Pro SP2, which allows me to check back on the forum here if things go belly up

---

### Post by freebird54 on 2007-04-12
Don't know about the error - but hda6 (grub hd0,5) looks like your boot drive.  Grub counts from 0,0 not a1 like fstab.  Hope that helps!

Still no idea how it moved.... Guess you'll have to edit the Grub entries you decide to keep out of that list.

---

### Post by justleen on 2007-04-12
after the upgrade, you got a new kernel version, thats why it adds all the extra options on the grub menu - so you can go back to an older kernel..

if i look at your fstab, your ubuntu resides on hda6..

---

### Post by vavroom on 2007-04-12
Thanks guys.  Unfortunately, changing to (hd0,6) gives me an Error 15:file not found!

Forcing to go through (hd0,5) seems to get me in, but it is NOT booting up normally, (nor booting off for that matter)...

---

### Post by sudo-fu on 2007-04-12
This happened to me on 6.06, too. It was quite easy to solve, no big deal. It's probably because in your Grub /boot/grub/menu.lst you have those lines with a single #. A comment has ## at the beginning of the line. During updates, Ubuntu uses the single # lines as default settings. For useful background info read about the difference between GRUB and Linux device names [here]("http://ubuntuos.wordpress.com/2006/07/31/howto-modify-grub-and-menu-list/").

This solved it for me: boot from a live CD and edit your menu.lst. If hda6 is your ubuntu root device, you should change the line "root            (hd0,4)" to "root     (hd0,5)".

Hope it works for you, too.

---

### Post by vavroom on 2007-04-12
Hello sudo-fu,

My menu.lst doesn't have single #.  THere are several comments, which I haven't shown.  What I showed that had a single # is the fstab result.

I can change from (hd0,4) to (hd0,5), but while I manage to get in, as I said before, it doesn't boot right.  Among other things, it takes twice as long as it used to, and it interupts the boot sequence quiving me a prompt:
root@computername: ~#

After typing just about anything in at the prompt, the booting proper commances.

This just isn't how it should boot.  Which makes me hesitant to boot from (hd0,5).  Or which tells me something went seriously wrong.  Now, of all the kernels listed in my grub list, which all show (hd0,4), if I try them on 5, then *all* behave the same way.

I must say, I love Ubuntu, but this has me baffled.  And unhappy :(

---

### Post by freebird54 on 2007-04-12
I don't understand the interruption to the boot to ask for a prompt, but the speed issue can pehaps be traced to the file system checking on your Windows drives.  In your fstab file, the very last item on the line is a 0, 1, or 2.  If you change that item to a 0 on the vfat drives, it will speed things up at the least.  This means changing:

```
UUID=45F0-24C8 /documents vfat defaults,utf8,umask=007,gid=46 0 1
```

into
```

UUID=45F0-24C8 /documents vfat defaults,utf8,umask=007,gid=46 0 0
```

This can also be done with the ntfs partition - and leave the filesystem checks to Windows.

Perhaps the other problem will become clearer when out of the clutter of a slow boot.  Or at least we'll have more time to figure it out!

---

### Post by vavroom on 2007-04-12
Thanks freebird, I'll give that a try when I get home tonight

---

### Post by vavroom on 2007-04-13
Bit later than planned, couldn't get to my computer last night.  Tried booting from (hd0,5) this morning, and it worked like a charm, none of the other issues I had.

I'm puzzled.  

In any case, thanks people, for the great assistance and patience :)

---

