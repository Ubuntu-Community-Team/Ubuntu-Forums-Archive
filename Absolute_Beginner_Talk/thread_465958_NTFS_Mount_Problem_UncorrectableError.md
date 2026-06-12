---
title: "NTFS Mount Problem: UncorrectableError"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by yesudeep on 2007-06-06
I have a problem mounting my NTFS partitions after Windows crashed on one of my computers.  
Windows is unable to start. However, Ubuntu shows me that it is unable to mount the NTFS partition
for Windows.  Here is the logged output from dmesg:

```

[   16.860326]  hda: hda1 hda2 hda3 < hda5 >
[   34.659419] Buffer I/O error on device hda1, logical block 10876537
[   38.575199] Buffer I/O error on device hda1, logical block 10876538
[   42.540817] Buffer I/O error on device hda1, logical block 10876539
[   46.428921] Buffer I/O error on device hda1, logical block 10876540
[   50.375528] Buffer I/O error on device hda1, logical block 10876541
[   54.348910] Buffer I/O error on device hda1, logical block 10876542
[   58.316621] Buffer I/O error on device hda1, logical block 10876543
[   62.292508] Buffer I/O error on device hda1, logical block 10876544
[   66.224216] Buffer I/O error on device hda1, logical block 10876545
[   70.207818] Buffer I/O error on device hda1, logical block 10876546
[   74.172579] Buffer I/O error on device hda1, logical block 10876547
[   78.122075] Buffer I/O error on device hda1, logical block 10876548
[   82.072793] Buffer I/O error on device hda1, logical block 10876549
[   86.018961] Buffer I/O error on device hda1, logical block 10876550
[   89.938567] Buffer I/O error on device hda1, logical block 10876551
[   93.883536] Buffer I/O error on device hda1, logical block 10876552
[   97.828993] Buffer I/O error on device hda1, logical block 10876553
[  101.804492] Buffer I/O error on device hda1, logical block 10876554
[  105.758112] Buffer I/O error on device hda1, logical block 10876555
[  109.726534] Buffer I/O error on device hda1, logical block 10876556
[  113.635430] Buffer I/O error on device hda1, logical block 10876557
[  117.564165] Buffer I/O error on device hda1, logical block 10876558
[  121.459427] Buffer I/O error on device hda1, logical block 10876559
[  125.370065] Buffer I/O error on device hda1, logical block 10876560
[  129.299773] Buffer I/O error on device hda1, logical block 10876561
[  133.244099] Buffer I/O error on device hda1, logical block 10876562
[  137.188902] Buffer I/O error on device hda1, logical block 10876563

```

And hereinafter follows the output from:

```

egrep -i 'ntfs|dma|fuse' /var/log/messages /var/log/messages.log /var/log/daemon.log

```

Output:

```

/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [    0.000000]   DMA             0 ->     4096
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   32.422038]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   32.422054]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   34.500432] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   34.555875] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   46.541129] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [   47.662924] fuse init (API version 7.8)
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  130.701772] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  130.701781] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876600
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  134.650623] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  134.650629] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876601
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  138.619598] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  138.619604] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876602
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  142.564717] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  142.564723] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876603
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  146.501990] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  146.501996] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876604
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  150.421868] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  150.421873] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876605
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  154.360965] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  154.360971] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876606
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  158.314296] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  158.314302] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876607
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  162.241260] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  162.241266] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876608
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  166.151292] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  166.151298] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876609
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  170.118373] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  170.118379] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876610
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  174.095288] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  174.095294] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876611
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  178.027924] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  178.027929] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876612
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  181.937965] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  181.937971] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876613
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  185.883733] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  185.883739] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876614
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  189.821549] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  189.821555] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876615
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  193.770125] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  193.770130] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876616
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  197.752521] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  197.752527] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876617
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  201.691009] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  201.691014] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876618
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  205.628829] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  205.628835] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876619
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  209.564454] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  209.564459] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876620
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  213.533374] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  213.533380] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876621
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  217.495438] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  217.495443] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876622
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  221.420731] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  221.420737] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876623
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  225.370613] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  225.370619] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876624
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  229.325569] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  229.325575] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876625
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  233.295095] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 20:59:35 neelkanth kernel: [  233.295101] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876626
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [    0.000000]   DMA             0 ->     4096
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   27.207135]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   27.207152]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   29.277508] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   29.330953] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   41.519146] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   42.587562] fuse init (API version 7.8)
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   47.142682] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   47.142691] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876600
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   51.130239] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   51.130246] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876601
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   55.102038] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   55.102044] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876602
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   59.057429] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   59.057438] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876603
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   63.022309] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   63.022315] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876604
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   67.009331] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   67.009337] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876605
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   70.953742] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   70.953748] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876606
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   74.908890] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   74.908896] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876607
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   78.823144] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   78.823149] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876608
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   82.756314] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   82.756320] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876609
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   86.712557] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   86.712562] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876610
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   90.689802] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   90.689808] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876611
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   94.650974] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   94.650980] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876612
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   98.596169] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [   98.596175] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876613
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  102.532250] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  102.532256] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876614
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  106.473048] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  106.473054] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876615

```

I'd appreciate someone helping out and getting my NTFS partition to mount.  I have seen szaka help
out with some NTFS problems.  Hopefully, he can help me out too.  :-)

Thanks.

Regards,
Yesudeep.

---

### Post by yesudeep on 2007-06-06
```

/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  110.450370] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  110.450376] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876616
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  114.407821] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  114.407827] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876617
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  118.341699] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  118.341704] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876618
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  122.252862] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  122.252867] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876619
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  126.197638] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  126.197644] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876620
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  130.126548] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  130.126554] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876621
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  134.103182] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  134.103188] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876622
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  138.057871] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  138.057877] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876623
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  141.978564] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  141.978570] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876624
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  145.898931] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  145.898937] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876625
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  149.837332] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  5 23:24:47 neelkanth kernel: [  149.837338] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876626
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [    0.000000]   DMA             0 ->     4096
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   26.013301]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   26.013317]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   28.067870] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   28.123453] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   39.992097] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   41.110302] fuse init (API version 7.8)
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   45.717577] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   45.717586] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876600
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   49.653228] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   49.653235] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876601
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   53.603401] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   53.603407] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876602
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   57.537793] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   57.537802] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876603
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   61.478197] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   61.478203] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876604
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   65.414803] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   65.414809] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876605
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   69.407403] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   69.407409] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876606
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   73.363797] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   73.363803] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876607
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   77.273043] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   77.273049] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876608
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   81.175854] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   81.175860] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876609
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   85.125212] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   85.125218] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876610
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   89.081797] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   89.081803] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876611
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   93.057937] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   93.057943] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876612
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   97.055122] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [   97.055127] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876613
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  100.974830] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  100.974836] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876614
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  104.943034] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  104.943040] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876615
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  108.863462] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  108.863468] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876616
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  112.807268] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  112.807273] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876617
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  116.770308] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  116.770314] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876618
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  120.679721] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  120.679727] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876619
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  124.579630] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  124.579635] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876620
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  128.575887] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  128.575893] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876621
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  132.483768] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  132.483773] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876622
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  136.461109] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  136.461115] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876623
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  140.377700] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  140.377706] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876624
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  144.298063] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  144.298069] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876625
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  148.227747] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 14:09:32 neelkanth kernel: [  148.227753] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876626
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [    0.000000]   DMA             0 ->     4096
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   20.404396]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   20.404413]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   22.471622] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   22.528455] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   44.213427] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   45.340147] fuse init (API version 7.8)
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   49.781573] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   49.781582] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876600
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   53.721970] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   53.721977] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876601
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   57.629473] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   57.629479] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876602
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   61.573805] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   61.573813] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876603
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   65.496242] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   65.496248] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876604

```

Third installment follows.  :-)

---

### Post by yesudeep on 2007-06-06
```

/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   69.447381] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   69.447387] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876605
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   73.414030] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   73.414036] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876606
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   77.376243] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   77.376249] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876607
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   81.341679] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   81.341685] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876608
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   85.254770] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   85.254776] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876609
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   89.234010] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   89.234016] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876610
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   93.172142] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   93.172148] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876611
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   97.127158] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [   97.127164] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876612
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  101.048944] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  101.048950] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876613
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  104.969665] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  104.969671] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876614
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  108.855981] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  108.855986] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876615
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  112.809701] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  112.809707] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876616
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  116.726595] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  116.726601] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876617
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  120.722890] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  120.722896] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876618
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  124.662443] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  124.662449] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876619
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  128.619488] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  128.619494] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876620
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  132.545909] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  132.545915] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876621
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  136.508970] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  136.508976] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876622
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  140.489322] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  140.489328] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876623
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  144.358963] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  144.358969] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876624
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  148.313235] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  148.313241] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876625
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  152.260543] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 16:57:57 neelkanth kernel: [  152.260549] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876626
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [    0.000000]   DMA             0 ->     4096
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   14.789366]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   14.789383]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   16.860023] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   16.913046] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   29.111452] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   30.094080] fuse init (API version 7.8)
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   34.659381] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   34.659390] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876600
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   38.575169] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   38.575176] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876601
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   42.540788] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   42.540794] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876602
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   46.428881] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   46.428889] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876603
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   50.375498] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   50.375505] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876604
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   54.348881] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   54.348887] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876605
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   58.316592] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   58.316598] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876606
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   62.292479] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   62.292485] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876607
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   66.224188] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   66.224194] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876608
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   70.207788] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   70.207795] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876609
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   74.172550] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   74.172556] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876610
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   78.122047] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   78.122052] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876611
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   82.072765] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   82.072771] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876612
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   86.018932] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   86.018938] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876613
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   89.938539] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   89.938545] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876614
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   93.883508] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   93.883513] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876615
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   97.828965] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [   97.828971] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876616
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  101.804464] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  101.804470] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876617
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  105.758083] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  105.758089] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876618
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  109.726506] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  109.726512] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876619
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  113.635402] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  113.635408] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876620
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  117.564137] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  117.564143] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876621
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  121.459399] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  121.459405] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876622
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  125.370036] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  125.370042] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876623
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  129.299745] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  129.299751] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876624
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  133.244071] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  133.244077] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876625
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  137.188874] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
/var/log/messages:Jun  6 18:06:32 neelkanth kernel: [  137.188880] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=10876626, high=0, low=10876626, sector=10876626

```

No more installments left.  :-)

Regards,
Yesudeep.

---

