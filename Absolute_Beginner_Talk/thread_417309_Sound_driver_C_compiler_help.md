---
title: "Sound driver C compiler help"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Gavner on 2007-04-21
I am trying to install some ALSA drivers for my sound card but every time I run. 

 ./configure --with-cards=ca0106 --with-sequencer=yes;make;make install

((That's what the site told me to run.))

When I input that I recieve:

```
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9rc4a/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9rc4a/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [install-modules] Error 1
root@randy-desktop:/usr/src/alsa/alsa-driver-1.0.9rc4a# ./install-sh
install:        no input file specified
root@randy-desktop:/usr/src/alsa/alsa-driver-1.0.9rc4a# ./configure
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Help me! My motherboards built in sound card sucks mega booty!

---

### Post by annda on 2007-04-21
first of all, 1.0.9 is older that the ubuntu package. do you really need to downgrade?

also, you'd better run make with sudo

```
./configure
sudo make
sudo make install
```

---

### Post by Gavner on 2007-04-21
Well if the ubuntu package is higher than that, why wont it detect my sound card? I have a Sound Blaster Audigy SE.

---

### Post by annda on 2007-04-21
do you see your card when you type this in the terminal:

cat /proc/asound/cards

---

### Post by Gavner on 2007-04-21
```
0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xfe02d000, irq 22
 [B]1 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x8c00 irq 19[/B]

```

Yea, it's the bold one.

---

### Post by annda on 2007-04-21
is it possible that you have two sound cards? or more likely an on-board sound chip and a card?

if so, try disabling the sound chip in BIOS.

---

### Post by Gavner on 2007-04-21
OK I'll try. Be back shortly!

---

### Post by Gavner on 2007-04-21
Okay I disabled the on board chip but I still have no sound.

---

### Post by annda on 2007-04-21
off the top of my head: right click the speaker icon on the panel and go to preferences. try to see if you can change the device in the drop-down list from nvidia to sound blaster. if you can't, you can try this:

try this command again:
```
cat /proc/asound/cards
```

if the output hasn't changed, it means that the kernel didn't notice the change.

you can try a trick i haven't tested, so back up the file in question first!
```

sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
```

then 
```

gksu gedit /etc/modprobe.d/alsa-base
```

and add the following line:
```
options snd-ca0106 index=0
```

reboot.

---

### Post by Gavner on 2007-04-21
The Nvidia one I think was the built in one. Once I disabled the chip through bios, that one disappeared. I think the "CA0106" is my sound card.


```

randy@randy-desktop:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0x9c00 irq 19

```

---

### Post by annda on 2007-04-21
does it work now? can you configure and use it?

---

### Post by Gavner on 2007-04-21
> **annda said:**
> does it work now? can you configure and use it?

No sound yet, but I can go into prefrences and see some volume bars.
I messed with those but no luck yet.

---

### Post by annda on 2007-04-21
try alsamixer from the terminal. make sure you unmute (M key) master and PCM.

---

### Post by Gavner on 2007-04-21
> **annda said:**
> try alsamixer from the terminal. make sure you unmute (M key) master and PCM.

HEY I GOT IT!
Somehow I got it to work through the prefrences... I don't know how but I did!
Thanks for all the help! I really appreciate it.


Still sounds a little crackly and popy though >_<
Edit: 
Nevermind i fixed it :)

---

