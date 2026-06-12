---
title: "Podxt in linux"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by BlazedForever on 2006-02-19
Hey all i just bought a line6 podxt a while ago but now i am realizing that i dont have linux drivers for it ,i found this site [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/) and downloaded the source to the driver but i can't for the life of me get it compiled under ubuntu i was hoping that maybe someone on here could download it and try to help me get it compiled. thx :) 

note: when i do 
make install i get this error

root@Xvium:/home/xvium/Desktop/line6usb-0.6# make install
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/xvium/Desktop/line6usb-0.6 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [default] Erro

---

### Post by kaamos on 2006-02-19
Not too shure about this but you could try installing the kernel headers.
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by nalmeth on 2006-02-19
This thing looks pretty sweet. How much did it set you back?

---

### Post by BlazedForever on 2006-02-19
like 500 bucks :P

---

### Post by BlazedForever on 2006-02-19
this is what i get after installing the headers


root@Xvium:/home/xvium/Desktop/line6usb-0.6# make install
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/xvium/Desktop/line6usb-0.6 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/xvium/Desktop/line6usb-0.6/audio.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/xvium/Desktop/line6usb-0.6/audio.o] Error 127
make[1]: *** [_module_/home/xvium/Desktop/line6usb-0.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [default] Error 2

---

### Post by nalmeth on 2006-02-19
yow! hopefully you get it going then

sudo apt-get install gcc-3.4

then try again

---

### Post by hovmod on 2006-03-12
Hi, guys!

I'm having trouble installing this driver as well, even now that I've followed the steps here in this thread. 

I get these errors: 

```

  Building modules, stage 2.
  MODPOST
*** Warning: "__mulsf3" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] undef ined!
*** Warning: "__ltsf2" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] undefi ned!
*** Warning: "__floatsisf" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] un defined!
*** Warning: "__fixdfsi" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] unde fined!
*** Warning: "__adddf3" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] undef ined!
*** Warning: "__extendsfdf2" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__subsf3" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] undef ined!
*** Warning: "__fixsfsi" [/home/tormod/download/line6usb-0.6.1/line6usb.ko] unde fined!
  CC      /home/tormod/download/line6usb-0.6.1/line6usb.mod.o
  LD [M]  /home/tormod/download/line6usb-0.6.1/line6usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/kernel/sound/usb
cp line6usb.ko /lib/modules/2.6.12-10-386/kernel/sound/usb
mkdir -p /usr/bin/bin
cp *.sh *.pl /usr/bin
depmod -a
modprobe line6usb
FATAL: Error inserting line6usb (/lib/modules/2.6.12-10-386/kernel/sound/usb/lin e6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```

And after running dmesg, this line6usb stuff is added to the log: 

```

[4295479.447000] line6usb: Unknown symbol __fixsfsi
[4295479.447000] line6usb: Unknown symbol __subsf3
[4295479.447000] line6usb: Unknown symbol __extendsfdf2
[4295479.447000] line6usb: Unknown symbol __adddf3
[4295479.447000] line6usb: Unknown symbol __fixdfsi
[4295479.447000] line6usb: Unknown symbol __floatsisf
[4295479.447000] line6usb: Unknown symbol __ltsf2
[4295479.447000] line6usb: Unknown symbol __mulsf3

```

Did you get it right in the end, BlazedForever?

---

### Post by AstarothCY on 2007-12-13
same error message as above (default Error 2)

---

### Post by fourmiii on 2007-12-14
You can find my solution in this thread  :

[http://ubuntuforums.org/showthread.php?t=640785](http://ubuntuforums.org/showthread.php?t=640785)

Have fun !!

---

### Post by AstarothCY on 2007-12-14
> **fourmiii said:**
> You can find my solution in this thread  :

[http://ubuntuforums.org/showthread.php?t=640785](http://ubuntuforums.org/showthread.php?t=640785)

Have fun !!

Thanks! I ended up installing it using subversion as per the programmer's instructions on the project's sourceforge page, which worked, but it looks like your patch should work just fine as well.

Is there a graphical frontend for this? Also, i can't seem to get Line 6 Edit to work using Wine, it crashes on the first screen. Any luck with that?

Oh yeah, for some reason now my MIDI (timidity) audio output is routed through the Pod so I can hear it in my guitar amplifier instead of my computer speakers when the pod is plugged in and I can't hear it at all anymore if the pod isn't plugged in. It worked fine before I installed line6usb. Any idea why it got hijacked?

---

