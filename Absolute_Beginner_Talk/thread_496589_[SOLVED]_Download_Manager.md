---
title: "[SOLVED] Download Manager"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2007-07-09
Hi is there some kind of download manager for Ubuntu that will let me schedule downloads to take place at a set time.

Thanks in advance. :)

---

### Post by Old Pink on 2007-07-09
Some download managers, not sure on how feature packed they are, worth a look. :) 

1) [Downloader for X.]("http://www.krasu.ru/soft/chuchelo/")
2) [Caitoo (former Kget).]("http://devel-home.kde.org/%7Ecaitoo/index.html") 
3) [Prozilla]("http://prozilla.delrom.ro/prozilla.html"). 
 4) [Wget]("http://wget.sunsite.dk/") (console, standard). 
5)  GUI for Wget: [Kmago]("http://kmago.sourceforge.net/"), [Gnome Transfer Manager]("http://gtm.sf.net/"), QTget, Xget, ...
6) [Aria.]("http://aria.rednoah.com/") 
7) [Axel]("http://www.lintux.cx/axel.html").
8.)  Download Accelerator Plus.
9) [GetLeft]("http://personal1.iddeo.es/andresgarci/getleft/english/download.html"). 
10) [Lftp]("http://lftp.yar.ru/").

Source: [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by KIAaze on 2007-07-09
I don't know but you can use crontab and wget for such tasks.
See:
```
man crontab
man wget
```
A little guide:
[http://www.adminschoice.com/docs/crontab.htm]("http://www.adminschoice.com/docs/crontab.htm")

For example to download [ftp://foo.tar.gz](ftp://foo.tar.gz) at 01:08 (every day in the year):
Type ```
crontab -e
```
Enter:
> 8     1     *     *     *         wget [ftp://foo.tar.gz](ftp://foo.tar.gz)
Save the file.
And that's all.

You can enter anything that works on the command-line in crontab.
This means that you can run programs and shellscripts. ;)

edit:
If you want to do it with a shellscript, the "date" command might be useful.

---

### Post by Qwerty_ on 2007-07-09
Half of Old Pink's links dont work. I think I might try with your crontab method KlAaze.

---

### Post by Qwerty_ on 2007-07-10
Well I installed Downloader for X from the repos and it looks like it will do my job :) Cheers.

---

