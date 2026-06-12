---
title: "Macbook Pro 8,3 graphics card switching under 13.10:"
date: 2014-02-13
forum: Apple Hardware Users
---

### Post by spitfirejunky on 2014-02-13
So I've managed to get my Macbook Pro EFI booting Ubuntu 13.10 with near perfection. Unfortunately, the Thunderbolt (Mini DisplayPort) doesn't work and I suspect this has something to do with my failure to get the discrete graphics running.

My current configuration gets my screen up using the following "outb" directives in GRUB:

```

outb 0x728 1
outb 0x710 2
outb 0x740 2

```

Including the amendment:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0"
```

This gets the integrated graphics card working with i915. However, whether or not I include "radeon.modeset=1", the Radeon is stuck in a state where no drivers are assigned to it but it's detected.

I've experimented with a million things including patching and compiling the source code from AMD Catalyst website, all of which either bricked or nearly bricked my laptop. The only thing I haven't tried is vgaswitcheroo, which I can't for the life of me get to manifest.

Attached are a couple of shots of where I'm at. Does anyone have any suggestions? Feel free to ask me for more details.

Thanks.

---

### Post by spitfirejunky on 2014-02-13
OK so I was clever enough to note the distinction between plain EFI booting and EFI **stub** booting.

Since my setup isn't possible without EFI booting (there is a way to throttle Macbooks to BIOS but that's moot here), the solution will only work for those of you with Ubuntu set up correctly with EFI booting.

Install rEFInd under Ubuntu using the Debian package: [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

```
sudo dpkg -i refind_0.7.7-1_amd64.deb
```

Read everything carefully to make sure there were no errors. If all went well, restart.

You will see a new rEFInd splash screen, the same one you should remember when you first replaced Mac OS X with Ubuntu.

There should be multiple Ubuntu boxes. If you look at the caption of each of the boxes, you will notice that they point to different boot locations. EFI **stub** booting happens when you select those boxes that point *directly* to your kernel partition. The GRUB box corresponds to your former setup with the i915 magic, but these latter boxes give you radeon magic, and consequently Thunderbolt and Mini DisplayPort magic.

I can now use my TV with my Macbook Pro. =)

---

