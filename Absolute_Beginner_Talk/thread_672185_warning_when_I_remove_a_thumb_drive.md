---
title: "warning when I remove a thumb drive"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by DVD-R on 2008-01-19
Hi gang,
I get a warning when I remove a usb thumb drive "unsafe removal"

There must be something I don't know because most win OS system don't give any warning when one removes a thumb drive.

what's up?  

Thanks :)

---

### Post by mcduck on 2008-01-19
Even in Windows you should always use the "Safely remove hardware"-tool in the system tray to avoid data loss when removing drives. With Ubuntu, right-click the drives icon on desktop and select "unmount" or "eject" to remove the drive.

---

### Post by mister_pink on 2008-01-19
To expand on that, this is an issue which is often debated. By default pen drives are mounted "no-sync", meaning that when you copy stuff to them it doesn't actually do it immediately. You might find that if you copy a small file to the pen drive and remove it without unmounting the file is gone when you plug it back in. The reason behind this is that it was meant to protect the flash from damage by repeatedly writing to it. Some people report that using sync on modern drives is fine though, but with the tiny amount of effort unmounting takes, I always just do that.

---

### Post by DVD-R on 2008-01-20
Thank you for your kind responses.
I had mis-interpreted the "unmount" process.
I thought that the system would not recognize the drive if I unmounted it,
So I was hesitant to take a chance on it.  

THANKS!!  :)

---

