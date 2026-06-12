---
title: "Kubuntu LiveCD Display Problem"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-08
Currently, I only have recent Kubuntu CD's, so I was trying them out on my new computer.  I honestly don't like KDE in anything but its look, so I was considering installing Kubuntu and then apt-getting the Ubuntu desktop.

Now, when I booted the CD, the screen was huge.  I have a 17 inch monitor, and the large size looked terrible.  I think the resolution must have either been 800x600 or 640x400.  Is this a driver thing, or did it just arbitrarly give me such a low setting?  Can this be fixed?  I have a recent ATI card.

---

### Post by jISh on 2006-09-08
It's alright, the default Xorg on the LiveCD couldn't figure out your monitor info. Easy to get working once you've installed Ubuntu.

Have your monitor's vertical/horizontal sync info handy (look in manual or google your monitor brand/model).

---

### Post by Darklighter137 on 2006-09-08
Hmm, okay.  My ATI card isn't an issue?

---

### Post by jISh on 2006-09-08
Shouldn't be. In fact, the CD doesn't even load ATI or nVidia drivers. You have to install them after you install Ubuntu. It's purely a monitor thing, happens to most people.

---

### Post by Darklighter137 on 2006-09-08
> **jISh said:**
> Shouldn't be. In fact, the CD doesn't even load ATI or nVidia drivers. You have to install them after you install Ubuntu. It's purely a monitor thing, happens to most people.

Great.  Now, about my computer itself.  It is an HP computer, and it comes with that strange boot recovery thing, and has a hidden partition for backing up data.  Will that affect an install?

---

### Post by jISh on 2006-09-08
No. You can delete that partition if you want. I have an HP and I totally nuked that partition. 

Keep it if you want to be able to reinstall Windows, either way it shouldn't present a problem.

---

### Post by Darklighter137 on 2006-09-08
The bootloader won't be an issue either?  I mean, the Windows side will work just fine?  Can I use those akward recovery disks (was it normal to have to make 16 of them?) to restore my computer after install?

---

### Post by jISh on 2006-09-08
To be honest, if for example you wipe everything except the recovery partition, and later decide to re-install Windows from that partition, I can't promise that your master boot record would be reverted. Windows always overwrites the MBR during install, but using a recovery CD is not a regular install of Windows, it's more of just extracting a prebuilt install.

If you install Ubuntu without wiping your current install of Windows (assuming you have one) there shouldn't be any problems with the boot loader.

---

### Post by Darklighter137 on 2006-09-08
Okay, thanks. ^_^

---

