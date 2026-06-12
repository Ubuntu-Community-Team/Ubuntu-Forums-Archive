---
title: "Unable To Uninstall Opera Browser?"
date: 2012-04-25
forum: Any Other OS
---

### Post by ken0069 on 2012-04-25
Linux Mint v12 w/Cinnamon desktop which was a clean install BTW.  

I've been having problems with both Opera and Firefox crashing so I decided to uninstall Opera and try a fresh download and reinstall to see if some files were corrupted.  Went into Synaptics and uninstalled Opera then re-installed it but nothing was downloaded so I'm "assuming" that the original download was used??  

Anyway, after the reinstall it crashed again so now I'm trying to purge the entire thing but can't?  I've run CLI with the purge command but it says that Opera is not installed?  I go into Synaptics and it's not shown as installed there either but I can still click the icon that is still on the desktop and it will open?????

So can someone please tell me how to remove Opera (or any other program for that matter) COMPLETELY??  What I want is for it to have to be downloaded again before it's installed.  

HELP

Ken

---

### Post by Perfect Storm on 2012-04-25
Usually when installing from package manager or a .deb, it will keep a "copy" of the downloaded packages.

Remove Opera completly
```
sudo apt-get purge <insert name>
```

clean up the packages you have downloaded through the time:
```
sudo apt-get clean && sudo apt-get autoclean
```

If you can't find the file in the package manager could be that you installed it a non-debian/ubuntu way? Or the package is installed under a different name? Try search eg. 'browser' instead of 'opera'.

---

### Post by ken0069 on 2012-04-25
> **Artificial Intelligence said:**
> Usually when installing from package manager or a .deb, it will keep a "copy" of the downloaded packages.

Remove Opera completly
```
sudo apt-get purge <insert name>
```clean up the packages you have downloaded through the time:
```
sudo apt-get clean && sudo apt-get autoclean
```If you can't find the file in the package manager could be that you installed it a non-debian/ubuntu way? Or the package is installed under a different name? Try search eg. 'browser' instead of 'opera'.


I already tried the command line apt-get purge thingie and it said opera was not installed.  Can't remember when our how I installed it as I've done a few other installs since then. In the past though I have installed some stuff from a direct download?  Went looking in the file system but didn't see opera anywhere except for the short cut on the desk top?  Where in the file system would or could it be?

Not sure I understand your search eg, "browser"?  How is this done as I'm not real proficient with the command line.

---

### Post by Perfect Storm on 2012-04-25
You don't have to search via CLI, you could open 'Synaptic Package Manager' and click the search button.

---

### Post by ken0069 on 2012-04-25
Well, search in Synaptics for "browser" turned up a bunch of stuff but nothing about opera?  

So where would it likely be installed in the file system?  If I have an idea of where to look, maybe I can find it that way?

Thanks

---

### Post by Perfect Storm on 2012-04-25
You could try;
```
locate opera
whereis opera

```

---

### Post by ken0069 on 2012-04-25
> **Artificial Intelligence said:**
> You could try;
```
locate opera
whereis opera

```

Here is the results of those commands in terminal.

```
ken@bedroom ~ $ whereis opera
opera: /usr/bin/opera /usr/lib/opera /usr/share/opera /usr/share/man/man1/opera.1.gz
```

```
/home/ken/.opera/cache/g_0018/opr002GT.tmp
/home/ken/.opera/cache/g_0018/opr002GU.tmp
/home/ken/.opera/cache/g_0018/opr002GV.tmp
/home/ken/.opera/cache/g_0019/opr002GW.tmp
/home/ken/.opera/cache/g_0019/opr002GX.tmp
/home/ken/.opera/cache/g_0019/opr002GY.tmp
/home/ken/.opera/cache/g_0019/opr002GZ.tmp
/home/ken/.opera/cache/g_0019/opr002H1.tmp
/home/ken/.opera/cache/g_0019/opr002H4.tmp
/home/ken/.opera/cache/g_0019/opr002H8.tmp
/home/ken/.opera/cache/g_0019/opr002HA.tmp
/home/ken/.opera/cache/g_0019/opr002HB.tmp
/home/ken/.opera/cache/g_0019/opr002HF.tmp
/home/ken/.opera/cache/g_0019/opr002HG.tmp
/home/ken/.opera/cache/g_0019/opr002HI.tmp
/home/ken/.opera/cache/g_0019/opr002HJ.tmp
/home/ken/.opera/cache/g_0019/opr002HK.tmp
/home/ken/.opera/cache/g_0019/opr002HO.tmp
/home/ken/.opera/cache/g_0019/opr002HP.tmp
/home/ken/.opera/cache/g_0019/opr002HQ.tmp
/home/ken/.opera/cache/g_0019/opr002HR.tmp
/home/ken/.opera/cache/g_0019/opr002HS.tmp
/home/ken/.opera/cache/g_0019/opr002HT.tmp
/home/ken/.opera/cache/g_0019/opr002HU.tmp
/home/ken/.opera/cache/g_0019/opr002HV.tmp
/home/ken/.opera/cache/g_0019/opr002HW.tmp
/home/ken/.opera/cache/g_0019/opr002HZ.tmp
/home/ken/.opera/cache/g_0019/opr002I2.tmp
/home/ken/.opera/cache/g_0019/opr002I4.tmp
/home/ken/.opera/cache/g_0019/opr002I7.tmp
/home/ken/.opera/cache/g_0019/opr002I8.tmp
/home/ken/.opera/cache/g_0019/opr002IA.tmp
/home/ken/.opera/cache/g_0019/opr002ID.tmp
/home/ken/.opera/cache/g_0019/opr002IE.tmp
/home/ken/.opera/cache/g_0019/opr002IG.tmp
/home/ken/.opera/cache/g_0019/opr002IH.tmp
/home/ken/.opera/cache/g_0019/opr002IQ.tmp
/home/ken/.opera/cache/g_0019/opr002IR.tmp
/home/ken/.opera/cache/g_0019/opr002IT.tmp
/home/ken/.opera/cache/g_0019/opr002IV.tmp
/home/ken/.opera/cache/g_0019/opr002IW.tmp
/home/ken/.opera/cache/g_0019/opr002IX.tmp
/home/ken/.opera/cache/g_0019/opr002IY.tmp
/home/ken/.opera/cache/g_0019/opr002IZ.tmp
/home/ken/.opera/cache/g_0019/opr002J0.tmp
/home/ken/.opera/cache/g_0019/opr002J6.tmp
/home/ken/.opera/cache/g_0019/opr002J8.tmp
/home/ken/.opera/cache/g_0019/opr002JB.tmp
/home/ken/.opera/cache/g_0019/opr002JC.tmp
/home/ken/.opera/cache/g_0019/opr002JD.tmp
/home/ken/.opera/cache/g_0019/opr002JF.tmp
/home/ken/.opera/cache/g_0019/opr002JH.tmp
/home/ken/.opera/cache/g_0019/opr002JI.tmp
/home/ken/.opera/cache/g_0019/opr002JJ.tmp
/home/ken/.opera/cache/g_0019/opr002JL.tmp
/home/ken/.opera/cache/g_0019/opr002JN.tmp
/home/ken/.opera/cache/g_0019/opr002JO.tmp
/home/ken/.opera/cache/g_0019/opr002JP.tmp
/home/ken/.opera/cache/g_0019/opr002JS.tmp
/home/ken/.opera/cache/g_0019/opr002JU.tmp
/home/ken/.opera/cache/g_0019/opr002JV.tmp
/home/ken/.opera/cache/g_0019/opr002K0.tmp
/home/ken/.opera/cache/g_0019/opr002K1.tmp
/home/ken/.opera/cache/g_0019/opr002K4.tmp
/home/ken/.opera/cache/g_0019/opr002K5.tmp
/home/ken/.opera/cache/g_0019/opr002K9.tmp
/home/ken/.opera/cache/g_0019/opr002KA.tmp
/home/ken/.opera/cache/g_0019/opr002KB.tmp
/home/ken/.opera/cache/g_0019/opr002KC.tmp
/home/ken/.opera/cache/g_0019/opr002KD.tmp
/home/ken/.opera/cache/g_0019/opr002KE.tmp
/home/ken/.opera/cache/g_0019/opr002KF.tmp
/home/ken/.opera/cache/g_001A/opr002KG.tmp
/home/ken/.opera/cache/g_001A/opr002KH.tmp
/home/ken/.opera/cache/g_001A/opr002KI.tmp
/home/ken/.opera/cache/g_001A/opr002KJ.tmp
/home/ken/.opera/cache/g_001A/opr002KK.tmp
/home/ken/.opera/cache/g_001A/opr002KL.tmp
/home/ken/.opera/cache/g_001A/opr002KM.tmp
/home/ken/.opera/cache/g_001A/opr002KO.tmp
/home/ken/.opera/cache/g_001A/opr002KP.tmp
/home/ken/.opera/cache/g_001A/opr002KS.tmp
/home/ken/.opera/cache/g_001A/opr002KT.tmp
/home/ken/.opera/cache/g_001A/opr002KU.tmp
/home/ken/.opera/cache/g_001A/opr002KX.tmp
/home/ken/.opera/cache/g_001A/opr002KZ.tmp
/home/ken/.opera/cache/g_001A/opr002L0.tmp
/home/ken/.opera/cache/g_001A/opr002L1.tmp
/home/ken/.opera/cache/g_001A/opr002L2.tmp
/home/ken/.opera/cache/g_001A/opr002L3.tmp
/home/ken/.opera/cache/g_001A/opr002L4.tmp
/home/ken/.opera/cache/g_001A/opr002L7.tmp
/home/ken/.opera/cache/g_001A/opr002L8.tmp
/home/ken/.opera/cache/g_001A/opr002LA.tmp
/home/ken/.opera/cache/g_001A/opr002LB.tmp
/home/ken/.opera/cache/g_001A/opr002LD.tmp
/home/ken/.opera/cache/g_001A/opr002LE.tmp
/home/ken/.opera/cache/g_001A/opr002LF.tmp
/home/ken/.opera/cache/g_001A/opr002LG.tmp
/home/ken/.opera/cache/g_001A/opr002LI.tmp
/home/ken/.opera/cache/g_001A/opr002LJ.tmp
/home/ken/.opera/cache/g_001A/opr002LK.tmp
/home/ken/.opera/cache/g_001A/opr002LL.tmp
/home/ken/.opera/cache/g_001A/opr002LM.tmp
/home/ken/.opera/cache/g_001A/opr002LN.tmp
/home/ken/.opera/cache/g_001A/opr002LO.tmp
/home/ken/.opera/cache/g_001A/opr002LR.tmp
/home/ken/.opera/cache/g_001A/opr002LS.tmp
/home/ken/.opera/cache/g_001A/opr002LT.tmp
/home/ken/.opera/cache/g_001A/opr002LU.tmp
/home/ken/.opera/cache/g_001A/opr002LV.tmp
/home/ken/.opera/cache/g_001A/opr002LW.tmp
/home/ken/.opera/cache/g_001A/opr002LX.tmp
/home/ken/.opera/cache/g_001A/opr002LY.tmp
/home/ken/.opera/cache/g_001A/opr002LZ.tmp
/home/ken/.opera/cache/g_001A/opr002M0.tmp
/home/ken/.opera/cache/g_001A/opr002M1.tmp
/home/ken/.opera/cache/g_001A/opr002M2.tmp
/home/ken/.opera/cache/g_001A/opr002M3.tmp
/home/ken/.opera/cache/g_001A/opr002M4.tmp
/home/ken/.opera/cache/g_001A/opr002M5.tmp
/home/ken/.opera/cache/g_001A/opr002M6.tmp
/home/ken/.opera/cache/g_001A/opr002M7.tmp
/home/ken/.opera/cache/g_001A/opr002M9.tmp
/home/ken/.opera/cache/g_001A/opr002MA.tmp
/home/ken/.opera/cache/g_001A/opr002MC.tmp
/home/ken/.opera/cache/g_001A/opr002ME.tmp
/home/ken/.opera/cache/g_001A/opr002MF.tmp
/home/ken/.opera/cache/g_001A/opr002MG.tmp
/home/ken/.opera/cache/g_001A/opr002MH.tmp
/home/ken/.opera/cache/g_001A/opr002MI.tmp
/home/ken/.opera/cache/g_001A/opr002MJ.tmp
/home/ken/.opera/cache/g_001A/opr002MM.tmp
/home/ken/.opera/cache/g_001A/opr002MN.tmp
/home/ken/.opera/cache/g_001A/opr002MP.tmp
/home/ken/.opera/cache/g_001A/opr002MQ.tmp
/home/ken/.opera/cache/g_001A/opr002MS.tmp
/home/ken/.opera/cache/g_001A/opr002MV.tmp
/home/ken/.opera/cache/g_001A/opr002MZ.tmp
/home/ken/.opera/cache/g_001A/opr002N0.tmp
/home/ken/.opera/cache/g_001A/opr002N1.tmp
/home/ken/.opera/cache/g_001A/opr002N3.tmp
/home/ken/.opera/cache/g_001A/opr002N4.tmp
/home/ken/.opera/cache/g_001A/opr002N5.tmp
/home/ken/.opera/cache/g_001A/opr002N6.tmp
/home/ken/.opera/cache/g_001A/opr002N9.tmp
/home/ken/.opera/cache/g_001A/opr002NB.tmp
/home/ken/.opera/cache/g_001A/opr002NC.tmp
/home/ken/.opera/cache/g_001A/opr002ND.tmp
/home/ken/.opera/cache/g_001A/opr002NL.tmp
/home/ken/.opera/cache/g_001A/opr002NM.tmp
/home/ken/.opera/cache/g_001A/opr002NN.tmp
/home/ken/.opera/cache/g_001A/opr002NO.tmp
/home/ken/.opera/cache/g_001A/opr002NP.tmp
/home/ken/.opera/cache/g_001A/opr002NQ.tmp
/home/ken/.opera/cache/g_001A/opr002NR.tmp
/home/ken/.opera/cache/g_001A/opr002NS.tmp
/home/ken/.opera/cache/g_001A/opr002NT.tmp
/home/ken/.opera/cache/g_001A/opr002NU.tmp
/home/ken/.opera/cache/g_001A/opr002NV.tmp
/home/ken/.opera/cache/g_001A/opr002NW.tmp
/home/ken/.opera/cache/g_001A/opr002NX.tmp
/home/ken/.opera/cache/g_001A/opr002NY.tmp
/home/ken/.opera/cache/g_001B/opr002O5.tmp
/home/ken/.opera/cache/g_001B/opr002O6.tmp
/home/ken/.opera/cache/g_001B/opr002O8.tmp
/home/ken/.opera/cache/g_001B/opr002O9.tmp
/home/ken/.opera/cache/g_001B/opr002OA.tmp
/home/ken/.opera/cache/g_001B/opr002OB.tmp
/home/ken/.opera/cache/g_001B/opr002OC.tmp
/home/ken/.opera/cache/g_001B/opr002OD.tmp
/home/ken/.opera/cache/g_001B/opr002OE.tmp
/home/ken/.opera/cache/g_001B/opr002OF.tmp
/home/ken/.opera/cache/g_001B/opr002OG.tmp
/home/ken/.opera/cache/g_001B/opr002OH.tmp
/home/ken/.opera/cache/g_001B/opr002OL.tmp
/home/ken/.opera/cache/g_001B/opr002ON.tmp
/home/ken/.opera/cache/g_001B/opr002OO.tmp
/home/ken/.opera/cache/g_001B/opr002OQ.tmp
/home/ken/.opera/cache/g_001B/opr002OS.tmp
/home/ken/.opera/cache/g_001B/opr002OU.tmp
/home/ken/.opera/cache/revocation/activity.opr
/home/ken/.opera/cache/revocation/dcache4.url
/home/ken/.opera/cache/revocation/g_0000
/home/ken/.opera/cache/revocation/vlink4.dat
/home/ken/.opera/cache/revocation/g_0000/opr0000X.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0001I.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0002W.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0002X.tmp
/home/ken/.opera/custom/defaults
/home/ken/.opera/custom/defaults/operaprefs.ini
/home/ken/.opera/dictionaries/dictionaries.xml
/home/ken/.opera/icons/192.168.0.1.idx
/home/ken/.opera/icons/addons.opera.com.idx
/home/ken/.opera/icons/cache
/home/ken/.opera/icons/crash.opera.com.idx
/home/ken/.opera/icons/dragracecentral.com.idx
/home/ken/.opera/icons/duckduckgo.com.idx
/home/ken/.opera/icons/en.wikipedia.org.idx
/home/ken/.opera/icons/get.adobe.com.idx
/home/ken/.opera/icons/http%3A%2F%2F192.168.0.1%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fcrash.opera.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fdragracecentral.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fimg.imgsmail.ru%2Fr%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fimg.yandex.net%2Fi%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmikestarkcfm.proboards.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmotorsportsvillage.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmsn.foxsports.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2FDuckDuckGo%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Faccuweather%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Famazon%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fask%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fbigpoint%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fbing%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fblekko%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fdownloadcom%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Febay%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Ffastmail%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fgoogle%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fgroupon.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fkayak%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fmyopera%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fopera%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fopera.sports.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Freddit%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fshopping%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fwikipedia%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fyahoo%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fyousendit%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fs.ytimg.com%2Fyt%2Ffavicon-refresh-vfldLzJxy.png
/home/ken/.opera/icons/http%3A%2F%2Fspeakeasy.net%2Fmegapath%2Fimages%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fstatic-portal.opera.com%2Fstatic%2Fmisc%2Fportal2%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fus.mc1617.mail.yahoo.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fvfnshootout.proboards.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.avg.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.biondoracing.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.dailymail.co.uk%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.dcwg.org%2Fwp-content%2Fuploads%2F2012%2F03%2Flogo2.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.eastsidespeedway.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.fastmail.fm%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.forbes.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.google.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.grainger.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.jayski.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.msdignition.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.nascar.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.opera.com%2Fbitmaps%2Fcommon%2Fspeed_dial-icon.png
/home/ken/.opera/icons/http%3A%2F%2Fwwwimages.adobe.com%2Fwww.adobe.com%2Ffavicon.png
/home/ken/.opera/icons/https%3A%2F%2Flogin.yahoo.com%2Ffavicon.png
/home/ken/.opera/icons/https%3A%2F%2Fmail.opera.com%2Ffavicon.png
/home/ken/.opera/icons/login.yahoo.com.idx
/home/ken/.opera/icons/mail.opera.com.idx
/home/ken/.opera/icons/mail.yandex.ru.idx
/home/ken/.opera/icons/mikestarkcfm.proboards.com.idx
/home/ken/.opera/icons/motorsportsvillage.com.idx
/home/ken/.opera/icons/msn.foxsports.com.idx
/home/ken/.opera/icons/my.opera.com.idx
/home/ken/.opera/icons/persistent.txt
/home/ken/.opera/icons/portal.opera.com.idx
/home/ken/.opera/icons/redir.opera.com.idx
/home/ken/.opera/icons/speakeasy.net.idx
/home/ken/.opera/icons/us.mc1617.mail.yahoo.com.idx
/home/ken/.opera/icons/vfnshootout.proboards.com.idx
/home/ken/.opera/icons/win.mail.ru.idx
/home/ken/.opera/icons/www.ask.com.idx
/home/ken/.opera/icons/www.avg.com.idx
/home/ken/.opera/icons/www.bing.com.idx
/home/ken/.opera/icons/www.biondoracing.com.idx
/home/ken/.opera/icons/www.dailymail.co.uk.idx
/home/ken/.opera/icons/www.dcwg.org.idx
/home/ken/.opera/icons/www.eastsidespeedway.com.idx
/home/ken/.opera/icons/www.fastmail.fm.idx
/home/ken/.opera/icons/www.forbes.com.idx
/home/ken/.opera/icons/www.google.com.idx
/home/ken/.opera/icons/www.grainger.com.idx
/home/ken/.opera/icons/www.jayski.com.idx
/home/ken/.opera/icons/www.msdignition.com.idx
/home/ken/.opera/icons/www.nascar.com.idx
/home/ken/.opera/icons/www.opera.com.idx
/home/ken/.opera/icons/www.youtube.com.idx
/home/ken/.opera/icons/yahoo.opera.com.idx
/home/ken/.opera/icons/cache/cookies4.dat
/home/ken/.opera/icons/cache/dcache4.url
/home/ken/.opera/icons/cache/g_0000
/home/ken/.opera/icons/cache/vlink4.dat
/home/ken/.opera/icons/cache/g_0000/opr00001.tmp
/home/ken/.opera/icons/cache/g_0000/opr00002.tmp
/home/ken/.opera/icons/cache/g_0000/opr00003.tmp
/home/ken/.opera/mail/accounts.ini
/home/ken/.opera/mail/indexer
/home/ken/.opera/mail/omailbase.dat
/home/ken/.opera/mail/indexer/message_id
/home/ken/.opera/opcache/dcache4.url
/home/ken/.opera/opcache/sesn
/home/ken/.opera/pstorage/00
/home/ken/.opera/pstorage/psindex.dat
/home/ken/.opera/pstorage/00/0E
/home/ken/.opera/pstorage/00/17
/home/ken/.opera/pstorage/00/19
/home/ken/.opera/pstorage/00/0E/00000000
/home/ken/.opera/pstorage/00/17/00000000
/home/ken/.opera/pstorage/00/19/00000000
/home/ken/.opera/sessions/autosave.win
/home/ken/.opera/sessions/autosave.win.bak
/home/ken/.opera/styles/user
/home/ken/.opera/styles/user/accessibility.css
/home/ken/.opera/styles/user/altdebugger.css
/home/ken/.opera/styles/user/classid.css
/home/ken/.opera/styles/user/contrastbw.css
/home/ken/.opera/styles/user/contrastwb.css
/home/ken/.opera/styles/user/disablebreaks.css
/home/ken/.opera/styles/user/disablefloats.css
/home/ken/.opera/styles/user/disableforms.css
/home/ken/.opera/styles/user/disablepositioning.css
/home/ken/.opera/styles/user/disabletables.css
/home/ken/.opera/styles/user/outline.css
/home/ken/.opera/styles/user/structureblock.css
/home/ken/.opera/styles/user/structureinline.css
/home/ken/.opera/styles/user/structuretables.css
/home/ken/.opera/styles/user/tablelayout.css
/home/ken/.opera/styles/user/toc.css
/home/ken/.opera/thumbnails/4f2225c0-76bd-11e1-882b-84adf18880a4.png
/home/ken/.opera/thumbnails/cc761a10-7dff-11e1-853c-841b571aa858.png
/home/ken/.opera/thumbnails/cc764120-7dff-11e1-853d-f4fd0d45a48e.png
/home/ken/.opera/thumbnails/cc766830-7dff-11e1-853e-b6251f949fc7.png
/home/ken/.opera/thumbnails/cc766830-7dff-11e1-853f-9b618dbb6411.png
/home/ken/.opera/thumbnails/cc768f40-7dff-11e1-8540-bb58133b9c4a.png
/home/ken/.opera/thumbnails/cc76b650-7dff-11e1-8541-cc78d28c13a4.png
/home/ken/.opera/toolbar/standard_toolbar.ini
/home/ken/.opera/vps/0000
/home/ken/.opera/vps/0001
/home/ken/.opera/vps/0003
/home/ken/.opera/vps/0004
/home/ken/.opera/vps/0005
/home/ken/.opera/vps/0006
/home/ken/.opera/vps/0007
/home/ken/.opera/vps/0008
/home/ken/.opera/vps/0009
/home/ken/.opera/vps/0010
/home/ken/.opera/vps/0012
/home/ken/.opera/vps/0000/adoc.bx
/home/ken/.opera/vps/0000/md.dat
/home/ken/.opera/vps/0000/url.axx
/home/ken/.opera/vps/0000/w.axx
/home/ken/.opera/vps/0000/wb.vx
/home/ken/.opera/vps/0001/adoc.bx
/home/ken/.opera/vps/0001/md.dat
/home/ken/.opera/vps/0001/url.axx
/home/ken/.opera/vps/0001/w.axx
/home/ken/.opera/vps/0001/wb.vx
/home/ken/.opera/vps/0003/adoc.bx
/home/ken/.opera/vps/0003/md.dat
/home/ken/.opera/vps/0003/url.axx
/home/ken/.opera/vps/0003/w.axx
/home/ken/.opera/vps/0003/wb.vx
/home/ken/.opera/vps/0004/adoc.bx
/home/ken/.opera/vps/0004/md.dat
/home/ken/.opera/vps/0004/url.axx
/home/ken/.opera/vps/0004/w.axx
/home/ken/.opera/vps/0004/wb.vx
/home/ken/.opera/vps/0005/adoc.bx
/home/ken/.opera/vps/0005/md.dat
/home/ken/.opera/vps/0005/url.axx
/home/ken/.opera/vps/0005/w.axx
/home/ken/.opera/vps/0005/wb.vx
/home/ken/.opera/vps/0006/adoc.bx
/home/ken/.opera/vps/0006/md.dat
/home/ken/.opera/vps/0006/url.axx
/home/ken/.opera/vps/0006/w.axx
/home/ken/.opera/vps/0006/wb.vx
/home/ken/.opera/vps/0007/adoc.bx
/home/ken/.opera/vps/0007/md.dat
/home/ken/.opera/vps/0007/url.axx
/home/ken/.opera/vps/0007/w.axx
/home/ken/.opera/vps/0007/wb.vx
/home/ken/.opera/vps/0008/adoc.bx
/home/ken/.opera/vps/0008/md.dat
/home/ken/.opera/vps/0008/url.axx
/home/ken/.opera/vps/0008/w.axx
/home/ken/.opera/vps/0008/wb.vx
/home/ken/.opera/vps/0009/adoc.bx
/home/ken/.opera/vps/0009/md.dat
/home/ken/.opera/vps/0009/url.axx
/home/ken/.opera/vps/0009/w.axx
/home/ken/.opera/vps/0009/wb.vx
/home/ken/.opera/vps/0010/adoc.bx
/home/ken/.opera/vps/0010/md.dat
/home/ken/.opera/vps/0010/url.axx
/home/ken/.opera/vps/0010/w.axx
/home/ken/.opera/vps/0010/wb.vx
/home/ken/.opera/vps/0012/adoc.bx
/home/ken/.opera/vps/0012/md.dat
/home/ken/.opera/vps/0012/url.axx
/home/ken/.opera/vps/0012/w.axx
/home/ken/.opera/vps/0012/wb.vx
/home/ken/.opera/webserver/users.xml
/home/ken/.opera/widgets/widgets.dat
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/cache
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/prefs.dat
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/cache/activity.opr
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/cache
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/prefs.dat
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/cache/activity.opr
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/cache
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/prefs.dat
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/cache/activity.opr
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/cache
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/prefs.dat
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/cache/activity.opr
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/cache
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/prefs.dat
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/cache/activity.opr
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/cache
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/prefs.dat
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/cache/activity.opr
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/cache
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/prefs.dat
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/cache/activity.opr
/home/ken/Desktop/opera-browser.desktop
/home/ken/Downloads/opera_11.11.2109_amd64.deb
/lib/modules/3.0.0-12-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
/usr/include/glib-2.0/gio/gmountoperation.h
/usr/include/gtk-2.0/gtk/gtkmountoperation.h
/usr/include/gtk-2.0/gtk/gtkprintoperation.h
/usr/include/gtk-2.0/gtk/gtkprintoperationpreview.h
/usr/lib/pymodules/python2.7/epsilon/cooperator.py
/usr/lib/pymodules/python2.7/epsilon/cooperator.pyc
/usr/lib/python2.6/dist-packages/twisted/test/test_cooperator.py
/usr/lib/python2.7/dist-packages/twisted/test/test_cooperator.py
/usr/lib/python2.7/dist-packages/twisted/test/test_cooperator.pyc
/usr/lib/python2.7/lib2to3/fixes/fix_operator.py
/usr/lib/python2.7/lib2to3/fixes/fix_operator.pyc
/usr/share/doc/python-launchpadlib/docs/operations.txt
/usr/share/doc/python-lazr.restfulclient/docs/operations.txt.gz
/usr/share/icons/Mint-X/apps/16/opera-browser.png
/usr/share/icons/Mint-X/apps/16/opera-widget-manager.png
/usr/share/icons/Mint-X/apps/16/opera.png
/usr/share/icons/Mint-X/apps/22/opera-browser.png
/usr/share/icons/Mint-X/apps/22/opera-widget-manager.png
/usr/share/icons/Mint-X/apps/22/opera.png
/usr/share/icons/Mint-X/apps/24/opera-browser.png
/usr/share/icons/Mint-X/apps/24/opera-widget-manager.png
/usr/share/icons/Mint-X/apps/24/opera.png
/usr/share/icons/Mint-X/apps/32/opera-browser.png
/usr/share/icons/Mint-X/apps/32/opera-widget-manager.png
/usr/share/icons/Mint-X/apps/32/opera.png
/usr/share/icons/Mint-X/apps/48/opera-browser.png
/usr/share/icons/Mint-X/apps/48/opera-widget-manager.png
/usr/share/icons/Mint-X/apps/48/opera.png
/usr/share/icons/Mint-X/apps/scalable/opera-browser.svg
/usr/share/icons/Mint-X/apps/scalable/opera-widget-manager.svg
/usr/share/icons/Mint-X/apps/scalable/opera.svg
/usr/share/linuxmint/common/artwork/opera
/usr/share/linuxmint/common/artwork/opera/bookmarks.adr
/usr/share/linuxmint/common/artwork/opera/operaprefs_default.ini
/usr/share/linuxmint/common/artwork/opera/operaprefs_fixed.ini
/usr/share/linuxmint/common/artwork/opera/pluginpath.ini
/usr/share/linuxmint/common/artwork/opera/search.ini
/usr/share/linuxmint/mintinstall/icons/opera-widget-manager.png
/usr/share/linuxmint/mintinstall/icons/opera.png
/usr/share/linuxmint/mintinstall/installed/opera-widget-manager.png
/usr/share/linuxmint/mintinstall/installed/opera.png
/usr/share/man/man7/operator.7.gz
/usr/share/pixmaps/pidgin/emblems/16/half-operator.png
/usr/share/pixmaps/pidgin/emblems/16/operator.png
/usr/share/pyshared/epsilon/cooperator.py
/usr/share/pyshared/twisted/test/test_cooperator.py
/usr/src/linux-headers-3.0.0-12-generic/include/config/dvb/usb/opera1.h
/var/cache/apt/archives/opera_11.61.1250-1linuxmint_i386.deb
/var/cache/apt/archives/opera_11.62.1347-1linuxmint_i386.deb
ken@bedroom ~ $ 

```

---

### Post by Perfect Storm on 2012-04-25
```
/var/cache/apt/archives/opera_11.61.1250-1linuxmint_i386.deb
/var/cache/apt/archives/opera_11.62.1347-1linuxmint_i386.deb
```

It's still in apt cache I see. It haven't been cleaned.

```
/home/ken/.opera/cache/g_0018/opr002GT.tmp
/home/ken/.opera/cache/g_0018/opr002GU.tmp
/home/ken/.opera/cache/g_0018/opr002GV.tmp
/home/ken/.opera/cache/g_0019/opr002GW.tmp
/home/ken/.opera/cache/g_0019/opr002GX.tmp
/home/ken/.opera/cache/g_0019/opr002GY.tmp
/home/ken/.opera/cache/g_0019/opr002GZ.tmp
/home/ken/.opera/cache/g_0019/opr002H1.tmp
/home/ken/.opera/cache/g_0019/opr002H4.tmp
/home/ken/.opera/cache/g_0019/opr002H8.tmp
/home/ken/.opera/cache/g_0019/opr002HA.tmp
/home/ken/.opera/cache/g_0019/opr002HB.tmp
/home/ken/.opera/cache/g_0019/opr002HF.tmp
/home/ken/.opera/cache/g_0019/opr002HG.tmp
/home/ken/.opera/cache/g_0019/opr002HI.tmp
/home/ken/.opera/cache/g_0019/opr002HJ.tmp
/home/ken/.opera/cache/g_0019/opr002HK.tmp
/home/ken/.opera/cache/g_0019/opr002HO.tmp
/home/ken/.opera/cache/g_0019/opr002HP.tmp
/home/ken/.opera/cache/g_0019/opr002HQ.tmp
/home/ken/.opera/cache/g_0019/opr002HR.tmp
/home/ken/.opera/cache/g_0019/opr002HS.tmp
/home/ken/.opera/cache/g_0019/opr002HT.tmp
/home/ken/.opera/cache/g_0019/opr002HU.tmp
/home/ken/.opera/cache/g_0019/opr002HV.tmp
/home/ken/.opera/cache/g_0019/opr002HW.tmp
/home/ken/.opera/cache/g_0019/opr002HZ.tmp
/home/ken/.opera/cache/g_0019/opr002I2.tmp
/home/ken/.opera/cache/g_0019/opr002I4.tmp
/home/ken/.opera/cache/g_0019/opr002I7.tmp
/home/ken/.opera/cache/g_0019/opr002I8.tmp
/home/ken/.opera/cache/g_0019/opr002IA.tmp
/home/ken/.opera/cache/g_0019/opr002ID.tmp
/home/ken/.opera/cache/g_0019/opr002IE.tmp
/home/ken/.opera/cache/g_0019/opr002IG.tmp
/home/ken/.opera/cache/g_0019/opr002IH.tmp
/home/ken/.opera/cache/g_0019/opr002IQ.tmp
/home/ken/.opera/cache/g_0019/opr002IR.tmp
/home/ken/.opera/cache/g_0019/opr002IT.tmp
/home/ken/.opera/cache/g_0019/opr002IV.tmp
/home/ken/.opera/cache/g_0019/opr002IW.tmp
/home/ken/.opera/cache/g_0019/opr002IX.tmp
/home/ken/.opera/cache/g_0019/opr002IY.tmp
/home/ken/.opera/cache/g_0019/opr002IZ.tmp
/home/ken/.opera/cache/g_0019/opr002J0.tmp
/home/ken/.opera/cache/g_0019/opr002J6.tmp
/home/ken/.opera/cache/g_0019/opr002J8.tmp
/home/ken/.opera/cache/g_0019/opr002JB.tmp
/home/ken/.opera/cache/g_0019/opr002JC.tmp
/home/ken/.opera/cache/g_0019/opr002JD.tmp
/home/ken/.opera/cache/g_0019/opr002JF.tmp
/home/ken/.opera/cache/g_0019/opr002JH.tmp
/home/ken/.opera/cache/g_0019/opr002JI.tmp
/home/ken/.opera/cache/g_0019/opr002JJ.tmp
/home/ken/.opera/cache/g_0019/opr002JL.tmp
/home/ken/.opera/cache/g_0019/opr002JN.tmp
/home/ken/.opera/cache/g_0019/opr002JO.tmp
/home/ken/.opera/cache/g_0019/opr002JP.tmp
/home/ken/.opera/cache/g_0019/opr002JS.tmp
/home/ken/.opera/cache/g_0019/opr002JU.tmp
/home/ken/.opera/cache/g_0019/opr002JV.tmp
/home/ken/.opera/cache/g_0019/opr002K0.tmp
/home/ken/.opera/cache/g_0019/opr002K1.tmp
/home/ken/.opera/cache/g_0019/opr002K4.tmp
/home/ken/.opera/cache/g_0019/opr002K5.tmp
/home/ken/.opera/cache/g_0019/opr002K9.tmp
/home/ken/.opera/cache/g_0019/opr002KA.tmp
/home/ken/.opera/cache/g_0019/opr002KB.tmp
/home/ken/.opera/cache/g_0019/opr002KC.tmp
/home/ken/.opera/cache/g_0019/opr002KD.tmp
/home/ken/.opera/cache/g_0019/opr002KE.tmp
/home/ken/.opera/cache/g_0019/opr002KF.tmp
/home/ken/.opera/cache/g_001A/opr002KG.tmp
/home/ken/.opera/cache/g_001A/opr002KH.tmp
/home/ken/.opera/cache/g_001A/opr002KI.tmp
/home/ken/.opera/cache/g_001A/opr002KJ.tmp
/home/ken/.opera/cache/g_001A/opr002KK.tmp
/home/ken/.opera/cache/g_001A/opr002KL.tmp
/home/ken/.opera/cache/g_001A/opr002KM.tmp
/home/ken/.opera/cache/g_001A/opr002KO.tmp
/home/ken/.opera/cache/g_001A/opr002KP.tmp
/home/ken/.opera/cache/g_001A/opr002KS.tmp
/home/ken/.opera/cache/g_001A/opr002KT.tmp
/home/ken/.opera/cache/g_001A/opr002KU.tmp
/home/ken/.opera/cache/g_001A/opr002KX.tmp
/home/ken/.opera/cache/g_001A/opr002KZ.tmp
/home/ken/.opera/cache/g_001A/opr002L0.tmp
/home/ken/.opera/cache/g_001A/opr002L1.tmp
/home/ken/.opera/cache/g_001A/opr002L2.tmp
/home/ken/.opera/cache/g_001A/opr002L3.tmp
/home/ken/.opera/cache/g_001A/opr002L4.tmp
/home/ken/.opera/cache/g_001A/opr002L7.tmp
/home/ken/.opera/cache/g_001A/opr002L8.tmp
/home/ken/.opera/cache/g_001A/opr002LA.tmp
/home/ken/.opera/cache/g_001A/opr002LB.tmp
/home/ken/.opera/cache/g_001A/opr002LD.tmp
/home/ken/.opera/cache/g_001A/opr002LE.tmp
/home/ken/.opera/cache/g_001A/opr002LF.tmp
/home/ken/.opera/cache/g_001A/opr002LG.tmp
/home/ken/.opera/cache/g_001A/opr002LI.tmp
/home/ken/.opera/cache/g_001A/opr002LJ.tmp
/home/ken/.opera/cache/g_001A/opr002LK.tmp
/home/ken/.opera/cache/g_001A/opr002LL.tmp
/home/ken/.opera/cache/g_001A/opr002LM.tmp
/home/ken/.opera/cache/g_001A/opr002LN.tmp
/home/ken/.opera/cache/g_001A/opr002LO.tmp
/home/ken/.opera/cache/g_001A/opr002LR.tmp
/home/ken/.opera/cache/g_001A/opr002LS.tmp
/home/ken/.opera/cache/g_001A/opr002LT.tmp
/home/ken/.opera/cache/g_001A/opr002LU.tmp
/home/ken/.opera/cache/g_001A/opr002LV.tmp
/home/ken/.opera/cache/g_001A/opr002LW.tmp
/home/ken/.opera/cache/g_001A/opr002LX.tmp
/home/ken/.opera/cache/g_001A/opr002LY.tmp
/home/ken/.opera/cache/g_001A/opr002LZ.tmp
/home/ken/.opera/cache/g_001A/opr002M0.tmp
/home/ken/.opera/cache/g_001A/opr002M1.tmp
/home/ken/.opera/cache/g_001A/opr002M2.tmp
/home/ken/.opera/cache/g_001A/opr002M3.tmp
/home/ken/.opera/cache/g_001A/opr002M4.tmp
/home/ken/.opera/cache/g_001A/opr002M5.tmp
/home/ken/.opera/cache/g_001A/opr002M6.tmp
/home/ken/.opera/cache/g_001A/opr002M7.tmp
/home/ken/.opera/cache/g_001A/opr002M9.tmp
/home/ken/.opera/cache/g_001A/opr002MA.tmp
/home/ken/.opera/cache/g_001A/opr002MC.tmp
/home/ken/.opera/cache/g_001A/opr002ME.tmp
/home/ken/.opera/cache/g_001A/opr002MF.tmp
/home/ken/.opera/cache/g_001A/opr002MG.tmp
/home/ken/.opera/cache/g_001A/opr002MH.tmp
/home/ken/.opera/cache/g_001A/opr002MI.tmp
/home/ken/.opera/cache/g_001A/opr002MJ.tmp
/home/ken/.opera/cache/g_001A/opr002MM.tmp
/home/ken/.opera/cache/g_001A/opr002MN.tmp
/home/ken/.opera/cache/g_001A/opr002MP.tmp
/home/ken/.opera/cache/g_001A/opr002MQ.tmp
/home/ken/.opera/cache/g_001A/opr002MS.tmp
/home/ken/.opera/cache/g_001A/opr002MV.tmp
/home/ken/.opera/cache/g_001A/opr002MZ.tmp
/home/ken/.opera/cache/g_001A/opr002N0.tmp
/home/ken/.opera/cache/g_001A/opr002N1.tmp
/home/ken/.opera/cache/g_001A/opr002N3.tmp
/home/ken/.opera/cache/g_001A/opr002N4.tmp
/home/ken/.opera/cache/g_001A/opr002N5.tmp
/home/ken/.opera/cache/g_001A/opr002N6.tmp
/home/ken/.opera/cache/g_001A/opr002N9.tmp
/home/ken/.opera/cache/g_001A/opr002NB.tmp
/home/ken/.opera/cache/g_001A/opr002NC.tmp
/home/ken/.opera/cache/g_001A/opr002ND.tmp
/home/ken/.opera/cache/g_001A/opr002NL.tmp
/home/ken/.opera/cache/g_001A/opr002NM.tmp
/home/ken/.opera/cache/g_001A/opr002NN.tmp
/home/ken/.opera/cache/g_001A/opr002NO.tmp
/home/ken/.opera/cache/g_001A/opr002NP.tmp
/home/ken/.opera/cache/g_001A/opr002NQ.tmp
/home/ken/.opera/cache/g_001A/opr002NR.tmp
/home/ken/.opera/cache/g_001A/opr002NS.tmp
/home/ken/.opera/cache/g_001A/opr002NT.tmp
/home/ken/.opera/cache/g_001A/opr002NU.tmp
/home/ken/.opera/cache/g_001A/opr002NV.tmp
/home/ken/.opera/cache/g_001A/opr002NW.tmp
/home/ken/.opera/cache/g_001A/opr002NX.tmp
/home/ken/.opera/cache/g_001A/opr002NY.tmp
/home/ken/.opera/cache/g_001B/opr002O5.tmp
/home/ken/.opera/cache/g_001B/opr002O6.tmp
/home/ken/.opera/cache/g_001B/opr002O8.tmp
/home/ken/.opera/cache/g_001B/opr002O9.tmp
/home/ken/.opera/cache/g_001B/opr002OA.tmp
/home/ken/.opera/cache/g_001B/opr002OB.tmp
/home/ken/.opera/cache/g_001B/opr002OC.tmp
/home/ken/.opera/cache/g_001B/opr002OD.tmp
/home/ken/.opera/cache/g_001B/opr002OE.tmp
/home/ken/.opera/cache/g_001B/opr002OF.tmp
/home/ken/.opera/cache/g_001B/opr002OG.tmp
/home/ken/.opera/cache/g_001B/opr002OH.tmp
/home/ken/.opera/cache/g_001B/opr002OL.tmp
/home/ken/.opera/cache/g_001B/opr002ON.tmp
/home/ken/.opera/cache/g_001B/opr002OO.tmp
/home/ken/.opera/cache/g_001B/opr002OQ.tmp
/home/ken/.opera/cache/g_001B/opr002OS.tmp
/home/ken/.opera/cache/g_001B/opr002OU.tmp
/home/ken/.opera/cache/revocation/activity.opr
/home/ken/.opera/cache/revocation/dcache4.url
/home/ken/.opera/cache/revocation/g_0000
/home/ken/.opera/cache/revocation/vlink4.dat
/home/ken/.opera/cache/revocation/g_0000/opr0000X.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0001I.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0002W.tmp
/home/ken/.opera/cache/revocation/g_0000/opr0002X.tmp
/home/ken/.opera/custom/defaults
/home/ken/.opera/custom/defaults/operaprefs.ini
/home/ken/.opera/dictionaries/dictionaries.xml
/home/ken/.opera/icons/192.168.0.1.idx
/home/ken/.opera/icons/addons.opera.com.idx
/home/ken/.opera/icons/cache
/home/ken/.opera/icons/crash.opera.com.idx
/home/ken/.opera/icons/dragracecentral.com.idx
/home/ken/.opera/icons/duckduckgo.com.idx
/home/ken/.opera/icons/en.wikipedia.org.idx
/home/ken/.opera/icons/get.adobe.com.idx
/home/ken/.opera/icons/http%3A%2F%2F192.168.0.1%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fcrash.opera.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fdragracecentral.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fimg.imgsmail.ru%2Fr%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fimg.yandex.net%2Fi%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmikestarkcfm.proboards.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmotorsportsvillage.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fmsn.foxsports.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2FDuckDuckGo%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Faccuweather%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Famazon%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fask%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fbigpoint%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fbing%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fblekko%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fdownloadcom%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Febay%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Ffastmail%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fgoogle%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fgroupon.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fkayak%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fmyopera%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fopera%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fopera.sports.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Freddit%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fshopping%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fwikipedia%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fyahoo%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fredir.opera.com%2Ffavicons%2Fyousendit%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fs.ytimg.com%2Fyt%2Ffavicon-refresh-vfldLzJxy.png
/home/ken/.opera/icons/http%3A%2F%2Fspeakeasy.net%2Fmegapath%2Fimages%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fstatic-portal.opera.com%2Fstatic%2Fmisc%2Fportal2%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fus.mc1617.mail.yahoo.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fvfnshootout.proboards.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.avg.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.biondoracing.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.dailymail.co.uk%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.dcwg.org%2Fwp-content%2Fuploads%2F2012%2F03%2Flogo2.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.eastsidespeedway.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.fastmail.fm%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.forbes.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.google.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.grainger.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.jayski.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.msdignition.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.nascar.com%2Ffavicon.png
/home/ken/.opera/icons/http%3A%2F%2Fwww.opera.com%2Fbitmaps%2Fcommon%2Fspeed_dial-icon.png
/home/ken/.opera/icons/http%3A%2F%2Fwwwimages.adobe.com%2Fwww.adobe.com%2Ffavicon.png
/home/ken/.opera/icons/https%3A%2F%2Flogin.yahoo.com%2Ffavicon.png
/home/ken/.opera/icons/https%3A%2F%2Fmail.opera.com%2Ffavicon.png
/home/ken/.opera/icons/login.yahoo.com.idx
/home/ken/.opera/icons/mail.opera.com.idx
/home/ken/.opera/icons/mail.yandex.ru.idx
/home/ken/.opera/icons/mikestarkcfm.proboards.com.idx
/home/ken/.opera/icons/motorsportsvillage.com.idx
/home/ken/.opera/icons/msn.foxsports.com.idx
/home/ken/.opera/icons/my.opera.com.idx
/home/ken/.opera/icons/persistent.txt
/home/ken/.opera/icons/portal.opera.com.idx
/home/ken/.opera/icons/redir.opera.com.idx
/home/ken/.opera/icons/speakeasy.net.idx
/home/ken/.opera/icons/us.mc1617.mail.yahoo.com.idx
/home/ken/.opera/icons/vfnshootout.proboards.com.idx
/home/ken/.opera/icons/win.mail.ru.idx
/home/ken/.opera/icons/www.ask.com.idx
/home/ken/.opera/icons/www.avg.com.idx
/home/ken/.opera/icons/www.bing.com.idx
/home/ken/.opera/icons/www.biondoracing.com.idx
/home/ken/.opera/icons/www.dailymail.co.uk.idx
/home/ken/.opera/icons/www.dcwg.org.idx
/home/ken/.opera/icons/www.eastsidespeedway.com.idx
/home/ken/.opera/icons/www.fastmail.fm.idx
/home/ken/.opera/icons/www.forbes.com.idx
/home/ken/.opera/icons/www.google.com.idx
/home/ken/.opera/icons/www.grainger.com.idx
/home/ken/.opera/icons/www.jayski.com.idx
/home/ken/.opera/icons/www.msdignition.com.idx
/home/ken/.opera/icons/www.nascar.com.idx
/home/ken/.opera/icons/www.opera.com.idx
/home/ken/.opera/icons/www.youtube.com.idx
/home/ken/.opera/icons/yahoo.opera.com.idx
/home/ken/.opera/icons/cache/cookies4.dat
/home/ken/.opera/icons/cache/dcache4.url
/home/ken/.opera/icons/cache/g_0000
/home/ken/.opera/icons/cache/vlink4.dat
/home/ken/.opera/icons/cache/g_0000/opr00001.tmp
/home/ken/.opera/icons/cache/g_0000/opr00002.tmp
/home/ken/.opera/icons/cache/g_0000/opr00003.tmp
/home/ken/.opera/mail/accounts.ini
/home/ken/.opera/mail/indexer
/home/ken/.opera/mail/omailbase.dat
/home/ken/.opera/mail/indexer/message_id
/home/ken/.opera/opcache/dcache4.url
/home/ken/.opera/opcache/sesn
/home/ken/.opera/pstorage/00
/home/ken/.opera/pstorage/psindex.dat
/home/ken/.opera/pstorage/00/0E
/home/ken/.opera/pstorage/00/17
/home/ken/.opera/pstorage/00/19
/home/ken/.opera/pstorage/00/0E/00000000
/home/ken/.opera/pstorage/00/17/00000000
/home/ken/.opera/pstorage/00/19/00000000
/home/ken/.opera/sessions/autosave.win
/home/ken/.opera/sessions/autosave.win.bak
/home/ken/.opera/styles/user
/home/ken/.opera/styles/user/accessibility.css
/home/ken/.opera/styles/user/altdebugger.css
/home/ken/.opera/styles/user/classid.css
/home/ken/.opera/styles/user/contrastbw.css
/home/ken/.opera/styles/user/contrastwb.css
/home/ken/.opera/styles/user/disablebreaks.css
/home/ken/.opera/styles/user/disablefloats.css
/home/ken/.opera/styles/user/disableforms.css
/home/ken/.opera/styles/user/disablepositioning.css
/home/ken/.opera/styles/user/disabletables.css
/home/ken/.opera/styles/user/outline.css
/home/ken/.opera/styles/user/structureblock.css
/home/ken/.opera/styles/user/structureinline.css
/home/ken/.opera/styles/user/structuretables.css
/home/ken/.opera/styles/user/tablelayout.css
/home/ken/.opera/styles/user/toc.css
/home/ken/.opera/thumbnails/4f2225c0-76bd-11e1-882b-84adf18880a4.png
/home/ken/.opera/thumbnails/cc761a10-7dff-11e1-853c-841b571aa858.png
/home/ken/.opera/thumbnails/cc764120-7dff-11e1-853d-f4fd0d45a48e.png
/home/ken/.opera/thumbnails/cc766830-7dff-11e1-853e-b6251f949fc7.png
/home/ken/.opera/thumbnails/cc766830-7dff-11e1-853f-9b618dbb6411.png
/home/ken/.opera/thumbnails/cc768f40-7dff-11e1-8540-bb58133b9c4a.png
/home/ken/.opera/thumbnails/cc76b650-7dff-11e1-8541-cc78d28c13a4.png
/home/ken/.opera/toolbar/standard_toolbar.ini
/home/ken/.opera/vps/0000
/home/ken/.opera/vps/0001
/home/ken/.opera/vps/0003
/home/ken/.opera/vps/0004
/home/ken/.opera/vps/0005
/home/ken/.opera/vps/0006
/home/ken/.opera/vps/0007
/home/ken/.opera/vps/0008
/home/ken/.opera/vps/0009
/home/ken/.opera/vps/0010
/home/ken/.opera/vps/0012
/home/ken/.opera/vps/0000/adoc.bx
/home/ken/.opera/vps/0000/md.dat
/home/ken/.opera/vps/0000/url.axx
/home/ken/.opera/vps/0000/w.axx
/home/ken/.opera/vps/0000/wb.vx
/home/ken/.opera/vps/0001/adoc.bx
/home/ken/.opera/vps/0001/md.dat
/home/ken/.opera/vps/0001/url.axx
/home/ken/.opera/vps/0001/w.axx
/home/ken/.opera/vps/0001/wb.vx
/home/ken/.opera/vps/0003/adoc.bx
/home/ken/.opera/vps/0003/md.dat
/home/ken/.opera/vps/0003/url.axx
/home/ken/.opera/vps/0003/w.axx
/home/ken/.opera/vps/0003/wb.vx
/home/ken/.opera/vps/0004/adoc.bx
/home/ken/.opera/vps/0004/md.dat
/home/ken/.opera/vps/0004/url.axx
/home/ken/.opera/vps/0004/w.axx
/home/ken/.opera/vps/0004/wb.vx
/home/ken/.opera/vps/0005/adoc.bx
/home/ken/.opera/vps/0005/md.dat
/home/ken/.opera/vps/0005/url.axx
/home/ken/.opera/vps/0005/w.axx
/home/ken/.opera/vps/0005/wb.vx
/home/ken/.opera/vps/0006/adoc.bx
/home/ken/.opera/vps/0006/md.dat
/home/ken/.opera/vps/0006/url.axx
/home/ken/.opera/vps/0006/w.axx
/home/ken/.opera/vps/0006/wb.vx
/home/ken/.opera/vps/0007/adoc.bx
/home/ken/.opera/vps/0007/md.dat
/home/ken/.opera/vps/0007/url.axx
/home/ken/.opera/vps/0007/w.axx
/home/ken/.opera/vps/0007/wb.vx
/home/ken/.opera/vps/0008/adoc.bx
/home/ken/.opera/vps/0008/md.dat
/home/ken/.opera/vps/0008/url.axx
/home/ken/.opera/vps/0008/w.axx
/home/ken/.opera/vps/0008/wb.vx
/home/ken/.opera/vps/0009/adoc.bx
/home/ken/.opera/vps/0009/md.dat
/home/ken/.opera/vps/0009/url.axx
/home/ken/.opera/vps/0009/w.axx
/home/ken/.opera/vps/0009/wb.vx
/home/ken/.opera/vps/0010/adoc.bx
/home/ken/.opera/vps/0010/md.dat
/home/ken/.opera/vps/0010/url.axx
/home/ken/.opera/vps/0010/w.axx
/home/ken/.opera/vps/0010/wb.vx
/home/ken/.opera/vps/0012/adoc.bx
/home/ken/.opera/vps/0012/md.dat
/home/ken/.opera/vps/0012/url.axx
/home/ken/.opera/vps/0012/w.axx
/home/ken/.opera/vps/0012/wb.vx
/home/ken/.opera/webserver/users.xml
/home/ken/.opera/widgets/widgets.dat
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/cache
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/prefs.dat
/home/ken/.opera/widgets/wuid-0be1c30e-5713-040a-029e-6c2e571369a9/cache/activity.opr
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/cache
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/prefs.dat
/home/ken/.opera/widgets/wuid-1eda32c1-7bd6-0f95-013f-8ffb7bd6f241/cache/activity.opr
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/cache
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/prefs.dat
/home/ken/.opera/widgets/wuid-33079811-1d60-05da-02f9-95431d60180a/cache/activity.opr
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/cache
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/prefs.dat
/home/ken/.opera/widgets/wuid-6bab3663-481b-022a-096c-ec58481b7ff2/cache/activity.opr
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/cache
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/prefs.dat
/home/ken/.opera/widgets/wuid-6efa3ddb-3006-0b44-0176-cbca30065688/cache/activity.opr
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/cache
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/prefs.dat
/home/ken/.opera/widgets/wuid-76fece89-6114-01de-037c-385461149c16/cache/activity.opr
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/cache
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/prefs.dat
/home/ken/.opera/widgets/wuid-7d154f04-8581-0dfc-0fe1-808a8581e020/cache/activity.opr
```

You can delete .opera directory in your home folder to free up space, if you're done with opera.

> /home/ken/Downloads/opera_11.11.2109_amd64.deb
/var/cache/apt/archives/opera_11.61.1250-1linuxmint_i386.deb
/var/cache/apt/archives/opera_11.62.1347-1linuxmint_i386.deb

I'm confused here. You have a manual-downloaded Opera 64-bit in your downloads folder. But in your apt archives you have 2 version of a linuxmint 32-bit .debs.


Try;
```
dpkg -l \*opera\*
```

---

### Post by ken0069 on 2012-04-25
```
ken@bedroom ~ $ sudo dpkg -l \*opera\*
[sudo] password for ken: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  opera          <none>         (no description available)
ken@bedroom ~ $ 

```

I must have installed it manually then.  I think the x64 was downloaded by mistake.  When I went to remove it though it was in the Synaptics Package Manager section and showed that it was installed?  That is where I tried to uninstall from to begin with.  Now Synaptics shows it IS NOT installed but it is.

Thanks

---

### Post by Perfect Storm on 2012-04-25
What you install manually (eg. not a .deb or from the sourcelist) will not show up as installed packages.

Could it be that you have installed Opera as .deb and from a installer script?

> /usr/share/linuxmint/mintinstall/installed/opera-widget-manager.png
/usr/share/linuxmint/mintinstall/installed/opera.png
On a second thought (I have no idea when it comes to Linux Mint), but this made me think, if Mint have some sort manual installer script for Opera?

---

### Post by ken0069 on 2012-04-25
So if it's not listed in package manager, but is still installed, is there a chance that it could have gotten installed a SECOND time through Package Manager then?  Remember, I DID uninstall it from Package Manager.

On Windowz I can right click on the desktop icon and select properties and see where the executable and program is in the system.

So if it's installed manually, is there a chance it can be uninstalled via Terminal?  And if so, do you know what the code would be to do that??

Thanks

---

### Post by Perfect Storm on 2012-04-25
You can remove the file manually.

[quote]ken@bedroom ~ $ whereis opera
opera: /usr/bin/opera /usr/lib/opera /usr/share/opera /usr/share/man/man1/opera.1.gz[/code]

```
cd /usr/bin
sudo rm -rf opera
cd /usr/lib
sudo rm -rf opera
cd /usr/share
sudo rm -rf opera
cd /usr/share/man/man1
sudo rm -rf opera.1.gz
```

just be careful with the rm command. When executed the files can't be restored.

---

### Post by ken0069 on 2012-04-26
Thanks, I'll give that a try when I get time.

Ken

---

