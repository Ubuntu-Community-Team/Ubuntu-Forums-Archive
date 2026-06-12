---
title: "MyBook with Ubuntu &amp; iMac"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2008-03-19
I need advice on partitioning of large MyBook for dual use in backing up Ubuntu laptop but also using TimeMachine on iMac.  Because of different filesystems used by each, can I do this?  Need to use gparted maybe?

(the drive is 1TB; iMac drive is 500GB but don't intend to mirror whole drive, just back up selected files; Ubuntu laptop drive is 160GB and again only to backup selectively)

thanks for any suggestions!

---

### Post by djbsteart1 on 2008-03-19
Because of the powers that be, I think that OSX can read fat32, which ubuntu can aswell. It isn't the greatest filesystem, but it suffices, So ubuntu should be able to partition the drive happily, or use gparted if you prefer. There could well be a FS that OSX and ubuntu have in commen but i am not sure.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-19
fat32 would work 
but hfs+ is mac os x default and i think gparted is working on support for it.

Edit : Just checked hfs+ is you can make em with it. and linux supports it i think.
i would try to use this first as long as you dont need to windows

---

### Post by flyingsolo on 2008-03-19
OK, so I got the hfs+ partition created and a Fat32 partition with apple disk utility but when I switch to the Ubuntu laptop, it doesn't 'see' (mount) the MyBook or either of its two partitions.  It should mount at least the Fat32 partition right?

---

