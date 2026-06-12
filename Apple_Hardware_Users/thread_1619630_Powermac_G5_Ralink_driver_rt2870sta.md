---
title: "Powermac G5 Ralink driver rt2870sta"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by Mattameus on 2010-11-12
I'm having trouble compiling the rt2870sta drivers on my g5 system, build failed at undefined symbols (which I hacked around and "fixed" by redefining __powerpc64__ in a few places and updating usb_buffer_alloc() -> usb_alloc_coherent(), usb_buffer_free() -> usb_free_coherent()
in the ralink driver as I saw was a change in newer kernels) and it compiles fine, but it still fails at modpost with the message:

FATAL: /home/user/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.o has no symtab?

readelf -S 
lists the symbol table size as 9700 (hex)

readelf says that .symtab contains 2416 entries, so obviously the symbol table is not empty... I have the sneaking suspicion this is a issue with the build environment... or does the ralink driver even work on ppc?

I'm running Maverick 10.10 PPC, I've installed build-essential, linux headers (linux-headers-2.6.35-22, linux-headers-2.6.35-22-powerpc64-smp), and the kernel source (linux-source-2.6.35), I also updated binutils (2.20.51.20100908 ) so I could recompile modpost (which compiling failed with the default version) and pointed the ralink Makefile to the linux source headers instead of the linux-headers.

---

