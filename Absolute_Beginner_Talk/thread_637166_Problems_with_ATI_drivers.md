---
title: "Problems with ATI drivers"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Khanser on 2007-12-10
Hello, I'm new to this forums and is the first time i have tryied to install linux on my computer so, i will go to the point:

I am runing ubuntu 7.10, i have an ATI Radeon X1600 and i have installed the drivers of the web without any problems but it goes like i have not the card installed, I have read other posts but i couldn't get an answer so i tryied to install envy but i get the "-Error: Dependency is not satisfiable: xserver-xorg-dev" error, I have gone to xorg.conf (as many users of this forum seems to need info at "Device") and here comes what i got:

Section "Device"
        Identifier      "Tarjeta de vídeo genérica"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

fglrxinfo spits this out:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)





I would be very grateful if someone could help me.

Thanks for your time, and forgive me about my English.

---

### Post by Pumalite on 2007-12-10
Try this:
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot

---

### Post by Khanser on 2007-12-10
when i do " sudo apt-get install xorg-driver-fglrx"

it gives me the message

"Los siguientes paquetes tienen dependencias incumplidas:
  xorg-driver-fglrx: Depende: libstdc++5 (>= 1:3.3.4-1) pero no es instalable
E: Paquetes rotos"

"The following packages have unsatisfable dependency:
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but is not satisfable
E: Packages broken"

---

### Post by Pumalite on 2007-12-10
Have you kept up with the updates?
Post the output of:
sudo apt-get install -f

---

### Post by Ub1476 on 2007-12-10
Make sure the sources is checked in System>Administration>Software Sources. You don't need to check "source-code".

---

### Post by Khanser on 2007-12-10
> **Pumalite said:**
> Have you kept up with the updates?
Post the output of:
sudo apt-get install -f

"Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados."

It says that nothing has been installed, downloaded and so

Also, at software sources i have all checked unless 'source-code', the last one.

---

### Post by Pumalite on 2007-12-10
Copy and paste the output here.

---

### Post by Khanser on 2007-12-10
ruben@ruben-desktop:~$ sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ruben@ruben-desktop:~$ 


And that's it

---

### Post by Khanser on 2007-12-10
Lol, since i thought i might have missunderstood your "sudo apt-get install -f" i tryied
" sudo apt-get install xorg-driver-fglrx -f" 

And is installing, i will try what you posted b4, i will post in a few minutes

---

### Post by Khanser on 2007-12-10
It seems xorg-driver-fglrx was installed successfully, but when i do "sudo aticonfig --initial" it ends up in a Core dumped error


.
..
..
b7fa1000-b7fa6000 r-xp 00000000 08:01 16893548   /usr/lib/libXrandr.so.2.1.0
b7fa6000-b7fa7000 rw-p 00005000 08:01 16893548   /usr/lib/libXrandr.so.2.1.0
b7fb0000-b7fb3000 rw-p b7fb0000 00:00 0 
b7fb3000-b7fcd000 r-xp 00000000 08:01 19841037   /lib/ld-2.6.1.so
b7fcd000-b7fcf000 rw-p 00019000 08:01 19841037   /lib/ld-2.6.1.so
bf9f0000-bfa06000 rw-p bf9f0000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Cancelado (core dumped)

---

