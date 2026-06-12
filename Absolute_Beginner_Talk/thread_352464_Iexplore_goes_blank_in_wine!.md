---
title: "Iexplore goes blank in wine!"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by kregg on 2007-02-03
I used automatix to install Wine

I used Winetools to install fonts, and used winecfg to set up the windows version to "Windows 98".

As far as I can remember, that is all I done. And well... Internet explorer doesn't work! Could anyone help get my internet explorer back :'(

(P.S. I took a screenshot, just incase it helps)

---

### Post by Gerard Barberi on 2007-02-03
I used a preconfigured script for my IE install and it works well.

wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-2.0.tar.gz) -O - | tar xvzf -

cd ies4linux-2.0

sh ies4linux

It will also install flash version 9

---

### Post by kregg on 2007-02-03
Ah I think I've installed that. I don't think it worked, but I'll try your way

---

### Post by kregg on 2007-02-03
Yeah I have done that. What do I need to type in to get ie6 to work?

---

### Post by glabouni on 2007-02-03
check this tutorial: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by kregg on 2007-02-03
I have tried that and I got the following:
```

/home/kregg/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/kregg/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/kregg/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/kregg/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 1532565 extra bytes at end of file.
ie_1.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_2.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_3.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_4.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 1464965 extra bytes at end of file.
ie_5.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 264823 extra bytes at end of file.
ie_6.cab: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 806829 extra bytes at end of file.
jscript.dll: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 935538 extra bytes at end of file.
setup.tdf: checksum error
/home/kregg/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 1012088 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.
```

---

### Post by kregg on 2007-02-04
Sorry to do this but help anybody?

---

### Post by andrebrait on 2008-04-24
actually... no

---

