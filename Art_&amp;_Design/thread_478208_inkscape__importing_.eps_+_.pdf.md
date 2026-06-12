---
title: "inkscape // importing .eps + .pdf"
date: 2007-06-19
forum: Art &amp; Design
---

### Post by jaskah on 2007-06-19
hello
i cannot import .eps or .pdf files into inkscape. do i need to install an extension for this?
any help greatly appreciated.
jason

---

### Post by silbar on 2007-06-20
My similar query got a response (from Kayosii) to install pstoedit, to convert (on the command line) somefilename.eps to somefilename.svg.  This SVG  file can then be opened in Inkscape.

HOWEVER, in my case, all I wanted to do was to add some axis labels to some EPS graphs created by another app.  I did not find this in any way easy to do (unlike AI).  For one thing, all the numerals on my axes were converted from a Times-like font to Helvetica. Also, the text tool seemed to want to create any new text in a huge way -- in a 10080 point font size!  You _can_ change this back to, say, 14 pt in the text tool window, but it is a pain to have to do this every time, even though you may have thought you had set the default font and size earlier.  (Am I missing something here.)  Also, the "Apply" button is not always highlighted, but you can get it active by switching font (say from Roman to Italic and back again).  And, finally, it isn't clear to me that I was ever able to save the SVG file in a way that could be successfully printed.

So, for me -- at least so far -- Inkscape is NOT A SOLUTION.  

I have also tried (and succeeded in) importing the EPS file into the GIMP (which I do like) but this loses the nice features of vector graphics.  

Another possibility that occurred to me was to see if I could import the EPS files into XFig.  Unfortunately, it seems that XFig, at least on this Ubuntu, DOESN'T import EPS, even though the HTML manual says it should.  (Apparently some XFig users on Windows can do so.)  And, I have not yet found a way to convert an EPS file into a *.fig file, which XFig can, of course, read.

Any help out there?  Or, some other app that can allow the editing of EPS?

---

### Post by silbar on 2007-06-20
Aha!  I've found out how to convert EPS into XFig from

[http://www.theorie.physik.uni-muenchen.de/lsvondelft/files/HowTo/epsinxfig.pdf](http://www.theorie.physik.uni-muenchen.de/lsvondelft/files/HowTo/epsinxfig.pdf)

which involves pstoedit using

pstoedit -f fig -psarg "-r600x600" myfilename.eps myfilename.fig

on the command line.  Thereafter, XFig can be used to work on the latter file and then the end result can be exported back to EPS (which we want for use in LaTeX) as mynewfilename.eps.

---

### Post by jaskah on 2007-06-20
thanks for your reply. 
i will keep looking, as this workaround seems really complicated...

---

### Post by AZzKikR on 2007-06-21
Xara Xtreme (open source on Linux) can import EPS and AI's. I think it can then export it to SVG. But perhaps some commandline tool is better for the conversion but I do not know one at this time. I am looking for one myself, too.

---

### Post by jaskah on 2007-06-21
thanks for your help!
i will have to give this a try.

---

### Post by marcabru on 2007-10-02
The Inkscape manual says, that "Besides SVG, Inkscape can import and export several other formats (EPS, PNG)." It is only the Ubuntu version that cannot do this? In that case, should i recompile Inkscape from sources?

It would be good to import EPS without further external conversion.

---

### Post by marcabru on 2007-10-02
"Requires pstoedit  and Skencil  to be installed."
So I did:
```
apt-get install skencil pstoedit
```
And tried again. Still no results, because:
```
xxx@xxx:~$ skencil
Segmentation fault (core dumped)
xxx@xxx:~$ 
```

---

### Post by kayosiii on 2007-10-04
PDF import for Inkscape was a Summer Of Code project that was completed this year - expect to see it as an option in the next version of Inkscape.

---

### Post by cemelmaci on 2007-11-15
hi

for Skencil SVN

sudo apt-get remove skencil

sudo apt-get install python2.4-dev python2.4 python-imaging  tcl8.4-dev tk8.4-dev

svn checkout [https://scm.wald.intevation.org/svn/skencil/skencil/branches/skencil-0.6](https://scm.wald.intevation.org/svn/skencil/skencil/branches/skencil-0.6)

cd skencil-0.6

/usr/bin/python2.4 setup.py configure

/usr/bin/python2.4 setup.py build

sudo /usr/bin/python2.4 setup.py install


Cheers,

Cem

---

### Post by Spin Doctor on 2008-04-11
I was trying to import .eps files into inkscape with no luck with its vanilla install. I then installed the following packages: imagemagick, pstoedit

And I can import .eps-files and .pdf-files, directy into inkscape.

---

### Post by kenjiru on 2008-04-27
It also solved my problem!

You can also convert .eps files to .svg using pstoedit [http://www.pstoedit.net](http://www.pstoedit.net) (needs GhostScript).

Here is the command:
```

pstoedit -f plot-svg my.eps my.svg

```

---

### Post by graben3 on 2008-05-08
I confirm this problem.

I have v 0.46 installed
Using Ubuntu Hardy 8.04

Out of the box inkscape did not open .eps files.

I did the following to make it open :

Go into synaptic.

Search for these packages and install them. Also install similar packages (I wanted it to work for sure !)

perlmagick
imagemagick
sketch
libwmf-bin
dia
pstoedit

(Not all these packages are necessary but I prefer to tell what I did to make it work so you can reproduce the same thing)

Then if you have troubles opening EPS files containing letters that have a hole in them, just see this :

[https://bugs.launchpad.net/inkscape/+bug/168448](https://bugs.launchpad.net/inkscape/+bug/168448)

Open this file :
/usr/share/inkscape/extensions/eps_input.inx

Where it is written this :
pstoedit -f plot-svg

replace it by this :
pstoedit -f plot-svg -mergetext -ssp

This fix the holes problems and some text being in separate letters so difficult to edit.

See the attached files. For me all letters like A, O, e, p, etc.. where not showing the hole in them. The -ssp & -mergetext fixed this in eps files.

Hope this works for you

---

### Post by graben3 on 2008-05-08
I confirm this problem.

I have v 0.46 installed
Using Ubuntu Hardy 8.04

Out of the box inkscape did not open .eps files.

I did the following to make it open :

Go into synaptic.

Search for these packages and install them. Also install similar packages (I wanted it to work for sure !)

perlmagick
imagemagick
sketch
libwmf-bin
dia
pstoedit

(Not all these packages are necessary but I prefer to tell what I did to make it work so you can reproduce the same thing

Then if you have troubles opening EPS files containing letters that have a hole in them (like a e o p q b , ...), just see this :

[https://bugs.launchpad.net/inkscape/+bug/168448](https://bugs.launchpad.net/inkscape/+bug/168448)

Open this file :
/usr/share/inkscape/extensions/eps_input.inx

Where it is written this :
pstoedit -f plot-svg

replace it by this :
pstoedit -f plot-svg -mergetext -ssp

This fix the holes problems and some text being in separate letters so difficult to edit.

Hope this works for you

---

### Post by sancho panza on 2008-05-27
Spin doctors tips worked. Thanks!

---

### Post by trondhuso on 2008-08-20
I have tried to open up a eps-file, but it didn't load correctly.

I get a message saying: 
Inkscape has received additional data from the script executed.  The script did not return an error, but this may indicate the results will not be as expected.

pstoedit: version 3.45 / DLL interface 108 (build Feb 28 2008 - release build - g++ 4.2.3 (Ubuntu 4.2.3-2ubuntu1)) : Copyright (C) 1993 - 2007 Wolfgang Glunz

I'll file a bug report for it.

-t-

---

### Post by engine on 2008-09-13
This looks like a thread where knowledgeable people hang out! and seems to cover issues with pstoedit and svg, so here's my questions: I want to use pstoedit to make svg from ps, and I've hit two problems.
```
- pstoedit -f plot_svg noyon.ps noyon.svg
```
tells me
```
Unsupported output format plot_svg
```
and then throws up a couple of screens of help including
```
plot-svg:               .svg:   svg  via GNU libplot    (/usr/lib/pstoedit/libp2edrvlplot.so)
This driver supports the following additional options: (specify using -f "format:-option1 -option2")
[          plotformat    : string        : plotutil format to generate]
```

Question 1. If I need /usr/lib/pstoedit/libp2edrvlplot.so, where do I get it from (and why isn't it in the pstoedit package)

Question 2. What is the format for the command? -f "format:-option1 -option2" doesn't work for me

Thanks in advance for any help!

---

### Post by liyanricaoqiyue1314 on 2008-09-15
To the married-Niu.      If that is not a Jiangsu-door furniture carpenter, Mei Niu doomed to marry a village of pottery Bozi wife. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Bozi home village of Tao Tao willing to spend with her sister-Niu for the pro-Gege Mei-yun.      Peach blossom in full bloom one day. - Niu made a home in Jiangsu's Wang is said to be a carpenter, he is to help fight-Niu furniture for the dowry. [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Wang linked to 20, a carpenter, keep-the first, Meiqingmuxiu, Douren favorite. [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Niu Mei Mei Nanzi never seen this, just Piaoyi Yan echocardiography have the feeling, but also face slightly Fatang.      Fortunately, not being the King is busy working carpenter found. [Runescape quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)     At this time, coincides with Nongmang season. Meiyun to Lane busy farm work, cooking at home-Niu hospitality Wang carpenter.      Wang carpenter while living doing carpentry, with the side-Niu chat.      Wang Mei Niu carpenter asked a lot of problems. [AOC Power Leveling](http://www.aoc-power-leveling.org)     Wang Mei Niu was a carpenter asked Mianhongerchi,. Thanks to Wang carpenter only pay attention to work and do not pay attention to observe.      Niu and Wang Mei carpenter contact Shijianyichang, bolder gradually larger. One day, she assured Wang carpenter questions:      "You have mountains there?? "      "We are the Great Plains there," says Wang carpenter replied, "do not see Hill. Tianba are all big."      "You have Baogu family, Yang Yu eat?? "Wang Mei Niu asked carpenter.      "We have Baogu home, not Yang Yu, but we do not eat Baogu." Wang-work carpenter Bianyue, "that is used to feed the finishing pigs."      "That is what you eat? "Mei Niu continue to ask.      "We eat rice," Wang carpenter said, "so throughout the year."      "Rice Gouchi?? "Mei Niu asked.      "Gouchi year of 2003 miles." Wang carpenter said, "every year sold several tons of surplus grain."       - Niu did not know "several tons of surplus grain" is the span mean, it inconvenient to ask for fear their Mochu Xi Wang carpenter laugh. [Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Day night, thinking about the day-Niu Wang carpenter, then a sleepless night.       Three days later, Wang Mei Niu carpenter Datan to the marriage, on the sorry for her, advised her out of the poor mountain valley, the mountains to. [Buy Aoc Power Leveling](http://www.aoc-power-leveling.org)      "To the mountains, to Gansha? "Niu-inexplicably asked.       "When my daughter-in-law ah? "Wang Xiaoxiao carpenter surreptitious manner.       Niu Mei Zhang De Crimson's face, quickly turned back to thatched houses, heart kept jumping. [Buy Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Wang left carpenter tools, catch up with the entrance of housing.       "Really." Wang carpenter Mangshuo, "You beautiful, I love you, really like you!"       "You Bieluan said." Mei Wu Zhuolian Niu said, "I would not agree to the Columbia." [Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      "He did not take advantage of the home," Wang said Niu carpenter-advised, "Do you think escape."       "Does not work." Mei Niu shaking his head said, "I have miles to the brother-for-daughter-in-law, brother can not be left regardless." [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)      "My hands of the rich." Wang carpenter serious, "your brother to stay 5,000 yuan, he casually enough to marry the daughter-in-law." [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)      Niu Dian Ledian-head. [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      Wang entered the house carpenter, cling-Niu, a while Kuangwen. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      - Niu homeopathy fell on the bed&#21398; [Runescape GP](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      The next day at dusk. Meiyunganwan farm work at home, no-Niu and Wang carpenter, Quejian table with red Buguo the 5000 money. Meiyun mind is the span that matter. [Rs quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)      Six months later, Mei Yun from the hands of traffickers to buy a woman a wife. [rs money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      Has just completed marriage. Mei Mei Yun Niu suddenly received from Jiangsu to the distress of the letter: I was fooled by Wang carpenter, a carpenter at home with his wife Wang, the children, he will I money to sell 15,000 to a local 30-year-old Bozi Wife&#21398; Come help me. [runescape shop](http://www.runescape-shop.com)      Meiyun read the letter, a sigh out: "Oh, I Yousha to be? on when the pro-change! "

---

### Post by m4lte on 2009-04-17
For me import worked after I installed *pstoedit* (I already had *imagemagick* installed, so I'm not sure if that's critical).

However I still have problems with some .eps files. An eps 2d graph from Matlab worked well, while with a 3d graph I only get an inconclusive error message.

---

### Post by snowguy on 2009-05-02
I had trouble importing an eps document into inkscape and wanted to share what finally worked for me. None of the solutions above did work. However thus did:
a) I typed epstopdf at the command line 
b) I was told to install sudo apt-get install texlive-extra-utils
c) I did: sudo apt-get install texlive-extra-utils
d) then I typed epstopdf myfile.eps from the command line
e) then I opened myfile.pdf in inkskape.

Viola!

---

