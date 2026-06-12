---
title: "[Linux Pinguy]"
date: 2011-08-12
forum: Any Other OS
---

### Post by anatolik on 2011-08-12
Hi,

I have 64bits Pinguy 11.04 (which is based on ubuntu 11.04).

There is one annoying issue with Docky. When left side doc is hiding it leaves screen artifacts. Check recorded screen video [http://www.youtube.com/watch?v=2iL6HyFs4OA]("http://www.youtube.com/watch?v=2iL6HyFs4OA").

Does anybody have the same problem? I am sure that this problem hits ubuntu 11.04 as well..

If I check "Fade on Hide option" in Docky configuration then this problem disappears (as docky does not slide anymore, it fades out). But I would like to be a good Linux citizen and file a bug (and hope that it'll be fixed soon). But whom to blame? Docky, Compiz, ATI drivers or kernel? Could anybody give me pointers so I can contact exact project and file bug there...

All packages is up-to-date
```
$ uname -a
Linux anatol-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ sudo lshw -class video
  *-display               
       description: VGA compatible controller
       product: RV630 [Radeon HD 2600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:60:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:68 memory:d0000000-dfffffff memory:f0000000-f000ffff ioport:1000(size=256) memory:f0020000-f003ffff
```

---

### Post by VanR on 2011-08-12
I just installed Pinguy 11.04 myself. I just dumped Docky and started using Avant Window Navigator. I like it better.

---

