---
title: "Installing Office 2003 in Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by whistlerspa on 2007-04-24
When trying to install Word, Powerpoint and Excel using Wine, the installation fails at the 
'writing system registry values' step. I managed to get it going with crossover office but paying for Linux software kind of defeats the object of using open source software in my book. 

My understanding is that CO is only customised Wine in any case. With CO install I did note that additional fonts were downloaded first - could this be relevant? 

Otherwise can anyone help point me in a solution or work around direction. I need Office 2003 for work purposes and don't want to dual boot..

---

### Post by Happy_Man on 2007-04-24
Try this howto:

[http://ubuntuforums.org/showthread.php?t=372011](http://ubuntuforums.org/showthread.php?t=372011)

---

### Post by TimelessRogue on 2007-04-24
While there may be a solution to your situation with Office 2003, this begs the question of why you don't accept and use OpenOffice, which it the built-in FREE office suite and which equals or surpasses most other office software?  You will have office software you don't have to pay for time and again as well as not having to use Wine to run an "outside" office suite ...

---

### Post by Sethalos on 2007-04-24
I'll just add this, I'm a new Ubuntu (or Linux for that matter) user and I installed WinXp via a VMware instance, and in that I added Office 2007.  However, I have yet to use it, I have used OpenOffice for everything so far. I find it as easy to use and hasn't crashed on me once.

Seth

P.s.  The reason for the VM'ing of XP is so that I don't have to dual boot, WinXp is needed for some custom work apps I'm required to use.

---

### Post by oilchangeguy on 2007-04-24
> **whistlerspa said:**
> When trying to install Word, Powerpoint and Excel using Wine, the installation fails at the 
'writing system registry values' step. I managed to get it going with crossover office but paying for Linux software kind of defeats the object of using open source software in my book. 

My understanding is that CO is only customised Wine in any case. With CO install I did note that additional fonts were downloaded first - could this be relevant? 

Otherwise can anyone help point me in a solution or work around direction. I need Office 2003 for work purposes and don't want to dual boot..

as far as open source software being free, there are many versions of linux which are not free. ubuntu as with most linux distros does not include the full open office suite. however go to [www.openoffice.org](www.openoffice.org) and download and install the full version. after learning a few new tricks (mostly so your office using friends can open and read an open office document) you'll find open office to be a very good office suite.

---

### Post by whistlerspa on 2007-04-24
Thanks guys but you're missing my point - i do use Open Office but my workplace requires the use of MS products. I need to edit and create documents in these programs. I would just like to be able to bring them home and edit or create new ones on my Linux boxes at home. I don't and don't want to use MS on my own computers.

---

### Post by kyphi on 2007-04-24
If Word must be used then your choices are:

1.  Crossover Linux
2.  VirtualBox, VMware etc
3.  Dual booting into WinXP (or whatever)

If you look at [http://winehq.com](http://winehq.com) you will see Codeweavers logo there too.  That Codeweavers asks for a very modest fee does not contradict "free software".  Read "free" as meaning freedom and liberty not free of charge.  Even programmers have to buy food so think of it as a donation to enable further development of "Wine".

Crossover to me means that I do not have to boot into XP as often as I used to.  With VirtualBox, running XP on Ubuntu I am almost ready to cut the cord.

---

### Post by whistlerspa on 2007-04-25
Right solved this by reading up on tips at wine hq. Both Office 97 and 2003  can be installed and run straight off the desktop just as they say (thanks guys). An update to the latest version from automatic updates may also have helped today.

The trick is (at least it proved so for me) to run regedit.exe from within Wine before attempting to run the appropriate Office setup.exe files from the CD disk within wine.

One can then set up appropriate launcher using e.g. for excel

env WINEPREFIX="/home/***/.wine" wine "C:\Program Files\Microsoft Office\Office11\EXCEL.EXE" 

for the Command and 

/home/***/.local/share/icons/b223_excel.0.xpm     for the appropriate icon. 

[Where *** is the name of your home directory] 

In my case Word 2003 proved slightly glitchy and wanted to run some setup files the first couple of launches but works OK now. Hopefully the software will continue to run.[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by bigal50 on 2007-04-25
> **whistlerspa said:**
> Thanks guys but you're missing my point - i do use Open Office but my workplace requires the use of MS products. I need to edit and create documents in these programs. I would just like to be able to bring them home and edit or create new ones on my Linux boxes at home. I don't and don't want to use MS on my own computers.

Until I retired I worked for a place that only used MS Office products.  I used Open Office since before version one and exchanged documents with others all the time. I changed my preferences so save the documents in Word, Excel Etc and all was fine. Most people that I worked with didn't even realize that I wasn't using MS Office. 

Allen

---

### Post by jaykothari on 2007-05-05
"We must be the change we wish to see in the world" This quote was said by Mahatma Gandhi if you were wondering.

---

### Post by fphsml on 2007-05-18
For me, the trouble is that MS Office actually has features that I use that Open Office does not have. Mainly grammar check and outlining. I installed an old copy of Office 97 successfully yesterday but could not get Office 2003 to install. It complained about registration key not being valid. Mine is a legitimate copy and it installed fine on my XP partition. Office 97 seems mostly adequate for now. Outlining works and I need it only when I am starting out with the document. I later move on to Open Office for editing it since I actually find its word completion useful. Grammar checker of Office 97 seemed less helpful when I tested it than 2003. But Open Office has none.

I wish Lyx has better editing features. Then I would not need any of these.

---

### Post by darell_m on 2007-05-27
I have successfully loaded MS 2003 running under wine but as I have fairly large excel files with macros I find I lose the macros in both open office and excel 2003 under wine. I failed with crossover as it kept saying i need a update version of windows. Any suggestions? PS My original files are in excel xp is that a problem as well?

Appreciate any advice.

---

### Post by schaefer on 2007-05-28
darell,

What you are going to need to do is go to Application->Crossover Office->Configuration. Click on the tab "Manage Bottles", then "Create new bottle". Select Windows 2000, click ok, and then select it and click "Make Default". You should then be able to install Office without any problems.

---

### Post by darell_m on 2007-05-28
> **schaefer said:**
> darell,

What you are going to need to do is go to Application->Crossover Office->Configuration. Click on the tab "Manage Bottles", then "Create new bottle". Select Windows 2000, click ok, and then select it and click "Make Default". You should then be able to install Office without any problems.

schaefer,:D
Thanks and I successfully loaded Office 2003 with crossover from your excellent advice. And it runs fine except still have corrupted VBA (checked source files in gmail on my XP computer and macros are fine). Anyway that is another problem, but with the advice Crossover worked a treat. Need to study crossover as cannot find the files in directories and would like desk icons but I'll need to study that some. Yup - I am a noob!

:confused:

---

