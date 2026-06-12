---
title: "Internet Explorer"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-07-17
I have successfully installed the ies4linux package and wine.  This may sound like a strange question, but how do I run IE now?  I have tried wine ie6, wine ies4linux, etc.. but nothing has worked.

---

### Post by aysiu on 2006-07-17
```
cd ~/bin
./ie6
```

---

### Post by amcavoy on 2006-07-17
There isn't anything in that folder...

---

### Post by aysiu on 2006-07-17
> **amcavoy said:**
> There isn't anything in that folder...
That's weird...

---

### Post by Arisna on 2006-07-17
Hmm...  How about:

```
sudo updatedb
locate ie6
```

?

---

### Post by amcavoy on 2006-07-18
I reinstalled it and came up with the following error:

```
Installing IE 6
 Initializing
 Creating Wine Prefix
 Extracting CAB files
/home/alex/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 53965 extra bytes at end of file.
/home/alex/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/alex/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/alex/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 97523 extra bytes at end of file.
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 1515823 extra bytes at end of file.
ie_1.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 1449670 extra bytes at end of file.
ie_2.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 2902339 extra bytes at end of file.
ie_3.cab: checksum error
ie_3.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 2440580 extra bytes at end of file.
ie_4.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 1440030 extra bytes at end of file.
ie_5.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 258920 extra bytes at end of file.
ie_6.cab: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 1546492 extra bytes at end of file.
jscript.dll: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 912073 extra bytes at end of file.
mssetup.dll: checksum error
/home/alex/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 1982348 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.

alex@ubuntu:~/ies4linux-2.0beta9$
```
Any idea how I might correct this?

Thank you very much for your help :) .

---

### Post by nalmeth on 2006-07-18
That output didn't come up before with the first installation?

~/bin is a folder that might have been added, ~/ is short for your home folder. Go there, and see if there is a folder called ie4linux, or anything similar that you didn't put there yourself. 

I don't know if the reinstallation was the right thing to do, those errors might just be due to the fact everything is already installed..

Keep posting back as you progress.

---

### Post by amcavoy on 2006-07-18
The first time I installed it, it seemed to be progressing fine until the terminal window closed.  I figured that it had been installed successfully, but then I couldn't find anything in the bin folder.  That's when I tried to reinstall it.  Hmm...

---

### Post by nalmeth on 2006-07-18
Hmm, ok

How did you install wine BTW? Did the script do that?

Do you have any other applications you installed into wine?

If not, then we can remove wine, plus it's configuration with this command:
```
sudo apt-get --purge remove wine
``` Then remove the bin folder.
```
rm -r ~/bin
``` (don't forget the ~/ ) :)
Reinstall wine
```
sudo apt-get install wine

winecfg
``` (enter winecfg when wine installation is done).

Close winecfg, and try the ie4linux script again. In fact, I would recommend downloading the script again fresh aswell.

Let us know what happens

---

### Post by Skia_42 on 2006-07-18
Just wondering, why do you want to install Internet Explorer wehn you have wonderfull secure alternatives such as firefox available?

---

### Post by brentoboy on 2006-07-18
this is a perfectly normal thing to do.  On windows, I have installed IE tab in firefox so that I can open things in IE -- as a web dev, you have to see what it looks like for all your target audience, even if they use IE.

I have never heard of ie4linux, but I can see how some people would be happy to use it.  For instance, my router's webpage has java controls that just dont work except in IE.  I havent needed to configure my router, but when I do, I have to get a windows laptop and plug into my network in order to use IE to config it, something like this would make a lot of sense.

but it isnt worth installing wine and a bunch of dlls to get it on my linux box (at least not personally) but I can relate to this guy's pain, to each his own.  (Maybe his wife/girlfriend/significant other demands IE)

---

