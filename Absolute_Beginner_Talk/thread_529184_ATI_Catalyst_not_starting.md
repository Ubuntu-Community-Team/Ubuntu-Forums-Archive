---
title: "ATI Catalyst not starting"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-08-18
Hi, I just installed my Radeon 9600 Mobile Pro with ATI's Linux drivers by following this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

It seems to be working as I can get the correct output in the verifying installation section. The output of fglrxinfo is 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

```

And ATI Catalyst Control Center has appeared on my Applications menu. So I clicked it and nothing happened. I checked out what its command is. It's amdcccle, so I entered this in the terminal and I got this output:

```
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    145 (Uknown extension)
  Minor opcode: 33 (Unknown request)
  Resource id:  0x76
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    145 (Uknown extension)
  Minor opcode: 48 (Unknown request)
  Resource id:  0x76
*** glibc detected *** amdcccle: munmap_chunk(): invalid pointer: 0xbffcfa8f ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7b5ef5b]
amdcccle[0x81c9c87]
amdcccle(AtiXUPcs_GetVal+0x68)[0x81c9ae8]
amdcccle[0x81c613b]
amdcccle(AtiXUDisp_InitContext+0x32)[0x81c5532]
amdcccle(AtiXUPriv_InitContext+0x51)[0x81c4861]
amdcccle(__AtiXUtil_Open+0xbb)[0x81c314b]
amdcccle(main+0x186)[0x8151446]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7b09ebc]
amdcccle[0x814e8d1]
======= Memory map: ========
08048000-08722000 r-xp 00000000 08:01 1689183    /usr/bin/amdcccle
08722000-087e2000 rwxp 006da000 08:01 1689183    /usr/bin/amdcccle
087e2000-0884a000 rwxp 087e2000 00:00 0          [heap]
b7915000-b791b000 r-xs 00000000 08:01 11878492   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b791b000-b791c000 r-xs 00000000 08:01 11880624   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b791c000-b791f000 r-xs 00000000 08:01 11880615   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b791f000-b7920000 r-xs 00000000 08:01 11880613   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b7920000-b7921000 r-xs 00000000 08:01 11880579   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b7921000-b7925000 r-xs 00000000 08:01 11878489   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7925000-b7926000 r-xs 00000000 08:01 11880576   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7926000-b7928000 r-xs 00000000 08:01 11880575   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b7928000-b792a000 r-xs 00000000 08:01 11880573   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b792a000-b792b000 r-xs 00000000 08:01 11880367   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b792b000-b792d000 r-xs 00000000 08:01 11880366   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b792d000-b7933000 r-xs 00000000 08:01 11880365   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b7933000-b7935000 r-xs 00000000 08:01 11880363   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7935000-b7937000 r-xs 00000000 08:01 11880362   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b7937000-b793f000 r-xs 00000000 08:01 11880358   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b793f000-b7945000 r-xs 00000000 08:01 11880287   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b7945000-b7946000 r-xs 00000000 08:01 11880286   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7946000-b7948000 r-xs 00000000 08:01 11880284   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7948000-b794e000 r-xs 00000000 08:01 11880261   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b794e000-b7951000 r-xs 00000000 08:01 11880258   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b7951000-b7955000 r-xs 00000000 08:01 11878474   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7955000-b7957000 r-xs 00000000 08:01 11880240   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7957000-b7958000 r-xs 00000000 08:01 11881103   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7958000-b7959000 r-xs 00000000 08:01 11881102   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7959000-b795a000 r-xs 00000000 08:01 11881101   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b795a000-b795b000 r-xs 00000000 08:01 11881100   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b795b000-b795c000 r-xs 00000000 08:01 11881099   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b795c000-b795f000 r-xs 00000000 08:01 11881098   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b795f000-b7964000 r-xs 00000000 08:01 11881097   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7964000-b7966000 r-xs 00000000 08:01 11881096   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7966000-b7967000 r-xs 00000000 08:01 11881095   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7967000-b7969000 r-xs 00000000 08:01 11881094   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7969000-b796a000 r-xs 00000000 08:01 11881093   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b796a000-b796f000 r-xs 00000000 08:01 11881091   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b796f000-b7973000 r-xs 00000000 08:01 11881080   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7973000-b7975000 r-xs 00000000 08:01 11881077   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7975000-b7978000 r-xs 00000000 08:01 11881027   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7978000-b7979000 r-xs 00000000 08:01 11881010   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7979000-b797b000 r-xs 00000000 08:01 11881007   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b797b000-b797f000 r-xs 00000000 08:01 11880960   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b797f000-b7985000 r-xs 00000000 08:01 11880959   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7985000-b7986000 r-xs 00000000 08:01 11880958   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7986000-b798e000 r-xs 00000000 08:01 11880957   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b798e000-b7990000 r-xs 00000000 08:01 11880884   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b7990000-b7993000 r-xs 00000000 08:01 11880707   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b7993000-b7995000 r-xs 00000000 08:01 11878504   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7995000-b7997000 r-xs 00000000 08:01 11880440   /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7997000-b79d2000 r-xp 00000000 08:01 1754109    /usr/lib/locale/en_US.utf8/LC_CTYPE
b79d2000-b79d3000 r-xp 00000000 08:01 1754114    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b79d3000-b79d4000 r-xp 00000000 08:01 1754117    /usr/lib/locale/en_US.utf8/LC_TIME
b79d4000-b7aab000 r-xp 00000000 08:01 1754108    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7aab000-b7aac000 r-xp 00000000 08:01 1754112    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7aac000-b7aad000 r-xp 00000000 08Aborted (core dumped)

```

What is going on???


I've gotten these drivers working on this laptop with my previous install (on an old hard drive). I wanted to up the screen resolution to 1600x1200. It worked, so what's the matter now?

Thanks!

---

### Post by dinostabOMG on 2007-08-18
UPDATE:

I got my resolution back up to 1600x1200 by following the first method in this howto:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

However, now the output of fglrxinfo is 
```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

```

This is confirmed by System->Proprietary Drivers. I am somehow not using the ATI drivers, but still getting my 1600x1200 resolution. Which means that Catalyst still won't open, but at least now I get the error message that tells me it is because the ATI drivers aren't in use. 

Well... I'm happy enough as my goal was to be running at this resolution. Hope some of this helps someone eventually.

---

