---
title: "ATI Drive and Quake Wars for Linux"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by blueridgedog on 2007-12-30
OK, I am an old time quake fan.  I saw the new game and a demo for Linux and I thought I would give it a try.  I have a decent graphics card and was running a correctly setup rig.

However, when attempting to run the game I receive the following error:

```
ERROR: The current video card / driver combination does not support the necessary features: GL_EXT_texture3D GL_ARB_texture_rectangle or GL_EXT_texture_rectangle GL_ARB_occlusion_query GL_ARB_vertex_program GL_ARB_fragment_program GL_ARB_shader_objects GL_ARB_vertex_shader GL_ARB_fragment_shader
```

I checked to make certain I had the ATI driver, even though System -> admin -> restricted drivers told me I did:

```
xorg-driver-fglrx is already the newest version.
```

I checked to be certain the drive was being used:

```
root@ripstop:/usr/local/games/etqw.demo# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6473 (8.37.6)
```

I looked at my xorg.conf to see that it was configured correctly, see below in case someone sees something that is wrong (this is an edited down list):

```
Section "Device"
        Identifier      "ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

EndSection

Section "Module"
        Load            "glx"
EndSection

Section "ServerFlags"
    Option "AIGLX" "on"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

Based on some web research, I decided to use aticonfig to configure my xorg.conf file, but it core dumps (repeatedly):

```
root@ripstop:/etc/X11# aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfa729f3 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d5792b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d00050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:12 11109094   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:12 11109094   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7cdc000-b7cdd000 rw-p b7cdc000 00:00 0 
b7cdd000-b7cdf000 r-xp 00000000 08:12 7127092    /lib/tls/i686/cmov/libdl-2.6.1.so

Large snip

b7f92000-b7f94000 rw-p 00019000 08:12 7127053    /lib/ld-2.6.1.so
bfa5e000-bfa73000 rw-p bfa5e000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

So, any ideas as to why it things I can't run the game?  I did at one time have xserver-xgl running.  Is that creating the following?

Section "Module"
        Load            "glx"
EndSection

---

### Post by blueridgedog on 2007-12-30
Please excuse the subject.  Should be ATI Driver.

---

### Post by blueridgedog on 2007-12-31
Well, as it turns out the Binary ATI drive simply is inadequate.  Others with ATI cards have the same problem.  If you have an ATI card and have gotten this game to work, let me know.  My research did give me a chance to clean up my xorg.conf file and learn a bit more about it.  Here are a few of the changes:

```
Section "Device"
        Identifier      "ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option "VideoOverlay"               "on"
        Option "OpenGLOverlay"              "off"
EndSection
Section "Module"
        Load            "glx"
        Load            "dri"
        Load            "GLcore"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```

---

### Post by Tux.Ice on 2007-12-31
how about wine or steam

---

### Post by Tux.Ice on 2007-12-31
or virtual box with windows xp home or pro installed

---

### Post by Tux.Ice on 2007-12-31
or dual boot

---

### Post by blueridgedog on 2007-12-31
I actually have a dual boot setup, but I just can't stand Vista and am looking forward to removing it.  I booted into Vista to try the demo and had to endure a half  hour of grinding as it updated superfetch and rebuilt all the index in case I wanted to run a given application or search for an arcane item.

---

