---
title: "Photo Permissions and Laptop Speakers"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by searchesend on 2008-01-14
Hey, I converted completely to Ubuntu (mistakenly) and am really impressed. I'm only a very basic user but I would like to 'iron out' the following minor glitches:-
1. On some Photo CD's my friend sent me I can't view some pictures (Don't have permission to view/copy?)
2. The built in laptop speakers work only when I make a mistake and it beeps. This isn't a major problem as I rarely use them. I updated the ALSA drivers last time and it changed a lot of settings, after losing heart I reinstalled Ubuntu.

Any help is much appreciated!

---

### Post by angryfirelord on 2008-01-15
1.) I'm not sure why you're getting "Permission Denied", but right-click on the file, click Properties, and click the Permissions tab. Make sure everything says at lead "Read-only" or Read-something.
2.) The beep is the "BIOS speaker", which in laptops is piped through the regular speaker. Run
```
alsamixer
```
and make sure that the "front" and "pcm" volumes are turned up.

---

### Post by searchesend on 2008-01-15
Yeah I checked the Permissions tab and it's checked as 'Read and Write' but I can't change anything - it says at the bottom 'You're not the owner so you can't change these permissions'

As for the Alsa Mixer, there's no sound when the Front and PCM are at full. My 3.5 jack out is working good though? There are a lot of related threads but they seem involved and need lots of trawling through to find the answer appropriate to my laptop.
Cheers for your help mate!

---

### Post by hyper_ch on 2008-01-15
Well, can you navigate to the cd-drive in the terminal?

Should be

```

cd /media/cd-rom

```

And then issue:

```

ls -al

```

and post that here and also say to which pictures you don't have access.

---

### Post by searchesend on 2008-01-15
matt@matt-laptop:~$ cd /media/cd-rom
bash: cd: /media/cd-rom: No such file or directory


Jesus you must get bored of dealing with ignorant people like me!

---

### Post by hyper_ch on 2008-01-15
well, I said I wasn't sure because I am not at my machine right now ;)

However if you have problems with paths (not knowing them right) you can use the magic of TAB COMPLETION ;)

```

cd /media/cd

```
And then press ONCE the TAB button --> if there is only one matching file/folder that starts with "cd" it will auto-complete that. If there are more, nothing will appear. If you then press TAB a second time, it will list the possibilities. Now that is really cool, right? ^^

And if it's not a cd in your drive, then you'll have to enter one of the dvd folders ;)

As said, not sure right now by heart which one it is, just try it out, you'll find the right one ;)

---

### Post by searchesend on 2008-01-15
damn straight thats cool!

matt@matt-laptop:/media/cdrom$ ls -al
total 641842
drwxr-xr-x 2 4294967295 4294967295    14924 2006-12-07 18:19 .
drwxr-xr-x 3 root       root           4096 2008-01-15 08:39 ..
-rw------- 1        501        501  3097804 2006-10-27 11:09 DSC00588.JPG
-rw------- 1        501        501  3016354 2006-10-27 11:10 DSC00589.JPG
-rw------- 1        501        501  3161921 2006-10-27 11:10 DSC00590.JPG
-rw------- 1        501        501  3168298 2006-11-07 20:00 DSC00685.JPG
-rw------- 1        501        501  3305917 2006-11-07 20:01 DSC00686.JPG
-rw------- 1        501        501  3186576 2006-11-09 21:44 DSC00689.JPG
-rw------- 1        501        501  3078833 2006-11-09 21:56 DSC00690.JPG
-rw-r--r-- 1        501        501  3378805 2006-11-17 09:28 DSC00691.JPG
-rw-r--r-- 1        501        501  3332005 2006-11-17 09:45 DSC00692.JPG
-rw------- 1        501        501  2926415 2006-11-09 22:25 DSC00693.JPG
-rw------- 1        501        501  2933471 2006-11-09 22:25 DSC00694.JPG
-rw------- 1        501        501  2765846 2006-11-09 22:26 DSC00695.JPG
-rw------- 1        501        501  2958562 2006-11-09 22:26 DSC00696.JPG
-rw------- 1        501        501   477393 2006-11-01 09:00 DSCF0697.JPG
-rw------- 1        501        501   487722 2006-11-02 04:15 DSCF0716.JPG
-rw------- 1        501        501   489270 2006-11-03 12:14 DSCF0758.JPG
-rw------- 1        501        501   496358 2006-11-04 06:00 DSCF0776.JPG
-rw-r--r-- 1        501        501   763717 2006-11-16 17:30 DSCF0794.JPG
-rw------- 1        501        501   490688 2006-11-04 09:19 DSCF0810.JPG
-rw------- 1        501        501   501209 2006-11-04 09:20 DSCF0812.JPG
-rw------- 1        501        501   498327 2006-11-05 02:08 DSCF0819.JPG
-rw------- 1        501        501   493156 2006-11-05 03:54 DSCF0848.JPG
-rw------- 1        501        501   494071 2006-11-05 05:27 DSCF0886.JPG
-rw-r--r-- 1        501        501   484237 2006-11-16 17:32 DSCF0955.JPG
-rw-r--r-- 1        501        501   632334 2006-11-16 17:19 DSCF0973.JPG
-rw------- 1        501        501   446822 2006-11-10 02:56 DSCF1022.JPG
-rw------- 1        501        501   487216 2006-11-10 03:02 DSCF1023.JPG
-rw------- 1        501        501   471419 2006-11-10 03:03 DSCF1024.JPG
-rw------- 1        501        501 25526550 2004-04-16 14:55 DSCF1502.AVI
-rw------- 1        501        501  3609029 2006-11-04 02:37 IMG_0792.JPG
-rw-r--r-- 1        501        501  3205560 2006-11-13 09:12 IMG_0793.JPG
-rw-r--r-- 1        501        501  2812766 2006-11-13 09:12 IMG_0794.JPG
-rw------- 1        501        501  2409770 2006-11-04 04:30 IMG_0795.JPG
-rw------- 1        501        501  2676087 2006-11-04 04:30 IMG_0796.JPG
-rw------- 1        501        501  2610186 2006-11-04 04:38 IMG_0797.JPG
-rw------- 1        501        501  3353242 2006-11-04 05:13 IMG_0798.JPG
-rw------- 1        501        501  3497830 2006-11-04 05:13 IMG_0799.JPG
-rw------- 1        501        501  3614595 2006-11-04 05:17 IMG_0800.JPG
-rw------- 1        501        501  2835544 2006-11-04 05:18 IMG_0801.JPG
-rw------- 1        501        501  2110679 2006-11-04 05:22 IMG_0802.JPG
-rw------- 1        501        501  3402697 2006-11-04 05:39 IMG_0803.JPG
-rw------- 1        501        501  3258714 2006-11-04 05:40 IMG_0804.JPG
-rw------- 1        501        501  3421006 2006-11-04 05:42 IMG_0805.JPG
-rw------- 1        501        501  3430498 2006-11-04 05:44 IMG_0806.JPG
-rw-r--r-- 1        501        501  2474197 2006-11-13 09:12 IMG_0807.JPG
-rw-r--r-- 1        501        501  2637460 2006-11-13 09:12 IMG_0808.JPG
-rw-r--r-- 1        501        501  3135526 2006-11-13 09:12 IMG_0809.JPG
-rw------- 1        501        501  2310757 2006-11-04 06:02 IMG_0810.JPG
-rw------- 1        501        501  2003103 2006-11-04 06:03 IMG_0811.JPG
-rw------- 1        501        501  2847130 2006-11-04 06:04 IMG_0812.JPG
-rw-r--r-- 1        501        501  3143983 2006-11-13 09:12 IMG_0813.JPG
-rw------- 1        501        501  3853753 2006-11-04 06:24 IMG_0814.JPG
-rw------- 1        501        501  3802657 2006-11-04 06:31 IMG_0815.JPG
-rw------- 1        501        501  3584077 2006-11-04 06:31 IMG_0816.JPG
-rw------- 1        501        501  3793778 2006-11-04 06:32 IMG_0817.JPG
-rw-r--r-- 1        501        501  2939589 2006-11-13 09:12 IMG_0818.JPG
-rw------- 1        501        501  3973977 2006-11-04 06:34 IMG_0819.JPG
-rw------- 1        501        501  4058403 2006-11-04 06:35 IMG_0820.JPG
-rw------- 1        501        501  4034380 2006-11-04 06:35 IMG_0821.JPG
-rw------- 1        501        501  3937834 2006-11-04 06:36 IMG_0822.JPG
-rw-r--r-- 1        501        501  1716105 2006-11-13 09:12 IMG_0823.JPG
-rw------- 1        501        501  2474104 2006-11-04 06:58 IMG_0824.JPG
-rw------- 1        501        501  2441910 2006-11-04 06:58 IMG_0825.JPG
-rw------- 1        501        501  2251694 2006-11-04 06:59 IMG_0827.JPG
-rw------- 1        501        501  2593084 2006-11-04 07:50 IMG_0831.JPG
-rw------- 1        501        501  3286096 2006-11-04 08:48 IMG_0832.JPG
-rw------- 1        501        501  3150466 2006-11-04 08:50 IMG_0834.JPG
-rw------- 1        501        501  2915875 2006-11-04 08:52 IMG_0835.JPG
-rw------- 1        501        501  3341560 2006-11-04 08:53 IMG_0836.JPG
-rw------- 1        501        501  2551084 2006-11-04 08:54 IMG_0837.JPG
-rw------- 1        501        501  2880434 2006-11-04 08:54 IMG_0838.JPG
-rw------- 1        501        501  2533863 2006-11-04 08:54 IMG_0839.JPG
-rw------- 1        501        501  1908779 2006-11-04 08:56 IMG_0840.JPG
-rw------- 1        501        501  2837299 2006-11-04 09:03 IMG_0841.JPG
-rw------- 1        501        501  2843995 2006-11-04 09:08 IMG_0842.JPG
-rw------- 1        501        501  3183251 2006-11-04 09:08 IMG_0843.JPG
-rw------- 1        501        501  2916408 2006-11-04 09:09 IMG_0844.JPG
-rw------- 1        501        501  2745417 2006-11-04 09:09 IMG_0845.JPG
-rw------- 1        501        501  2930530 2006-11-04 09:09 IMG_0846.JPG
-rw------- 1        501        501  2827999 2006-11-04 09:10 IMG_0847.JPG
-rw-r--r-- 1        501        501  2648297 2006-11-13 09:12 IMG_0848.JPG
-rw------- 1        501        501  3233909 2006-11-04 09:15 IMG_0849.JPG
-rw------- 1        501        501  3370561 2006-11-04 09:16 IMG_0850.JPG
-rw------- 1        501        501  3197813 2006-11-04 09:16 IMG_0851.JPG
-rw------- 1        501        501  1696556 2006-11-04 09:18 IMG_0852.JPG
-rw------- 1        501        501  2272682 2006-11-04 09:18 IMG_0853.JPG
-rw------- 1        501        501  3233284 2006-11-04 09:22 IMG_0854.JPG
-rw------- 1        501        501  2722081 2006-11-04 09:22 IMG_0855.JPG
-rw------- 1        501        501  1456228 2006-11-05 02:14 IMG_0856.JPG
-rw------- 1        501        501  1740093 2006-11-05 02:15 IMG_0857.JPG
-rw------- 1        501        501  2443267 2006-11-05 02:48 IMG_0858.JPG
-rw------- 1        501        501  2567384 2006-11-05 02:48 IMG_0859.JPG
-rw------- 1        501        501  2420591 2006-11-05 02:48 IMG_0860.JPG
-rw------- 1        501        501  2172628 2006-11-05 02:50 IMG_0861.JPG
-rw------- 1        501        501  2345305 2006-11-05 03:13 IMG_0862.JPG
-rw------- 1        501        501  2826427 2006-11-05 03:14 IMG_0863.JPG
-rw------- 1        501        501  1634678 2006-11-05 03:22 IMG_0864.JPG
-rw------- 1        501        501  1616042 2006-11-05 03:22 IMG_0865.JPG
-rw------- 1        501        501  2034117 2006-11-05 03:26 IMG_0866.JPG
-rw------- 1        501        501  2600659 2006-11-05 03:27 IMG_0867.JPG
-rw------- 1        501        501  2155599 2006-11-05 03:28 IMG_0868.JPG
-rw------- 1        501        501  3132358 2006-11-05 03:34 IMG_0869.JPG
-rw------- 1        501        501  2248115 2006-11-05 03:36 IMG_0870.JPG
-rw------- 1        501        501  2268889 2006-11-05 03:43 IMG_0871.JPG
-rw------- 1        501        501  2159104 2006-11-05 03:43 IMG_0872.JPG
-rw-r--r-- 1        501        501  2282530 2006-11-13 09:12 IMG_0873.JPG
-rw------- 1        501        501  2963857 2006-11-05 03:46 IMG_0874.JPG
-rw------- 1        501        501  2843945 2006-11-05 03:57 IMG_0875.JPG
-rw------- 1        501        501  3117887 2006-11-05 04:00 IMG_0876.JPG
-rw------- 1        501        501  2858684 2006-11-05 04:03 IMG_0877.JPG
-rw------- 1        501        501  1685403 2006-11-05 04:04 IMG_0878.JPG
-rw------- 1        501        501  2744557 2006-11-05 04:06 IMG_0879.JPG
-rw------- 1        501        501  2881665 2006-11-05 04:07 IMG_0880.JPG
-rw------- 1        501        501  3147586 2006-11-05 04:08 IMG_0881.JPG
-rw------- 1        501        501  2564116 2006-11-05 04:09 IMG_0882.JPG
-rw------- 1        501        501  3231396 2006-11-05 04:10 IMG_0883.JPG
-rw------- 1        501        501  2360162 2006-11-05 04:12 IMG_0884.JPG
-rw------- 1        501        501  1813322 2006-11-05 04:15 IMG_0885.JPG
-rw------- 1        501        501  2932760 2006-11-05 04:16 IMG_0886.JPG
-rw------- 1        501        501  2203992 2006-11-05 04:18 IMG_0887.JPG
-rw------- 1        501        501  2696095 2006-11-05 04:20 IMG_0888.JPG
-rw------- 1        501        501  2773920 2006-11-05 04:34 IMG_0889.JPG
-rw------- 1        501        501  1839737 2006-11-05 04:46 IMG_0890.JPG
-rw------- 1        501        501  2772565 2006-11-05 05:06 IMG_0891.JPG
-rw------- 1        501        501  3242870 2006-11-05 05:08 IMG_0892.JPG
-rw------- 1        501        501  3504554 2006-11-05 05:09 IMG_0893.JPG
-rw------- 1        501        501  2449932 2006-11-05 05:28 IMG_0894.JPG
-rw------- 1        501        501  2637065 2006-11-05 05:30 IMG_0895.JPG
-rw------- 1        501        501  2691715 2006-11-05 05:56 IMG_0896.JPG
-rw------- 1        501        501  2469819 2006-11-05 05:57 IMG_0897.JPG
-rw------- 1        501        501  2756508 2006-11-05 05:57 IMG_0898.JPG
-rw------- 1        501        501  1791953 2006-11-05 05:58 IMG_0899.JPG
-rw------- 1        501        501  1536244 2006-11-05 05:58 IMG_0900.JPG
-rw------- 1        501        501  2729786 2006-11-05 06:08 IMG_0901.JPG
-rw------- 1        501        501  2896236 2006-11-05 08:18 IMG_0902.JPG
-rw------- 1        501        501  2816750 2006-11-05 08:18 IMG_0903.JPG
-rw------- 1        501        501  3027175 2006-11-05 08:19 IMG_0904.JPG
-rw------- 1        501        501  2776375 2006-11-05 08:20 IMG_0905.JPG
-rw-r--r-- 1        501        501  2095420 2006-11-13 09:12 IMG_0906.JPG
-rw------- 1        501        501  2393207 2006-11-05 08:57 IMG_0907.JPG
-rw-r--r-- 1        501        501  2109667 2006-11-13 09:13 IMG_0908.JPG
-rw------- 1        501        501  2033507 2006-11-05 09:14 IMG_0909.JPG
-rw------- 1        501        501  1467349 2006-11-07 02:06 IMG_0910.JPG
-rw-r--r-- 1        501        501  1686537 2006-11-13 09:13 IMG_0911.JPG
-rw------- 1        501        501  2277235 2006-11-07 09:06 IMG_0912.JPG
-rw------- 1        501        501  1987576 2006-11-07 09:07 IMG_0913.JPG
-rw------- 1        501        501  2768118 2006-11-07 09:08 IMG_0914.JPG
-rw------- 1        501        501  2581123 2006-11-07 09:14 IMG_0915.JPG
-rw------- 1        501        501  2130924 2006-11-07 09:16 IMG_0916.JPG
-rw------- 1        501        501  1867844 2006-11-07 09:18 IMG_0917.JPG
-rw------- 1        501        501  1939491 2006-11-07 11:37 IMG_0918.JPG
-rw------- 1        501        501  1875252 2006-11-07 11:48 IMG_0919.JPG
-rw------- 1        501        501  1740599 2006-11-07 11:49 IMG_0920.JPG
-rw------- 1        501        501  1619641 2006-11-07 11:53 IMG_0921.JPG
-rw-r--r-- 1        501        501  1269848 2006-11-13 09:13 IMG_0922.JPG
-rw-r--r-- 1        501        501  1746058 2006-11-13 09:13 IMG_0923.JPG
-rw-r--r-- 1        501        501  1704074 2006-11-13 09:13 IMG_0924.JPG
-rw------- 1        501        501  1970776 2006-11-07 12:22 IMG_0925.JPG
-rw------- 1        501        501  1662219 2006-11-07 12:23 IMG_0926.JPG
-rw------- 1        501        501  1637077 2006-11-07 12:26 IMG_0927.JPG
-rw------- 1        501        501  1709453 2006-11-07 12:26 IMG_0928.JPG
-rw------- 1        501        501  1719329 2006-11-08 01:58 IMG_0929.JPG
-rw-r--r-- 1        501        501  1399356 2006-11-13 09:13 IMG_0930.JPG
-rw-r--r-- 1        501        501  1492229 2006-11-13 09:13 IMG_0931.JPG
-rw-r--r-- 1        501        501  2024845 2006-11-13 09:13 IMG_0932.JPG
-rw------- 1        501        501  2234678 2006-11-08 02:36 IMG_0934.JPG
-rw------- 1        501        501  2498627 2006-11-08 02:45 IMG_0935.JPG
-rw------- 1        501        501  1715603 2006-11-08 02:51 IMG_0940.JPG
-rw------- 1        501        501  2036549 2006-11-08 02:51 IMG_0941.JPG
-rw------- 1        501        501  1928715 2006-11-08 02:51 IMG_0942.JPG
-rw------- 1        501        501  1723951 2006-11-08 02:58 IMG_0944.JPG
-rw------- 1        501        501  1751251 2006-11-08 02:58 IMG_0945.JPG
-rw------- 1        501        501  1745892 2006-11-08 02:58 IMG_0946.JPG
-rw------- 1        501        501  2484870 2006-11-08 02:59 IMG_0947.JPG
-rw------- 1        501        501  1822883 2006-11-08 02:59 IMG_0948.JPG
-rw------- 1        501        501  2083497 2006-11-08 02:59 IMG_0949.JPG
-rw------- 1        501        501  2118409 2006-11-08 02:59 IMG_0950.JPG
-rw------- 1        501        501  1981259 2006-11-08 03:00 IMG_0951.JPG
-rw------- 1        501        501  1882538 2006-11-08 03:01 IMG_0952.JPG
-rw------- 1        501        501  1639075 2006-11-08 03:01 IMG_0953.JPG
-rw------- 1        501        501  2003864 2006-11-08 03:01 IMG_0954.JPG
-rw------- 1        501        501  1810709 2006-11-08 03:27 IMG_0956.JPG
-rw-r--r-- 1        501        501  2065558 2006-11-13 09:13 IMG_0957.JPG
-rw------- 1        501        501  2316349 2006-11-08 03:29 IMG_0958.JPG
-rw-r--r-- 1        501        501  1741354 2006-11-13 09:14 IMG_0959.JPG
-rw------- 1        501        501  2386445 2006-11-08 03:30 IMG_0960.JPG
-rw------- 1        501        501  2225822 2006-11-08 03:31 IMG_0961.JPG
-rw-r--r-- 1        501        501  2058779 2006-11-13 09:14 IMG_0962.JPG
-rw-r--r-- 1        501        501  1807863 2006-11-13 09:14 IMG_0963.JPG
-rw-r--r-- 1        501        501  1305785 2006-11-13 09:14 IMG_0964.JPG
-rw------- 1        501        501  1645439 2006-11-08 06:50 IMG_0965.JPG
-rw------- 1        501        501  1548175 2006-11-08 06:50 IMG_0966.JPG
-rw------- 1        501        501  2562505 2006-11-08 07:16 IMG_0967.JPG
-rw------- 1        501        501  2407648 2006-11-08 10:49 IMG_0968.JPG
-rw------- 1        501        501  2412957 2006-11-08 10:50 IMG_0969.JPG
-rw------- 1        501        501  2164600 2006-11-08 10:50 IMG_0970.JPG
-rw------- 1        501        501  2201949 2006-11-08 11:10 IMG_0971.JPG
-rw------- 1        501        501  1667744 2006-11-08 11:27 IMG_0972.JPG
-rw------- 1        501        501  1918776 2006-11-08 11:45 IMG_0973.JPG
-rw------- 1        501        501  2012347 2006-11-08 11:59 IMG_0974.JPG
-rw------- 1        501        501  1362113 2006-11-08 12:17 IMG_0975.JPG
-rw------- 1        501        501  1752782 2006-11-08 12:20 IMG_0976.JPG
-rw------- 1        501        501  2096317 2006-11-09 02:52 IMG_0977.JPG
-rw------- 1        501        501  2365083 2006-11-09 02:52 IMG_0978.JPG
-rw------- 1        501        501  2246280 2006-11-09 02:54 IMG_0979.JPG
-rw-r--r-- 1        501        501  1916812 2006-11-13 09:14 IMG_0980.JPG
-rw-r--r-- 1        501        501  1883753 2006-11-13 09:14 IMG_0981.JPG
-rw------- 1        501        501  2473451 2006-11-09 02:55 IMG_0982.JPG
-rw------- 1        501        501  2111235 2006-11-09 02:56 IMG_0983.JPG
-rw------- 1        501        501  2273354 2006-11-09 02:56 IMG_0984.JPG
-rw------- 1        501        501  2493183 2006-11-09 02:56 IMG_0985.JPG
-rw------- 1        501        501  2191865 2006-11-09 02:56 IMG_0986.JPG
-rw------- 1        501        501  2412090 2006-11-09 02:56 IMG_0987.JPG
-rw------- 1        501        501  1982740 2006-11-09 02:56 IMG_0988.JPG
-rw------- 1        501        501  2393363 2006-11-09 02:56 IMG_0989.JPG
-rw------- 1        501        501  2131080 2006-11-09 02:56 IMG_0990.JPG
-rw------- 1        501        501  2486045 2006-11-09 03:01 IMG_0991.JPG
-rw------- 1        501        501  2597257 2006-11-09 04:10 IMG_0992.JPG
-rw------- 1        501        501  2063284 2006-11-09 04:10 IMG_0993.JPG
-rw------- 1        501        501  1775767 2006-11-09 04:10 IMG_0994.JPG
-rw------- 1        501        501  2237214 2006-11-09 04:11 IMG_0995.JPG
-rw-r--r-- 1        501        501  2448325 2006-11-13 09:14 IMG_0996.JPG
-rw-r--r-- 1        501        501  3204069 2006-11-13 09:14 IMG_0997.JPG
-rw------- 1        501        501  2879332 2006-11-09 04:33 IMG_0999.JPG
-rw-r--r-- 1        501        501  1739082 2006-11-13 09:14 IMG_1000.JPG
-rw------- 1        501        501  1929358 2006-11-09 04:41 IMG_1001.JPG
-rw------- 1        501        501  2377954 2006-11-09 04:42 IMG_1002.JPG
-rw------- 1        501        501  1595472 2006-11-10 02:08 IMG_1003.JPG
-rw------- 1        501        501   975045 2006-11-10 02:22 IMG_1005.JPG
-rw------- 1        501        501   969643 2006-11-10 02:29 IMG_1006.JPG
-rw------- 1        501        501  1104189 2006-11-10 02:32 IMG_1007.JPG
-rw------- 1        501        501  1001484 2006-11-10 02:32 IMG_1008.JPG
-rw------- 1        501        501  1008435 2006-11-10 02:33 IMG_1009.JPG
-rw------- 1        501        501  1471284 2006-11-10 02:33 IMG_1010.JPG
-rw------- 1        501        501  1552311 2006-11-10 02:34 IMG_1011.JPG
-rw------- 1        501        501  1462012 2006-11-10 02:34 IMG_1012.JPG
-rw------- 1        501        501  1555096 2006-11-10 02:36 IMG_1013.JPG
-rw------- 1        501        501  1621792 2006-11-10 02:37 IMG_1014.JPG
-rw------- 1        501        501  1587479 2006-11-10 02:40 IMG_1015.JPG
-rw------- 1        501        501  1607751 2006-11-10 02:41 IMG_1016.JPG
-rw------- 1        501        501  1607974 2006-11-10 02:43 IMG_1017.JPG
-rw------- 1        501        501  1711286 2006-11-10 02:43 IMG_1018.JPG
-rw------- 1        501        501  1874292 2006-11-10 02:43 IMG_1019.JPG
-rw------- 1        501        501  1961426 2006-11-10 02:44 IMG_1020.JPG
-rw------- 1        501        501  1613224 2006-11-10 02:44 IMG_1021.JPG
-rw------- 1        501        501  1563096 2006-11-10 02:44 IMG_1022.JPG
-rw------- 1        501        501  1730988 2006-11-10 02:45 IMG_1023.JPG
-rw------- 1        501        501  1946025 2006-11-10 02:45 IMG_1024.JPG
-rw------- 1        501        501  2084920 2006-11-10 02:45 IMG_1025.JPG
-rw------- 1        501        501  2160606 2006-11-10 02:45 IMG_1026.JPG
-rw------- 1        501        501  2232952 2006-11-10 02:45 IMG_1027.JPG
-rw------- 1        501        501  1819443 2006-11-10 02:47 IMG_1029.JPG
-rw------- 1        501        501  1808783 2006-11-10 02:47 IMG_1030.JPG
-rw------- 1        501        501  1878918 2006-11-10 02:48 IMG_1031.JPG
-rw------- 1        501        501  1710946 2006-11-10 02:48 IMG_1032.JPG
-rw------- 1        501        501  1600337 2006-11-10 02:48 IMG_1033.JPG
-rw------- 1        501        501  1853326 2006-11-10 02:48 IMG_1034.JPG
-rw------- 1        501        501  1952078 2006-11-10 02:49 IMG_1035.JPG
-rw------- 1        501        501  1599984 2006-11-10 02:49 IMG_1036.JPG
-rw------- 1        501        501  1717546 2006-11-10 02:50 IMG_1037.JPG
-rw------- 1        501        501  1626897 2006-11-10 02:50 IMG_1038.JPG
-rw------- 1        501        501  1647755 2006-11-10 02:51 IMG_1039.JPG
-rw------- 1        501        501  1650767 2006-11-10 02:54 IMG_1040.JPG
-rw------- 1        501        501  1825739 2006-11-10 02:57 IMG_1047.JPG
-rw------- 1        501        501  1695956 2006-11-10 02:59 IMG_1048.JPG
-rw------- 1        501        501  1761706 2006-11-10 02:59 IMG_1049.JPG
-rw-r--r-- 1        501        501  1891885 2006-11-13 09:14 IMG_1050.JPG
-rw-r--r-- 1        501        501  1807291 2006-11-13 09:14 IMG_1051.JPG
-rw------- 1        501        501  1939078 2006-11-10 03:05 IMG_1052.JPG
-rw------- 1        501        501  1804750 2006-11-10 03:06 IMG_1053.JPG
-rw------- 1        501        501  2021617 2006-11-10 03:06 IMG_1054.JPG
-rw-r--r-- 1        501        501  1783442 2006-11-13 09:14 IMG_1055.JPG
-rw------- 1        501        501  2086758 2006-11-10 04:17 IMG_1056.JPG
-rw------- 1        501        501  2425052 2006-11-10 04:25 IMG_1057.JPG
-rw------- 1        501        501  2374376 2006-11-10 04:26 IMG_1058.JPG
-rw-r--r-- 1        501        501  2147422 2006-11-13 09:14 IMG_1059.JPG
-rw------- 1        501        501  2876895 2006-11-10 05:47 IMG_1060.JPG
-rw-r--r-- 1        501        501  1524456 2006-11-13 09:14 IMG_1061.JPG
-rw-r--r-- 1        501        501  1636263 2006-11-13 09:14 IMG_1062.JPG
-rw------- 1        501        501  1516556 2006-11-11 17:26 IMG_1063.JPG
-rw------- 1        501        501  1896923 2006-11-11 17:40 IMG_1064.JPG
-rw------- 1        501        501  1826702 2006-11-11 17:40 IMG_1065.JPG
-rw------- 1        501        501  1955648 2006-11-11 17:41 IMG_1066.JPG
-rw------- 1        501        501  1511161 2006-11-26 16:37 Nepal 2 020.jpg
-rw------- 1        501        501  1615770 2006-11-26 16:38 Nepal 2 054.jpg
-rw------- 1        501        501  1580543 2006-11-26 16:38 Nepal 2 057.jpg
matt@matt-laptop:/media/cdrom$ 


There's a string of photos I can't open at the start from 'DSC00588.jpg' to 'DSC00690.jpg'. I can't open most of the 'IMG' files e.g. 'IMG_1066.jpg' and the final string of 'Nepal 2---.jpg'.

---

### Post by searchesend on 2008-01-15
A better way to say it is all files starting with
'-rw-r--r-- '
are the ones i can view

---

### Post by hyper_ch on 2008-01-15
I bet you can view IMG_1062.JPG but not IMG_1063.JPG, right?

Problem is you don't have the permissions to even read most of the pictures. Only user with system id 501 has those rights. Simpelst thing would be to copy them as root to some other place and then chown them to your user.

```

mkdir /home/USER/Desktop/CD-Pics
sudo cp /media/cdrom/* /home/USER/Desktop/CD-Pics/
sudo chown USER.USER /home/USER/Desktop/CD-Pics/*

```

First you create a folder on your desktop
Then you copy the pictures there
And finally you change ownership of the files to your user

Just replace "USER" with your actual username.

---

### Post by searchesend on 2008-01-15
Nice one mate! I don't know how you learn this stuff but thanks for sharing THE KNOWLEDGE.

---

### Post by hyper_ch on 2008-01-15
Now if you have this problems a bit more often, then you could turn it into a bash script:

```

#!/bin/bash
USER=  # put your username here!
mkdir /home/$USER/Desktop/CD-Pics
chown $USER.$USER /home/$USER/Desktop/CD-Pics
cp /media/cdrom/* /home/$USER/Desktop/CD-Pics/
chown $USER.$USER /home/$USER/Desktop/CD-Pics/*

```

Put the above in a file (e.g. imagecopy.sh) and make sure you set the right value for USER=   (e.g.  USER=searchesend) and then run it with:
```

sudo sh imagecopy.sh

```

Problem is we need to run it as root because copying and chowning require root priveleges.... otherwise you will be asked twice to enter your password.

Running/executing anything as root is inherently dangerous! Just make sure paths and stuff is alright and that you reviewed the code!

---

### Post by searchesend on 2008-01-15
Cheers man, I tried 'making a bash' but ran into a glitch, not to worry though I can just use the method before. Nice photo there dude.

---

### Post by hyper_ch on 2008-01-15
what didn't work with the bash script?

---

### Post by searchesend on 2008-01-15
#!/bin/bash
This worked fine,
USER=  # put your username here!
tried putting my user name in and from what i remember it worked fine but as soon as i try the following with the $ in front of my user name is says it's not valid? I tried it without the $ but does the $ denote a root file?
mkdir /home/$USER/Desktop/CD-Pics
chown $USER.$USER /home/$USER/Desktop/CD-Pics
cp /media/cdrom/* /home/$USER/Desktop/CD-Pics/
chown $USER.$USER /home/$USER/Desktop/CD-Pics/*

---

### Post by searchesend on 2008-01-15
I wont be able to to respond until about 1pm (english time) tomorrow!

---

### Post by hyper_ch on 2008-01-16
then you did not put in your correct username. It's the one you use to login with. When you open the terminal you'll also see it on the far left of the (terminal) window....

---

### Post by searchesend on 2008-01-16
matt@matt-laptop:~$ #!/bin/bash
matt@matt-laptop:~$ USER=  #matt
matt@matt-laptop:~$ mkdir /home/$Matt/Desktop/Photos
mkdir: cannot create directory `/home//Desktop/Photos': No such file or directory
matt@matt-laptop:~$ 

To do this will I need to make a permanent folder on my Desktop? I'm not going to need to do this often so I may be better off doing it the way you showed me before... it is interesting though. I guess this is how you get addicted to Linux!

---

### Post by hyper_ch on 2008-01-16
Ok,

(1)
> 
Put the above in a file (e.g. imagecopy.sh) 


(2)
> 
set the right value for USER= (e.g. USER=searchesend)


---

### Post by searchesend on 2008-01-16
ah excellent, I presumed by file you meant terminal, sorry. Didn't know you could do that in files! So the next time I need to change the permissions of pictures I drop them into a folder on the desktop named 'CD-Pics'? Thank you for your help.

---

