---
title: "install ubuntu on compressed root file system"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2007-06-09
how do i install ubuntu on a compressed root file system. is their a way to have said file system read/write. what will i need to do to the kernel for this to work. i have an old computer with an even older harddrive and the person only feels safe using ubuntu instead of some other linux. as you can tell i know a little linux but not enough to do this. any help will be very much liked. thank you for taking the time to read this.

---

### Post by reacocard on 2007-06-09
I do not think this is possible. I was looking into doing this myself a little while ago, and came up with very little of use. Ext3 and ReiserFS do not support transparent compression, in fact, the only linux FS I found that supports transparent compression was ZFS, but currently ZFS cannot be booted from, and is thus useless for the root partition. Maybe in a year or two boot from ZFS will be possible, but for now it is not.

---

### Post by FleetAdmiral74 on 2007-06-09
I am not sure about a compressed filesystem...but what about something like xubuntu? Made for lower hardware, that might work, still based and supported off of Ubuntu. How much space are we talking about here?

---

### Post by emparq on 2007-06-10
> **reacocard said:**
> I do not think this is possible. I was looking into doing this myself a little while ago, and came up with very little of use. Ext3 and ReiserFS do not support transparent compression, in fact, the only linux FS I found that supports transparent compression was ZFS, but currently ZFS cannot be booted from, and is thus useless for the root partition. Maybe in a year or two boot from ZFS will be possible, but for now it is not.

Are you sure it's not bootable? Sun/Apple recently announced Apple's upcoming OS X Leopard is going to use ZFS as its default file system.

[http://gizmodo.com/gadgets/apple/zfs-now-default-file-system-in-apples-os-x-leopard-266531.php]("http://gizmodo.com/gadgets/apple/zfs-now-default-file-system-in-apples-os-x-leopard-266531.php")
[http://www.engadget.com/2007/06/07/sun-says-apple-is-switching-to-zfs-in-leopard/]("http://www.engadget.com/2007/06/07/sun-says-apple-is-switching-to-zfs-in-leopard/")

Of course, it's possible they might still be using HFS+ for the boot partition, but it sounds to me like they're going all-out ZFS now (something that I think would benefit the linux world a ton, from all the wild praise I've been reading about it).

---

### Post by reacocard on 2007-06-10
> **emparq said:**
> Are you sure it's not bootable? Sun/Apple recently announced Apple's upcoming OS X Leopard is going to use ZFS as its default file system.

[http://gizmodo.com/gadgets/apple/zfs-now-default-file-system-in-apples-os-x-leopard-266531.php]("http://gizmodo.com/gadgets/apple/zfs-now-default-file-system-in-apples-os-x-leopard-266531.php")
[http://www.engadget.com/2007/06/07/sun-says-apple-is-switching-to-zfs-in-leopard/]("http://www.engadget.com/2007/06/07/sun-says-apple-is-switching-to-zfs-in-leopard/")

Of course, it's possible they might still be using HFS+ for the boot partition, but it sounds to me like they're going all-out ZFS now (something that I think would benefit the linux world a ton, from all the wild praise I've been reading about it).

I know the currently stable version is unbootable, maybe they've added it in the devel version.  If that's so, then it's just a matter of time before it becomes available in Ubuntu.

EDIT: Wikipedia to the rescue: [http://en.wikipedia.org/wiki/ZFS#Solaris_implementation_issues](http://en.wikipedia.org/wiki/ZFS#Solaris_implementation_issues)
So it's not available in the stable, but it is in the development version.

---

