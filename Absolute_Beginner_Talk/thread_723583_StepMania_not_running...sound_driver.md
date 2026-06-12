---
title: "StepMania not running...sound driver?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by neoMAX on 2008-03-13
EDIT: Resolved:

Go to System > Preferences > Sound and change the Default Mixer device.





I've extracted Stepmania to my program directory and i ran ./stepmania in terminal but it does this:

```
StepMania 3.9
Log starting 2008-03-13 17:45:23
Loading window: gtk
OS: Linux ver 020622
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.6.1
Threads library: NPTL 2.6.1
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 0/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
Language: english
Theme: default
Error: Couldn't find a sound driver that works
neomax@neomax-desktop:~/My Programs/StepMania-3.9$ ./stepmania
StepMania 3.9
Log starting 2008-03-13 17:46:10
Loading window: gtk
OS: Linux ver 020622
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.6.1
Threads library: NPTL 2.6.1
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 0/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
Language: english
Theme: default
Error: Couldn't find a sound driver that works

```

It is probably because I installed the realtek drivers for my motherboard from the mobo CD. any ideas on how to fix it?

---

