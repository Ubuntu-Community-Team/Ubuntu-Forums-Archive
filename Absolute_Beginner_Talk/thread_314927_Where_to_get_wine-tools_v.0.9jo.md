---
title: "Where to get wine-tools v.0.9jo?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Degeim on 2006-12-08
Hello!

I'm trying to use this [http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]("http://ubuntuforums.org/showthread.php?t=149585&highlight=wine")
guide to guide me through the installation of Wine, but since the download link to Wine-tools doesn't work, the rest of the guide is kinda hard to follow. I am able to find the 1.30-version of WT from sourceforge, but that one doesn't include many of the commands mentioned in the guide.

Google or Yahoo searches gives me nothing but broken links, so my last hope is that someone here may have the winetools-0.9jo-III.tar.gz-file for me.

Hope someone can help me!


Thanks, 
Degeim

---

### Post by deadgobby on 2006-12-08
Try DL Automatix and see if it all goes well for you. It will install Wine for you with out trying to build for source AKA tar ball.
[http://getautomatix.com/wiki/index.php?title=Main_Page](http://getautomatix.com/wiki/index.php?title=Main_Page)
Gobby

---

### Post by HawaiinShirts4Life on 2006-12-10
I noticed that the download for winetools is down as well and that there arn't any other sites (that i could find to download it) but have you looked at other programs like wine-doors [http://www.wine-doors.org/](http://www.wine-doors.org/) i think it should do what your looking for it to do
-HawaiinShirts4Life

---

### Post by HawaiinShirts4Life on 2006-12-11
also as of today winehq.com isnt working either i wonder why
-HawaiinShirts4Life

---

### Post by gargoyle on 2006-12-12
It seems Wine-Tool is still down. 
Dec 12, 2006

---

### Post by nkayesmith on 2006-12-18
I've mirrored the winetools 0.9jo targz at [download.formationos.net]("http://download.formationos.net"). Enjoy.

EDIT: The latest version of winetools at download.formationos.net has a slight modification in it by myself, in order to make winetools compatible with the most recent wine versions.

---

### Post by sylv3rblade on 2006-12-27
A million tnx for the mirror!

---

### Post by hyper_ch on 2006-12-28
Where does WT download the files to? It has problems fetching the mfc40.dll but I can download it manually... so I put it into the windows\system32 folder and restarted WT but it still tries to download it again.

---

### Post by nkayesmith on 2007-01-04
> **sjau said:**
> Where does WT download the files to? It has problems fetching the mfc40.dll but I can download it manually... so I put it into the windows\system32 folder and restarted WT but it still tries to download it again.

Can you tell me where you are getting mfc40.dll from? It seems the winetools source for mfc40.dll and mfc42.dll is permanently down...so I will write your mfc40 source into winetools.

---

### Post by nkayesmith on 2007-01-04
> **HawaiinShirts4Life said:**
> I noticed that the download for winetools is down as well and that there arn't any other sites (that i could find to download it) but have you looked at other programs like wine-doors [http://www.wine-doors.org/](http://www.wine-doors.org/) i think it should do what your looking for it to do
-HawaiinShirts4Life

Winedoors is not stable yet - but it looks promising.

---

### Post by bodhi.zazen on 2007-01-04
> **nkayesmith said:**
> Winedoors is not stable yet - but it looks promising.

LOL yes this is true, not only of Winedoors but also of wine itself :p

---

### Post by nkayesmith on 2007-01-04
> **bodhi.zazen said:**
> LOL yes this is true, not only of Winedoors but also of wine itself :p

:p - Good point there...However, I would not recommend Winedoors yet because 0.1 is not even finished.

---

### Post by dawhistler on 2007-01-04
Maybe this will help?


[http://download.formationos.net/](http://download.formationos.net/)

[http://www.dll-files.com/dllindex/pop.php?mfc40](http://www.dll-files.com/dllindex/pop.php?mfc40)

[http://www.dll-files.com/dllindex/pop.php?mfc42](http://www.dll-files.com/dllindex/pop.php?mfc42)


I just found this and wanted you to try it out.

good luck.

---

### Post by nkayesmith on 2007-01-04
> **dawhistler said:**
> Maybe this will help?


[http://download.formationos.net/](http://download.formationos.net/)


Download.formationos.net is my mirror! and that's where I'll be putting the modified version :)

Thanks for the links - unfortunately the mirror does not allow direct links, so I've decided to host mfc40 and 42 on my own site, where it can be fetched by winetools.

---

### Post by nkayesmith on 2007-01-04
Done! The new version is now at download.formationos.net. I've called it 0.9.4 :p

EDIT: Was a bit careless with that. I've just posted a new version - the previous one didn't know when the download was finished.

---

### Post by mastapat11 on 2007-01-11
Here's a working URL to the original:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by nkayesmith on 2007-01-11
> **mastapat11 said:**
> Here's a working URL to the original:
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

Ah, the original is back up again. The file hasn't changed though - the problems previously reported (version, mfc*.dll) will be there if you download from the original site.

---

### Post by B()X_BREAKER on 2007-01-18
I downloaded winetools from the main site witch was an openoffice.de server. After installing I ran wt and got an error saying 

winetools cannot run with a wine version older than 20050628...

But I have 0.9.29 release from 2007 :confused: ](*,)

---

### Post by nkayesmith on 2007-01-18
> **B()X_BREAKER said:**
> I downloaded winetools from the main site witch was an openoffice.de server. After installing I ran wt and got an error saying 

winetools cannot run with a wine version older than 20050628...

But I have 0.9.29 release from 2007 :confused: ](*,)

See [http://ubuntuforums.org/showthread.php?t=149585&page=43](http://ubuntuforums.org/showthread.php?t=149585&page=43)

---

### Post by B()X_BREAKER on 2007-01-18
:o  WOW that was fast! Thank you! I searched before I posted but was only looking for wintools. I have done  all this before and thought everything would go smooth as usual. Guess it's just my luck :rolleyes:

---

### Post by B()X_BREAKER on 2007-01-18
](*,)  This just isn't my day. Now I am getting an error installing dcom98 saying a newer version had been installed. Could this have been done already from automatix2 or when I ran winecfg before installing winetools?

---

### Post by hito1 on 2007-01-25
> **B()X_BREAKER said:**
> ](*,)  This just isn't my day. Now I am getting an error installing dcom98 saying a newer version had been installed. Could this have been done already from automatix2 or when I ran winecfg before installing winetools?
I had the same problem, I used automatix2 to install wine, but I didn't run winecfg before wt.

---

### Post by nkayesmith on 2007-01-25
> 
I had the same problem, I used automatix2 to install wine, but I didn't run winecfg before wt.


This is probably because of recent improvements to the latest wine versions, (probably) making dcom98 unnecessary. 

You can safely skip that step, ignore future warnings, and proceed.

---

