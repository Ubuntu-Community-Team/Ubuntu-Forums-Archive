---
title: "Help Burning DVDs"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-03-01
Hey

Im having trouble burning dvds with my laptop. Its a gateway with a dual layer dvd burner/re-writer. I have had no problems burning cds with K3B, but when it comes to burning a dvd... it will make it to about 23% and then i get I/O errors and it fails. Please Someone Help me... i want to back up most of my media files and other important files as ill be upgrading my hard drive and will thus loose everything :(

thanks
~Lance

---

### Post by frodon on 2006-03-01
Could you post the k3b log ("show debug information" button) ?

So i will see what kind of error it is.

---

### Post by noob_Lance on 2006-03-01
```

System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
QSI DVD+-RW SDW-082 LX44 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R16; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/home/lance/Desktop/music.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 8.2x1385KBps.
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
         0/2380275712 ( 0.0%) @0x, remaining ??:??
    655360/2380275712 ( 0.0%) @0.1x, remaining 1754:59
   5177344/2380275712 ( 0.2%) @1.0x, remaining 252:18
   6356992/2380275712 ( 0.3%) @0.2x, remaining 224:03
   8617984/2380275712 ( 0.4%) @0.5x, remaining 178:52
  10584064/2380275712 ( 0.4%) @0.4x, remaining 160:27
  13041664/2380275712 ( 0.5%) @0.5x, remaining 139:09
  15499264/2380275712 ( 0.7%) @0.5x, remaining 124:36
  18776064/2380275712 ( 0.8%) @0.7x, remaining 111:05
  21004288/2380275712 ( 0.9%) @0.5x, remaining 104:50
  23887872/2380275712 ( 1.0%) @0.6x, remaining 96:59
  25427968/2380275712 ( 1.1%) @0.3x, remaining 97:14
  27852800/2380275712 ( 1.2%) @0.5x, remaining 92:54
  31621120/2380275712 ( 1.3%) @0.8x, remaining 85:24
  33292288/2380275712 ( 1.4%) @0.4x, remaining 85:46
  36077568/2380275712 ( 1.5%) @0.6x, remaining 82:18
  39190528/2380275712 ( 1.6%) @0.7x, remaining 79:38
  41844736/2380275712 ( 1.8%) @0.6x, remaining 77:18
  45481984/2380275712 ( 1.9%) @0.8x, remaining 73:34
  46170112/2380275712 ( 1.9%) @0.1x, remaining 75:49
  48529408/2380275712 ( 2.0%) @0.5x, remaining 74:28
  51183616/2380275712 ( 2.2%) @0.6x, remaining 72:48
  53248000/2380275712 ( 2.2%) @0.4x, remaining 72:50
  55705600/2380275712 ( 2.3%) @0.5x, remaining 71:38
  58556416/2380275712 ( 2.5%) @0.6x, remaining 70:02
  61014016/2380275712 ( 2.6%) @0.5x, remaining 69:41
  63864832/2380275712 ( 2.7%) @0.6x, remaining 68:18
  66879488/2380275712 ( 2.8%) @0.6x, remaining 66:52
  70254592/2380275712 ( 3.0%) @0.7x, remaining 65:45
  72613888/2380275712 ( 3.1%) @0.5x, remaining 65:08
  75071488/2380275712 ( 3.2%) @0.5x, remaining 64:29
  77561856/2380275712 ( 3.3%) @0.5x, remaining 64:19
  80576512/2380275712 ( 3.4%) @0.6x, remaining 63:15
  85164032/2380275712 ( 3.6%) @1.0x, remaining 61:05
  87490560/2380275712 ( 3.7%) @0.5x, remaining 61:08
  90701824/2380275712 ( 3.8%) @0.7x, remaining 60:09
  94732288/2380275712 ( 4.0%) @0.9x, remaining 58:42
  97189888/2380275712 ( 4.1%) @0.5x, remaining 58:43
 101416960/2380275712 ( 4.3%) @0.9x, remaining 57:17
 103088128/2380275712 ( 4.3%) @0.4x, remaining 57:25
 105742336/2380275712 ( 4.4%) @0.6x, remaining 57:21
 108199936/2380275712 ( 4.5%) @0.5x, remaining 57:02
 109772800/2380275712 ( 4.6%) @0.3x, remaining 57:13
 111443968/2380275712 ( 4.7%) @0.4x, remaining 57:40
 113115136/2380275712 ( 4.8%) @0.4x, remaining 57:47
 114982912/2380275712 ( 4.8%) @0.4x, remaining 57:47
 117145600/2380275712 ( 4.9%) @0.5x, remaining 57:57
 119603200/2380275712 ( 5.0%) @0.5x, remaining 57:38
 122486784/2380275712 ( 5.1%) @0.6x, remaining 57:08
 123240448/2380275712 ( 5.2%) @0.2x, remaining 57:59
 127467520/2380275712 ( 5.4%) @0.9x, remaining 56:51
 129204224/2380275712 ( 5.4%) @0.4x, remaining 56:54
 131006464/2380275712 ( 5.5%) @0.4x, remaining 57:13
 134840320/2380275712 ( 5.7%) @0.8x, remaining 56:20
 136347648/2380275712 ( 5.7%) @0.3x, remaining 56:30
 139264000/2380275712 ( 5.9%) @0.6x, remaining 56:19
 142409728/2380275712 ( 6.0%) @0.7x, remaining 55:47
 145260544/2380275712 ( 6.1%) @0.6x, remaining 55:23
 147718144/2380275712 ( 6.2%) @0.5x, remaining 55:24
 151748608/2380275712 ( 6.4%) @0.9x, remaining 54:34
 153714688/2380275712 ( 6.5%) @0.4x, remaining 54:33
 157024256/2380275712 ( 6.6%) @0.7x, remaining 54:16
 158728192/2380275712 ( 6.7%) @0.4x, remaining 54:21
 161120256/2380275712 ( 6.8%) @0.5x, remaining 54:24
 165216256/2380275712 ( 6.9%) @0.9x, remaining 53:37
 167182336/2380275712 ( 7.0%) @0.4x, remaining 53:36
 169738240/2380275712 ( 7.1%) @0.5x, remaining 53:36
 171704320/2380275712 ( 7.2%) @0.4x, remaining 53:35
 176226304/2380275712 ( 7.4%) @1.0x, remaining 52:44
 178290688/2380275712 ( 7.5%) @0.4x, remaining 52:54
 182353920/2380275712 ( 7.7%) @0.9x, remaining 52:13
 184385536/2380275712 ( 7.7%) @0.4x, remaining 52:12
 187826176/2380275712 ( 7.9%) @0.7x, remaining 51:56
 190185472/2380275712 ( 8.0%) @0.5x, remaining 51:49
 192741376/2380275712 ( 8.1%) @0.5x, remaining 51:38
 196280320/2380275712 ( 8.2%) @0.7x, remaining 51:22
 200704000/2380275712 ( 8.4%) @0.9x, remaining 50:40
 203751424/2380275712 ( 8.6%) @0.6x, remaining 50:23
 206897152/2380275712 ( 8.7%) @0.7x, remaining 50:14
 209485824/2380275712 ( 8.8%) @0.5x, remaining 50:05
 211714048/2380275712 ( 8.9%) @0.5x, remaining 50:01
 215941120/2380275712 ( 9.1%) @0.9x, remaining 49:36
 218103808/2380275712 ( 9.2%) @0.5x, remaining 49:34
 221937664/2380275712 ( 9.3%) @0.8x, remaining 49:06
 225443840/2380275712 ( 9.5%) @0.7x, remaining 48:54
 229441536/2380275712 ( 9.6%) @0.8x, remaining 48:26
 233504768/2380275712 ( 9.8%) @0.9x, remaining 47:57
 236421120/2380275712 ( 9.9%) @0.6x, remaining 47:54
 240418816/2380275712 (10.1%) @0.8x, remaining 47:28
 243630080/2380275712 (10.2%) @0.7x, remaining 47:12
 247201792/2380275712 (10.4%) @0.8x, remaining 47:01
 251330560/2380275712 (10.6%) @0.9x, remaining 46:35
 254672896/2380275712 (10.7%) @0.7x, remaining 46:19
 259096576/2380275712 (10.9%) @0.9x, remaining 45:58
 261095424/2380275712 (11.0%) @0.4x, remaining 45:59
 262832128/2380275712 (11.0%) @0.4x, remaining 46:03
 265191424/2380275712 (11.1%) @0.5x, remaining 46:07
 268566528/2380275712 (11.3%) @0.7x, remaining 45:52
 271974400/2380275712 (11.4%) @0.7x, remaining 45:36
 274038784/2380275712 (11.5%) @0.4x, remaining 45:43
 276889600/2380275712 (11.6%) @0.6x, remaining 45:34
 280068096/2380275712 (11.8%) @0.7x, remaining 45:22
 283672576/2380275712 (11.9%) @0.8x, remaining 45:12
 286031872/2380275712 (12.0%) @0.5x, remaining 45:09
 289472512/2380275712 (12.2%) @0.7x, remaining 44:54
 292421632/2380275712 (12.3%) @0.6x, remaining 44:51
 294191104/2380275712 (12.4%) @0.4x, remaining 44:54
 297631744/2380275712 (12.5%) @0.7x, remaining 44:39
 299892736/2380275712 (12.6%) @0.5x, remaining 44:44
 302645248/2380275712 (12.7%) @0.6x, remaining 44:37
 306380800/2380275712 (12.9%) @0.8x, remaining 44:20
 308445184/2380275712 (13.0%) @0.4x, remaining 44:26
 310804480/2380275712 (13.1%) @0.5x, remaining 44:23
 314638336/2380275712 (13.2%) @0.8x, remaining 44:05
 317390848/2380275712 (13.3%) @0.6x, remaining 44:05
 320110592/2380275712 (13.4%) @0.6x, remaining 43:58
 320143360/2380275712 (13.4%) @0.0x, remaining 44:17
 324861952/2380275712 (13.6%) @1.0x, remaining 43:58
 327221248/2380275712 (13.7%) @0.5x, remaining 43:55
 330465280/2380275712 (13.9%) @0.7x, remaining 43:43
 332627968/2380275712 (14.0%) @0.5x, remaining 43:48
 334594048/2380275712 (14.1%) @0.4x, remaining 43:48
 338755584/2380275712 (14.2%) @0.9x, remaining 43:29
 341180416/2380275712 (14.3%) @0.5x, remaining 43:31
 344326144/2380275712 (14.5%) @0.7x, remaining 43:21
 346685440/2380275712 (14.6%) @0.5x, remaining 43:18
 348848128/2380275712 (14.7%) @0.5x, remaining 43:22
 353173504/2380275712 (14.8%) @0.9x, remaining 43:02
 354353152/2380275712 (14.9%) @0.2x, remaining 43:09
 355565568/2380275712 (14.9%) @0.3x, remaining 43:22
 358875136/2380275712 (15.1%) @0.7x, remaining 43:10
 361332736/2380275712 (15.2%) @0.5x, remaining 43:07
 365264896/2380275712 (15.3%) @0.8x, remaining 42:56
 367165440/2380275712 (15.4%) @0.4x, remaining 42:56
 368705536/2380275712 (15.5%) @0.3x, remaining 43:00
 370573312/2380275712 (15.6%) @0.4x, remaining 43:06
 373227520/2380275712 (15.7%) @0.6x, remaining 43:01
 375128064/2380275712 (15.8%) @0.4x, remaining 43:01
 376668160/2380275712 (15.8%) @0.3x, remaining 43:10
 379092992/2380275712 (15.9%) @0.5x, remaining 43:06
 380895232/2380275712 (16.0%) @0.4x, remaining 43:07
 382271488/2380275712 (16.1%) @0.3x, remaining 43:17
 384729088/2380275712 (16.2%) @0.5x, remaining 43:13
 385810432/2380275712 (16.2%) @0.2x, remaining 43:20
 387579904/2380275712 (16.3%) @0.4x, remaining 43:26
 389054464/2380275712 (16.3%) @0.3x, remaining 43:30
 390922240/2380275712 (16.4%) @0.4x, remaining 43:30
 391774208/2380275712 (16.5%) @0.2x, remaining 43:44
 396230656/2380275712 (16.6%) @0.9x, remaining 43:23
 400097280/2380275712 (16.8%) @0.8x, remaining 43:13
 402915328/2380275712 (16.9%) @0.6x, remaining 43:06
 405045248/2380275712 (17.0%) @0.4x, remaining 43:04
 408027136/2380275712 (17.1%) @0.6x, remaining 43:01
 411271168/2380275712 (17.3%) @0.7x, remaining 42:50
 414613504/2380275712 (17.4%) @0.7x, remaining 42:40
 416153600/2380275712 (17.5%) @0.3x, remaining 42:47
 417366016/2380275712 (17.5%) @0.3x, remaining 42:52
 421724160/2380275712 (17.7%) @0.9x, remaining 42:34
 422969344/2380275712 (17.8%) @0.3x, remaining 42:43
 425099264/2380275712 (17.9%) @0.4x, remaining 42:41
 426508288/2380275712 (17.9%) @0.3x, remaining 42:45
 428965888/2380275712 (18.0%) @0.5x, remaining 42:45
 430145536/2380275712 (18.1%) @0.2x, remaining 42:50
 432308224/2380275712 (18.2%) @0.5x, remaining 42:48
 432996352/2380275712 (18.2%) @0.1x, remaining 43:01
 434962432/2380275712 (18.3%) @0.4x, remaining 43:00
 437321728/2380275712 (18.4%) @0.5x, remaining 42:56
 437911552/2380275712 (18.4%) @0.1x, remaining 43:10
 441647104/2380275712 (18.6%) @0.8x, remaining 42:56
 445120512/2380275712 (18.7%) @0.7x, remaining 42:45
 447545344/2380275712 (18.8%) @0.5x, remaining 42:45
 451018752/2380275712 (18.9%) @0.7x, remaining 42:33
 453148672/2380275712 (19.0%) @0.5x, remaining 42:31
 456785920/2380275712 (19.2%) @0.8x, remaining 42:23
 458948608/2380275712 (19.3%) @0.5x, remaining 42:21
 461963264/2380275712 (19.4%) @0.6x, remaining 42:13
 464453632/2380275712 (19.5%) @0.5x, remaining 42:12
 467337216/2380275712 (19.6%) @0.6x, remaining 42:05
 471433216/2380275712 (19.8%) @0.9x, remaining 41:50
 473104384/2380275712 (19.9%) @0.4x, remaining 41:55
 476119040/2380275712 (20.0%) @0.6x, remaining 41:47
 478019584/2380275712 (20.1%) @0.4x, remaining 41:47
 480083968/2380275712 (20.2%) @0.4x, remaining 41:49
 482344960/2380275712 (20.3%) @0.5x, remaining 41:46
 486866944/2380275712 (20.5%) @1.0x, remaining 41:28
 490602496/2380275712 (20.6%) @0.8x, remaining 41:20
 493256704/2380275712 (20.7%) @0.6x, remaining 41:15
 497582080/2380275712 (20.9%) @0.9x, remaining 40:59
 500006912/2380275712 (21.0%) @0.5x, remaining 40:59
 503283712/2380275712 (21.1%) @0.7x, remaining 40:50
 505937920/2380275712 (21.3%) @0.6x, remaining 40:45
 508461056/2380275712 (21.4%) @0.5x, remaining 40:44
 512425984/2380275712 (21.5%) @0.8x, remaining 40:31
 515571712/2380275712 (21.7%) @0.7x, remaining 40:23
 518422528/2380275712 (21.8%) @0.6x, remaining 40:20
 521961472/2380275712 (21.9%) @0.7x, remaining 40:10
 526123008/2380275712 (22.1%) @0.9x, remaining 39:56
 528744448/2380275712 (22.2%) @0.6x, remaining 39:55
 531398656/2380275712 (22.3%) @0.6x, remaining 39:50
 532905984/2380275712 (22.4%) @0.3x, remaining 39:55
 536051712/2380275712 (22.5%) @0.7x, remaining 39:47
 538509312/2380275712 (22.6%) @0.5x, remaining 39:43
 542605312/2380275712 (22.8%) @0.9x, remaining 39:34
 545947648/2380275712 (22.9%) @0.7x, remaining 39:25
 548306944/2380275712 (23.0%) @0.5x, remaining 39:22
 552239104/2380275712 (23.2%) @0.8x, remaining 39:13
 554303488/2380275712 (23.3%) @0.4x, remaining 39:12
 558792704/2380275712 (23.5%) @0.9x, remaining 38:57
 561676288/2380275712 (23.6%) @0.6x, remaining 38:54
 565510144/2380275712 (23.8%) @0.8x, remaining 38:43
 567902208/2380275712 (23.9%) @0.5x, remaining 38:40
 572293120/2380275712 (24.0%) @0.9x, remaining 38:29
 574750720/2380275712 (24.1%) @0.5x, remaining 38:25
 576913408/2380275712 (24.2%) @0.5x, remaining 38:23
 579960832/2380275712 (24.4%) @0.6x, remaining 38:20
 580714496/2380275712 (24.4%) @0.2x, remaining 38:25
 585072640/2380275712 (24.6%) @0.9x, remaining 38:12
 588185600/2380275712 (24.7%) @0.7x, remaining 38:08
 589463552/2380275712 (24.8%) @0.3x, remaining 38:10
 594411520/2380275712 (25.0%) @1.0x, remaining 37:54
 596574208/2380275712 (25.1%) @0.5x, remaining 37:55
 598540288/2380275712 (25.1%) @0.4x, remaining 37:54
 600211456/2380275712 (25.2%) @0.4x, remaining 37:54
 601686016/2380275712 (25.3%) @0.3x, remaining 37:59
 604602368/2380275712 (25.4%) @0.6x, remaining 37:53
 606502912/2380275712 (25.5%) @0.4x, remaining 37:52
 609550336/2380275712 (25.6%) @0.6x, remaining 37:48
 611713024/2380275712 (25.7%) @0.5x, remaining 37:46
 613777408/2380275712 (25.8%) @0.4x, remaining 37:45
 616038400/2380275712 (25.9%) @0.5x, remaining 37:45
 618201088/2380275712 (26.0%) @0.5x, remaining 37:43
 619872256/2380275712 (26.0%) @0.4x, remaining 37:43
 622231552/2380275712 (26.1%) @0.5x, remaining 37:43
 624001024/2380275712 (26.2%) @0.4x, remaining 37:42
 626360320/2380275712 (26.3%) @0.5x, remaining 37:39
 628129792/2380275712 (26.4%) @0.4x, remaining 37:42
 630816768/2380275712 (26.5%) @0.6x, remaining 37:37
 633438208/2380275712 (26.6%) @0.6x, remaining 37:33
 633503744/2380275712 (26.6%) @0.0x, remaining 37:43
 635404288/2380275712 (26.7%) @0.4x, remaining 37:42
 637566976/2380275712 (26.8%) @0.5x, remaining 37:40
 639336448/2380275712 (26.9%) @0.4x, remaining 37:42
 641204224/2380275712 (26.9%) @0.4x, remaining 37:41
 641204224/2380275712 (26.9%) @0.0x, remaining 37:50
 643661824/2380275712 (27.0%) @0.5x, remaining 37:49
 645038080/2380275712 (27.1%) @0.3x, remaining 37:50
 647299072/2380275712 (27.2%) @0.5x, remaining 37:47
 649068544/2380275712 (27.3%) @0.4x, remaining 37:49
 650444800/2380275712 (27.3%) @0.3x, remaining 37:51
 651657216/2380275712 (27.4%) @0.3x, remaining 37:53
 652705792/2380275712 (27.4%) @0.2x, remaining 37:58
 653885440/2380275712 (27.5%) @0.2x, remaining 38:01
 655065088/2380275712 (27.5%) @0.2x, remaining 38:03
 656146432/2380275712 (27.6%) @0.2x, remaining 38:08
 656244736/2380275712 (27.6%) @0.0x, remaining 38:16
 659095552/2380275712 (27.7%) @0.6x, remaining 38:10
 660570112/2380275712 (27.8%) @0.3x, remaining 38:13
 660570112/2380275712 (27.8%) @0.0x, remaining 38:21
 661848064/2380275712 (27.8%) @0.3x, remaining 38:23
 663322624/2380275712 (27.9%) @0.3x, remaining 38:26
 665387008/2380275712 (28.0%) @0.4x, remaining 38:24
 666435584/2380275712 (28.0%) @0.2x, remaining 38:29
 668598272/2380275712 (28.1%) @0.5x, remaining 38:26
 671186944/2380275712 (28.2%) @0.5x, remaining 38:21
 673153024/2380275712 (28.3%) @0.4x, remaining 38:22
 674627584/2380275712 (28.3%) @0.3x, remaining 38:23
 677183488/2380275712 (28.4%) @0.5x, remaining 38:18
 678723584/2380275712 (28.5%) @0.3x, remaining 38:21
 680656896/2380275712 (28.6%) @0.4x, remaining 38:19
 683409408/2380275712 (28.7%) @0.6x, remaining 38:14
 685342720/2380275712 (28.8%) @0.4x, remaining 38:15
 686030848/2380275712 (28.8%) @0.1x, remaining 38:19
 688193536/2380275712 (28.9%) @0.5x, remaining 38:16
 690454528/2380275712 (29.0%) @0.5x, remaining 38:15
 692027392/2380275712 (29.1%) @0.3x, remaining 38:15
 694091776/2380275712 (29.2%) @0.4x, remaining 38:13
 696647680/2380275712 (29.3%) @0.5x, remaining 38:11
 698908672/2380275712 (29.4%) @0.5x, remaining 38:07
 700186624/2380275712 (29.4%) @0.3x, remaining 38:09
 701956096/2380275712 (29.5%) @0.4x, remaining 38:10
 703528960/2380275712 (29.6%) @0.3x, remaining 38:10
 705200128/2380275712 (29.6%) @0.4x, remaining 38:09
 705200128/2380275712 (29.6%) @0.0x, remaining 38:19
 707854336/2380275712 (29.7%) @0.6x, remaining 38:14
 709918720/2380275712 (29.8%) @0.4x, remaining 38:11
 710574080/2380275712 (29.9%) @0.1x, remaining 38:18
 711852032/2380275712 (29.9%) @0.3x, remaining 38:19
 714801152/2380275712 (30.0%) @0.6x, remaining 38:12
 717324288/2380275712 (30.1%) @0.5x, remaining 38:10
 719224832/2380275712 (30.2%) @0.4x, remaining 38:08
 721879040/2380275712 (30.3%) @0.6x, remaining 38:03
 723779584/2380275712 (30.4%) @0.4x, remaining 38:04
 725286912/2380275712 (30.5%) @0.3x, remaining 38:04
 728006656/2380275712 (30.6%) @0.6x, remaining 37:58
 729972736/2380275712 (30.7%) @0.4x, remaining 37:58
 731348992/2380275712 (30.7%) @0.3x, remaining 37:59
 733413376/2380275712 (30.8%) @0.4x, remaining 37:56
 734494720/2380275712 (30.9%) @0.2x, remaining 38:01
 736362496/2380275712 (30.9%) @0.4x, remaining 37:59
 738426880/2380275712 (31.0%) @0.4x, remaining 37:56
 741081088/2380275712 (31.1%) @0.6x, remaining 37:53
 743538688/2380275712 (31.2%) @0.5x, remaining 37:49
 743538688/2380275712 (31.2%) @0.0x, remaining 37:56
 745406464/2380275712 (31.3%) @0.4x, remaining 37:56
 747569152/2380275712 (31.4%) @0.5x, remaining 37:53
 750026752/2380275712 (31.5%) @0.5x, remaining 37:49
 751796224/2380275712 (31.6%) @0.4x, remaining 37:50
:-[ WRITE@LBA=599f0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/home/lance/Desktop/music.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=8 


```

---

### Post by frodon on 2006-03-01
It's quiet strange, because the error message is not really explicit.
Maybe your iso file is corrupted, you could try to mount it in order to see possible error messages.
Input/Output errors i got was generally due to UTF-8 names or joliet names longer than 64, i guess you didn't get any warning messages.

If you can't get more informations i advice you to change some option and run some simulation therefore you won't lose dvd for nothing.
You could try to force the input to iso-8*** in the advanced setting of the burning window for example.

Sorry no more ideas for the moment :(

---

### Post by taurus on 2006-03-01
You also may want to run DMA on your DVD drive because it will take forever to burn it at 0.7x!!!  Here is a link regarding DMA...

[https://wiki.ubuntu.com/DMA?highlight=%28DMA%29](https://wiki.ubuntu.com/DMA?highlight=%28DMA%29)

---

### Post by DiscoKiller on 2006-03-01
try setting the burn speed to 4x when burning iso's. not sure i know what i`m talking about but i have had problems in the past where my write speed has been to high, didnt get any error messages like that though, oh well every little helps


DK

---

### Post by taurus on 2006-03-01
[QUOTE=DiscoKiller]try setting the burn speed to 4x when burning iso's. not sure i know what i`m talking about but i have had problems in the past where my write speed has been to high, didnt get any error messages like that though, oh well every little helps

DK[/QUOTE]
Actually, his write speed is under 1x (from the log)!!!  ;)

---

### Post by chaumurky on 2006-03-01
Have you tried burning a DVD with another program?

---

### Post by DiscoKiller on 2006-03-01
[QUOTE=taurus]Actually, his write speed is under 1x (from the log)!!!  ;)[/QUOTE]

yah i noticed, however if i set my speed ti high it chucks out an error regardless of actual writing speed.

---

### Post by noob_Lance on 2006-03-01
burn using what other program.. i only know of K3B

---

### Post by RaiSuli on 2006-03-01
You could try Gnomebaker, it's in the repositories.

But first check, if DMA is activated for your dvd-drive. In the terminal enter

sudo hdparm /dev/hdd  <-- change hdd to the location of your dvd-burner.

---

### Post by noob_Lance on 2006-03-01
/dev/dvdrw:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument



nope.. guess not

---

### Post by RaiSuli on 2006-03-01
ok, try:

sudo hdparm -d1 /dev/dvdrw

This should put dma on.

---

### Post by noob_Lance on 2006-03-01
it did and it worked... but the computer dosnt read it back after i burn it... it comes up as a blank disk still :(

---

