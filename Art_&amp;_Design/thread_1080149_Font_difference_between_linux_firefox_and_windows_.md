---
title: "Font difference between linux firefox and windows firefox."
date: 2009-02-25
forum: Art &amp; Design
---

### Post by muCh4 on 2009-02-25
Recently switched to ubuntu (again!) and got some work in progress. What was my surprise when I realised that page I was working on on windows is a bit messed up with fonts in linux. I use verdana in this project and somehow in linux it appears to have bigger spaces between rows. 
What's more I've checked webbys I've already done and they appear to have the same problem too. (not all of them luckilly) I must admit I've never checked if the page was displayed properly under the same browsers on linux and windows.
What's the issue and how to solve it? :)

Here's example: [www.fitforyou.pl](www.fitforyou.pl) (it's polish so don't be shocked with weird signs ;)) - in three 'borders' in the bottom text 'leaves' it's proper space. It wasn't like that in windows.

Help will be really appreciated. Thanks in advance.

---

### Post by smartboyathome on 2009-02-25
Install "msttcorefonts" (via sudo apt-get install msttcorefonts in a terminal) and it should look like it did on Windows.

But Linux doesn't include what web developers so call "web safe fonts" because they are proprietary and you need to pay license fees (technically, msttcorefonts is illegal). I the name for those fonts are a misnomer (imo), and actually hurt Linux because they think of it as an afterthought.

---

### Post by Sand &amp; Mercury on 2009-02-25
> **smartboyathome said:**
> Install "msttcorefonts" (via sudo apt-get install msttcorefonts in a terminal) and it should look like it did on Windows.

But Linux doesn't include what web developers so call "web safe fonts" because they are proprietary and you need to pay license fees (technically, msttcorefonts is illegal). I the name for those fonts are a misnomer (imo), and actually hurt Linux because they think of it as an afterthought.
Actually, it's not. They're just not allowed to distribute them with Ubuntu OOTB because that would count as 'adding value' to it.
[http://en.wikipedia.org/wiki/Mscorefonts#cite_note-1](http://en.wikipedia.org/wiki/Mscorefonts#cite_note-1)

---

### Post by muCh4 on 2009-02-25
I have msttcorefonts already installed. What may be the problem? I didn't change anything in firefox (font sizes).

---

### Post by -yay- on 2009-02-25
I've noticed this problem before, firefox seems to render verdana a bit spacier. Opera for linux is also a bit strange, sometimes verdana looks like bold arial on opera.

I'm not sure how to solve this problem from a web designer standpoint, I thought about conditional comments but I don't think they're OS specific.

---

### Post by mcduck on 2009-02-26
As a web designer you pretty much have to accept the fact that font rendering, and even the available fonts, can change. In the end the only control you really have over fonts is their size and if they are sans-serif or serif (and even those can change if the user has defined own settings in the browser's options), boldness and italics.

You can't really even expect the viewer to have Verdana or Arial.

---

### Post by ikisham on 2009-02-26
Anyway, as an observer, they look well 'in place' for me at your site.

---

### Post by Ginger The Cat on 2009-04-07
What about this site then. It looks wrong on Firefox 3.0.8 Ubuntu Jaunty for me. Installing msttcorefonts made no difference.

[http://www.thrivingcandlebusiness.com/]("http://www.thrivingcandlebusiness.com/")

Looks fine on XP Firefox 3.0.8 and IE 8.

Doing a Ctrl+ fixes it.

---

