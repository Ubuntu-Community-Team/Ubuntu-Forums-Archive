---
title: "Installing Win7 after Ubuntu"
date: 2011-04-13
forum: Any Other OS
---

### Post by Kzap333 on 2011-04-13
Hey guys,
I've been off the forum for a long while, so forgive me if I'm posting this in the wrong place.
I have a couple of questions I would like to raise about installing Windows 7 on a computer with Ubuntu and XP already installed.
First off my situation is as follows:
I like using Ubuntu for everything on my computer but I do a lot of video editing and need to have a windows partition for a couple of programs, mainly Adobe After Effects and Premiere.
Anyway recently my XP partition has been playing up and it eventually blue screened on me, Ubuntu is still working fine. Although I could probably fix this I thought it was about time I updated to the 64bit edition of Windows 7.
I thought this would involved Windows reformatting all my hard drives but a friend of mine informed me that I could just install Windows 7 on one partition and leave everything else in tact.
Now I've backed almost everything up just in case but my questions are:
 - Can I install Windows 7 on the old XP partition?
 - If I do this will all the other partitions stay in tact?
 - Most importantly will GRUB recognize the new Windows 7 OS OR Windows overwrite GRUB anyway?
 - Basically will I end up having to re-install Ubuntu after installing Win7?

Finally are there any other thing's I need to keep in mind when installing Windows 7.

Thanks in advance.

---

### Post by fdm on 2011-04-13
- Can I install Windows 7 on the old XP partition?

Yes, you can. I'd format just for the ease, but booting into Linux and deleting files installed by WinXP has worked fine for me in the past. You might look into running the dos diagnostics tool from your hard drive's manufacturer and a memtest to ensure hardware was not the cause of WinXP's instability.

- If I do this will all the other partitions stay in tact?

Yes, as long as you don't delete them by accident.

- Most importantly will GRUB recognize the new Windows 7 OS OR Windows overwrite GRUB anyway?

Yes, Win7 will overwrite your GRUB as any Windows installation will. There are many ways to reinstall it, and it should see Win7 automatically afterwards.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

- Basically will I end up having to re-install Ubuntu after installing Win7?

No, just reinstall GRUB using info from the forum or the link above.

---

### Post by Kzap333 on 2011-04-13
> **fdm said:**
> - Can I install Windows 7 on the old XP partition?

Yes, you can. I'd format just for the ease, but booting into Linux and deleting files installed by WinXP has worked fine for me in the past. You might look into running the dos diagnostics tool from your hard drive's manufacturer and a memtest to ensure hardware was not the cause of WinXP's instability.

- If I do this will all the other partitions stay in tact?

Yes, as long as you don't delete them by accident.

- Most importantly will GRUB recognize the new Windows 7 OS OR Windows overwrite GRUB anyway?

Yes, Win7 will overwrite your GRUB as any Windows installation will. There are many ways to reinstall it, and it should see Win7 automatically afterwards.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

- Basically will I end up having to re-install Ubuntu after installing Win7?

No, just reinstall GRUB using info from the forum or the link above.
Thank you very much. The instructions on that link seem simple enough. Should be a lot easier than I expected, so glad I don't have to reinstall everything :).

---

