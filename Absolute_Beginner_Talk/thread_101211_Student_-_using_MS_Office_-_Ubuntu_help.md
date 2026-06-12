---
title: "Student - using MS Office - Ubuntu help"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by hobnobsandtea on 2005-12-09
I am a CompScience Student whos college uses soley Micro$oft products.
Anyhow, I have the lastest UBUNTU release on my laptop, and I am fed up having to read stuff in college or print it out to bring home due to Micro$oft not releasing a linux version of MS Office. 

Is there any way around it???

---

### Post by earobinson on 2005-12-09
open office will open .doc files, also you could save the .doc as .rtf and open office will do even better.

Also a really cool web app is [http://www.writely.com/](http://www.writely.com/) you can edit docs on line. Gmail also just lauched a doc reader (no write) if you emal a doc to your self you can read it as a web page.

Hope this helps

---

### Post by bored2k on 2005-12-09
What file formats? There is [OpenOffice]("http://www.openoffice.org/") which opens almost if not everything from the MS Office suite. Note: It comes preinstalled on any Ubuntu version out there.

To get the latest 2.0 final, you need this line in your sources.list:
```
sudo gedit /etc/apt/sources.list
``` and add:
```
deb http://people.ubuntu.com/~doko/OOo2 ./
```
Then
```
sudo apt-get update && sudo apt-get dist-upgrade -y --force-yes
```

---

### Post by esperantisto on 2005-12-09
I am an OOo user for quite long &#8212; from 1.0.1 to just installed 2.0.1 RC3 (all under Windows &#8212; now trying the water in Ubuntu). Unfortunately, despite of major improvements, compatibility with MS Word is not perfect. Most problematic are pictures and other OLE objects &#8212; they're very likely to be displaced. This is a problem both if you open in OOo documents created with MS Word and if you open in Word documents exported to .doc by OOo. There are some other issues like nested tables, spacing above/below paragraphs ets &#8212; if you're interested, browse [http://qa.openoffice.org]("http://qa.openoffice.org"). However, if you only need to read/print out documents **and** those graphics and other stuff are not critical (you agree to manually set them to place, if necessary) &#8212; OOo is OK. I'd advise only to donwload and install OOo2 final &#8212; Breezy Badger includes some RC, AFAIK. I'd also point out that if you need your documents look exactly as in Word, you'll have to install in your system respective fonts: Linux counterparts of Windows fonts (say, Times compared to Times New Roman) have slightly (and sometimes not slightly) different metrics.

---

### Post by earobinson on 2005-12-09
you could also try staroffice not sure if this is better as i have never used it

---

### Post by bored2k on 2005-12-09
Star Office is not free. OOo is pretty much the same.

---

### Post by earobinson on 2005-12-09
oops, sorry about that, Guess I learned something :)

---

### Post by patrick295767 on 2005-12-09
[QUOTE=hobnobsandtea]I am a CompScience Student whos college uses soley Micro$oft products.
Anyhow, I have the lastest UBUNTU release on my laptop, and I am fed up having to read stuff in college or print it out to bring home due to Micro$oft not releasing a linux version of MS Office. 

Is there any way around it???[/QUOTE]
  
I was also in your case when I was student... I had, and loved Crossover Weager, that enabled me to use the standard microsoft programs (real program of microsoft into Linux box) ...like office winword, powerpoint ... (wine prg disciple)
'cos the problem of the openoffice is that it's very very crap for any files coming from the windows world ... there is always one or thousand bugs, ... and you know teachers and friends won't accept mistakes in their reports !! That's your carreer & future that's is menaced !
I adopted this solution ... 

Let us know your progresses !!
  
Kind regards, greetz'
  
Pat'

---

### Post by Brunellus on 2005-12-09
[QUOTE=hobnobsandtea]I am a CompScience Student whos college uses soley Micro$oft products.
Anyhow, I have the lastest UBUNTU release on my laptop, and I am fed up having to read stuff in college or print it out to bring home due to Micro$oft not releasing a linux version of MS Office. 

Is there any way around it???[/QUOTE]
Yes.  Use OpenOffice to open and read MS Office documents.  Compatibility is pretty good.

---

### Post by earobinson on 2005-12-10
[QUOTE=Brunellus]Yes.  Use OpenOffice to open and read MS Office documents.  Compatibility is pretty good.[/QUOTE]
Unless there are images or long docs or anything out of the norm

---

### Post by benk on 2005-12-10
hobnobsandtea:

You should try to lobby your profs to either convert completely to OO.org or to convert their documents into .pdf files. Quite frankly I find that OpenOffice is pathetic for the things that I need it for (opening Word files with embeded graphics and equations).

It surprises me that a Computer Science Department isn't more with it (not just at your university I'm sure)...why would any academic institution force their students to use Microsoft Office when they could easily be using a free alternative? Most of the profs at my university offer only .pdf files so compatibility issues are not a problem at my university.

If you can't convince your profs to convert the files into .pdf files, then I think the only thing left to do is to use crossover office.

---

### Post by Rackerz on 2005-12-10
I use Crossover Office, it's the only solution for me if i need to use docs from Windows.

---

### Post by thinhlegolas on 2005-12-10
[QUOTE=benk] Most of the profs at my university offer only .pdf files so compatibility issues are not a problem at my university.
[/QUOTE]

Yep, just convert to pdf and use Acrobat Reader to open it :)

---

### Post by patrick295767 on 2005-12-13
[QUOTE=Brunellus]Yes.  Use OpenOffice to open and read MS Office documents.  Compatibility is pretty good.[/QUOTE]
  
For people workign with big reports (doc) and very specific applications crossreferences / images / drawings, there is always sthg wrong. For a student, it's really hell. Portability between microsoft office-openoffice is really crap, and getting into troubles most of time... 
 
I experienced thsi and got only troubles ...
For students, please use crossover weager  (not so much expencive prg)
  
Good Luck !

Pat'

---

### Post by nocturn on 2005-12-13
[QUOTE=esperantisto]I am an OOo user for quite long — from 1.0.1 to just installed 2.0.1 RC3 (all under Windows — now trying the water in Ubuntu). Unfortunately, despite of major improvements, compatibility with MS Word is not perfect. Most problematic are pictures and other OLE objects — they're very likely to be displaced. 
[/quote]

To be fair, yes this is true.  

Unfortunately, it is also true when opening a word97 doc in office XP, or even worse, a Word 6 document...  
Saving to older MS office versions has never worked well for me in MS Office either.

OpenOffice at least handles it's own older formats quite well.

---

### Post by Wes24 on 2005-12-13
What about AbiWord? I 'm using it for a few days now and it feels good. It surely is a lot more responsive then oOo and looks better imho. Don't know about compatibility with MSOffice though.

---

### Post by nocturn on 2005-12-13
[QUOTE=Wes24]What about AbiWord? I 'm using it for a few days now and it feels good. It surely is a lot more responsive then oOo and looks better imho. Don't know about compatibility with MSOffice though.[/QUOTE]

Abi is nice, but has its limitations too.

MS Office support is worse then in OO
Abi has a hard time with large files (100+ pages).

---

### Post by sonny on 2005-12-13
[QUOTE=bored2k]Star Office is not free. OOo is pretty much the same.[/QUOTE]
StarOffice can be free, I downloaded version 5 from their website, you just have to sign as a poor student that don't have money to buy you lunch, or something like that, and they will say, ok poor little child come on download it for free.

---

### Post by Lord Illidan on 2005-12-13
Is RTF support good in Open Office? Cos` you could use them instead. 
Also, another question related to this. Does Wine handle Office 2003 well?

---

### Post by nocturn on 2005-12-13
[QUOTE=sonny]StarOffice can be free, I downloaded version 5 from their website, you just have to sign as a poor student that don't have money to buy you lunch, or something like that, and they will say, ok poor little child come on download it for free.[/QUOTE]

StarOffice 5 is quite old...  OpenOffice is free, so why not use that?

---

### Post by patrick295767 on 2005-12-13
[QUOTE=nocturn]StarOffice 5 is quite old...  OpenOffice is free, so why not use that?[/QUOTE]

'cos fake compatibility with regular windows microsoft office

greetz

---

### Post by sonny on 2005-12-13
[QUOTE=nocturn]StarOffice 5 is quite old...  OpenOffice is free, so why not use that?[/QUOTE]
I prefer open office, I was just pointing that staroffice can be free, and I'm pretty sure that you can still cheat them with the poor student license. ;) 

By the way, OO DOES have some incompatibility problems, as pointed earlier, with graphics, equations, and ole objects, in the spreadsheet if you have some "advance" formulas or you manage scenarios in Excel those might not perform as well in OO. But as an alternative you can live with it and not missing at all Excel. Also I've heard that StarOffice has better compatibility with MS-Office.

---

### Post by M3ta7h3ad on 2005-12-13
I too have had the delight of experiencing "OO.org compatibility with MS Office".

273 worksheet spreadsheet, ordered using coloured tabs to signify the current progress of each one. Loaded into openoffice one desperate evening as my windows install was naffed up.

273 Worksheets.. with zero coloured tabs... the complete file had been erased of coloured tab data. AAAAAARRRGGGHHHH!!!!! basically a years worth of work completely naffed up due to Open Office and my lack of consideration for its "compatibility".

Its about as compatible as oil and water, yeah.. you can fill a glass with both, one works as a refreshing drink, the other.. would probably kill you.

Crossover office or WINE (for the freebie!) is the only real way forward.

---

### Post by mistergq on 2005-12-13
Crossover Office is your best choice as you will be able to run Word, Powerpoint, and Excel in Linux.  I am not sure about Access.  Good luck and let us know how it goes.

---

### Post by hobnobsandtea on 2005-12-14
thanks for all replies, most helpful and educating ... will give crossover a shot,

---

### Post by jeremy on 2005-12-14
[QUOTE=M3ta7h3ad]273 worksheet spreadsheet, ordered using coloured tabs to signify the current progress of each one. Loaded into openoffice one desperate evening as my windows install was naffed up.[/QUOTE]
The moral to this tale is ALWAYS make sure you have a backup!

---

