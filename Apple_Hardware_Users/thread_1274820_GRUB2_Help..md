---
title: "GRUB2 Help."
date: 2009-09-25
forum: Apple Hardware Users
---

### Post by Ravernomina on 2009-09-25
Hello everyone. Im trying to install GRUB2 for EFI and i need a little help. I have a 64bit EFI on a MacBook Pro 15" 2.53 GHZ.

Please give me a hand (: Thanks
       Ravernomina



```

```

---

### Post by Bachstelze on 2009-09-25
Moved to Apple Users. [This thread]("http://ubuntuforums.org/showthread.php?t=995704") might help.

---

### Post by Ravernomina on 2009-09-25
Get bumping

---

### Post by pxwpxw on 2009-09-25
A tarball 'bootusb.tar.gz' on the grub2-efi thread, post 1002 has grub2 efi bootx64.efi which you can install on OSX partition to boot ubuntu on HD, the menu will just need a new entry to boot from HD rather than the Live USB, but you should see the existing grub efi boot menu initially ok.

There should be a HD booting menuentry example or help on the grub2 efi thread from MBP5x efi people.

If you have rEFIt in a /efi folder already, just merge the grubefi /efi contents with that. 

[http://ubuntuforums.org/showpost.php?p=7956232&postcount=1002](http://ubuntuforums.org/showpost.php?p=7956232&postcount=1002)

---

