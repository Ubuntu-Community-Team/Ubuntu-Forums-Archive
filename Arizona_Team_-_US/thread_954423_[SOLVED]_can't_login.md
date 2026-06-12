---
title: "[SOLVED] can't login"
date: 2008-10-21
forum: Arizona Team - US
---

### Post by msgtucson on 2008-10-21
I just downloaded and installed hardy heron 8.04.1 on my vm. All went well, but I was never prompted for a username and password. I get to the login screen and can't get past that. New to Ubuntu.

---

### Post by FutanariKitty on 2008-10-21
Assuming you're using GRUB as your bootloader in your VM, you can drop into single user mode relatively easily. During boot, press ESC when prompted by GRUB, bringing up the boot menu. Highlight the Ubuntu 8.04.1 entry, tap 'E' to edit the entry. Highlight the line that begins with 'kernel' then add the keyword 'single' to the end of the line. Tap the enter key to return to the listing, and press 'B' to boot the altered entry. (You may want to double check GRUB's documentation, I don't have a PC to test those instructions on).

If all goes well, the system will begin to boot and drop you to a command line with root access. From there, it's simple.

```
adduser <user>
passwd <user>
```

Reboot and have fun! If that doesn't work, you could always just try reinstalling. I seem to remember ages ago the Ubuntu installer giving me similar issues.

---

### Post by msgtucson on 2008-10-22
Thanks,
Guess I had a bad install. Reinstalled and works fine

---

