---
title: "appleir with ubuntu-server 7.10 inconsistent behavior"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by tsella on 2007-12-25
using latest ubuntu-server (7.10) on a mac mini i get an inconsistent behavior from the apple mote.

1. i'm using the dev/input device (/dev/usb/hiddev0 does not produce any results directly or with lirc, so i went ahead and used dev/input instead via /dev/input/by-path/pci-0000:00:1d.3-usb-0:2:1.0-event-)

2. using kernel 2.6.22-14-server

when i click any remote key for longer than a single short keypress, the output from the remote will stop inconsistently - to illustrate using lirc - a single short click would result with a counter of 00 while a longer click should result in that counter raising - in my case it stops, some times at 06, sometimes at 24, sometimes at 01. no consistency what so ever.

now the real strange thing - if i boot using the ubuntu-desktop livecd and do the same thing via terminal, it works fine - so i'm guessing this has to do with the kernel.

any ideas?

---

