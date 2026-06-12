---
title: "Wine problem"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-07-06
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"CDAUDIO".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini

```
[mci]

MPEGVideo=mciqtz.drv

MPEGVideo2=mciqtz.drv

avivideo=mciavi.drv

cdaudio=mcicda.drv

sequencer=mciseq.drv

vcr=mcivisca.drv

; videodisc=mcipionr.drv

waveaudio=mciwave.drv



[drivers32]

MSACM.imaadpcm=imaadp32.acm

MSACM.msadpcm=msadp32.acm

MSACM.msg711=msg711.acm

MSACM.winemp3=winemp3.acm

VIDC.MRLE=msrle32.dll

VIDC.MSVC=msvidc32.dll

VIDC.CVID=iccvid.dll

; VIDC.IV50=ir50_32.dll

; VIDC.IV31=ir32_32.dll

; VIDC.IV32=ir32_32.dll
```

i do have that mci thingy so what else i'm doing wrong?

---

### Post by jethro10 on 2006-07-06
I really dont know your answer but before someone can help you will need to expand on this problem.

Is this while installing wine?

More likely, this is while trying to install a windows program? If this is so, check your program out here [http://appdb.winehq.org/](http://appdb.winehq.org/) . Its a compatability list of programs that will run in wine. Yours might not?

Jeff

---

### Post by ignorance on 2006-07-06
it's when i try to run a program in wine and according to you site link it's non-comptible but that doesn't mean it is not going to work under wine.

---

### Post by aeto on 2006-07-06
well..

1) It isn't listed there
2) It isn't listed there
3) It isn't listed there

So...it only means its not compatible. So its upto u to get it working. If it fails to adhere, then tough luck i guess. Can't complain.

---

