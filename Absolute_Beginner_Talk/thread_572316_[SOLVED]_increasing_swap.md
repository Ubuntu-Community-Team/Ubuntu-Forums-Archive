---
title: "[SOLVED] increasing swap?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-10-10
hi,

i had 256mb ran and increased it to 756.9mb the swap original was 729mb...

i have gparted live cd...

do i just boot n add double the new ram by moving the slider in gparted? 
do i need to compact linux before i do this?

thanks

---

### Post by overdrank on 2007-10-10
> **hopelessone said:**
> hi,

i had 256mb ran and increased it to 756.9mb the swap original was 729mb...

i have gparted live cd...

do i just boot n add double the new ram by moving the slider in gparted? 
do i need to compact linux before i do this?

thanks

HI maybe this link will help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Good luck!

---

### Post by hopelessone on 2007-10-10
no sorry i read that before i posted...

any ideas?

---

### Post by floke on 2007-10-10
Why do you want more swap?
Try 'top' from the terminal to see how much you are using.
I barely scratch mine with around 600m of RAM.

---

### Post by hopelessone on 2007-10-10
hey...tahnks for the top tip !!

i had an error in me log files yesterday and after the screensaver went on it took 20 minutes to get log back in...the hard drive was full on for that time..

Oct  9 21:46:16 lotus kernel: [135404.331945] nautilus invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
Oct  9 21:46:17 lotus kernel: [135404.332016]  [out_of_memory+389/448] [COLOR="Red"]out_of_memory+0x185/0x1c0[/COLOR]
Oct  9 21:46:17 lotus kernel: [135404.332081]  [__alloc_pages+740/832] __alloc_pages+0x2e4/0x340
Oct  9 21:46:17 lotus kernel: [135404.332101]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Oct  9 21:46:17 lotus kernel: [135404.332149]  [__do_page_cache_readahead+265/592] __do_page_cache_readahead+0x109/0x250
Oct  9 21:46:17 lotus kernel: [135404.332190]  [io_schedule+29/48] io_schedule+0x1d/0x30
Oct  9 21:46:17 lotus kernel: [135404.332209]  [__wait_on_bit_lock+91/112] __wait_on_bit_lock+0x5b/0x70
Oct  9 21:46:17 lotus kernel: [135404.332216]  [sync_page+0/80] sync_page+0x0/0x50
Oct  9 21:46:17 lotus kernel: [135404.332271]  [filemap_nopage+341/832] filemap_nopage+0x155/0x340
Oct  9 21:46:17 lotus kernel: [135404.332328]  [__handle_mm_fault+328/2816] __handle_mm_fault+0x148/0xb00
Oct  9 21:46:17 lotus kernel: [135404.332424]  [do_page_fault+294/1664] do_page_fault+0x126/0x680
Oct  9 21:46:17 lotus kernel: [135404.332442]  [do_gettimeofday+54/256] do_gettimeofday+0x36/0x100
Oct  9 21:46:17 lotus kernel: [135404.332498]  [do_page_fault+0/1664] do_page_fault+0x0/0x680
Oct  9 21:46:17 lotus kernel: [135404.332510]  [error_code+114/128] error_code+0x72/0x80
Oct  9 21:46:17 lotus kernel: [135404.332549]  [iw_handler_get_iwstats+48/80] iw_handler_get_iwstats+0x30/0x50
Oct  9 21:46:17 lotus kernel: [135404.332584]  =======================
Oct  9 21:46:17 lotus kernel: [135404.332587] Mem-info:
Oct  9 21:46:17 lotus kernel: [135404.332590] DMA per-cpu:
Oct  9 21:46:17 lotus kernel: [135404.332595] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  9 21:46:17 lotus kernel: [135404.332599] Normal per-cpu:
Oct  9 21:46:17 lotus kernel: [135404.332603] CPU    0: Hot: hi:  186, btch:  31 usd: 152   Cold: hi:   62, btch:  15 usd:  43
Oct  9 21:46:17 lotus kernel: [135404.332610] Active:91264 inactive:90907 dirty:0 writeback:0 unstable:0
Oct  9 21:46:17 lotus kernel: [135404.332612]  free:1871 slab:6392 mapped:83 pagetables:857 bounce:0
Oct  9 21:46:17 lotus kernel: [135404.332618] DMA free:3044kB min:72kB low:88kB high:108kB active:4088kB inactive:4008kB present:16256kB pages_scanned:13905 all_unreclaimable? yes
Oct  9 21:46:17 lotus kernel: [135404.332622] lowmem_reserve[]: 0 745 745
Oct  9 21:46:17 lotus kernel: [135404.332631] Normal free:4440kB min:3456kB low:4320kB high:5184kB active:360968kB inactive:359620kB present:763524kB pages_scanned:1209494 all_unreclaimable? yes
Oct  9 21:46:17 lotus kernel: [135404.332635] lowmem_reserve[]: 0 0 0
Oct  9 21:46:17 lotus kernel: [135404.332641] DMA: 1*4kB 92*8kB 8*16kB 2*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3044kB
Oct  9 21:46:17 lotus kernel: [135404.332656] Normal: 272*4kB 9*8kB 1*16kB 2*32kB 18*64kB 2*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 4440kB
Oct  9 21:46:17 lotus kernel: [135404.332674] Swap cache: add 335012, delete 335012, find 14961/29018, race 0+1
Oct  9 21:46:17 lotus kernel: [135404.332677] [COLOR="Red"]Free swap  = 0kB[/COLOR]
Oct  9 21:46:17 lotus kernel: [135404.332680] Total swap = 746980kB
Oct  9 21:46:17 lotus kernel: [135404.332682] Free swap:            0kB
Oct  9 21:46:17 lotus kernel: [135404.340712] 196480 pages of RAM
Oct  9 21:46:17 lotus kernel: [135404.340718] 0 pages of HIGHMEM
Oct  9 21:46:17 lotus kernel: [135404.340720] 2737 reserved pages
Oct  9 21:46:17 lotus kernel: [135404.340723] 2305 pages shared
Oct  9 21:46:17 lotus kernel: [135404.340725] 0 pages swap cached
Oct  9 21:46:17 lotus kernel: [135404.340727] 0 pages dirty
Oct  9 21:46:17 lotus kernel: [135404.340730] 0 pages writeback
Oct  9 21:46:17 lotus kernel: [135404.340732] 83 pages mapped
Oct  9 21:46:17 lotus kernel: [135404.340735] 6392 pages slab
Oct  9 21:46:17 lotus kernel: [135404.340737] 857 pages pagetables
Oct  9 21:46:17 lotus kernel: [135404.356037] [COLOR="Red"]Out of memory: kill process 18662 (amule) score 56923 or a child[/COLOR]
Oct  9 21:46:17 lotus kernel: [135404.356059] Killed process 18662 (amule)
Oct  9 21:46:17 lotus kernel: [135404.406178][COLOR="Red"] hostname invoked oom-killer: gfp_mask=0x280d2, order=0, oomkilladj=-17[/COLOR]
Oct  9 21:46:17 lotus kernel: [135404.406246]  [out_of_memory+389/448] out_of_memory+0x185/0x1c0
Oct  9 21:46:17 lotus kernel: [135404.406308]  [__alloc_pages+740/832] __alloc_pages+0x2e4/0x340
Oct  9 21:46:17 lotus kernel: [135404.406322]  [vma_adjust+271/1072] vma_adjust+0x10f/0x430
Oct  9 21:46:17 lotus kernel: [135404.406374]  [__handle_mm_fault+2247/2816] __handle_mm_fault+0x8c7/0xb00
Oct  9 21:46:17 lotus kernel: [135404.406398]  [vma_merge+223/464] vma_merge+0xdf/0x1d0
Oct  9 21:46:17 lotus kernel: [135404.406471]  [do_page_fault+294/1664] do_page_fault+0x126/0x680
Oct  9 21:46:17 lotus kernel: [135404.406542]  [do_page_fault+0/1664] do_page_fault+0x0/0x680
Oct  9 21:46:17 lotus kernel: [135404.406552]  [error_code+114/128] error_code+0x72/0x80
Oct  9 21:46:17 lotus kernel: [135404.406589]  [iw_handler_get_iwstats+48/80] iw_handler_get_iwstats+0x30/0x50

went on for 20 mins...

---

### Post by hopelessone on 2007-10-10
hey i just noticed it said 
top - 23:52:40 up 2 days, 15:44,  3 users,  load average: 0.61, 0.79, 0.72

**[SIZE="3"]3 USERS ???!!![/SIZE]**

whats that about??

---

### Post by Vixis on 2007-10-10
> **hopelessone said:**
> hey i just noticed it said 
top - 23:52:40 up 2 days, 15:44,  3 users,  load average: 0.61, 0.79, 0.72

**[SIZE="3"]3 USERS ???!!![/SIZE]**

whats that about??

all running terminals are qualified as different users, also there are root user for system wide processes.
So it is ok.

---

### Post by asmoore82 on 2007-10-10
[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

---

### Post by hopelessone on 2007-10-10
thanks but the link you posted is the same as the second post...

so the refresher...

1. can gparted increase swap?
2. if so do i just move the sliber bar and click ok?

the original 2 questions...

thanks...

---

### Post by floke on 2007-10-10
(1) Yes
(2) Delete swap partition - resize partition next to it - create new swap partition in empty space.

---

### Post by hopelessone on 2007-10-10
Vixis - informative thanks buddy !!!
floke - thanks a mill !!!!!!!!

thanks to everyone..

---

### Post by rsambuca on 2007-10-10
People are just trying to save you some trouble by asking the logical question:  Are you sure you need to increase your swap?  For most users with your specs, the existing swap is more than sufficient.

---

### Post by hopelessone on 2007-10-10
thanks rsambuca...

i thinks its weird also that i ran out of swap...

---

### Post by rsambuca on 2007-10-10
What is the output of this terminal command?

free -m

---

### Post by hopelessone on 2007-10-10
currently :
@lotus:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           756        749          7          0          7        507
-/+ buffers/cache:        234        522
Swap:          729        211        518
@lotus:~$

---

### Post by rsambuca on 2007-10-10
Well, since you have over 500MB of free RAM, and tons of space on your swap, you don't really need to increase your swap, unless you start doing some ram-heavy work.

---

### Post by philinux on 2007-10-10
I've got 320 meg ram swap is 1 gig.

On sys mon  It showing  162 meg ram (53%) used and currently 33 of 909 meg (3.6%) used swap. Only thing running is firefox and sysmon

---

