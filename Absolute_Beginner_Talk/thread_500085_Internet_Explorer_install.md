---
title: "Internet Explorer install"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by ye103910 on 2007-07-13
Help!  I've tried to install Internet Explorer 6 through various means including Wine (and Wine-Doors) but have managed to get nowhere so far.  The closest I've got to success I've copied below:

ye103910@ye103910-ubuntu:~$ wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
--16:57:48--  [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
           => `ies4linux-latest.tar.gz.1'
Resolving [www.tatanka.com.br](www.tatanka.com.br)... 208.97.138.133
Connecting to www.tatanka.com.br|208.97.138.133|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 340,006 (332K) [application/x-gzip]

100%[====================================>] 340,006      150.45K/s             

16:57:51 (149.98 KB/s) - `ies4linux-latest.tar.gz.1' saved [340006/340006]
ye103910@ye103910-ubuntu:~$ tar zvxf ies4linux-latest.tar.gz
ies4linux-2.0.5/
ies4linux-2.0.5/lib/
ies4linux-2.0.5/lib/messages.sh
ies4linux-2.0.5/lib/flash.sh
ies4linux-2.0.5/lib/install.sh
ies4linux-2.0.5/lib/download.sh
ies4linux-2.0.5/lib/ies4linux.svg
ies4linux-2.0.5/lib/ui.sh
ies4linux-2.0.5/lib/functions.sh
ies4linux-2.0.5/lib/terminal.sh
ies4linux-2.0.5/winereg/
ies4linux-2.0.5/winereg/ie55.reg
ies4linux-2.0.5/winereg/ie6.reg
ies4linux-2.0.5/winereg/homepage.reg
ies4linux-2.0.5/winereg/.ie1.reg
ies4linux-2.0.5/winereg/ie5.reg
ies4linux-2.0.5/winereg/.ie2.reg
ies4linux-2.0.5/ui/
ies4linux-2.0.5/ui/ies4linux.py
ies4linux-2.0.5/ui/gtkgui.py
ies4linux-2.0.5/lang/
ies4linux-2.0.5/lang/csCZ.sh
ies4linux-2.0.5/lang/ptBR.sh
ies4linux-2.0.5/lang/enUS.sh
ies4linux-2.0.5/lang/nlNL.sh
ies4linux-2.0.5/lang/heIL.sh
ies4linux-2.0.5/lang/itIT.sh
ies4linux-2.0.5/lang/frFR.sh
ies4linux-2.0.5/lang/ruRU.sh
ies4linux-2.0.5/lang/trTR.sh
ies4linux-2.0.5/lang/jaJP.sh
ies4linux-2.0.5/lang/nbNO.sh
ies4linux-2.0.5/lang/zhTW.sh
ies4linux-2.0.5/lang/huHU.sh
ies4linux-2.0.5/lang/plPL.sh
ies4linux-2.0.5/lang/daDK.sh
ies4linux-2.0.5/lang/esAR.sh
ies4linux-2.0.5/lang/deDE.sh
ies4linux-2.0.5/lang/bgBG.sh
ies4linux-2.0.5/lang/zhCN.sh
ies4linux-2.0.5/lang/skSK.sh
ies4linux-2.0.5/lang/slSI.sh
ies4linux-2.0.5/lang/svSE.sh
ies4linux-2.0.5/lang/roRO.sh
ies4linux-2.0.5/lang/ltLT.sh
ies4linux-2.0.5/lang/etET.sh
ies4linux-2.0.5/lang/esES.sh
ies4linux-2.0.5/lang/caES.sh
ies4linux-2.0.5/lang/esMX.sh
ies4linux-2.0.5/lang/fiFI.sh
ies4linux-2.0.5/lang/eoXX.sh
ies4linux-2.0.5/lang/siSI.sh
ies4linux-2.0.5/lang/srYU.sh
ies4linux-2.0.5/lang/idID.sh
ies4linux-2.0.5/lang/lvLV.sh
ies4linux-2.0.5/lang/msMY.sh
ies4linux-2.0.5/LICENSE
ies4linux-2.0.5/README
ies4linux-2.0.5/ies4linux
ye103910@ye103910-ubuntu:~$ cd ies4linux-2.0.5/
ye103910@ye103910-ubuntu:~/ies4linux-2.0.5$ ./ies4linux
Welcome, ye103910! I'm IEs4Linux.
I can install IE 6, 5.5 and 5.0 for you easily and quickly.
You are just four 'enter's away from your IEs.

I'll ask you some questions now. Just answer y or n (default answer is the bold one)

IE 6 will be installed automatically.
Do you want to install IE 5.5 SP2 too? [ y / n ] y

And do you want to install IE 5.01 SP2? [ y / n ] y

IEs can be installed using one of the following locales:
EN-US PT-BR DE FR ES IT NL SV JA KO NO
DA CN TW FI PL HU AR HE CS PT RU EL TR
Default is EN-US. Hit enter to keep it or choose a different one:


By default, I will install everything at /home/ye103910/.ies4linux
I will also install Flash 9 plugin and create Desktop shortcuts.
Is that ok for you? (To configure advanced options type n) [ y / n ] y

All right! Let's start the installations...

Downloading everything we need
  DCOM98.EXE
--16:58:42--  [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
           => `/home/ye103910/.ies4linux/downloads/DCOM98.EXE'
Resolving download.microsoft.com... 1.0.0.0
Connecting to download.microsoft.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

When trying Wine-Doors, the window goes grey and stays like that forever (well it seems like forever) so I have to do a Force Quit on it.

Any ideas anyone?

Thanks

---

### Post by cogadh on 2007-07-13
My only advice, don't install it. From the Wine official FAQ:
> **How do I install Internet Explorer in Wine?**
In short; you don't. Trying to install IE in Wine will more than likely break things due to the components and registry entries that it installs. If you need to install applications in Wine that require Internet Explorer then you install Wine's IE replacement which consists of two parts.

First you install the Gecko IE engine replacement by running the following in the terminal; wine iexplore [http://www.winehq.org](http://www.winehq.org)

The second part is installing the registry entries to fool programs; Go to [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) scroll down to HKEY_LOCAL_MACHINE and then add the "Internet Explorer" keys using regedit.

---

### Post by ye103910 on 2007-07-13
Ahh, that makes more sense - thanks for pointing that out.  However, when I run "wine iexplore" I do get a window pop open with the title bar reading "Wine Internet Explorer" but the content of the window is completely blank.  Is this correct?

Thanks!

---

### Post by Nussbaum on 2007-07-13
I don't know what the OP wants to do with IE. If its to test websites wouldn't it mean having IE usethe gecko engine that it displays webpages the same way as firefox does? Also you use iets4linux, it might not be the same thing the people of wine are talking about(i assume they mean installing with only wine and not use that prog). On the other hand maybe they are ofcourse.

Anyway your problem looks more like a connection problem to me, though im no expert.

---

### Post by Rui Pais on 2007-07-13
Hi,
i always had some problem when i tried to install ie4linux...
Usually i get better results with winetools.
[Here the link]("http://www.von-thadden.de/Joachim/WineTools/"), if you want to check it.
It install ie (and all need by ie) and some other Windows apps.

About your issue...
> **ye103910 said:**
> ...
Downloading everything we need
  DCOM98.EXE
--16:58:42--  [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
           => `/home/ye103910/.ies4linux/downloads/DCOM98.EXE'
Resolving download.microsoft.com... 1.0.0.0
Connecting to download.microsoft.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

Windows (and probabily emulators) deal with DNS in different ways then Linux... that look like the ie installer tries to download DCOM83.EXE but fail to resolve the address (thats why the 1.0.0.0...)

you may want to add/replace your DNS IPs to /etc/resolv.conf if that fail only contains the IP of  your gateway...

or you can manually download the DCOM98.EXE to your /home/ye103910/.ies4linux/downloads/ and restart the installation. Assuming installer is intelligent enough to detect the already downloaded file (that some times MS apps don't do it :shock: ...)

---

### Post by cogadh on 2007-07-13
**Nussbaum**, some Windows programs check for the presence of Internet Explorer before they will allow the install to continue. Installing the Gecko engine and making those registry edits avoids that problem.

**Rui Pais**, WineTools hasn't been updated in two years, is it still a valid Wine management application? In fact, I think they removed it from the Ubuntu repositories because it is no longer maintained.

> **ye103910 said:**
> Ahh, that makes more sense - thanks for pointing that out.  However, when I run "wine iexplore" I do get a window pop open with the title bar reading "Wine Internet Explorer" but the content of the window is completely blank.  Is this correct?

Thanks!
It should be a blank page, but you should also get a prompt to install the Gecko engine. After the engine is downloaded and installed, the page will display normally. Since you already tried installing IE, there may be a problem with installing Gecko. Try running "uninstaller" in a terminal and removing Internet Explorer. If that doesn't fix the problem, you can alway delete and recreate your .wine directory. That will erase everything you have already done with Wine, though.

---

### Post by wormser on 2007-07-13
I installed it with this [guide]("http://www.psychocats.net/ubuntu/ies4linux").

---

### Post by qamelian on 2007-07-13
All that went wrong is that your connection to download Dcom98 timed out. Try re-running the script for ies4linux again. I needed to do this 4 or 5 times before it successfully downloaded.

---

### Post by Rui Pais on 2007-07-13
> **cogadh said:**
> 
**Rui Pais**, WineTools hasn't been updated in two years, is it still a valid Wine management application? In fact, I think they removed it from the Ubuntu repositories because it is no longer maintained.
hi,( i didn't saw you question to me till gamelian post...)
Yes i think winetools is not maintained or its development its stopped for a long... but as long as installs, its just a tar.gz with a bunch of scripts... the purpose is to use it to install ie5 or 6, that is identically old and not developed anymore :lol:

But i confess the last time i use it was on edgy (luckily i don't need it lately), so maybe it will not work with wine version on Feisty. 
It was just a tip for the case ie4linux keep failing.

> **qamelian said:**
> All that went wrong is that your connection to download Dcom98 timed out. Try re-running the script for ies4linux again. I needed to do this 4 or 5 times before it successfully downloaded.

Don't know if it's thats simple... it says "Connecting to download.microsoft.com|1.0.0.0|:80... failed". 10.0.0.0 is not a public IP and is usually what you get when DNS fail to resolve external addresses. But maybe the error massage it's not accurate...

---

### Post by qamelian on 2007-07-13
> **Rui Pais said:**
> Don't know if it's thats simple... it says "Connecting to download.microsoft.com|1.0.0.0|:80... failed". 10.0.0.0 is not a public IP and is usually what you get when DNS fail to resolve external addresses. But maybe the error massage it's not accurate...

All I know is that I had the exact same thing happen including the same error message and I resolved it by retrying several times. Eventually, the address resolved correctly and I was able to complete the download.

---

### Post by kittyhawk63 on 2007-07-13
> **wormser said:**
> I installed it with this [guide]("http://www.psychocats.net/ubuntu/ies4linux").

Wormser,
Thanks for the link. The instructions are simple and the install was successful. This guide will install IE6 although it is called ies4linux. You will have a choice during installation to choose if you also want to install IE5.5/IE5. 

Thanks Wormser. You came through again.
kh

---

### Post by amadeus266 on 2007-07-13
I posted this in another thread but didn't get a response yet so I figured I'd try here.


I tired both the instructions on ies4linux site and those on aysiu's site and both end the same way for me. The installer starts up, downloads the files, states that it is installing, then terminal window vanishes. No Install!
I have wine 0.9.33 and cabextract installed. Running Feisty.

---

### Post by kittyhawk63 on 2007-07-14
> **amadeus266 said:**
> I posted this in another thread but didn't get a response yet so I figured I'd try here.
 I tired both the instructions on ies4linux site and those on aysiu's site and both end the same way for me. The installer starts up, downloads the files, states that it is installing, then terminal window vanishes. No Install!
I have wine 0.9.33 and cabextract installed. Running Feisty.

Amadeus, try Wormser's link. I had absolutely no problem installing IE. The instructions are really clear "if" you take your time, understand what is being said, and then doing it. The best to you. Hope you're successful.
kh

---

### Post by tei on 2007-07-14
try this, it work for me

1) download files manually

[http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
[http://activex.microsoft.com/controls/vc/mfc40.cab](http://activex.microsoft.com/controls/vc/mfc40.cab)
[http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe](http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe)

and move them into "/home/<your name>/.ies4linux/downloads/"

[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ADVAUTH.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ADVAUTH.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/CRLUPD.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/CRLUPD.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTCORE.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTCORE.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTSUP.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/FONTSUP.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/HHUPD.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/HHUPD.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IEDOM.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IEDOM.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_EXTRA.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_EXTRA.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S1.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S1.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S2.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S2.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S3.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S3.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S4.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S4.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S5.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S5.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S6.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IE_S6.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SCR56EN.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SCR56EN.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SETUPW95.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/SETUPW95.CAB)
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/VGX.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/VGX.CAB)

and move them into "/home/<your name>/.ies4linux/downloads/ie6/EN-US/"

2) create file name "files" in "/home/<your name>/.ies4linux/downloads/" with this

> DCOM98.EXE
mfc40.cab
249973USA8.exe
/ie6/EN-US/ADVAUTH.CAB
/ie6/EN-US/CRLUPD.CAB
/ie6/EN-US/HHUPD.CAB
/ie6/EN-US/IEDOM.CAB
/ie6/EN-US/IE_EXTRA.CAB
/ie6/EN-US/IE_S1.CAB
/ie6/EN-US/IE_S2.CAB
/ie6/EN-US/IE_S5.CAB
/ie6/EN-US/IE_S4.CAB
/ie6/EN-US/IE_S3.CAB
/ie6/EN-US/IE_S6.CAB
/ie6/EN-US/SCR56EN.CAB
/ie6/EN-US/SETUPW95.CAB
/ie6/EN-US/FONTCORE.CAB
/ie6/EN-US/FONTSUP.CAB
/ie6/EN-US/VGX.CAB


3) install it again!!! ^^

hope this help ^^

ps. sorry for my poor eng :p

---

### Post by amadeus266 on 2007-07-15
O.K. It worked on this computer this time. But using the same instructions on my computer at work stopped at setting up wine links (or something like that, it's been 2 days since I tried.) thanks.

---

### Post by f1uxam on 2007-07-17
Don't allow update checker to install Wine 0.9.41 -- the URL entry bar in IE6 will go dead, showing only an "h".  Wine version 0.9.40 works fine.
And the #1 reason to have ie4linux is that one can have ActiveX apps work.  I have an HE-AAC streaming music player working just fine (though it complains of not finding DirectSound output).

---

### Post by DougieFresh4U on 2007-07-25
If you go to** Ubuntu CE**, then go to there** Popular Packages** page, there is a download for **IE4 installer. **
It will add **IE4 Installer** to your** Applications>Internet** and once you click that, it will install **IE6  AND put launcher under Applications>Internet.**
Worked great for me and was so simple and quick. 
Great work to the person who created that, ThanksIE6  AND put launcher under Applications>Internet.

---

### Post by philinux on 2007-09-17
> **ye103910 said:**
> Ahh, that makes more sense - thanks for pointing that out.  However, when I run "wine iexplore" I do get a window pop open with the title bar reading "Wine Internet Explorer" but the content of the window is completely blank.  Is this correct?

Thanks!

You have to use wine iexplore [http://webaddress](http://webaddress) it will then display the web site!

---

### Post by eleybourn on 2007-10-09
If you have the problem resolving download.microsoft.com you can always force it in your hosts file. 

```

> nslookup download.microsoft.com
...
Address: 210.9.72.167
...

```
```

> sudo nano /etc/hosts
...
210.9.72.167   download.microsoft.com
(save and quit - ^O ^X)

```
and it should work. You can remove the line once the download is complete. And ie4linux is excellent for webdevelopers testing cross platform, so the gecko solution is not valid for my situation. :-)

---

