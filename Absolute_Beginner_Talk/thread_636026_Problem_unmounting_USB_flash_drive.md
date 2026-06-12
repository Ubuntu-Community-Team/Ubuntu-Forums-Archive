---
title: "Problem unmounting USB flash drive"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Reshuken on 2007-12-09
Hello guys. Today while using my USB flash drive normally I couldn't eject it properly; it gives me an error saying that it cannot unmount the volume. I don't know what could be the cause, so I appreciate any help. By the way, it's not only with this USB drive, it happens with others that I have tried too.

Thanks in advance.

---

### Post by Countra on 2007-12-09
some one gave a [COLOR="Red"]bump[/COLOR] to the nearest bum :)

---

### Post by rkd on 2007-12-09
I don't understand the problem, but a Google search for the two error messages led me to this page:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368)

That says the problem can be caused by volume or file names that have unusual characters in them (such as apostrophe or any non ASCII character, as I understand it).  A later entry in the thread says that they cured the problem by removing

/media/.hal-mtab

I don't know what /media/.hal-mtab is so I don't know how safe it is to remove it.  Perhaps you should make a copy of it somewhere then remove it to see whether that fixes the problem without causing other problems.  Put it back if it causes other problems.  Perhaps further searches for the error messages or for /media/.hal-mtab would turn up more information about the problem, but I stopped at this point.

---

### Post by Reshuken on 2007-12-09
OK. I removed the file (/media/.hal-mtab) and it seemed that it fixed the problem but it gave some errors regarding the other partition of my HD with WinXP on it (it was mounted by default and it couldn't be unmounted because it wasn't mounted by Hal or something).

Anyway, I restored the file and the problem seems to be gone because I don't get the error message again. But, I find that the drive it's still listed, although it seems that it no longer is mounted (I know this because it won't give me problems when I unplug my flash drive). Any way to fix this?
It's not that it's a big deal, but it is kinda annoying. Thanks again.

---

### Post by rkd on 2007-12-09
Sorry, I don't know enough about Ubuntu yet to help further on this.  I hope someone else looks at this thread and can help further.

---

### Post by nsilva on 2007-12-09
You can try to force the unmount
```
sudo umount -f /media/partition
```

or try to do the lazy unmount (read more in the man page)
```
sudo umount -l /media/partition
```

---

### Post by Reshuken on 2007-12-09
Thanks for the tip, but I guess I was vague in my last post.

You see, I was able to fix the problem regarding the partition by putting again the file I had removed and although the problem with my flash drive seems to be gone, because I don't get any error message when I eject it (the icon on the desktop disappears and all), the flash drive is still listed as plugged in. Granted, I don't get any error when I physically unplug my flash drive anymore, so it's safe to assume that it works correctly in that regard.

Hope that clears some things up. So, any advice?

---

### Post by Countra on 2007-12-21
postomancer *bump*

---

### Post by jeffus_il on 2007-12-21
Are you sure that there are no programs accessing the usb drive, close all file manager windows that may be displaying the drive, also it may take a little while for the open buffers on the drive to be written so wait a bit after unmounting.

---

### Post by tech9 on 2007-12-21
> **nsilva said:**
> You can try to force the unmount
```
sudo umount -f /media/partition
```or try to do the lazy unmount (read more in the man page)
```
sudo umount -l /media/partition
```

usually a simple umount should do the trick...

most likely the partition should show as sdb1

to verify

```
sudo fdisk -l
```

then command would be...

```
sudo umount /dev/sdb1
```

---

