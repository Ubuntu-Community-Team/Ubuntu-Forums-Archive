---
title: "Can I use the same SWAP partition for two distros"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-19
Hi, I have a laptop with appr. 40GB of space, and I would like to run ubuntu with 30 GB and the run KUbuntu with the rest. And yes I want them separately in a dual boot. If not it [goes wrong]("http://ubuntuforums.org/showpost.php?p=2872887&postcount=6")

The question is: Can I use the same 1gb SWAP drive for both installations or would I have to make a swap drive for each of them?

---

### Post by kevinlyfellow on 2007-06-19
Yep, can be shared.  In fact it should do it all almost automatically.  Check to make sure its in /etc/fstab

---

### Post by floke on 2007-06-19
It's fine - they will both detect and use the same swap partition.

---

### Post by tgalati4 on 2007-06-19
I do it all the time with several distros.  You should be aware of one thing:  Suspend-to-disk.  If one distro session is put to sleep and the image is written to disk, then you boot into a different distro, it clobbers your sleep session.

This is normally not a problem for a few reasons:

1.  Resuming from disk takes almost as long as booting cold.  There's really not enough of a time savings to do it.

2.  Your open pages and applications can normally presevered in a "session" when you logout so when switching distros, you can still keep most of your favorite apps preloaded.

3.  If you are constantly switching distros, then you probably don't have too much invested in any single one to be worried about how your desktop session is set up.

Swap partitions are vital for testing Live Distros as the swap will be detected and used for a larger ramdisk, making your computer run faster than running from CD alone.

---

### Post by Luffield on 2007-06-21
Good to know it's possible (I want to install Debian and Ubuntu on my new computer).
But to the original poster: why don't you simply install the kde-desktop package in Ubuntu and select the desktop you want to use when you log in? Wouldn't it be more efficient?

---

### Post by bootslap on 2007-06-21
Yes , you can. I have I GB swap partition and it is doing fine with so many live distros that I use.

---

### Post by atria on 2007-06-21
If the swap isn't utilised properly, you can always use it with swapon

```
man swapon
```

---

### Post by anaconda on 2007-06-21
Yes, but there is 1 problem!!!

When you install the 2nd linux it will format the swap partition again, and that means the UUID of your swap partition changes! And the first linux cant find it anymore.

This can be solved by editing your /etc/fstab -file and either changing the UUID of your swap partition to be correct or (better) changing the UUID to the old style of:
/dev/sda2 instead of the UUID

Note your swap partition prpåably isb't sda2, check what it is and change the sda2 to your swap partition.

---

### Post by KIAaze on 2007-06-21
> **anaconda said:**
> Yes, but there is 1 problem!!!

When you install the 2nd linux it will format the swap partition again, and that means the UUID of your swap partition changes! And the first linux cant find it anymore.


??
Then why did I never have any problems when installing multiple distros?
I never even heard of all this UUID stuff.
Does it depend on how you install them (chain loading or not)?

---

### Post by kasperbs on 2007-06-21
> But to the original poster: why don't you simply install the kde-desktop package in Ubuntu and select the desktop you want to use when you log in? Wouldn't it be more efficient?
For a few reasons actually:
I only wanted KDE so that I could install [LinuxMCE Beta2]("http://linuxmce.com/").
If you install the KDE desktop inside Ubuntu, all the software from KDE will also be installed in your Ubuntu environment (if you dont mind that, then its fine)
The other reason was that I wanted to be able to use KDE without worrying about my Ubuntu system. because setting up something like Linuxmce will need a lot of configurations and since it is still in beta it might need quite a few hacks to work the way I wanted it. And since some of the files are shared if you install KDE inside Ubuntu and didn't want to risk that.

---

