---
title: "Obtaining LaTeX"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2008-04-18
Hi everyone, I'm looking to obtain LaTex for typing up engineering papers (which I have never used before) for my Ubuntu computers. I've searched using aptitude, and found many matches, but I'm not sure which is right for me, although I would prefer a GUI and not something completely text-based (if possible). Any suggestions? Thanks!

---

### Post by Bachstelze on 2008-04-18
The Gentoo Wiki has a good starting page for LaTeX :

[http://gentoo-wiki.com/HOWTO_TeX](http://gentoo-wiki.com/HOWTO_TeX)

Obviously, the installation steps are a bit different for Ubuntu, just do

```
sudo apt-get install tetex-base tetex-bin
```

instead of all the *emerge* stuff, and skip to chapter 3.

---

### Post by beren.olvar on 2008-04-18
If you are looking for a nice GUI, you should try installing kile
Is very friendly and allows you to compile your source with just one click

```

sudo apt-get install kile

```

cheers

---

### Post by polmir on 2008-04-18
> tetex-base tetex-binThis old version of latex. teTeX is no longer developed upstream, and has been replaced by the TeX Live
collection.


```
sudo apt-get install texlive-doc-en
```This is documentation.

Type in terminal and search
```
apt-cache search texlive
```
If you have WYSIWYG-frontend for LaTeX --- install
```
sudo apt-get install lyx
```

edid:

kile is good idea.

---

### Post by Bachstelze on 2008-04-18
> **polmir said:**
> This old version of latex. teTeX is no longer developed upstream

So what? It still has everything anyone would need from a LaTeX distribution... **Newer is not necessarily better!**

---

### Post by polmir on 2008-04-18
> Newer is not necessarily better!

Yes by English. What about utf8. You know other language.

---

### Post by Bachstelze on 2008-04-18
Thanks, I'm very well aware of other languages. In fact, as you could have guessed by looking on the upper right corner of my posts, I am *not* English. And I'd also like to bring your attention to the following facts :

1) You do not have to use UTF-8 to write in other languages. You know ISO-8859-*.
2) Last time I checked, adding UTF-8 support to teTeX was ridiculously easy.

---

### Post by Frenske on 2008-04-18
I think kile requires KDE resps. You could use texmaker. There are more or less similar. Never tried kile. The only drawback  is that there is no project management (not sure kile has either) just been using texniccentre for a long time.

[http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)

---

### Post by woaiwojia on 2008-04-18
i can not output papers in chinese

---

### Post by polmir on 2008-04-18
@**HymnToLife **
tetex is not friendly for users my language.
It requires additional interventions. It is my family language Polish. 
tetex made up always addition only.
(iso8859-2/cp1250)

---

### Post by amyst on 2008-04-18
I've tried both kile and texmaker. Both have interface tweaks that are very user friendly, I dare say even more convenient than TeXnicCenter. Ignore the fact that the look of kde doesn't match gnome, my overall experience with kile is better,

If you get kile, make sure that once you compile a .tex file, latex the file, convert it from dvi to ps, and then to pdf so you can see the .eps images in your .ps or .pdf output.

Additional package I find useful with lots of math equations includes:  

texlive-math-extra

---

### Post by nemesis8601 on 2008-04-19
After installing latex it seems I have no free disk space on my ext3 partition. Is there a way I can extend this partition? I can't seem to use open office or firefox now :(

I also can't remove any programs using aptitude. It says there is an error so the package couldn't be parsed or opened due to no disk space.

---

### Post by polmir on 2008-04-19
Erase downloaded archive files
```
sudo apt-get clean
```

Erase old downloaded archive files
```
sudo apt-get autoclean
```

---

### Post by nemesis8601 on 2008-04-19
Thanks, that worked great. Now is there a way I can make the ext3 partition larger? I have Ubuntu installed on my laptop on a 60GB HDD, and I was hoping this day wouldn't come....

---

### Post by polmir on 2008-04-19
[ftp://ftp.gust.org.pl/TeX/info/lshort/english/lshort.pdf]("ftp://ftp.gust.org.pl/TeX/info/lshort/english/lshort.pdf")

[http://www.tug.org/texlive/doc.html]("http://www.tug.org/texlive/doc.html")
[http://www.tug.org/texlive/]("http://www.tug.org/texlive/")
[http://www.tug.org/texlive/doc/texlive-en/live.html]("http://www.tug.org/texlive/doc/texlive-en/live.html")

---

### Post by frisket on 2008-04-24
> **polmir said:**
> @**HymnToLife **
tetex is not friendly for users my language.
It requires additional interventions. It is my family language Polish. 
tetex made up always addition only.
(iso8859-2/cp1250)

There is an extensive and very active Polish TeX Users Group
at [http://www.ntg.nl/lug/pl.html](http://www.ntg.nl/lug/pl.html)

P

---

### Post by pabix on 2008-06-28
woaiwojia:
See this tutorial for LaTeX and Chinese fonts

[http://ubuntuforums.org/showthread.php?t=350101]("http://ubuntuforums.org/showthread.php?t=350101")

---

