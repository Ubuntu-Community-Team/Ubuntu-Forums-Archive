---
title: "Read/write to external usb disk w. ntfs."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-05-14
I have an external USB harddrive with the ntfs filesystem. I have installed the ntfs configuration tool via Synaptic. When I connect the usb cabel the disk shows up on the desktop(as an icon), but it belongs to «root».

When I open nautilus as root(gksu nautilus) I still cant write to it. I have chcked the Enable write support for external device in the ntfs program. 

Any suggestion for what I can do?

Thanks:)

---

### Post by LaRoza on 2007-05-14
Any reason why you need ntfs? If you can not get ntfs to work, you can format it as FAT32 or EXT3.

If you do not have ntfs3g, you need it for writing, not reading, ntfs.

---

### Post by _sAm_ on 2007-05-14
*_Any reason why you need ntfs?_*
Yes, its not mine - I am only going to transfer some files to it. 

As I said the ntfs3g are installed(via synaptic).

---

