---
title: "K3b acting weird"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-10-24
k3b wont make a successful burning process...

here is what gives me in the log:

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4163B A103 (/dev/hdb, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 2037322 (4172435456 bytes)
Pipe throughput: 639719424 bytes read, 639715072 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdb obs=32k seek=0'
/dev/hdb: "Current Write Speed" is 8.2x1352KBps.
    3964928/4172435456 ( 0.1%) @0.6x, remaining 87:36 RBU 100.0% UBU   2.9%
   14188544/4172435456 ( 0.3%) @2.2x, remaining 39:04 RBU 100.0% UBU  44.1%
   35291136/4172435456 ( 0.8%) @4.6x, remaining 21:29 RBU 100.0% UBU  64.7%
   54362112/4172435456 ( 1.3%) @4.1x, remaining 18:56 RBU 100.0% UBU  29.4%
   74612736/4172435456 ( 1.8%) @4.4x, remaining 16:28 RBU 100.0% UBU  26.5%
  102367232/4172435456 ( 2.5%) @6.0x, remaining 14:34 RBU 100.0% UBU  91.2%
  130285568/4172435456 ( 3.1%) @6.0x, remaining 12:55 RBU 100.0% UBU  85.3%
  154927104/4172435456 ( 3.7%) @5.3x, remaining 12:06 RBU 100.0% UBU  70.6%
  178585600/4172435456 ( 4.3%) @5.1x, remaining 11:55 RBU 100.0% UBU  44.1%
  190742528/4172435456 ( 4.6%) @2.5x, remaining 12:10 RBU 100.0% UBU  76.5%
  219021312/4172435456 ( 5.2%) @6.1x, remaining 11:25 RBU 100.0% UBU  58.8%
  232325120/4172435456 ( 5.6%) @2.9x, remaining 11:52 RBU 100.0% UBU  85.3%
  244416512/4172435456 ( 5.9%) @2.6x, remaining 12:03 RBU 100.0% UBU  32.4%
  272171008/4172435456 ( 6.5%) @6.0x, remaining 11:27 RBU 100.0% UBU  94.1%
  300122112/4172435456 ( 7.2%) @6.0x, remaining 11:10 RBU 100.0% UBU  91.2%
  328171520/4172435456 ( 7.9%) @6.1x, remaining 10:44 RBU 100.0% UBU  91.2%
  348127232/4172435456 ( 8.3%) @4.3x, remaining 10:48 RBU 100.1% UBU  29.4%
  370835456/4172435456 ( 8.9%) @4.9x, remaining 10:35 RBU 100.0% UBU  94.1%
  381648896/4172435456 ( 9.1%) @2.3x, remaining 10:45 RBU 100.0% UBU  41.2%
  409632768/4172435456 ( 9.8%) @6.0x, remaining 10:33 RBU 100.0% UBU  85.3%
  437387264/4172435456 (10.5%) @6.0x, remaining 10:14 RBU 100.0% UBU  94.1%
  465305600/4172435456 (11.2%) @6.0x, remaining 9:57 RBU 100.0% UBU  82.4%
  489553920/4172435456 (11.7%) @5.2x, remaining 9:54 RBU 100.0% UBU  85.3%
  517242880/4172435456 (12.4%) @6.0x, remaining 9:39 RBU 100.0% UBU  44.1%
  545062912/4172435456 (13.1%) @6.0x, remaining 9:25 RBU 100.0% UBU  88.2%
  573079552/4172435456 (13.7%) @6.1x, remaining 9:18 RBU 100.0% UBU  82.4%
  587857920/4172435456 (14.1%) @3.2x, remaining 9:20 RBU 100.0% UBU  73.5%
:-[ WRITE@LBA=48400h failed with SK=4h/ASC=09h/ACQ=01h]: Input/output error
:-( write failed: Input/output error
/dev/hdb: flushing cache
:-[ FLUSH CACHE failed with SK=4h/ASC=09h/ACQ=01h]: Input/output error
/dev/hdb: updating RMA
/dev/hdb: closing disc
:-[ CLOSE DISC failed with SK=5h/ASC=72h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdb=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2037322 -use-the-force-luke=dummy -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2037322
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.02% done, estimate finish Tue Jan  8 04:25:34 2002
  0.05% done, estimate finish Tue Jan  8 04:25:34 2002
  0.07% done, estimate finish Tue Jan  8 04:25:34 2002
  0.10% done, estimate finish Tue Jan  8 04:25:34 2002
  0.12% done, estimate finish Tue Jan  8 04:39:06 2002
  0.15% done, estimate finish Tue Jan  8 04:36:52 2002
  0.17% done, estimate finish Tue Jan  8 04:35:16 2002
  0.20% done, estimate finish Tue Jan  8 04:34:01 2002
  0.22% done, estimate finish Tue Jan  8 04:33:05 2002
  0.25% done, estimate finish Tue Jan  8 04:32:21 2002
  0.27% done, estimate finish Tue Jan  8 04:31:44 2002
  0.30% done, estimate finish Tue Jan  8 04:31:12 2002
  0.32% done, estimate finish Tue Jan  8 04:30:47 2002
  0.34% done, estimate finish Tue Jan  8 04:30:24 2002
  0.37% done, estimate finish Tue Jan  8 04:30:05 2002
  0.39% done, estimate finish Tue Jan  8 04:29:48 2002
  0.42% done, estimate finish Tue Jan  8 04:29:33 2002
  0.44% done, estimate finish Tue Jan  8 04:29:20 2002
  0.47% done, estimate finish Tue Jan  8 04:29:08 2002
  0.49% done, estimate finish Tue Jan  8 04:28:57 2002
  0.52% done, estimate finish Tue Jan  8 04:28:47 2002
  0.54% done, estimate finish Tue Jan  8 04:28:39 2002
  0.56% done, estimate finish Tue Jan  8 04:28:31 2002
  0.59% done, estimate finish Tue Jan  8 04:28:23 2002
  0.61% done, estimate finish Tue Jan  8 04:28:16 2002
  0.64% done, estimate finish Tue Jan  8 04:30:47 2002
  0.66% done, estimate finish Tue Jan  8 04:30:35 2002
  0.69% done, estimate finish Tue Jan  8 04:30:24 2002
  0.71% done, estimate finish Tue Jan  8 04:30:14 2002
  0.74% done, estimate finish Tue Jan  8 04:30:05 2002
  0.76% done, estimate finish Tue Jan  8 04:29:56 2002
  0.79% done, estimate finish Tue Jan  8 04:29:48 2002
  0.81% done, estimate finish Tue Jan  8 04:29:40 2002
  0.83% done, estimate finish Tue Jan  8 04:37:32 2002
  0.86% done, estimate finish Tue Jan  8 04:39:08 2002
  0.88% done, estimate finish Tue Jan  8 04:38:45 2002
  0.91% done, estimate finish Tue Jan  8 04:38:24 2002
  0.93% done, estimate finish Tue Jan  8 04:38:04 2002
  0.96% done, estimate finish Tue Jan  8 04:37:45 2002
  0.98% done, estimate finish Tue Jan  8 04:39:08 2002
  1.01% done, estimate finish Tue Jan  8 04:38:48 2002
  1.03% done, estimate finish Tue Jan  8 04:38:29 2002
  1.06% done, estimate finish Tue Jan  8 04:38:12 2002
  1.08% done, estimate finish Tue Jan  8 04:37:54 2002
  1.10% done, estimate finish Tue Jan  8 04:39:08 2002
  1.13% done, estimate finish Tue Jan  8 04:40:19 2002
  1.15% done, estimate finish Tue Jan  8 04:40:00 2002
  1.18% done, estimate finish Tue Jan  8 04:41:07 2002
  1.20% done, estimate finish Tue Jan  8 04:40:48 2002
  1.23% done, estimate finish Tue Jan  8 04:40:30 2002
  1.25% done, estimate finish Tue Jan  8 04:40:12 2002
  1.28% done, estimate finish Tue Jan  8 04:41:13 2002
  1.30% done, estimate finish Tue Jan  8 04:40:56 2002
  1.33% done, estimate finish Tue Jan  8 04:40:39 2002
  1.35% done, estimate finish Tue Jan  8 04:40:23 2002
  1.37% done, estimate finish Tue Jan  8 04:40:06 2002
  1.40% done, estimate finish Tue Jan  8 04:39:51 2002
  1.42% done, estimate finish Tue Jan  8 04:39:36 2002
  1.45% done, estimate finish Tue Jan  8 04:39:22 2002
  1.47% done, estimate finish Tue Jan  8 04:40:16 2002
  1.50% done, estimate finish Tue Jan  8 04:40:02 2002
  1.52% done, estimate finish Tue Jan  8 04:39:48 2002
  1.55% done, estimate finish Tue Jan  8 04:39:34 2002
  1.57% done, estimate finish Tue Jan  8 04:39:21 2002
  1.60% done, estimate finish Tue Jan  8 04:39:08 2002
  1.62% done, estimate finish Tue Jan  8 04:38:56 2002
  1.64% done, estimate finish Tue Jan  8 04:38:44 2002
  1.67% done, estimate finish Tue Jan  8 04:39:32 2002
  1.69% done, estimate finish Tue Jan  8 04:39:20 2002
  1.72% done, estimate finish Tue Jan  8 04:39:08 2002
  1.74% done, estimate finish Tue Jan  8 04:38:57 2002
  1.77% done, estimate finish Tue Jan  8 04:38:46 2002
  1.79% done, estimate finish Tue Jan  8 04:38:35 2002
  1.82% done, estimate finish Tue Jan  8 04:38:24 2002
  1.84% done, estimate finish Tue Jan  8 04:38:14 2002
  1.87% done, estimate finish Tue Jan  8 04:38:57 2002
  1.89% done, estimate finish Tue Jan  8 04:38:47 2002
  1.91% done, estimate finish Tue Jan  8 04:38:37 2002
  1.94% done, estimate finish Tue Jan  8 04:38:27 2002
  1.96% done, estimate finish Tue Jan  8 04:38:17 2002
  1.99% done, estimate finish Tue Jan  8 04:38:08 2002
  2.01% done, estimate finish Tue Jan  8 04:37:59 2002
  2.04% done, estimate finish Tue Jan  8 04:37:50 2002
  2.06% done, estimate finish Tue Jan  8 04:38:29 2002
  2.09% done, estimate finish Tue Jan  8 04:38:20 2002
  2.11% done, estimate finish Tue Jan  8 04:38:59 2002
  2.14% done, estimate finish Tue Jan  8 04:38:50 2002
  2.16% done, estimate finish Tue Jan  8 04:38:40 2002
  2.18% done, estimate finish Tue Jan  8 04:38:32 2002
  2.21% done, estimate finish Tue Jan  8 04:38:23 2002
  2.23% done, estimate finish Tue Jan  8 04:38:59 2002
  2.26% done, estimate finish Tue Jan  8 04:39:35 2002
  2.28% done, estimate finish Tue Jan  8 04:39:26 2002
  2.31% done, estimate finish Tue Jan  8 04:39:17 2002
  2.33% done, estimate finish Tue Jan  8 04:39:08 2002
  2.36% done, estimate finish Tue Jan  8 04:39:00 2002
  2.38% done, estimate finish Tue Jan  8 04:38:51 2002
  2.41% done, estimate finish Tue Jan  8 04:38:43 2002
  2.43% done, estimate finish Tue Jan  8 04:38:36 2002
  2.45% done, estimate finish Tue Jan  8 04:38:27 2002
  2.48% done, estimate finish Tue Jan  8 04:39:00 2002
  2.50% done, estimate finish Tue Jan  8 04:38:52 2002
  2.53% done, estimate finish Tue Jan  8 04:38:45 2002
  2.55% done, estimate finish Tue Jan  8 04:38:37 2002
  2.58% done, estimate finish Tue Jan  8 04:38:30 2002
  2.60% done, estimate finish Tue Jan  8 04:38:22 2002
  2.63% done, estimate finish Tue Jan  8 04:38:15 2002
  2.65% done, estimate finish Tue Jan  8 04:38:08 2002
  2.68% done, estimate finish Tue Jan  8 04:38:38 2002
  2.70% done, estimate finish Tue Jan  8 04:38:31 2002
  2.72% done, estimate finish Tue Jan  8 04:38:24 2002
  2.75% done, estimate finish Tue Jan  8 04:38:17 2002
  2.77% done, estimate finish Tue Jan  8 04:38:11 2002
  2.80% done, estimate finish Tue Jan  8 04:38:04 2002
  2.82% done, estimate finish Tue Jan  8 04:37:58 2002
  2.85% done, estimate finish Tue Jan  8 04:37:51 2002
  2.87% done, estimate finish Tue Jan  8 04:38:20 2002
  2.90% done, estimate finish Tue Jan  8 04:38:13 2002
  2.92% done, estimate finish Tue Jan  8 04:38:07 2002
  2.95% done, estimate finish Tue Jan  8 04:38:00 2002
  2.97% done, estimate finish Tue Jan  8 04:37:54 2002
  2.99% done, estimate finish Tue Jan  8 04:37:48 2002
  3.02% done, estimate finish Tue Jan  8 04:37:42 2002
  3.04% done, estimate finish Tue Jan  8 04:37:36 2002
  3.07% done, estimate finish Tue Jan  8 04:38:03 2002
  3.09% done, estimate finish Tue Jan  8 04:37:57 2002
  3.12% done, estimate finish Tue Jan  8 04:37:51 2002
  3.14% done, estimate finish Tue Jan  8 04:37:46 2002
  3.17% done, estimate finish Tue Jan  8 04:37:40 2002
  3.19% done, estimate finish Tue Jan  8 04:37:34 2002
  3.22% done, estimate finish Tue Jan  8 04:37:29 2002
  3.24% done, estimate finish Tue Jan  8 04:37:23 2002
  3.26% done, estimate finish Tue Jan  8 04:37:49 2002
  3.29% done, estimate finish Tue Jan  8 04:37:43 2002
  3.31% done, estimate finish Tue Jan  8 04:37:38 2002
  3.34% done, estimate finish Tue Jan  8 04:37:32 2002
  3.36% done, estimate finish Tue Jan  8 04:37:27 2002
  3.39% done, estimate finish Tue Jan  8 04:37:22 2002
  3.41% done, estimate finish Tue Jan  8 04:37:17 2002
  3.44% done, estimate finish Tue Jan  8 04:37:12 2002
  3.46% done, estimate finish Tue Jan  8 04:37:36 2002
  3.49% done, estimate finish Tue Jan  8 04:37:31 2002
  3.51% done, estimate finish Tue Jan  8 04:37:26 2002
  3.53% done, estimate finish Tue Jan  8 04:37:21 2002
  3.56% done, estimate finish Tue Jan  8 04:37:16 2002
  3.58% done, estimate finish Tue Jan  8 04:37:11 2002
  3.61% done, estimate finish Tue Jan  8 04:37:06 2002
  3.63% done, estimate finish Tue Jan  8 04:37:02 2002
  3.66% done, estimate finish Tue Jan  8 04:37:24 2002
  3.68% done, estimate finish Tue Jan  8 04:37:20 2002
  3.71% done, estimate finish Tue Jan  8 04:37:15 2002
  3.73% done, estimate finish Tue Jan  8 04:37:10 2002
  3.76% done, estimate finish Tue Jan  8 04:37:06 2002
  3.78% done, estimate finish Tue Jan  8 04:37:01 2002
  3.80% done, estimate finish Tue Jan  8 04:36:57 2002
  3.83% done, estimate finish Tue Jan  8 04:36:53 2002
  3.85% done, estimate finish Tue Jan  8 04:37:14 2002
  3.88% done, estimate finish Tue Jan  8 04:37:10 2002
  3.90% done, estimate finish Tue Jan  8 04:37:05 2002
  3.93% done, estimate finish Tue Jan  8 04:37:01 2002
  3.95% done, estimate finish Tue Jan  8 04:36:57 2002
  3.98% done, estimate finish Tue Jan  8 04:36:53 2002
  4.00% done, estimate finish Tue Jan  8 04:36:48 2002
  4.03% done, estimate finish Tue Jan  8 04:36:44 2002
  4.05% done, estimate finish Tue Jan  8 04:36:40 2002
  4.07% done, estimate finish Tue Jan  8 04:37:01 2002
  4.10% done, estimate finish Tue Jan  8 04:36:57 2002
  4.12% done, estimate finish Tue Jan  8 04:36:53 2002
  4.15% done, estimate finish Tue Jan  8 04:36:49 2002
  4.17% done, estimate finish Tue Jan  8 04:36:45 2002
  4.20% done, estimate finish Tue Jan  8 04:36:41 2002
  4.22% done, estimate finish Tue Jan  8 04:36:37 2002
  4.25% done, estimate finish Tue Jan  8 04:36:33 2002
  4.27% done, estimate finish Tue Jan  8 04:36:53 2002
  4.29% done, estimate finish Tue Jan  8 04:36:49 2002
  4.32% done, estimate finish Tue Jan  8 04:36:45 2002
  4.34% done, estimate finish Tue Jan  8 04:36:41 2002
  4.37% done, estimate finish Tue Jan  8 04:37:00 2002
  4.39% done, estimate finish Tue Jan  8 04:36:56 2002
  4.42% done, estimate finish Tue Jan  8 04:36:53 2002
  4.44% done, estimate finish Tue Jan  8 04:36:49 2002
  4.47% done, estimate finish Tue Jan  8 04:36:45 2002
  4.49% done, estimate finish Tue Jan  8 04:36:41 2002
  4.52% done, estimate finish Tue Jan  8 04:36:38 2002
  4.54% done, estimate finish Tue Jan  8 04:36:34 2002
  4.57% done, estimate finish Tue Jan  8 04:36:31 2002
  4.59% done, estimate finish Tue Jan  8 04:36:49 2002
  4.61% done, estimate finish Tue Jan  8 04:36:45 2002
  4.64% done, estimate finish Tue Jan  8 04:36:42 2002
  4.66% done, estimate finish Tue Jan  8 04:36:38 2002
  4.69% done, estimate finish Tue Jan  8 04:36:35 2002
  4.71% done, estimate finish Tue Jan  8 04:36:31 2002
  4.74% done, estimate finish Tue Jan  8 04:36:28 2002
  4.76% done, estimate finish Tue Jan  8 04:36:25 2002
  4.79% done, estimate finish Tue Jan  8 04:36:42 2002
  4.81% done, estimate finish Tue Jan  8 04:36:39 2002
  4.84% done, estimate finish Tue Jan  8 04:36:35 2002
  4.86% done, estimate finish Tue Jan  8 04:36:32 2002
  4.88% done, estimate finish Tue Jan  8 04:36:29 2002
  4.91% done, estimate finish Tue Jan  8 04:36:25 2002
  4.93% done, estimate finish Tue Jan  8 04:36:22 2002
  4.96% done, estimate finish Tue Jan  8 04:36:19 2002
  4.98% done, estimate finish Tue Jan  8 04:36:36 2002
  5.01% done, estimate finish Tue Jan  8 04:36:33 2002
  5.03% done, estimate finish Tue Jan  8 04:36:29 2002
  5.06% done, estimate finish Tue Jan  8 04:36:26 2002
  5.08% done, estimate finish Tue Jan  8 04:36:23 2002
  5.11% done, estimate finish Tue Jan  8 04:36:39 2002
  5.13% done, estimate finish Tue Jan  8 04:36:36 2002
  5.15% done, estimate finish Tue Jan  8 04:36:53 2002
  5.18% done, estimate finish Tue Jan  8 04:37:09 2002
  5.20% done, estimate finish Tue Jan  8 04:37:05 2002
  5.23% done, estimate finish Tue Jan  8 04:37:02 2002
  5.25% done, estimate finish Tue Jan  8 04:36:59 2002
  5.28% done, estimate finish Tue Jan  8 04:36:56 2002
  5.30% done, estimate finish Tue Jan  8 04:37:11 2002
  5.33% done, estimate finish Tue Jan  8 04:37:08 2002
  5.35% done, estimate finish Tue Jan  8 04:37:05 2002
  5.37% done, estimate finish Tue Jan  8 04:37:02 2002
  5.40% done, estimate finish Tue Jan  8 04:36:59 2002
  5.42% done, estimate finish Tue Jan  8 04:36:56 2002
  5.45% done, estimate finish Tue Jan  8 04:36:53 2002
  5.47% done, estimate finish Tue Jan  8 04:36:50 2002
  5.50% done, estimate finish Tue Jan  8 04:37:05 2002
  5.52% done, estimate finish Tue Jan  8 04:37:02 2002
  5.55% done, estimate finish Tue Jan  8 04:36:59 2002
  5.57% done, estimate finish Tue Jan  8 04:36:56 2002
  5.60% done, estimate finish Tue Jan  8 04:36:53 2002
  5.62% done, estimate finish Tue Jan  8 04:36:50 2002
  5.64% done, estimate finish Tue Jan  8 04:36:47 2002
  5.67% done, estimate finish Tue Jan  8 04:36:44 2002
  5.69% done, estimate finish Tue Jan  8 04:36:58 2002
  5.72% done, estimate finish Tue Jan  8 04:36:55 2002
  5.74% done, estimate finish Tue Jan  8 04:36:53 2002
  5.77% done, estimate finish Tue Jan  8 04:36:50 2002
  5.79% done, estimate finish Tue Jan  8 04:36:47 2002
  5.82% done, estimate finish Tue Jan  8 04:36:44 2002
  5.84% done, estimate finish Tue Jan  8 04:36:41 2002
  5.87% done, estimate finish Tue Jan  8 04:36:38 2002
  5.89% done, estimate finish Tue Jan  8 04:36:53 2002
  5.92% done, estimate finish Tue Jan  8 04:36:50 2002
  5.94% done, estimate finish Tue Jan  8 04:36:47 2002
  5.96% done, estimate finish Tue Jan  8 04:36:44 2002
  5.99% done, estimate finish Tue Jan  8 04:36:41 2002
  6.01% done, estimate finish Tue Jan  8 04:36:39 2002
  6.04% done, estimate finish Tue Jan  8 04:36:36 2002
  6.06% done, estimate finish Tue Jan  8 04:36:33 2002
  6.09% done, estimate finish Tue Jan  8 04:36:47 2002
  6.11% done, estimate finish Tue Jan  8 04:36:44 2002
  6.14% done, estimate finish Tue Jan  8 04:36:42 2002
  6.16% done, estimate finish Tue Jan  8 04:36:39 2002
  6.19% done, estimate finish Tue Jan  8 04:36:36 2002
  6.21% done, estimate finish Tue Jan  8 04:36:34 2002
  6.23% done, estimate finish Tue Jan  8 04:36:31 2002
  6.26% done, estimate finish Tue Jan  8 04:36:29 2002
  6.28% done, estimate finish Tue Jan  8 04:36:42 2002
  6.31% done, estimate finish Tue Jan  8 04:36:39 2002
  6.33% done, estimate finish Tue Jan  8 04:36:37 2002
  6.36% done, estimate finish Tue Jan  8 04:36:34 2002
  6.38% done, estimate finish Tue Jan  8 04:37:03 2002
  6.41% done, estimate finish Tue Jan  8 04:37:16 2002
  6.43% done, estimate finish Tue Jan  8 04:37:13 2002
  6.45% done, estimate finish Tue Jan  8 04:37:11 2002
  6.48% done, estimate finish Tue Jan  8 04:37:08 2002
  6.50% done, estimate finish Tue Jan  8 04:37:21 2002
  6.53% done, estimate finish Tue Jan  8 04:37:18 2002
  6.55% done, estimate finish Tue Jan  8 04:37:15 2002
  6.58% done, estimate finish Tue Jan  8 04:37:28 2002
  6.60% done, estimate finish Tue Jan  8 04:37:25 2002
  6.63% done, estimate finish Tue Jan  8 04:37:23 2002
  6.65% done, estimate finish Tue Jan  8 04:37:20 2002
  6.68% done, estimate finish Tue Jan  8 04:37:18 2002
  6.70% done, estimate finish Tue Jan  8 04:37:15 2002
  6.72% done, estimate finish Tue Jan  8 04:37:12 2002
  6.75% done, estimate finish Tue Jan  8 04:37:25 2002
  6.77% done, estimate finish Tue Jan  8 04:37:22 2002
  6.80% done, estimate finish Tue Jan  8 04:37:20 2002
  6.82% done, estimate finish Tue Jan  8 04:37:17 2002
  6.85% done, estimate finish Tue Jan  8 04:37:15 2002
  6.87% done, estimate finish Tue Jan  8 04:37:12 2002
  6.90% done, estimate finish Tue Jan  8 04:37:09 2002
  6.92% done, estimate finish Tue Jan  8 04:37:07 2002
  6.95% done, estimate finish Tue Jan  8 04:37:19 2002
  6.97% done, estimate finish Tue Jan  8 04:37:16 2002
  6.99% done, estimate finish Tue Jan  8 04:37:14 2002
  7.02% done, estimate finish Tue Jan  8 04:37:12 2002
  7.04% done, estimate finish Tue Jan  8 04:37:09 2002
  7.07% done, estimate finish Tue Jan  8 04:37:07 2002
  7.09% done, estimate finish Tue Jan  8 04:37:04 2002
  7.12% done, estimate finish Tue Jan  8 04:37:02 2002
  7.14% done, estimate finish Tue Jan  8 04:37:14 2002
  7.17% done, estimate finish Tue Jan  8 04:37:11 2002
  7.19% done, estimate finish Tue Jan  8 04:37:09 2002
  7.22% done, estimate finish Tue Jan  8 04:37:06 2002
  7.24% done, estimate finish Tue Jan  8 04:37:04 2002
  7.27% done, estimate finish Tue Jan  8 04:37:02 2002
  7.29% done, estimate finish Tue Jan  8 04:36:59 2002
  7.31% done, estimate finish Tue Jan  8 04:36:57 2002
  7.34% done, estimate finish Tue Jan  8 04:36:55 2002
  7.36% done, estimate finish Tue Jan  8 04:37:06 2002
  7.39% done, estimate finish Tue Jan  8 04:37:04 2002
  7.41% done, estimate finish Tue Jan  8 04:37:02 2002
  7.44% done, estimate finish Tue Jan  8 04:36:59 2002
  7.46% done, estimate finish Tue Jan  8 04:36:57 2002
  7.49% done, estimate finish Tue Jan  8 04:36:55 2002
  7.51% done, estimate finish Tue Jan  8 04:36:53 2002
  7.53% done, estimate finish Tue Jan  8 04:36:50 2002
  7.56% done, estimate finish Tue Jan  8 04:37:01 2002
  7.58% done, estimate finish Tue Jan  8 04:36:59 2002
  7.61% done, estimate finish Tue Jan  8 04:36:57 2002
  7.63% done, estimate finish Tue Jan  8 04:36:55 2002
  7.66% done, estimate finish Tue Jan  8 04:36:53 2002
  7.68% done, estimate finish Tue Jan  8 04:36:50 2002
  7.71% done, estimate finish Tue Jan  8 04:36:48 2002
  7.73% done, estimate finish Tue Jan  8 04:36:46 2002
  7.76% done, estimate finish Tue Jan  8 04:36:57 2002
  7.78% done, estimate finish Tue Jan  8 04:36:55 2002
  7.80% done, estimate finish Tue Jan  8 04:36:53 2002
  7.83% done, estimate finish Tue Jan  8 04:36:50 2002
  7.85% done, estimate finish Tue Jan  8 04:36:48 2002
  7.88% done, estimate finish Tue Jan  8 04:36:46 2002
  7.90% done, estimate finish Tue Jan  8 04:36:44 2002
  7.93% done, estimate finish Tue Jan  8 04:36:42 2002
  7.95% done, estimate finish Tue Jan  8 04:36:53 2002
  7.98% done, estimate finish Tue Jan  8 04:36:50 2002
  8.00% done, estimate finish Tue Jan  8 04:36:48 2002
  8.03% done, estimate finish Tue Jan  8 04:36:46 2002
  8.05% done, estimate finish Tue Jan  8 04:36:44 2002
  8.07% done, estimate finish Tue Jan  8 04:36:42 2002
  8.10% done, estimate finish Tue Jan  8 04:36:40 2002
  8.12% done, estimate finish Tue Jan  8 04:36:38 2002
  8.15% done, estimate finish Tue Jan  8 04:36:48 2002
  8.17% done, estimate finish Tue Jan  8 04:36:46 2002
  8.20% done, estimate finish Tue Jan  8 04:36:44 2002
  8.22% done, estimate finish Tue Jan  8 04:36:42 2002
  8.25% done, estimate finish Tue Jan  8 04:36:40 2002
  8.27% done, estimate finish Tue Jan  8 04:36:38 2002
  8.30% done, estimate finish Tue Jan  8 04:36:37 2002
  8.32% done, estimate finish Tue Jan  8 04:36:35 2002
  8.34% done, estimate finish Tue Jan  8 04:36:45 2002
  8.37% done, estimate finish Tue Jan  8 04:36:43 2002
  8.39% done, estimate finish Tue Jan  8 04:36:41 2002
  8.42% done, estimate finish Tue Jan  8 04:36:39 2002
  8.44% done, estimate finish Tue Jan  8 04:36:37 2002
  8.47% done, estimate finish Tue Jan  8 04:36:35 2002
  8.49% done, estimate finish Tue Jan  8 04:36:33 2002
  8.52% done, estimate finish Tue Jan  8 04:36:31 2002
  8.54% done, estimate finish Tue Jan  8 04:36:41 2002
  8.57% done, estimate finish Tue Jan  8 04:36:39 2002
  8.59% done, estimate finish Tue Jan  8 04:36:37 2002
  8.61% done, estimate finish Tue Jan  8 04:36:35 2002
  8.64% done, estimate finish Tue Jan  8 04:36:33 2002
  8.66% done, estimate finish Tue Jan  8 04:36:31 2002
  8.69% done, estimate finish Tue Jan  8 04:36:30 2002
  8.71% done, estimate finish Tue Jan  8 04:36:28 2002
  8.74% done, estimate finish Tue Jan  8 04:36:37 2002
  8.76% done, estimate finish Tue Jan  8 04:36:35 2002
  8.79% done, estimate finish Tue Jan  8 04:36:34 2002
  8.81% done, estimate finish Tue Jan  8 04:36:32 2002
  8.84% done, estimate finish Tue Jan  8 04:36:30 2002
  8.86% done, estimate finish Tue Jan  8 04:36:28 2002
  8.88% done, estimate finish Tue Jan  8 04:36:26 2002
  8.91% done, estimate finish Tue Jan  8 04:36:25 2002
  8.93% done, estimate finish Tue Jan  8 04:36:23 2002
  8.96% done, estimate finish Tue Jan  8 04:36:32 2002
  8.98% done, estimate finish Tue Jan  8 04:36:30 2002
  9.01% done, estimate finish Tue Jan  8 04:36:29 2002
  9.03% done, estimate finish Tue Jan  8 04:36:27 2002
  9.06% done, estimate finish Tue Jan  8 04:36:25 2002
  9.08% done, estimate finish Tue Jan  8 04:36:23 2002
  9.11% done, estimate finish Tue Jan  8 04:36:32 2002
  9.13% done, estimate finish Tue Jan  8 04:36:31 2002
  9.15% done, estimate finish Tue Jan  8 04:36:40 2002
  9.18% done, estimate finish Tue Jan  8 04:36:38 2002
  9.20% done, estimate finish Tue Jan  8 04:36:36 2002
  9.23% done, estimate finish Tue Jan  8 04:36:35 2002
  9.25% done, estimate finish Tue Jan  8 04:36:33 2002
  9.28% done, estimate finish Tue Jan  8 04:36:31 2002
  9.30% done, estimate finish Tue Jan  8 04:36:29 2002
  9.33% done, estimate finish Tue Jan  8 04:36:28 2002
  9.35% done, estimate finish Tue Jan  8 04:36:37 2002
  9.38% done, estimate finish Tue Jan  8 04:36:35 2002
  9.40% done, estimate finish Tue Jan  8 04:36:33 2002
  9.42% done, estimate finish Tue Jan  8 04:36:31 2002
  9.45% done, estimate finish Tue Jan  8 04:36:30 2002
  9.47% done, estimate finish Tue Jan  8 04:36:28 2002
  9.50% done, estimate finish Tue Jan  8 04:36:26 2002
  9.52% done, estimate finish Tue Jan  8 04:36:25 2002
  9.55% done, estimate finish Tue Jan  8 04:36:33 2002
  9.57% done, estimate finish Tue Jan  8 04:36:32 2002
  9.60% done, estimate finish Tue Jan  8 04:36:30 2002
  9.62% done, estimate finish Tue Jan  8 04:36:28 2002
  9.65% done, estimate finish Tue Jan  8 04:36:27 2002
  9.67% done, estimate finish Tue Jan  8 04:36:25 2002
  9.69% done, estimate finish Tue Jan  8 04:36:23 2002
  9.72% done, estimate finish Tue Jan  8 04:36:53 2002
  9.74% done, estimate finish Tue Jan  8 04:36:51 2002
  9.77% done, estimate finish Tue Jan  8 04:36:49 2002
  9.79% done, estimate finish Tue Jan  8 04:36:48 2002
  9.82% done, estimate finish Tue Jan  8 04:36:56 2002
  9.84% done, estimate finish Tue Jan  8 04:36:54 2002
  9.87% done, estimate finish Tue Jan  8 04:36:53 2002
  9.89% done, estimate finish Tue Jan  8 04:36:51 2002
  9.92% done, estimate finish Tue Jan  8 04:36:49 2002
  9.94% done, estimate finish Tue Jan  8 04:36:48 2002
  9.96% done, estimate finish Tue Jan  8 04:36:46 2002
  9.99% done, estimate finish Tue Jan  8 04:36:44 2002
 10.01% done, estimate finish Tue Jan  8 04:36:53 2002
 10.04% done, estimate finish Tue Jan  8 04:36:51 2002
 10.06% done, estimate finish Tue Jan  8 04:36:49 2002
 10.09% done, estimate finish Tue Jan  8 04:36:48 2002
 10.11% done, estimate finish Tue Jan  8 04:36:46 2002
 10.14% done, estimate finish Tue Jan  8 04:36:44 2002
 10.16% done, estimate finish Tue Jan  8 04:36:43 2002
 10.18% done, estimate finish Tue Jan  8 04:36:41 2002
 10.21% done, estimate finish Tue Jan  8 04:36:49 2002
 10.23% done, estimate finish Tue Jan  8 04:36:48 2002
 10.26% done, estimate finish Tue Jan  8 04:36:46 2002
 10.28% done, estimate finish Tue Jan  8 04:36:45 2002
 10.31% done, estimate finish Tue Jan  8 04:36:43 2002
 10.33% done, estimate finish Tue Jan  8 04:36:41 2002
 10.36% done, estimate finish Tue Jan  8 04:36:40 2002
 10.38% done, estimate finish Tue Jan  8 04:36:38 2002
 10.41% done, estimate finish Tue Jan  8 04:36:37 2002
 10.43% done, estimate finish Tue Jan  8 04:36:45 2002
 10.46% done, estimate finish Tue Jan  8 04:36:43 2002
 10.48% done, estimate finish Tue Jan  8 04:36:41 2002
 10.50% done, estimate finish Tue Jan  8 04:36:40 2002
 10.53% done, estimate finish Tue Jan  8 04:36:38 2002
 10.55% done, estimate finish Tue Jan  8 04:36:37 2002
 10.58% done, estimate finish Tue Jan  8 04:36:35 2002
 10.60% done, estimate finish Tue Jan  8 04:36:34 2002
 10.63% done, estimate finish Tue Jan  8 04:36:42 2002
 10.65% done, estimate finish Tue Jan  8 04:36:40 2002
 10.68% done, estimate finish Tue Jan  8 04:36:39 2002
 10.70% done, estimate finish Tue Jan  8 04:36:37 2002
 10.73% done, estimate finish Tue Jan  8 04:36:35 2002
 10.75% done, estimate finish Tue Jan  8 04:36:34 2002
 10.77% done, estimate finish Tue Jan  8 04:36:32 2002
 10.80% done, estimate finish Tue Jan  8 04:36:31 2002
 10.82% done, estimate finish Tue Jan  8 04:36:39 2002
 10.85% done, estimate finish Tue Jan  8 04:36:37 2002
 10.87% done, estimate finish Tue Jan  8 04:36:36 2002
 10.90% done, estimate finish Tue Jan  8 04:36:34 2002
 10.92% done, estimate finish Tue Jan  8 04:36:33 2002
 10.95% done, estimate finish Tue Jan  8 04:36:31 2002
 10.97% done, estimate finish Tue Jan  8 04:36:30 2002
 11.00% done, estimate finish Tue Jan  8 04:36:28 2002
 11.02% done, estimate finish Tue Jan  8 04:36:36 2002
 11.04% done, estimate finish Tue Jan  8 04:36:34 2002
 11.07% done, estimate finish Tue Jan  8 04:36:33 2002
 11.09% done, estimate finish Tue Jan  8 04:36:32 2002
 11.12% done, estimate finish Tue Jan  8 04:36:30 2002
 11.14% done, estimate finish Tue Jan  8 04:36:29 2002
 11.17% done, estimate finish Tue Jan  8 04:36:27 2002
 11.19% done, estimate finish Tue Jan  8 04:36:26 2002
 11.22% done, estimate finish Tue Jan  8 04:36:33 2002
 11.24% done, estimate finish Tue Jan  8 04:36:32 2002
 11.26% done, estimate finish Tue Jan  8 04:36:30 2002
 11.29% done, estimate finish Tue Jan  8 04:36:29 2002
 11.31% done, estimate finish Tue Jan  8 04:36:28 2002
 11.34% done, estimate finish Tue Jan  8 04:36:26 2002
 11.36% done, estimate finish Tue Jan  8 04:36:25 2002
 11.39% done, estimate finish Tue Jan  8 04:36:23 2002
 11.41% done, estimate finish Tue Jan  8 04:36:31 2002
 11.44% done, estimate finish Tue Jan  8 04:36:29 2002
 11.46% done, estimate finish Tue Jan  8 04:36:28 2002
 11.49% done, estimate finish Tue Jan  8 04:36:26 2002
 11.51% done, estimate finish Tue Jan  8 04:36:25 2002
 11.53% done, estimate finish Tue Jan  8 04:36:24 2002
 11.56% done, estimate finish Tue Jan  8 04:36:22 2002
 11.58% done, estimate finish Tue Jan  8 04:36:21 2002
 11.61% done, estimate finish Tue Jan  8 04:36:28 2002
 11.63% done, estimate finish Tue Jan  8 04:36:27 2002
 11.66% done, estimate finish Tue Jan  8 04:36:25 2002
 11.68% done, estimate finish Tue Jan  8 04:36:24 2002
 11.71% done, estimate finish Tue Jan  8 04:36:23 2002
 11.73% done, estimate finish Tue Jan  8 04:36:21 2002
 11.76% done, estimate finish Tue Jan  8 04:36:20 2002
 11.78% done, estimate finish Tue Jan  8 04:36:19 2002
 11.81% done, estimate finish Tue Jan  8 04:36:17 2002
 11.83% done, estimate finish Tue Jan  8 04:36:24 2002
 11.85% done, estimate finish Tue Jan  8 04:36:23 2002
 11.88% done, estimate finish Tue Jan  8 04:36:22 2002
 11.90% done, estimate finish Tue Jan  8 04:36:20 2002
 11.93% done, estimate finish Tue Jan  8 04:36:19 2002
 11.95% done, estimate finish Tue Jan  8 04:36:18 2002
 11.98% done, estimate finish Tue Jan  8 04:36:16 2002
 12.00% done, estimate finish Tue Jan  8 04:36:15 2002
 12.03% done, estimate finish Tue Jan  8 04:36:22 2002
 12.05% done, estimate finish Tue Jan  8 04:36:21 2002
 12.08% done, estimate finish Tue Jan  8 04:36:19 2002
 12.10% done, estimate finish Tue Jan  8 04:36:18 2002
 12.12% done, estimate finish Tue Jan  8 04:36:17 2002
 12.15% done, estimate finish Tue Jan  8 04:36:16 2002
 12.17% done, estimate finish Tue Jan  8 04:36:14 2002
 12.20% done, estimate finish Tue Jan  8 04:36:13 2002
 12.22% done, estimate finish Tue Jan  8 04:36:20 2002
 12.25% done, estimate finish Tue Jan  8 04:36:19 2002
 12.27% done, estimate finish Tue Jan  8 04:36:17 2002
 12.30% done, estimate finish Tue Jan  8 04:36:16 2002
 12.32% done, estimate finish Tue Jan  8 04:36:15 2002
 12.34% done, estimate finish Tue Jan  8 04:36:13 2002
 12.37% done, estimate finish Tue Jan  8 04:36:20 2002
 12.39% done, estimate finish Tue Jan  8 04:36:19 2002
 12.42% done, estimate finish Tue Jan  8 04:36:18 2002
 12.44% done, estimate finish Tue Jan  8 04:36:16 2002
 12.47% done, estimate finish Tue Jan  8 04:36:15 2002
 12.49% done, estimate finish Tue Jan  8 04:36:14 2002
 12.52% done, estimate finish Tue Jan  8 04:36:21 2002
 12.54% done, estimate finish Tue Jan  8 04:36:19 2002
 12.57% done, estimate finish Tue Jan  8 04:36:18 2002
 12.59% done, estimate finish Tue Jan  8 04:36:17 2002
 12.61% done, estimate finish Tue Jan  8 04:36:16 2002
 12.64% done, estimate finish Tue Jan  8 04:36:14 2002
 12.66% done, estimate finish Tue Jan  8 04:36:13 2002
 12.69% done, estimate finish Tue Jan  8 04:36:12 2002
 12.71% done, estimate finish Tue Jan  8 04:36:19 2002
 12.74% done, estimate finish Tue Jan  8 04:36:17 2002
 12.76% done, estimate finish Tue Jan  8 04:36:16 2002
 12.79% done, estimate finish Tue Jan  8 04:36:15 2002
 12.81% done, estimate finish Tue Jan  8 04:36:14 2002
 12.84% done, estimate finish Tue Jan  8 04:36:12 2002
 12.86% done, estimate finish Tue Jan  8 04:36:11 2002
 12.88% done, estimate finish Tue Jan  8 04:36:10 2002
 12.91% done, estimate finish Tue Jan  8 04:36:16 2002
 12.93% done, estimate finish Tue Jan  8 04:36:15 2002
 12.96% done, estimate finish Tue Jan  8 04:36:14 2002
 12.98% done, estimate finish Tue Jan  8 04:36:13 2002
 13.01% done, estimate finish Tue Jan  8 04:36:12 2002
 13.03% done, estimate finish Tue Jan  8 04:36:10 2002
 13.06% done, estimate finish Tue Jan  8 04:36:09 2002
 13.08% done, estimate finish Tue Jan  8 04:36:08 2002
 13.11% done, estimate finish Tue Jan  8 04:36:07 2002
 13.13% done, estimate finish Tue Jan  8 04:36:13 2002
 13.16% done, estimate finish Tue Jan  8 04:36:12 2002
 13.18% done, estimate finish Tue Jan  8 04:36:11 2002
 13.20% done, estimate finish Tue Jan  8 04:36:10 2002
 13.23% done, estimate finish Tue Jan  8 04:36:09 2002
 13.25% done, estimate finish Tue Jan  8 04:36:07 2002
 13.28% done, estimate finish Tue Jan  8 04:36:06 2002
 13.30% done, estimate finish Tue Jan  8 04:36:05 2002
 13.33% done, estimate finish Tue Jan  8 04:36:11 2002
 13.35% done, estimate finish Tue Jan  8 04:36:10 2002
 13.38% done, estimate finish Tue Jan  8 04:36:09 2002
 13.40% done, estimate finish Tue Jan  8 04:36:08 2002
 13.42% done, estimate finish Tue Jan  8 04:36:07 2002
 13.45% done, estimate finish Tue Jan  8 04:36:05 2002
 13.47% done, estimate finish Tue Jan  8 04:36:04 2002
 13.50% done, estimate finish Tue Jan  8 04:36:03 2002
 13.52% done, estimate finish Tue Jan  8 04:36:09 2002
 13.55% done, estimate finish Tue Jan  8 04:36:08 2002
 13.57% done, estimate finish Tue Jan  8 04:36:07 2002
 13.60% done, estimate finish Tue Jan  8 04:36:06 2002
 13.62% done, estimate finish Tue Jan  8 04:36:05 2002
 13.65% done, estimate finish Tue Jan  8 04:36:04 2002
 13.67% done, estimate finish Tue Jan  8 04:36:03 2002
 13.69% done, estimate finish Tue Jan  8 04:36:01 2002
 13.72% done, estimate finish Tue Jan  8 04:36:08 2002
 13.74% done, estimate finish Tue Jan  8 04:36:06 2002
 13.77% done, estimate finish Tue Jan  8 04:36:05 2002
 13.79% done, estimate finish Tue Jan  8 04:36:04 2002
 13.82% done, estimate finish Tue Jan  8 04:36:03 2002
 13.84% done, estimate finish Tue Jan  8 04:36:02 2002
 13.87% done, estimate finish Tue Jan  8 04:36:01 2002
 13.89% done, estimate finish Tue Jan  8 04:36:00 2002
 13.92% done, estimate finish Tue Jan  8 04:36:06 2002
 13.94% done, estimate finish Tue Jan  8 04:36:05 2002
 13.96% done, estimate finish Tue Jan  8 04:36:04 2002
 13.99% done, estimate finish Tue Jan  8 04:36:03 2002
 14.01% done, estimate finish Tue Jan  8 04:36:01 2002
 14.04% done, estimate finish Tue Jan  8 04:36:00 2002
 14.06% done, estimate finish Tue Jan  8 04:35:59 2002
 14.09% done, estimate finish Tue Jan  8 04:35:58 2002
 14.11% done, estimate finish Tue Jan  8 04:36:04 2002
 14.14% done, estimate finish Tue Jan  8 04:36:03 2002
 14.16% done, estimate finish Tue Jan  8 04:36:02 2002
 14.19% done, estimate finish Tue Jan  8 04:36:01 2002
 14.21% done, estimate finish Tue Jan  8 04:36:00 2002
 14.23% done, estimate finish Tue Jan  8 04:35:59 2002
 14.26% done, estimate finish Tue Jan  8 04:35:58 2002
 14.28% done, estimate finish Tue Jan  8 04:35:57 2002
 14.31% done, estimate finish Tue Jan  8 04:36:03 2002
 14.33% done, estimate finish Tue Jan  8 04:36:01 2002
 14.36% done, estimate finish Tue Jan  8 04:36:00 2002
 14.38% done, estimate finish Tue Jan  8 04:35:59 2002
 14.41% done, estimate finish Tue Jan  8 04:35:58 2002
 14.43% done, estimate finish Tue Jan  8 04:35:57 2002
 14.46% done, estimate finish Tue Jan  8 04:35:56 2002
 14.48% done, estimate finish Tue Jan  8 04:35:55 2002
 14.50% done, estimate finish Tue Jan  8 04:35:54 2002
 14.53% done, estimate finish Tue Jan  8 04:36:00 2002
 14.55% done, estimate finish Tue Jan  8 04:35:59 2002
 14.58% done, estimate finish Tue Jan  8 04:35:58 2002
 14.60% done, estimate finish Tue Jan  8 04:35:57 2002
 14.63% done, estimate finish Tue Jan  8 04:35:56 2002
 14.65% done, estimate finish Tue Jan  8 04:35:55 2002
 14.68% done, estimate finish Tue Jan  8 04:36:07 2002
 14.70% done, estimate finish Tue Jan  8 04:36:06 2002
 14.73% done, estimate finish Tue Jan  8 04:36:05 2002
 14.75% done, estimate finish Tue Jan  8 04:36:04 2002
 14.77% done, estimate finish Tue Jan  8 04:36:03 2002
 14.80% done, estimate finish Tue Jan  8 04:36:09 2002
 14.82% done, estimate finish Tue Jan  8 04:36:08 2002
 14.85% done, estimate finish Tue Jan  8 04:36:07 2002
 14.87% done, estimate finish Tue Jan  8 04:36:06 2002
 14.90% done, estimate finish Tue Jan  8 04:36:04 2002
 14.92% done, estimate finish Tue Jan  8 04:36:03 2002
 14.95% done, estimate finish Tue Jan  8 04:36:02 2002
 14.97% done, estimate finish Tue Jan  8 04:36:01 2002
 15.00% done, estimate finish Tue Jan  8 04:36:07 2002
 15.02% done, estimate finish Tue Jan  8 04:36:06 2002
 15.04% done, estimate finish Tue Jan  8 04:36:05 2002
 15.07% done, estimate finish Tue Jan  8 04:36:04 2002
 15.09% done, estimate finish Tue Jan  8 04:36:03 2002
 15.12% done, estimate finish Tue Jan  8 04:36:02 2002
 15.14% done, estimate finish Tue Jan  8 04:36:01 2002
 15.17% done, estimate finish Tue Jan  8 04:36:00 2002
 15.19% done, estimate finish Tue Jan  8 04:36:05 2002
 15.22% done, estimate finish Tue Jan  8 04:36:04 2002
 15.24% done, estimate finish Tue Jan  8 04:36:03 2002
 15.27% done, estimate finish Tue Jan  8 04:36:02 2002
 15.29% done, estimate finish Tue Jan  8 04:36:01 2002
 15.31% done, estimate finish Tue Jan  8 04:36:00 2002

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid cad 1 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-johnnyw/k3bOHvQva.tmp -rational-rock -hide-list /tmp/kde-johnnyw/k3bATSg7a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-johnnyw/k3bOyiW3a.tmp -no-cache-inodes -udf -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-johnnyw/k3bgFcD1a.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid cad 1 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-johnnyw/k3bpbIsMa.tmp -rational-rock -hide-list /tmp/kde-johnnyw/k3bHb7Lmc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-johnnyw/k3b10pGfc.tmp -no-cache-inodes -udf -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-johnnyw/k3bLeVgIa.tmp 

```

---

### Post by johnnyw on 2007-10-24
would  someone help me?

---

### Post by johnnyw on 2007-10-24
can someoooone help meee please?

---

### Post by chili555 on 2007-10-24
This may be helpful:

[http://osdir.com/ml/kde.k3b/2006-04/msg00133.html](http://osdir.com/ml/kde.k3b/2006-04/msg00133.html)

This suggests it's a known bug with growisofs (for which K3b is a wrapper):

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/91210](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/91210)

Many entries found in Google; no clear solutions.

---

### Post by johnnyw on 2007-10-25
this same thing did not happen with dapper

---

