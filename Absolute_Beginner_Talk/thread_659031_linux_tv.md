---
title: "linux tv"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by gjschouten on 2008-01-05
Hey everybody,

I installed my pinnacle pctv usb2 device using *the ubuntu em28xx wiki guide* yesterday.

It worked perfectly, even with sound. 

Today i started my laptop again and there is no video of the tv in either *kdetv xawtv nor in tvtime*. When i start* tvtime *it gives me: 
"No Signal, cannot open capture device /dev/video0 no such file or directory". 

Now i don't even see a video0 file or directory when i browse through /dev folder.. can someone help me i tried to googling for solutions now for 4 hours.

greetings GJ, Holland

---

### Post by exneo002 on 2008-01-05
I know almost nothing about this but the program might suck try ubuntu ultimate edtion or linux mint or maybe eve linuxmce if you aren't afraid of wipeing your hd

---

### Post by nick_h on 2008-01-05
It sounds like the driver is not loading.  What is the output from:
```
lsmod | grep em28xx
```

---

### Post by gjschouten on 2008-01-05
hey man... 
i tried  lsmod | grep em28xx but it doesn't give any output at all

---

### Post by spydon on 2008-01-05
You can try out the application "klear".
Install it with ```
sudo apt-get install klear
``` or find it in synaptic or in add/remove apps.

---

### Post by nick_h on 2008-01-05
> i tried lsmod | grep em28xx but it doesn't give any output at all
The driver doesn't seem to be loaded.  You can try to load it manually with:
```
sudo modprobe em28xx
```
Then check the output of the *lsmod* and that the directories exist.

---

### Post by gjschouten on 2008-01-05
FATAL: Error inserting em28xx (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

on modprobe em28xx

---

### Post by nick_h on 2008-01-06
Did you look at the output of dmesg to see what the error was?
```
dmesg | grep -i em28xx
```
or if that doesn't return anything, look through the entire output using:
```
dmesg | less
```

---

### Post by gjschouten on 2008-01-06
dmesg | grep -i em28xx
[   34.764494] em28xx: Unknown parameter `options'
[   34.772800] em28xx: Unknown parameter `options'
[   34.784086] em28xx_audio: Unknown symbol em28xx_unregister_extension
[   34.784198] em28xx_audio: Unknown symbol em28xx_register_extension
[   34.828822] em28xx: Unknown parameter `options'
[   34.829692] em2880_dvb: Unknown symbol em28xx_i2c_call_clients
[   34.829994] em2880_dvb: Unknown symbol em28xx_unregister_extension
[   34.830173] em2880_dvb: Unknown symbol em28xx_register_extension

what should i do abou that u think??

---

### Post by nick_h on 2008-01-06
Did the wiki guide ask you to set any options?
```
cat /etc/modprobe.d/options
```

It may also help if you post a link to the wiki you used to install it.

---

### Post by gjschouten on 2008-01-06
cat /etc/modprobe.d/options
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

---

### Post by gjschouten on 2008-01-06
[https://wiki.ubuntu.com/em28xx?highlight=%28em28xx%29](https://wiki.ubuntu.com/em28xx?highlight=%28em28xx%29)

this wiki doesn't tell me about setting any options

---

### Post by nick_h on 2008-01-06
Can you think of anything that has changed since yesterday?  Did it ever work after a re-boot?

The only think I can think of suggesting is to rebuild the module.

```
cd v4l-dvb-kernel
make
sudo make install
```

and then try to load the module again.

---

### Post by gjschouten on 2008-01-06
v4l-dvb-kernel# make
................................
................."...............

make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.o
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3251:7: error: invalid suffix "c29..d3dd6a0" on integer constant
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3251: error: expected '=', ',', ';', 'asm' or '__attribute__' before numeric constant
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3254: error: stray '@' in program
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3254: error: stray '@' in program
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3254: error: stray '@' in program
/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.c:3254: error: stray '@' in program
make[3]: *** [/lib/firmware/v4l-dvb-kernel/v4l/em28xx-video.o] Error 1
make[2]: *** [_module_/lib/firmware/v4l-dvb-kernel/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/lib/firmware/v4l-dvb-kernel/v4l'
make: *** [all] Error 2

gives me errors..is there maybe a way to totally uninstall the v4l and em28 off the system and then reinstall?

---

### Post by nick_h on 2008-01-06
> is there maybe a way to totally uninstall the v4l and em28 off the system and then reinstall?
You can remove the source code by typing:
```
rm -r v4l-dvb-kernel
```
You can't remove the modules from the /lib/modules/2.6.22-14-generic directory because they will have overwritten the originals. (but this won't matter because a new install will overwrite the ones you have there now)

You can the use the hg clone command again to get the source.

---

