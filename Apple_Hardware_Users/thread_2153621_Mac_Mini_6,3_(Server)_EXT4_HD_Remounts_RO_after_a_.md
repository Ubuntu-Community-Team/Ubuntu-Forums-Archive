---
title: "Mac Mini 6,3 (Server) EXT4 HD Remounts RO after a few minutes"
date: 2013-06-11
forum: Apple Hardware Users
---

### Post by ghetto2ivy on 2013-06-11
Running 13.04 but issue existed with 12.04 

After 5 or so minutes booted up, Ubuntu has trouble writing to the Journal and the drive converts to read only. Hard to post dmesg since dmesg sometimes becomes read only before the error.

Normally, I'd suspect hard drive failure, but in Os X it passes all the hardware diagnostics, as it does from a USB drive boot. In 12.04 i had assumed some odd kernel bug and went ahead and modified fstab to continue on errors, don't want to do that anymore!

Not sure what gives!

---

### Post by ghetto2ivy on 2013-06-11
From dmesg:

> [  451.621946] EXT4-fs error (device sda1): ext4_ext_check_inode:467: inode #37: comm duplicity: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)
[  451.621953] Aborting journal on device sda1-8.
[  451.622077] EXT4-fs (sda1): Remounting filesystem read-only
[  451.622457] EXT4-fs error (device sda1): ext4_ext_check_inode:467: inode #37: comm duplicity: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)
[  451.622769] EXT4-fs error (device sda1): ext4_ext_check_inode:467: inode #39: comm duplicity: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)
[  451.623034] EXT4-fs error (device sda1): ext4_ext_check_inode:467: inode #39: comm duplicity: bad header/extent: invalid magic - magic 0, entries 0, max 0(0), depth 0(0)


---

