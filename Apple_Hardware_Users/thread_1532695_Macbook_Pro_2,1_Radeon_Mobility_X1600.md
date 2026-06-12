---
title: "Macbook Pro 2,1 Radeon Mobility X1600"
date: 2010-07-16
forum: Apple Hardware Users
---

### Post by shinzon36 on 2010-07-16
I would appreciate any help with this problem. I've been using Lucid for about a month on my Macbook Pro 2,1 and noticed last night that I could no longer switch to "Extra" or "Normal" visual effects under system appearance preferences, but I had no problem doing this before. The system just searches for drivers and then says that the desktop effects could not be enabled. I believe I even had OpenGL working as well. I did a fresh install to a new partition, and I could use "Extra" and "Normal" with no problem, but I don't think I had OpenGL working on the fresh install- but I may be mistaken.

I worked on this all last night, and I've included a lot of the information below that I saw requested from others when trying to solve similar problems. I apologize for the length, but I thought it better to get it all out there:

&#9675; glxinfo | grep vendor                   
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[1]    2073 segmentation fault  glxinfo | 
       2074 exit 1              grep vendor

&#9675; LIBGL_DEBUG=verbose glxinfo        
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
[1]    2116 segmentation fault  sudo LIBGL_DEBUG=verbose glxinfo

&#9675; lspci -nn | grep VGA                         
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]

&#9675; sudo lshw -C display                         
  *-display               
       description: VGA compatible controller
       product: M56P [Radeon Mobility X1600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:29 memory:80000000-8fffffff(prefetchable) ioport:3000(size=256) memory:98300000-9830ffff memory:98320000-9833ffff(prefetchable)

&#9675; dmesg | grep drm                        
[    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
[    1.089781] [drm] Initialized drm 1.1.0 20060810
[    1.133333] [drm] radeon kernel modesetting enabled.
[    1.135165] [drm] radeon: Initializing kernel modesetting.
[    1.135324] [drm] register mmio base: 0x98300000
[    1.135326] [drm] register mmio size: 65536
[    1.135676] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[    1.135702] [drm] Generation 2 PCI interface, using max accessible memory
[    1.135706] [drm] radeon: VRAM 256M
[    1.135708] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[    1.135710] [drm] radeon: GTT 512M
[    1.135712] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[    1.135828] [drm] radeon: using MSI.
[    1.135869] [drm] radeon: irq initialized.
[    1.136685] [drm] Detected VRAM RAM=256M, BAR=256M
[    1.136688] [drm] RAM width 128bits DDR
[    1.136822] [drm] radeon: 256M of VRAM memory ready
[    1.136825] [drm] radeon: 512M of GTT memory ready.
[    1.136845] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.138353] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[    1.138395] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[    1.138416] [drm] radeon: cp idle (0x10000C03)
[    1.138459] [drm] Loading R500 Microcode
[    1.140276] [drm] radeon: ring at 0x0000000020000000
[    1.140332] [drm] ring test succeeded in 5 usecs
[    1.140520] [drm] radeon: ib pool ready.
[    1.140644] [drm] ib test succeeded in 0 usecs
[    1.140865] [drm] Default TV standard: NTSC
[    1.140981] [drm] Radeon Display Connectors
[    1.140983] [drm] Connector 0:
[    1.140985] [drm]   LVDS
[    1.140987] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[    1.140990] [drm]   Encoders:
[    1.140991] [drm]     LCD1: INTERNAL_LVTM1
[    1.140993] [drm] Connector 1:
[    1.140995] [drm]   S-video
[    1.140997] [drm]   Encoders:
[    1.140998] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[    1.141000] [drm] Connector 2:
[    1.141007] [drm]   DVI-I
[    1.141008] [drm]   HPD1
[    1.141011] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    1.141013] [drm]   Encoders:
[    1.141015] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[    1.141017] [drm] Connector 3:
[    1.141018] [drm]   VGA
[    1.141021] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    1.141023] [drm]   Encoders:
[    1.141025] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    1.436174] [drm] fb mappable at 0x800C0000
[    1.436177] [drm] vram apper at 0x80000000
[    1.436179] [drm] size 5299200
[    1.436181] [drm] fb depth is 24
[    1.436183] [drm]    pitch is 5888
[    1.436257] fb0: radeondrmfb frame buffer device
[    1.436267] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0

Thanks.

---

