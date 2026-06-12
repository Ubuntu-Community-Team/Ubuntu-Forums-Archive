---
title: "[SOLVED] Can't install Gutsy with encrypted FS from alternate CD (64 bit)"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Golem XIV on 2008-02-15
Hi all,

I'm trying to install Gutsy with a fully encrypted FS using the Alternate CD for AMD64.  The procedure runs OK but at the end the computer turns off instead of rebooting and when I turn it on I get a "GRUB Error 15".

The interesting thing is that the Kubuntu Alternate CD (also 64 bit) installed fine, but I prefer "normal" (i.e. Gnome) Gutsy.

Oh and yes, I do have a 64 bit processor (AMD Turion x2).

Any ideas?

---

### Post by rok3R on 2008-02-15
Since you are not having any problems installing Kubuntu , Why dont you install the gnome Desktop on Kubuntu ?

```
sudo apt-get install ubuntu-desktop gnome
```

This will get u gnome desktop...

BTW y arent u using live CD?

---

### Post by Golem XIV on 2008-02-15
> **rok3R said:**
> Since you are not having any problems installing Kubuntu , Why dont you install the gnome Desktop on Kubuntu ?

```
sudo apt-get install ubuntu-desktop gnome
```

This will get u gnome desktop...

BTW y arent u using live CD?

I prefer not to mix KDE & Gnome.  I have some problems with Kubuntu and I hate the way the menus get all whacked out.

I'm not using the Live CD because you can't set full filesystem encryption from it.  You have to use the Alternate CD for that.

I'm currently looking at Truecrypt, it claims that as of v.5.0 it can do full FS encryption.

---

### Post by dstew on 2008-02-15
Is the file system encrypted right from the start? Can grub see files on the encrypted system?

---

### Post by Golem XIV on 2008-02-15
> **dstew said:**
> Is the file system encrypted right from the start? Can grub see files on the encrypted system?

I'm trying to set it up so that it's encrypted from the start.  I'm doing a clean install, overwriting whatever was on the disk before.  Something screws up, the computer shuts down (turns off) and when I turn it on again GRUB won't work (I've since found out that Error 15 is File Not Found)

---

### Post by dstew on 2008-02-15
Grub can only read normal file systems, like ext3. If you put the kernel image into an encrypted file system, grub won't be able to see it. I don't know much about encrypted systems though, so maybe you have an unencrypted /boot partition?

---

### Post by Golem XIV on 2008-02-15
> **dstew said:**
> Grub can only read normal file systems, like ext3. If you put the kernel image into an encrypted file system, grub won't be able to see it. I don't know much about encrypted systems though, so maybe you have an unencrypted /boot partition?

Sorry, I guess I wasn't clear enough.

I want to set up a clean install, only Ubuntu Gutsy, removing anything that was on the disk before.  I want this system to be completely encrypted (except for the /boot partition, of course).  This can be achieved only with the Alternate CD.

After I boot from the alternate CD, I select the LVM encryption option, accept all the defaults and let it set up the system.  Once it has finished the installation, the system is supposed to reboot but instead it shuts down.  When I turn it on I get a "GRUB Error 15" message.

This same procedure works when I use the Kubuntu Gutsy alternate CD and it correctly creates the (unencrypted) /boot partition and the encrypted partition(s) where everything else is.  This system was working fine, but as I said, I would like to avoid installing gnome-desktop on it if at all possible.

I have checked the CD for defects and it has none.  I also downloaded and burned a second copy with the same results.

---

### Post by dstew on 2008-02-15
OK, thanks, I get it now. So it should work, since there is a separate /boot partition. The install failure sounds like something that might happen if the installer runs up against some limit, like it runs out of memory or disk space. The other possibility is that the eject-disk-reboot part depends on some installer routines that don't work with the hardware it finds itself in. But if you want to get crazy, you can install directly over the internet, using the unetbootin utility ([see this thread]("http://ubuntuforums.org/showthread.php?p=3400831")). I don't know if this will be any different, but since you won't have a disk, you won't have problems at the eject-disk stage of the installation. I did an internet install once, and it was like the Alternate Install CD. I don't know if you can do your encrypted install this way, but maybe.

---

### Post by Golem XIV on 2008-02-19
The problem sorted itself out in an unexpected way.

I have managed to install the system as described.  At that moment I didn't see what did I do to solve this glitch, but I was happy that my encrypted Ubuntu worked.  Then I started playing with alsa and completely hosed the sound system.  No big deal, I said to myself, just reinstall (you can see I come from a Windows background :)).  On reinstall, the same problem appeared.

AHA! said I, probably what happened was a glitch of the partitioner - after all, it's creating the same partitions, same sizes, etc. - it may have gotten confused.

Pulled out the Vista recovery CDs and let them wreak havoc on my system.  Remember, I was trying to nuke the previous partitioning scheme.

Once the Recovery CDs repartitioned and reformatted the drive, I cancelled the installation and made sure that the previous scheme was good and dead (by booting from the Live CD).  So far so good.  Stick in the Alternate CD, boot, select options...  same problem.  System shuts down, only this time when I turned it on I didn't get "GRUB Error 15", I just got a blank screen.

Well, we're getting somewhere, I said to myself.  Obviously the installer could/would not install GRUB on my system for some reason.  The GRUB error I was getting previously was my old GRUB (from a "normal", unencrypted Ubuntu install) no being able to find the kernel, since it is now hidden and garbled.

I tried several times to reinstall with no success.  The last time I tried I was doing some other stuff around the house and I would only drop by the computer to see how is the installation going on.  I booted, selected the install option and went away.  After 1/2 an hour I came back, selected language and keyboard, went off.  1/2 hour later, selected the next option, went away... You get the idea.

To cut a long story short, by not doing anything right away and letting the prompts "sit" idle for a while the system miraculously ended the installation correctly.  I rebooted, typed in my passphrase and the system booted fine.  It's been working satisfactorily for several days now and I can't see any performance degradation on account of the background encryption/decryption.  I am a happy camper :)

What I think happened is that one or several of the installation scripts were still running when the prompts were presented and the option selecting would kill/corrupt it (them).  By not entering my selections right away, I gave the script(s) time to finish correctly and configure the system accordingly.

I am posting this in case someone runs into a similar problem.  Thanks to all that tried to help.

---

