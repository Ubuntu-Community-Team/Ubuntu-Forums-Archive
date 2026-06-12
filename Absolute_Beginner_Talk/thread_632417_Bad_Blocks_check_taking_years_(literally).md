---
title: "Bad Blocks check taking years (literally)"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by osmdian on 2007-12-05
Hey Guys,

i tried to boot my Ubuntu and it would not start. It told me that it had to do a fsck. It stopped at 62.0% and than gave a lot of errors. It told me to do a fsck manually which i did. I typed fsck and let it run. It gave me a lot of errors along the lines "blabla is damaged do you want to rewrite info<yes>
After a while it did not continue but somehow went on to a blue screen which told me x server could not be started.
The boot before i had downloaded kubuntu onto my gutsy gibbon ubuntu, maybe that caused all the trouble.
I am now logged in using the life cd. I ran fsck from here which again got me nowhere.
Then i run two badblock checks, this one:
```

sudo e2fsck -c /dev/sda1 
```

And the one bellow. They both stopped at certain values, first at 21million of 23m and the one bellow at 84m of 95m. They did not literally stop, but i just aborted, because the process had slowed down so much, that it would probably take years.

My question is now: Whats my problem here? Xorg is probably damaged to. Is there a way to bring back my current instalation of ubuntu: If i just format my disk and reinstall ubuntu or kubuntu, will this problem go away or is my harddisk physically damaged?
Should i look for a new harddisk?

Sorry for the lenghty text and thanks in advance for any help.

Dave 

```
ubuntu@ubuntu:~$ sudo badblocks -v /dev/sda1
Checking blocks 0 to 95048540
Checking for bad blocks (read-only test): m^[[C^[[C       28884608/       950485^[[D^[[D^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B       29165696/       9580762888076288/       95048540
580763048076304/       95048540
580763058076305/       95048540
580763068076306/       95048540
580763078076307/       95048540
58076308
58076309
58076310
58076311
58076312
58076313
58076314
58076315
58076316
58076317
58076318
58076319
58076320
58076321
58076322
58076323
58076324
58076325
58076326
58076327
58076328
58076329
58076330
58076331
58076332
58076333
58076334
58076335
58076336
58076337
58076338
58076339
58076340
58076341
58076342
58076343
58076344
58076345
58076346
58076347
58076348
58076349
58076350
58076351
58076352
58076353
58076354
58076355
58076356
58076357
58076358
58076359
58076360
58076361
58076362
58076363
58076364
58076365
58076366
58076367
58076368
58076369
58076370
58076371
58076372
58076373
58076374
58076375
58076376
58076377
58076378
58076379
58076380
58076381
58076382
58076383
58076384
58076385
58076386
58076387
58076388
58076389
58076390
58076391
58076392
58076393
58076394
58076395
58076396
58076397
58076398
58076399
58076400
58076401
58076402
58076403
58076404
58076405
58076406
58076407
58076408
58076409
58076410
58076411
58076412
58076413
58076414
58076415
58076416
58076417
58076418
58076419
584611768461176/       95048540
584611808461180/       95048540
584611818461181/       95048540
584611828461182/       95048540
584611838461183/       95048540
834982883498288/       95048540
834983363498336/       95048540
834983373498337/       95048540
##
ä#834983383498338/       95048540
ääää##


+
834983393498339/       95048540
834985843498584/       95048540
834986003498600/       95048540
834986013498601/       95048540
834986023498602/       95048540
834986033498603/       95048540
834993603499360/       95048540
834993883499388/       95048540
834993893499389/       95048540
834993903499390/       95048540
834993913499391/       95048540
835023843502384/       95048540
bb835023883502388/       95048540
835023893502389/       95048540
835023903502390/       95048540
835023913502391/       95048540
841598484159848/       95048540
   841598804159880/       95048540
841598814159881/       95048540
841598824159882/       95048540
841598834159883/       95048540
841601284160128/       95048540
841601404160140/       95048540
841601414160141/       95048540
841601424160142/       95048540
841601434160143/       95048540
841603844160384/       95048540
841604044160404/       95048540
841604054160405/       95048540
841604064160406/       95048540
841604074160407/       95048540
841606484160648/       95048540
841606684160668/       95048540
841606694160669/       95048540
841606704160670/       95048540
841606714160671/       95048540
841611684161168/       95048540

```

---

### Post by irish_flu on 2007-12-05
If you don't stand to lose valuable data, then by all means reformat (making sure to repartition) and start again.  If it dies on you, then you can go look for a new hard disk.

No use blowing cash just because of a bad disk partition (though it does sorta look like your hard drive may be on its way out).

---

### Post by pjkoczan on 2007-12-05
I've seen this happen before. It's not necessarily a bad disk. What you might want to do before reinstalling/reformatting is add the -y option to your fsck command. This will cause fsck to automatically answer "yes" to the "do you want to repair the bad block?" questions. That worked for me the last time I saw it.

If this happens again, then you should be suspicious of disk failure. Until then, I wouldn't worry too much, though you should make a backup of important data on another disk.

---

