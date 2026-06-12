---
title: "COMO Instlar un win sin perder Grub?"
date: 2007-02-20
forum: Argentina Team
---

### Post by javier.der on 2007-02-20
Che, gente linda.

Tengo win y ubuntu con dualboot hace mas de un año, el win solo lo levanto con vmware, pero quiero reinstalarlo para usarlo ya sin vmware, digamos, para juegos.

Mi pregunta es: como instalo el win sin que me pise el grub?
O, como recupero el grub una vez que la instalación de windows me lo borró?

---

### Post by kowal on 2007-02-20
[http://ubuntuforums.org/showthread.php?t=341990](http://ubuntuforums.org/showthread.php?t=341990)

---

### Post by ariel on 2007-02-25
Creo que al instalar windows, no hay forma de evitar que borre el grub de la MBR del disco. Pero es facil reinstalar grub despues que windows lo piso:

 > GRUB Restore after Windows breaks it:
   1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
   2. Open a Terminal. Go SuperUser (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.
   3. Type "grub" which makes a GRUB prompt appear.
   4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". 
      Use whatever your computer spits out for the following lines.
   5. Type "root (hd0,3)".
   6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. 
      If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
      Nota: yo tuve que usar: "setup (hd0)"
   7. Type "quit".
   8. Restart the system. Remove the bootable CD.

---

