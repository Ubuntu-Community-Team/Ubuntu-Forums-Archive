---
title: "Amarok broken on edgy"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2007-04-26
Ok i posted this same thing today but i stop because i was thinkin i fixed it but i didnt i cant run amarok after i uninstalled and reinstalled it..it wont open ive tried to run amarokapp in the terminal only to get this..



X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...

after that it says its updating the database after running the splash and doesn't work it just stops and cuts off or something any one know how to fix this? thanks

---

### Post by aidanr on 2007-04-26
those errors are due to the wacom devices in your xorg.conf, you can safely comment them out if you don't have a wacom device, not sure if it will help the amarok issue but try it anyway

[http://ubuntuforums.org/showpost.php?p=1264009&postcount=3](http://ubuntuforums.org/showpost.php?p=1264009&postcount=3)

---

### Post by HybridTheory on 2007-04-26
I dont get it do i enter all that crap in the terminal ...? lol.. :confused:

---

### Post by aidanr on 2007-04-26
kinda, type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo kate /etc/X11/xorg.conf
``` and comment (#) out the wacom stuff like that guy did, save and then press ctrl+alt+backspace to restart X and see if that makes any difference

if you're not using kate, substitute whatever your text editor is gedit/kwrite/nano/mousepad whatever, and if X doesn't restart type ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo reboot
```

again i'm not sure if it will solve the problem (it will at least get rid of those errors)

---

### Post by lizerazu on 2007-04-30
I'm having this problem also.
Did this fix the problem? I'll try it after work.

---

