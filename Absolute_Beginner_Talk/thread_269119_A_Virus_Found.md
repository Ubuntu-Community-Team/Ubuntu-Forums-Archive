---
title: "A Virus Found"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Malta paul on 2006-10-01
I scaned my system with Aegis Virus Scanner and found that in the folder of codecs which I had down loaded using Easyubuntu. A virus W32/Madistr.a@MM which I think is a subtype worm, was reported in the VP31VFW.dll file.  Aegis was unable to deleat or qurantine this file. I did find the file in /user/lib/codecs/ and checked its properties, the owner was root and it was listed as a Dos/Windows Excutable. Any way I can delete the AP31VFW.dll file?  
Thanks Guys, Paul

---

### Post by wieman01 on 2006-10-01
> sudo rm /user/lib/codecs/AP31VFW.dll
From terminal window.

---

### Post by george_apan on 2006-10-01
sudo rm /usr/lib/codecs/VP31VFW.dll
from a terminal, will do.

EDIT: Not fast enough... :)

---

### Post by Perfect Storm on 2006-10-01
Proplerly a false detection. Just be careful when deleting files.

Better will be if you scan with another virus scanner to confirm/dis-confirm.

---

### Post by wieman01 on 2006-10-01
> **Artificial Intelligence said:**
> Proplerly a false detection. Just be careful when deleting files.

Better will be if you scan with another virus scanner to confirm/dis-confirm.
Good point. But I would really be interested how this virus got there in the first place. This is strange indeed.

---

### Post by Perfect Storm on 2006-10-01
I've seen alot of false detections by so called anti-virus applications. So I won't rely to heavly upon them.

Therefore it's better to scan also with other anti-virus scanners. I've wrote two howtos in the howto section.


If it's is a virus, it properly came though the installations of the codecs32 (root access).

---

### Post by Perfect Storm on 2006-10-01
[http://vil.nai.com/vil/content/v_99040.htm](http://vil.nai.com/vil/content/v_99040.htm)

It's an .exe worm for windows. So it's properly false detection.

---

### Post by Malta paul on 2006-10-01
Many thanks everyone, for your quick response. I am learning! sudo rm did the trick. I can confirm the 'virus' did come with the codecs32, because when I removed all the codecs the file had gone (including all the other files) once reinstalling it was back.   :)

---

### Post by Perfect Storm on 2006-10-01
Try install and run another anti-virus application.

---

### Post by wieman01 on 2006-10-01
> **Artificial Intelligence said:**
> I've seen alot of false detections by so called anti-virus applications. So I won't rely to heavly upon them.

Therefore it's better to scan also with other anti-virus scanners. I've wrote two howtos in the howto section.


If it's is a virus, it properly came though the installations of the codecs32 (root access).
Deleting a DLL is probably safe. There is no need to be too cautious I reckon. No DLL's are supposed to be in a Linux file system, or am I wrong?

---

### Post by Perfect Storm on 2006-10-01
If it's the w32codecs, then you'll need them to play various close source multi-media files.

List of codecs files in w32codec:
```
/usr/lib
/usr/lib/codecs
/usr/lib/codecs/AvidQTAVUICodec.qtx
/usr/lib/codecs/BeHereiVideo.qtx
/usr/lib/codecs/CLRVIDDC.DLL
/usr/lib/codecs/CtWbJpg.DLL
/usr/lib/codecs/DECVW_32.DLL
/usr/lib/codecs/LCMW2.dll
/usr/lib/codecs/LCODCCMW2E.dll
/usr/lib/codecs/LCodcCMP.dll
/usr/lib/codecs/QuickTime.qts
/usr/lib/codecs/QuickTimeEssentials.qtx
/usr/lib/codecs/QuickTimeInternetExtras.qtx
/usr/lib/codecs/VDODEC32.dll
/usr/lib/codecs/ViVD2.dll
/usr/lib/codecs/acelpdec.ax
/usr/lib/codecs/alf2cd.acm
/usr/lib/codecs/aslcodec_dshow.dll
/usr/lib/codecs/aslcodec_vfw.dll
/usr/lib/codecs/asusasv2.dll
/usr/lib/codecs/asusasvd.dll
/usr/lib/codecs/ativcr2.dll
/usr/lib/codecs/atrac3.acm
/usr/lib/codecs/atrc.so.6.0
/usr/lib/codecs/avimszh.dll
/usr/lib/codecs/avizlib.dll
/usr/lib/codecs/clrviddd.dll
/usr/lib/codecs/cook.so
/usr/lib/codecs/cook.so.6.0
/usr/lib/codecs/ctadp32.acm
/usr/lib/codecs/ddnt.so.6.0
/usr/lib/codecs/divx.dll
/usr/lib/codecs/divx_c32.ax
/usr/lib/codecs/divxa32.acm
/usr/lib/codecs/divxc32.dll
/usr/lib/codecs/divxdec.ax
/usr/lib/codecs/dnet.so.6.0
/usr/lib/codecs/drv2.so.6.0
/usr/lib/codecs/drv3.so.6.0
/usr/lib/codecs/drv4.so.6.0
/usr/lib/codecs/drvc.so
/usr/lib/codecs/dspr.so.6.0
/usr/lib/codecs/huffyuv.dll
/usr/lib/codecs/i263_32.drv
/usr/lib/codecs/iac25_32.ax
/usr/lib/codecs/iccvid.dll
/usr/lib/codecs/icmw_32.dll
/usr/lib/codecs/imaadp32.acm
/usr/lib/codecs/imc32.acm
/usr/lib/codecs/ir32_32.dll
/usr/lib/codecs/ir41_32.dll
/usr/lib/codecs/ir50_32.dll
/usr/lib/codecs/ivvideo.dll
/usr/lib/codecs/jp2avi.dll
/usr/lib/codecs/l3codeca.acm
/usr/lib/codecs/l3codecx.ax
/usr/lib/codecs/lhacm.acm
/usr/lib/codecs/lsvxdec.dll
/usr/lib/codecs/m3jp2k32.dll
/usr/lib/codecs/m3jpeg32.dll
/usr/lib/codecs/m3jpegdec.ax
/usr/lib/codecs/mcdvd_32.dll
/usr/lib/codecs/mcmjpg32.dll
/usr/lib/codecs/mi-sc4.acm
/usr/lib/codecs/mpg4c32.dll
/usr/lib/codecs/mpg4ds32.ax
/usr/lib/codecs/msadp32.acm
/usr/lib/codecs/msg711.acm
/usr/lib/codecs/msgsm32.acm
/usr/lib/codecs/msh261.drv
/usr/lib/codecs/msms001.vwp
/usr/lib/codecs/msnaudio.acm
/usr/lib/codecs/msrle32.dll
/usr/lib/codecs/msscds32.ax
/usr/lib/codecs/msvidc32.dll
/usr/lib/codecs/mvoiced.vwp
/usr/lib/codecs/nsrt2432.acm
/usr/lib/codecs/pclepim1.dll
/usr/lib/codecs/qdv.dll
/usr/lib/codecs/qpeg32.dll
/usr/lib/codecs/qtmlClient.dll
/usr/lib/codecs/rt32dcmp.dll
/usr/lib/codecs/scg726.acm
/usr/lib/codecs/sipr.so.6.0
/usr/lib/codecs/sp5x_32.dll
/usr/lib/codecs/tm20dec.ax
/usr/lib/codecs/tokf.so.6.0
/usr/lib/codecs/tokr.so.6.0
/usr/lib/codecs/tsccvid.dll
/usr/lib/codecs/tsd32.dll
/usr/lib/codecs/tssoft32.acm
/usr/lib/codecs/tvqdec.dll
/usr/lib/codecs/ubv263d+.ax
/usr/lib/codecs/ubvmp4d.dll
/usr/lib/codecs/ultimo.dll
/usr/lib/codecs/vdowave.drv
/usr/lib/codecs/vgpix32d.dll
/usr/lib/codecs/vid_3ivX.xa
/usr/lib/codecs/vid_cvid.xa
/usr/lib/codecs/vid_cyuv.xa
/usr/lib/codecs/vid_h261.xa
/usr/lib/codecs/vid_h263.xa
/usr/lib/codecs/vid_iv32.xa
/usr/lib/codecs/vid_iv41.xa
/usr/lib/codecs/vid_iv50.xa
/usr/lib/codecs/vivog723.acm
/usr/lib/codecs/vmnc.dll
/usr/lib/codecs/voxmsdec.ax
/usr/lib/codecs/vp31vfw.dll
/usr/lib/codecs/vp4vfw.dll
/usr/lib/codecs/vp5vfw.dll
/usr/lib/codecs/vp6vfw.dll
/usr/lib/codecs/vp7vfw.dll
/usr/lib/codecs/vssh264.dll
/usr/lib/codecs/vssh264core.dll
/usr/lib/codecs/vssh264dec.dll
/usr/lib/codecs/vsshdsd.dll
/usr/lib/codecs/vsslight.dll
/usr/lib/codecs/vsswlt.dll
/usr/lib/codecs/wma9dmod.dll
/usr/lib/codecs/wmadmod.dll
/usr/lib/codecs/wmsdmod.dll
/usr/lib/codecs/wmspdmod.dll
/usr/lib/codecs/wmv8ds32.ax
/usr/lib/codecs/wmv9dmod.dll
/usr/lib/codecs/wmvadvd.dll
/usr/lib/codecs/wmvdmod.dll
/usr/lib/codecs/wmvds32.ax
/usr/lib/codecs/wnvplay1.dll
/usr/lib/codecs/wnvwinx.dll
/usr/lib/codecs/wvc1dmod.dll
/usr/lib/codecs/zmbv.dll
/usr/lib/win32
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/doc
/usr/share/doc/w32codecs
/usr/share/doc/w32codecs/contents.htm
/usr/share/doc/w32codecs/formats.htm
/usr/share/doc/w32codecs/contents.txt
/usr/share/doc/w32codecs/formats.txt
/usr/share/doc/w32codecs/copyright
/usr/share/doc/w32codecs/changelog.Debian.gz
/usr/lib/win32/zmbv.dll
/usr/lib/win32/wvc1dmod.dll
/usr/lib/win32/wnvwinx.dll
/usr/lib/win32/wnvplay1.dll
/usr/lib/win32/wmvds32.ax
/usr/lib/win32/wmvdmod.dll
/usr/lib/win32/wmvadvd.dll
/usr/lib/win32/wmv9dmod.dll
/usr/lib/win32/wmv8ds32.ax
/usr/lib/win32/wmspdmod.dll
/usr/lib/win32/wmsdmod.dll
/usr/lib/win32/wmadmod.dll
/usr/lib/win32/wma9dmod.dll
/usr/lib/win32/vsswlt.dll
/usr/lib/win32/vsslight.dll
/usr/lib/win32/vsshdsd.dll
/usr/lib/win32/vssh264dec.dll
/usr/lib/win32/vssh264core.dll
/usr/lib/win32/vssh264.dll
/usr/lib/win32/vp7vfw.dll
/usr/lib/win32/vp6vfw.dll
/usr/lib/win32/vp5vfw.dll
/usr/lib/win32/vp4vfw.dll
/usr/lib/win32/vp31vfw.dll
/usr/lib/win32/voxmsdec.ax
/usr/lib/win32/vmnc.dll
/usr/lib/win32/vivog723.acm
/usr/lib/win32/vid_iv50.xa
/usr/lib/win32/vid_iv41.xa
/usr/lib/win32/vid_iv32.xa
/usr/lib/win32/vid_h263.xa
/usr/lib/win32/vid_h261.xa
/usr/lib/win32/vid_cyuv.xa
/usr/lib/win32/vid_cvid.xa
/usr/lib/win32/vid_3ivX.xa
/usr/lib/win32/vgpix32d.dll
/usr/lib/win32/vdowave.drv
/usr/lib/win32/ultimo.dll
/usr/lib/win32/ubvmp4d.dll
/usr/lib/win32/ubv263d+.ax
/usr/lib/win32/tvqdec.dll
/usr/lib/win32/tssoft32.acm
/usr/lib/win32/tsd32.dll
/usr/lib/win32/tsccvid.dll
/usr/lib/win32/tokr.so.6.0
/usr/lib/win32/tokf.so.6.0
/usr/lib/win32/tm20dec.ax
/usr/lib/win32/sp5x_32.dll
/usr/lib/win32/sipr.so.6.0
/usr/lib/win32/scg726.acm
/usr/lib/win32/rt32dcmp.dll
/usr/lib/win32/qtmlClient.dll
/usr/lib/win32/qpeg32.dll
/usr/lib/win32/qdv.dll
/usr/lib/win32/pclepim1.dll
/usr/lib/win32/nsrt2432.acm
/usr/lib/win32/mvoiced.vwp
/usr/lib/win32/msvidc32.dll
/usr/lib/win32/msscds32.ax
/usr/lib/win32/msrle32.dll
/usr/lib/win32/msnaudio.acm
/usr/lib/win32/msms001.vwp
/usr/lib/win32/msh261.drv
/usr/lib/win32/msgsm32.acm
/usr/lib/win32/msg711.acm
/usr/lib/win32/msadp32.acm
/usr/lib/win32/mpg4ds32.ax
/usr/lib/win32/mpg4c32.dll
/usr/lib/win32/mi-sc4.acm
/usr/lib/win32/mcmjpg32.dll
/usr/lib/win32/mcdvd_32.dll
/usr/lib/win32/m3jpegdec.ax
/usr/lib/win32/m3jpeg32.dll
/usr/lib/win32/m3jp2k32.dll
/usr/lib/win32/lsvxdec.dll
/usr/lib/win32/lhacm.acm
/usr/lib/win32/l3codecx.ax
/usr/lib/win32/l3codeca.acm
/usr/lib/win32/jp2avi.dll
/usr/lib/win32/ivvideo.dll
/usr/lib/win32/ir50_32.dll
/usr/lib/win32/ir41_32.dll
/usr/lib/win32/ir32_32.dll
/usr/lib/win32/imc32.acm
/usr/lib/win32/imaadp32.acm
/usr/lib/win32/icmw_32.dll
/usr/lib/win32/iccvid.dll
/usr/lib/win32/iac25_32.ax
/usr/lib/win32/i263_32.drv
/usr/lib/win32/huffyuv.dll
/usr/lib/win32/dspr.so.6.0
/usr/lib/win32/drvc.so
/usr/lib/win32/drv4.so.6.0
/usr/lib/win32/drv3.so.6.0
/usr/lib/win32/drv2.so.6.0
/usr/lib/win32/dnet.so.6.0
/usr/lib/win32/divxdec.ax
/usr/lib/win32/divxc32.dll
/usr/lib/win32/divxa32.acm
/usr/lib/win32/divx_c32.ax
/usr/lib/win32/divx.dll
/usr/lib/win32/ddnt.so.6.0
/usr/lib/win32/ctadp32.acm
/usr/lib/win32/cook.so.6.0
/usr/lib/win32/cook.so
/usr/lib/win32/clrviddd.dll
/usr/lib/win32/avizlib.dll
/usr/lib/win32/avimszh.dll
/usr/lib/win32/atrc.so.6.0
/usr/lib/win32/atrac3.acm
/usr/lib/win32/ativcr2.dll
/usr/lib/win32/asusasvd.dll
/usr/lib/win32/asusasv2.dll
/usr/lib/win32/aslcodec_vfw.dll
/usr/lib/win32/aslcodec_dshow.dll
/usr/lib/win32/alf2cd.acm
/usr/lib/win32/acelpdec.ax
/usr/lib/win32/ViVD2.dll
/usr/lib/win32/VDODEC32.dll
/usr/lib/win32/QuickTimeInternetExtras.qtx
/usr/lib/win32/QuickTimeEssentials.qtx
/usr/lib/win32/QuickTime.qts
/usr/lib/win32/LCodcCMP.dll
/usr/lib/win32/LCODCCMW2E.dll
/usr/lib/win32/LCMW2.dll
/usr/lib/win32/DECVW_32.DLL
/usr/lib/win32/CtWbJpg.DLL
/usr/lib/win32/CLRVIDDC.DLL
/usr/lib/win32/BeHereiVideo.qtx
/usr/lib/win32/AvidQTAVUICodec.qtx


```

---

### Post by george_apan on 2006-10-01
vp31vfw.dll is a vfw decoder for VP3. Open-source decoders for this format are available and included in every player. So, you're safe deleting it.

---

### Post by Malta paul on 2006-10-01
Thank you for the W32 codec list 'Artificial intelligence' and all the other good advice from yourself and all the other good folk out their. I have now tested out my multi-media players (DVD & Music) and all work fine without VP31VFW.dll, so problem solved.
Ubuntu system and community is great.:)

---

### Post by wieman01 on 2006-10-01
> **Artificial Intelligence said:**
> If it's the w32codecs, then you'll need them to play various close source multi-media files.
There we go... Thanks, have never paid attention to that. :-)

---

### Post by Malta paul on 2006-10-02
Well, Well I took ‘Artificial Intelligence’ advise and checked the file with two other antivirus programs, by down loading the file and putting it on a clean formatted floppy then rebooting into windows then carried out the virus checks. Guess what? it was clean! Ubuntu had not let me down. Must have been a false alarm after all. 
Thank everyone for your good advice.  
:) :)

---

