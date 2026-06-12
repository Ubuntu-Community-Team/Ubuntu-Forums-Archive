---
title: "i need a portable terminal"
date: 2011-05-31
forum: Any Other OS
---

### Post by brunobliss on 2011-05-31
Hey guys, i need a linux operating system without a GUI, just the command line shell\terminal, what should i get?

---

### Post by sanderd17 on 2011-05-31
What do you want to do with it? Ubuntu server edition doesn't have a GUI, but that doesn't make it ligth. And DSL has a GUI but is only 50 MB big.

---

### Post by cracker89 on 2011-05-31
Search the forum.. :)

[http://ubuntuforums.org/showthread.php?t=885727](http://ubuntuforums.org/showthread.php?t=885727)

---

### Post by brunobliss on 2011-05-31
> **sanderd17 said:**
> What do you want to do with it? Ubuntu server edition doesn't have a GUI, but that doesn't make it ligth. And DSL has a GUI but is only 50 MB big.

I want to use it in my network to wake up machines using WOL.

 so basically instead of plugging in my netbook all of the time to run these commands, i simply need an OS that is command line based, takes minimal memory and processor and that allows me to install WOL in it.

I don't mind if i have to run this in a virtual machine, although it would be awesome to run it under windows.

Picture DosBox portable, i want LinuxBox portable.

---

### Post by cracker89 on 2011-05-31
Hmm... pendrivelinux? 

[http://wiki.grml.org/doku.php?id=usb#boot_grml_from_usb-stick_firewire-device](http://wiki.grml.org/doku.php?id=usb#boot_grml_from_usb-stick_firewire-device)

And once its on the pendrive, and it boots then go on to shell (init 3) and your application.
Or you can do it through windows using, for eg, qemu to boot to a virtual machine.

---

### Post by brunobliss on 2011-05-31
thank you for the suggestions cracker, i found about openBSD along the way which might actually be exactly what i need, or at least the second best option ...

It seems to be a no GUI OS and it's about 12Mb :) i'll let you guys know how this will work out.

---

### Post by krapp on 2011-05-31
> **brunobliss said:**
> Hey guys, i need a linux operating system without a GUI, just the command line shell\terminal, what should i get?

Nearly any Linux distro in which you can install a base system without X can do this.

I would recommend Debian, as it allows you to do it with a graphical installer. ;)

---

### Post by el_koraco on 2011-05-31
Well, it's obvious. Arch!

---

### Post by brunobliss on 2011-06-01
well guys i found a solution.

Using vmplayer i installed openBSD.
Created a shortcut to my desktop.

done. simple.

machine state is always saved so i don't even have to boot, takes me two seconds to be back on the system. I haven't tested how low on memory i can go with this machine, but right now i'm using 128mb ram for the vm and it works like a charm. I tried 8mb first but it didn't boot, go figure.

cheers and thanks for all the help \ suggestions !!:popcorn:

---

