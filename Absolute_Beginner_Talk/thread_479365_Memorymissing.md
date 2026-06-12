---
title: "Memorymissing"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by lledurt on 2007-06-20
I upgraded from 2 to 4 gb of ram.  all the modules are the same (800mhz OCZ DDR2)  The system bios is showing all 4 but 7.04 is only showing 3.
I installed VM ware  and player but uninstalled them so I don't think it is being robbed by them.  I run virtual Box but have only given it 512mb.  Is there a way to check to see why or where the memory is going.  I have seen threads with problems over 4gb but none under.
I am a  newbie so compiling my own kernel is really not desired. Should I just wait fr the 7.10?
P.J.

---

### Post by forestpixie on 2007-06-20
I believe it's to do with total max memory of 4Gb - you need to take into account swap space - could be wrong though!

---

### Post by Seisen on 2007-06-20
Are you running 32-bit or 64-bit?

---

### Post by cogadh on 2007-06-20
You might have a bad stick of memory, even though your BIOS is properly reporting its presence (BIOS doesn't actually check its function). Reboot and choose the Memtest boot option in GRUB. This will perform extensive read/write tests on all of your memory and could identify if one of them is bad.

---

### Post by lledurt on 2007-06-20
I am not sure if I am 64 or 32 but I don't think I have a bad stick of memory.  I do have 4gb of l2 on the processor (dual core E6600 i think).  Here is my kern.log where it address the memory.  It says something about 4gb 3 high and 1 low.  I don't know if that is because of a bad stice or not.

P.J.

Jun 20 21:07:51 jedi kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jun 20 21:07:51 jedi kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jun 20 21:07:51 jedi kernel: Symbols match kernel version 2.6.20.
Jun 20 21:07:51 jedi kernel: No module symbols loaded - kernel modules not enabled. 
Jun 20 21:07:51 jedi kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jun 20 21:07:51 jedi kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 20 21:07:51 jedi kernel: [    0.000000] sanitize start
Jun 20 21:07:51 jedi kernel: [    0.000000] sanitize end
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000008f000 end: 000000000008f000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 000000000008f000 size: 0000000000011000 end: 00000000000a0000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000bed28000 end: 00000000bee28000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bee28000 size: 0000000000099000 end: 00000000beec1000 type: 4
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000beec1000 size: 0000000000ec8000 end: 00000000bfd89000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfd89000 size: 0000000000008000 end: 00000000bfd91000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfd91000 size: 000000000009a000 end: 00000000bfe2b000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfe2b000 size: 0000000000005000 end: 00000000bfe30000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfe30000 size: 000000000007b000 end: 00000000bfeab000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfeab000 size: 0000000000003000 end: 00000000bfeae000 type: 3
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfeae000 size: 0000000000044000 end: 00000000bfef2000 type: 4
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfef2000 size: 000000000000d000 end: 00000000bfeff000 type: 3
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bfeff000 size: 0000000000001000 end: 00000000bff00000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000bff00000 size: 0000000000100000 end: 00000000c0000000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() start: 0000000100000000 size: 0000000040000000 end: 0000000140000000 type: 1
Jun 20 21:07:51 jedi kernel: [    0.000000] copy_e820_map() type is E820_RAM
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bee28000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bee28000 - 00000000beec1000 (ACPI NVS)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000beec1000 - 00000000bfd89000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfd89000 - 00000000bfd91000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfd91000 - 00000000bfe2b000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfe2b000 - 00000000bfe30000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfe30000 - 00000000bfeab000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfeab000 - 00000000bfeae000 (ACPI data)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfeae000 - 00000000bfef2000 (ACPI NVS)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfef2000 - 00000000bfeff000 (ACPI data)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 20 21:07:51 jedi kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 20 21:07:51 jedi kernel: [    0.000000] Warning only 4GB will be used.
Jun 20 21:07:51 jedi kernel: [    0.000000] Use a PAE enabled kernel.
Jun 20 21:07:51 jedi kernel: [    0.000000] 3200MB HIGHMEM available.
Jun 20 21:07:51 jedi kernel: [    0.000000] 896MB LOWMEM available.
Jun 20 21:07:51 jedi kernel: [    0.000000] found SMP MP-table at 000fe200
Jun 20 21:07:51 jedi kernel: [    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Jun 20 21:07:51 jedi kernel: [    0.000000] Zone PFN ranges:

---

