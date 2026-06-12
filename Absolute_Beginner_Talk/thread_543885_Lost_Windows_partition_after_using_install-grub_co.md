---
title: "Lost Windows partition after using install-grub command"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by viperflyer on 2007-09-05
I was hoping to move GRUB from a hard-drive that is dying a slow death to a good drive which already has Windows XP installed on it. I used command "sudo grub-install /dev/hda1" hoping to install GRUB on this good drive and at the same time be able to use Windows XP. However, in the process I have lost the drive altogether. I tried uninstalling GRUB by booting from Windows XP CD but I don't see that partition at all to log in and use FIXMBR, instead it asks me to format the drive and install Windows from scratch. Has the drive been completely erased by using above command? Please help - I have been experimenting with Ubuntu for not too long and can't avoid using Windows until I hone my Ubuntu skills. Plus, much of my important stuff was on that drive which I don't have access to right now. Please help!

I am not sure if I need to configure the other GRUB and add Windows entry to it. If that's the case then how do I select that newly installed GRAB as I now have 2 GRUBs on 2 separate drives, right? I was able to access the other drive using ntfs-config 0.5.5 utility - not anymore.

---

### Post by celettu on 2007-09-05
Don't panic. Your XP installation is still there. What probably happened is that grub was installed on the MBR, without an entry to boot XP.

Best thing to do is add an entry to your grub configuration file. Open a terminal and type this:

```
sudo nano /boot/grub/menu.lst
```

It'll ask for your password.

In that file, add this at the bottom:

```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1

```

Now reboot.

Hope that helps.

---

### Post by viperflyer on 2007-09-05
Thanks a lot for a very quick reply. The boot menu already had the entry for the Windows XP and when I selected Windows, it presented with the same boon menu by recounting the default 10 seconds of timer. However, as your rightly pointed out GRUB was installed overwriting MBR and hence the issue. I was able to fix it using FIXBOOT C: command using Win XP install CD. I panicked earlier quite a bit because, I was really surprised that the XP boot CD didn't find Windows folder on C: drive and thought of it as unformatted drive. (any clue why this was the case?). However, I had another Windows installation on D: drive and I selected that folder for repair for the heck of it and gave FIXBOOT C: command which fixed it for me.

I see there are many threads on this issue but I had to create another one because I thought this was a unique problem. Anyhow, thanks very much!

---

