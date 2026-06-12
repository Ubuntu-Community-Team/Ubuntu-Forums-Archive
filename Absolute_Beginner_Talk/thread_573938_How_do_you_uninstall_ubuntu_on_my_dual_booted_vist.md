---
title: "How do you uninstall ubuntu on my dual booted vista?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Bunnytard on 2007-10-12
I'm not liking ubuntu dual booted on my vista. How do I like delete it?

---

### Post by Johan_SV on 2007-10-12
First make sure you have a working Vista DVD which you can boot.

 In Windows Vista, remove the partition(s) used by Linux Ubuntu. Then reboot your PC with your Vista DVD in it. Once that is launched, select the Repair option in the menu. It will launch a console. In there, type 'fixmbr' (without the quotes) to install Microsoft's boot loader.

Before you do this, please wait for some input from others, since I'm not 100% sure if Vista's boot DVD uses the same method as with XP.

---

### Post by por100pre1 on 2007-10-12
You need to restore the original MBR, read [this]("http://support.microsoft.com/kb/927392/en-us") carefully.

---

### Post by Bunnytard on 2007-10-22
> **Johan_SV said:**
> First make sure you have a working Vista DVD which you can boot.

 In Windows Vista, remove the partition(s) used by Linux Ubuntu. Then reboot your PC with your Vista DVD in it. Once that is launched, select the Repair option in the menu. It will launch a console. In there, type 'fixmbr' (without the quotes) to install Microsoft's boot loader.

Before you do this, please wait for some input from others, since I'm not 100% sure if Vista's boot DVD uses the same method as with XP.

I don't have a vista cd since my computer came pre-installed with vista.

---

### Post by bks on 2007-10-31
I actually just stumbled my way through uninstalling Ubuntu, as well. I used disk management in Vista to try to remove the Ubuntu partitions and in doing so messed up Grub which rendered the system unbootable. However, I used an XP CD I had and created a new partition from the space that Ubuntu was using, which removed Grub, and the system booted into Vista with no problems. Once I was back in Vista I reformatted the new raw partition I created with the XP disk and now there's more space for applications.

***Note: I am a devoted Ubuntu user, I was removing it at the request of the person purchasing my laptop. I tried to convince him otherwise, but he is still too afraid to try. I'll win him over yet.***

---

### Post by It_Was_Luck on 2007-10-31
The arterniative to not having a vista cd is to burn yourself a supergrub cd, it can do exactly hthe same as what "fixmbr" will do in a recovery cd, if you need anymore info on it just ask.

Also...

Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)

---

