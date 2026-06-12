---
title: "Modifying TEXINPUTS (path to LaTeX packages)"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by evillan on 2008-03-24
As described in [https://help.ubuntu.com/community/La...097aa143d130c7](https://help.ubuntu.com/community/La...097aa143d130c7), I created a directory to place my locally installed LaTeX packages in /home/username/packages. Then I changed TEXINPUTS ("export TEXINPUTS=~/packages/:" in bash) so TeXlive will be able to find it.

This worked fine.

However, I wan't to make sub directories, for example /home/username/packages/packagename, where files related to "packagename" are placed. But then I have to change TEXINPUTS, because the sub directories are not included already. So I wan't to modify TEXINPUTS so it includes all sub dirs without having to manually specify this for every package?
How is this achieved?

Thank you.

---

### Post by frisket on 2008-04-09
> How is this achieved?
By reading the documentation. In this case the FAQ at [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=what-TDS](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=what-TDS)

Put your personal packages in ~/texmf/tex/latex/<packagename> and then run texhash.

Local (shareable) updates to standard packages go in /usr/local/share/texmf/... (using sudo texhash afterwards)

Both those directory trees are already included in the config at /etc/texmf/texmf.cnf so anything in there will be recognised once you update with texhash

TEXINPUTS has been obsolete for years.

///Peter

---

### Post by Hicksrules on 2008-06-25
> **frisket said:**
> By reading the documentation. In this case the FAQ at [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=what-TDS](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=what-TDS)

Put your personal packages in ~/texmf/tex/latex/<packagename> and then run texhash.

Local (shareable) updates to standard packages go in /usr/local/share/texmf/... (using sudo texhash afterwards)

Both those directory trees are already included in the config at /etc/texmf/texmf.cnf so anything in there will be recognised once you update with texhash

TEXINPUTS has been obsolete for years.

///Peter
Hi.

I used to keep all my cls and sty files in in my working directory (/usr/local/...).  I recently discovered the ability to set the TEXINPUTS command for cls and sty files...  My question is more pedagogiacal than anything (I got everything working fine).  What is the texhash command.... What exactly does it do?

Michael

---

### Post by leejack43 on 2008-06-25
Nokia Phones
Nokia 1112
Nokia 1200
Nokia 1208
Nokia 1650
Nokia 2310
Nokia 2610
Nokia 2630
Nokia 2760
Nokia 3109 Classic
Nokia 3110 Classic
Nokia 3110 Evolve
Nokia 3500 Classic
Nokia 5070
heriplazaplusltd
Nokia 5200
Nokia 5300 XpressMusic
Nokia 5310 XpressMusic
Nokia 5500 Sport
Nokia 5610 XpressMusic
Nokia 5700 XpressMusic
Nokia 6080
Nokia 6086
Nokia 6110 Navigator
Nokia 6111
Nokia 6120 Classic
Nokia 6121 Classic
Nokia 6131
Nokia 6233
Nokia 6267
Nokia 6280
Nokia 6288
Nokia 6300
Nokia 6301
Nokia 6500 Classic
Nokia 6500 Slide
Nokia 6555
Nokia 7373
Nokia 7390
Nokia 7500 Prism
Nokia 7900 Prism
Nokia 8600 Luna
Nokia 8800 Arte
Nokia 8800 Sapphire Arte
Nokia 8800 Sirocco Edition
Nokia E50
Nokia E51
Nokia E61i
Nokia E65
Nokia E90 Communicator
Nokia N70
Nokia N73
Nokia N76
Nokia N77
Nokia N78
Nokia N81
Nokia N82
Nokia N92
Nokia N93
Nokia N93i
Nokia N95 8gb
Nokia N96

Nokia Music Phones

---

### Post by hugmenot on 2008-06-25
It indexes the so-called TEXMF trees. A texmf tree has a standard layout but tex doesn't search through all directories for every file it needs, it just looks up paths via the texhash index. The layout is specified in the TDS spec: [http://en.wikipedia.org/wiki/TeX_Directory_Structure](http://en.wikipedia.org/wiki/TeX_Directory_Structure)

You can keep your personal texmf tree in your home directory and ~/texmf is the default.

---

### Post by hugmenot on 2008-06-25
Better explanation: [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=inst-wlcf](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=inst-wlcf)

---

