---
title: "fglrx configuration problems"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-12-31
Im trying to play WoW but it cant start 3d acceleration:

when i type flgrxinfo i get this:
Error: unable to open display :0

glxgears works fine. compiz works fine.

i read this might be helpful:
 dmesg | grep fglrx
[17462130.204000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17462130.204000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17462130.204000] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[17462130.208000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17462130.216000] [fglrx] total      GART = 134217728
[17462130.216000] [fglrx] free       GART = 118222848
[17462130.216000] [fglrx] max single GART = 118222848
[17462130.216000] [fglrx] total      LFB  = 122900480
[17462130.216000] [fglrx] free       LFB  = 104345600
[17462130.216000] [fglrx] max single LFB  = 104345600
[17462130.216000] [fglrx] total      Inv  = 0
[17462130.216000] [fglrx] free       Inv  = 0
[17462130.216000] [fglrx] max single Inv  = 0
[17462130.216000] [fglrx] total      TIM  = 0
[17496729.604000] [fglrx:firegl_rmmap] *ERROR* map 0xf2e6be50 still in use (map_count=1)
[17496729.604000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf2e6be40 still mapped
[17496729.604000] [fglrx:firegl_rmmap] *ERROR* map 0xf2e6bcd0 still in use (map_count=1)
[17496729.604000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf2e6bcc0 still mapped
[17496729.604000] [fglrx:firegl_rmmap] *ERROR* map 0xf2e6bdd0 still in use (map_count=1)
[17496729.604000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf2e6bdc0 still mapped
[17496729.604000] [fglrx:firegl_rmmap] *ERROR* map 0xf2e6bed0 still in use (map_count=1)
[17496729.604000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf2e6bec0 still mapped
[17496729.604000] [fglrx:firegl_rmmap] *ERROR* map 0xf2e6b9d0 still in use (map_count=1)
[17496729.604000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf2e6b9c0 still mapped
[17496742.960000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17496742.960000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17496742.960000] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[17496742.960000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17496742.968000] [fglrx] total      GART = 134217728
[17496742.968000] [fglrx] free       GART = 118222848
[17496742.968000] [fglrx] max single GART = 118222848
[17496742.968000] [fglrx] total      LFB  = 122900480
[17496742.972000] [fglrx] free       LFB  = 104345600
[17496742.972000] [fglrx] max single LFB  = 104345600
[17496742.972000] [fglrx] total      Inv  = 0
[17496742.972000] [fglrx] free       Inv  = 0
[17496742.972000] [fglrx] max single Inv  = 0
[17496742.972000] [fglrx] total      TIM  = 0


any help will be great thanks

---

### Post by carlosfocker on 2007-01-05
What video card do you have?

Open a terminal and type:

glxinfo

Post the output

---

