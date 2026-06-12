---
title: "I installed ubuntu, and now I can't boot to either windows or ubuntu"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by duo8675309 on 2007-09-16
I'm really sorry if this has already been posted, but I can't get internet to work with my ubuntu live cd, and the only oportunity I have to use the web is over at my friends house, so as you can tell I'm under a limited time scedule. Now before I installed ubuntu, I had an 80g hard drive with Vista installed onto it. This is what I was booting off of. I also had a 160g hard drive that I stored media on (why am I talking in past tense? I still have these...) anyway. I just recently bought a 500g external hard drive to backup my files, and since I didn't think I'd need all 500g, I decided to install ubuntu on this. So I formatted the whole drive and installed ubuntu onto it, rebooted, and when it started back up GRUB would give me either error 22 or error 17 or I think error 2. Anyway, I went to the BIOS and set my boot order to boot off the CD Drive first, the 500g external second, and my 80g third. Now it says that there is no OS installed on my hard drive. I've installed ubuntu literally 15 times, and I'm pretty damn sure it's installed. I'm almost to the point of not even caring if I get ubuntu working or not. I just want my computer back. If there's a way to come out of this with ubuntu working then I'll be really happy, but at the moment I would be more than happy to just go back to windows. Thank you in advance for any advise you may have!

P.S. I know ubuntu probably won't run that well of an external hard drive. I don't expect it to. I just would like to have the option of running ubuntu when I start up my computer. Just as a change of pace.

---

### Post by GuitarRocker2562 on 2007-09-16
Ubuntu will not install to an external hard drive and jsut boot, you would need it setup in a special way that I don't know. If you want windows working and you have the Vista repair cd or dvd or whatever run that and run fixmbr. If you don't have this, you will need to make a new partiton on one of your internal drives and install ubuntu there, your problem is that grub can't boot itself from that external drive. If that doesn't make sense to you, just read more about how grub works.

---

### Post by duo8675309 on 2007-09-16
> **GuitarRocker2562 said:**
> Ubuntu will not install to an external hard drive and jsut boot, you would need it setup in a special way that I don't know. If you want windows working and you have the Vista repair cd or dvd or whatever run that and run fixmbr. If you don't have this, you will need to make a new partiton on one of your internal drives and install ubuntu there, your problem is that grub can't boot itself from that external drive. If that doesn't make sense to you, just read more about how grub works.

No, I understand this. I wish I had know that before hand. I tried installing it on my internal harddrive and it wouldn't partition it for some reason. Is there a way to get the original windows bootloader onto a CD that I could take home with me tonight? I don't have the vista repair CD.

EDIT: Something similar has happened before where I had to reinstall the windows bootloader and fdisk wouldn't work from the vista cd. Will fixmbr work?

---

### Post by alienexplorers on 2007-09-16
Run fixmbr off the vista disk and the reload grub following the directions in my signature line. If you have no access to the vista disk you can try super grub disk.

---

