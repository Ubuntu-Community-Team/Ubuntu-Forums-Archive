---
title: "Problema con tableta digitalizadora"
date: 2007-04-24
forum: Argentina Team
---

### Post by R@ül on 2007-04-24
Hola gente, necesito ayuda, no puedo hacer andar la tableta digitalizadora UC-Logic 4030, busque en la red y segui paso a paso el how-to de Daniel [https://help.ubuntu.com/community/TabletSetupWizardpen]("https://help.ubuntu.com/community/TabletSetupWizardpen")
compile el driver, está la regla en udev pero para que vean les paso esto....
[B]
raul@raul-desktop:~$ sudo bash
root@raul-desktop:~# echo 'BUS=="usb", KERNEL=="event*", SYSFS{product}=="Tablet WP4030U", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"' >> /etc/udev/rules.d/010_local.rules
root@raul-desktop:~# exit
exit
raul@raul-desktop:~$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                                                             [ OK ] 
raul@raul-desktop:~$ ls -la /dev/tablet-event
ls: /dev/tablet-event: No existe el fichero ó directorio

[/B]
/dev/tablet-event no existe
Sé que es complicado el que me puedan ayudar, ya que no es un dispositivo muy común que digamos, UC-Logic provee a genius y algunos otros, saludos.

---

