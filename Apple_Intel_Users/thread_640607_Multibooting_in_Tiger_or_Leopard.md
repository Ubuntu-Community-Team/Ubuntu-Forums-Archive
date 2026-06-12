---
title: "Multibooting in Tiger or Leopard?"
date: 2007-12-14
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-12-14
I already had my new MacBook set up to multi-boot three Linux OSes (including Gutsy) with OS X Tiger.
Then, disaster struck and my HD failed (on a 10-week old machine).
OK, so Apple replaced the HD and re-installed the OS X Tiger and I set about getting my Linux OSes back.
But, now I find that Boot Camp is now longer available as a free download and can only be used through Leopard.
OK, I've ordered Leopard and expect to get it early next week. However, I really would like to get Ubuntu working on Tiger while I'm waiting.

So, I have two questions:
1) Is there any way around the unavailability of Boot Camp in Tiger to repartition the MacBook HD to prepare it for dual-booting?
2) I had seen somewhere that Leopard was somewhat more reluctant than Tiger to accept Linux OSes in a multi-boot situation. Any truth in this?

Thanks
Paul

---

### Post by cyberdork33 on 2007-12-14
> **PaulFXH said:**
> 1) Is there any way around the unavailability of Boot Camp in Tiger to repartition the MacBook HD to prepare it for dual-booting?
gparted and partedmagic can shrink hfs+ partitions. You can also use the OSX commandline utility (which is what bootcamp is a frontend to):
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

> 2) I had seen somewhere that Leopard was somewhat more reluctant than Tiger to accept Linux OSes in a multi-boot situation. Any truth in this?
Not really... I guess there are a few obstacles, but once you get it working, it is like multi-booting with tiger. Although, you might just wait, as we all had troubles doing an 'upgrade', but instead had to start from scratch with Leopard.

[http://ubuntuforums.org/showthread.php?t=596520](http://ubuntuforums.org/showthread.php?t=596520)
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

---

### Post by PaulFXH on 2007-12-14
@cyberdork33
Thanks for that useful information.
I'll probably fiddle around with PartedMagic and see if I can install Gutsy.
Then I'll clean install Leopard when I get it.
I'm in the fortunate position here that I'm doing this solely for fun. If I mess up, nothing of any consequence is lost.

---

### Post by PaulFXH on 2007-12-15
Yesterday you said
> gparted and partedmagic can shrink hfs+ partitions.
Well, I tried this on my MacBook with Partition Magic and although the usual Gparted stuff came up, the Resize/Move command was unable to do anything on the hfs+ partition.
Indeed, the permitted maximum and minimum sizes given for this partition were both stated to be exactly the same as the existing size. This obviously suggests that no shrinking of this partition is going to be allowed.
Am I overlooking something here?

Thanks
Paul

---

### Post by PaulFXH on 2007-12-15
OK, it seems you have to disable journaling beforehand on the hfs+ volume you want to resize.
Anyway, it's worked now and I've set up my ext3 partitions.
Actually, given that this free utility has worked so easily, what's the big deal about boot camp?

---

### Post by cyberdork33 on 2007-12-15
> **PaulFXH said:**
> boot camp?
  it isn't a big deal in my book. Especially now that you can just use Disk Utility (in Leopard) and non-destructively add partitions if you really want to do it from the Mac side.

---

### Post by tiiim on 2007-12-16
> **PaulFXH said:**
> OK, it seems you have to disable journaling beforehand on the hfs+ volume you want to resize.
Anyway, it's worked now and I've set up my ext3 partitions.
Actually, given that this free utility has worked so easily, what's the big deal about boot camp?

Boot camp is just the front end, leopard allows you to resize via disk utility. However if you can use the terminal its exactly the same just no fancy graphics. :)

---

