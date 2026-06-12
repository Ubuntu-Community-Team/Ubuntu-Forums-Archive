---
title: "ICH6, alsa upgrade to 1.0.11"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-06-10
help please :D 

I have a packard bell easy note laptop (A8 I think) running Dapper. Anyway the sound chipset is an ICH6. This seems to be all over the forums here as being problematic. Some people have reported working sound using the .10 alsa drivers which I am baffled by as is that not what Dapper uses? Anyway, I have no sound - and read somewhere on here that there is a fix for ICH6 chipsets in alsa 1.0.11.

So, time this (machine) went all the way to 11.

I have downloaded the tar files, and extrated them into the following directories..

/usr/src/alsa/
/usr/src/alsa/alsa-driver-1.0.11
/usr/src/alsa/alsa-firmware-1.0.11
/usr/src/alsa/alsa-lib-1.0.11
/usr/src/alsa/alsa-oss-1.0.11
/usr/src/alsa/alsa-plugins-1.0.11
/usr/src/alsa/alsa-utils-1.0.11

I have also installed (via synaptic) all the build packages I think I need and the kernel headers.

I am trying to commands. One from the alsa site, and one recommended on this forum. Both are giving errors.

```
root@carla:/usr/src/alsa/alsa-driver-1.0.11# ./configure --with-cards=hda-intel --with-sequencer=yes;make;make install
bash: ./configure: No such file or directory
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.11'
ln -sf ../alsa-kernel alsa-kernel
ln -sf alsa-kernel sound
ln -sf alsa-kernel/scripts scripts
make[1]: *** No rule to make target `utils/mod-deps.c', needed by `utils/mod-deps'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.11'
make: *** [dummy1] Error 2
rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.11/acore'
Makefile:5: /usr/src/alsa/alsa-driver-1.0.11/toplevel.config: No such file or directory
Makefile:6: /usr/src/alsa/alsa-driver-1.0.11/Makefile.conf: No such file or directory
/usr/src/alsa/alsa-driver-1.0.11/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.11/acore'
make: *** [install-modules] Error 1
root@carla:/usr/src/alsa/alsa-driver-1.0.11#
```

and ...

```
root@carla:/usr/src/alsa/alsa-driver-1.0.11# ./configure --with-cards=hda-intel --with-sequencer=yes;make;make install
bash: ./configure: No such file or directory
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.11'
ln -sf ../alsa-kernel alsa-kernel
ln -sf alsa-kernel sound
ln -sf alsa-kernel/scripts scripts
make[1]: *** No rule to make target `utils/mod-deps.c', needed by `utils/mod-deps'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.11'
make: *** [dummy1] Error 2
rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.11/acore'
Makefile:5: /usr/src/alsa/alsa-driver-1.0.11/toplevel.config: No such file or directory
Makefile:6: /usr/src/alsa/alsa-driver-1.0.11/Makefile.conf: No such file or directory
/usr/src/alsa/alsa-driver-1.0.11/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.11/acore'
make: *** [install-modules] Error 1
root@carla:/usr/src/alsa/alsa-driver-1.0.11#
```

so first question, can someone advise me on how to resolve these errors. And the second question, is can anyone confirm that the alsa 11 release will work for ICH6.

I have heard rumours that disabling the modem could work. I have no need for the modem, I use ethernet and the wireless card (if I can make it work.) Can anyone suggest how to disable the modem. It might be something worth trying.

Thanks in advance,
John

---

### Post by pompeyjohn on 2006-06-11
*polite bump*

---

### Post by Bokonon on 2006-07-09
I am sorry to hear that you are having troubles and wish I could give you a solution.  I have the same chipset and it works with my Dell XPS m170.  I get sound in, microphone, subwoofer, everything.  Modem is enabled, but I do not actually use it.

All I can say is that I am using ALSA 1.0.10, so I do not think that is the problem.  Perhaps 11 will have some help for some people, but for me, everything works fine.

---

