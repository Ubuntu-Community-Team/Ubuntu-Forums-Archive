---
title: "Convert uif to iso ?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by FAS786 on 2007-06-24
I wana convert a UIF To a ISO File
Are there any converters which work with Ubuntu

Magic ISO is not ubuntu type

i hear you can try something with wine any instructions im a newbe?

---

### Post by atria on 2007-06-24
The only way i know to convert that format to iso is to use magiciso with wine on linux.

Basically the dummy steps are:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo aptitude update
sudo aptitude install wine

winecfg
wine "path to magiciso installer"
wine "path to magiciso.exe"

```

Do note that wine is quite a big software altogether and you might want to read more about it before trying my instructions.

---

### Post by Seirios on 2008-01-16
There is this prog I don't know if it works.

[http://aluigi.altervista.org/mytoolz.htm](http://aluigi.altervista.org/mytoolz.htm)

Compile with:

gcc -lz uif2iso.c -o uif2iso


Hope it helps!

---

### Post by PatheticMoFo on 2008-02-02
@Seirios

Thank you so much for that link, that program works perfectly. I did not want to have to get MagicISO!

---

### Post by breaking on 2008-02-08
thanks for the hint, worked great for me to.

just a note:
to compile, type make in the unpacked directory of uif2iso.
(u need zlib1g-dev package installed of course)


cheers. :KS

---

### Post by talon223 on 2008-02-11
haha..i just ran "wine uif2iso file.uif file2.iso" ...haha..ghetto, but it worked perfect and quick.

---

### Post by sheilnaik on 2008-02-16
> **talon223 said:**
> haha..i just ran "wine uif2iso file.uif file2.iso" ...haha..ghetto, but it worked perfect and quick.

Worked great for me too!  Thanks a lot!

---

### Post by enchance on 2008-02-20
> **Seirios said:**
> There is this prog I don't know if it works.

[http://aluigi.altervista.org/mytoolz.htm](http://aluigi.altervista.org/mytoolz.htm)

Compile with:

gcc -lz uif2iso.c -o uif2iso


Hope it helps!
Worked great! although I just followed the directions in the file itself.
```
make
```
Then I copied the resulting file to the uif folder and ran
```
./uif2iso file.uif newfile.iso
```

This program's a keeper! :KS

---

### Post by Huss on 2008-02-29
Universal image format? Pfft! 

Luigis' program worked nicely with small uif s but couldn't handle files in the gigabytes for me.

---

### Post by Huss on 2008-02-29
Magic ISO in wine worked for me. I couldn't convert it into an ISO (the trial version only lets you make 600mb ISO files) but it extracted everything.

---

### Post by efguerre on 2008-03-23
I followed these steps:

```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo aptitude update
sudo aptitude install wine

winecfg

winefile

```

winefile will help you to explore where your *.exe file is located. And then install Setup_MagicISO.exe. 
MagicISO can read uif and extract to your HD all the files that a uif file has, burn or etc..
Wine is very nice

UBUNTU ROCKS!

---

### Post by thedark2 on 2008-04-10
You can check <a href=http://www.teseter.com>Ubuntu .uif converter</a> for some info and links regarding .uif images

---

### Post by Vadi on 2008-04-17
Here's a program that does it graphically: [http://www.majorsilence.com/apps/2iso-gui/2iso-pack-v1.2.tar.gz](http://www.majorsilence.com/apps/2iso-gui/2iso-pack-v1.2.tar.gz)

---

