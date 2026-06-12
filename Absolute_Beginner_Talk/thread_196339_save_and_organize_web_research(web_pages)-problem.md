---
title: "save and organize web research(web pages)-problem"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by alex72 on 2006-06-14
Hai Guys,
This is my first Tread.
I have faced many problem while saving and organizing web pages online for offline viewing. I have even tried many product like furl, offline browser...but, not satisfied with the performance. Tools like webcoppier, [Keepoint]("http://www.keepoint.com"), [Web content saver ]("http://www.macropool.com/en/")etc.. yet i need to try.
If u pple are aware of some web research, Internet research, Academic software, which allows to save and organize web research(web pages) for offline viewing, plse let me know.

---

### Post by wyohermit on 2006-06-20
You might try one of these firefox extensions

scrapbook or clipmarks

---

### Post by aysiu on 2006-06-20
You might want to try DownThemAll, too.

---

### Post by alex72 on 2006-06-22
[QUOTE=wyohermit]You might try one of these firefox extensions

scrapbook or clipmarks[/QUOTE]


I had downloaded clipmark but the thing it is just like Google notebook, Allows to gather online pages making a rough collection similar to scrapbook but I can not view those saved web pages offline. 
I m looking for a tool which allows me save web page not one but thousands of web pages, organized properly so that i can retrive those later on.


Thanks wyohermit!!..

---

### Post by Zikes on 2006-06-22
I think you should look into wget and crontab.  You can use wget to mirror entire sites with the -m option, and you can use a simple file full of URLs using the -i option.  Plus, crontab can be used to automatically run it every hour or so.  Using the -N option with wget will turn on timestamping so that only the newest files are grabbed in successive runs.  wget is also very efficient in that it doesn't have to disconnect and reconnect between files, it'll keep the connection alive for each file it retrieves.

More info on wget here: [http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
And cron/crontab: [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

One of the things I love about Linux, there's so much you can do without having to install new programs :D

---

### Post by alex72 on 2006-06-23
[QUOTE=Zikes]I think you should look into wget and crontab.  You can use wget to mirror entire sites with the -m option, and you can use a simple file full of URLs using the -i option.  Plus, crontab can be used to automatically run it every hour or so.  Using the -N option with wget will turn on timestamping so that only the newest files are grabbed in successive runs.  wget is also very efficient in that it doesn't have to disconnect and reconnect between files, it'll keep the connection alive for each file it retrieves.

More info on wget here: [http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
And cron/crontab: [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

One of the things I love about Linux, there's so much you can do without having to install new programs :D[/QUOTE]



Hai Zaikes
I don't want to leave IE] (*,) , at this stage I even can not think anything with out IE.
Crontab looks good but it for unix, solaris..

---

### Post by alex72 on 2006-07-10
> **alex72 said:**
> Hai Guys,
This is my first Tread.
I have faced many problem while saving and organizing web pages online for offline viewing. I have even tried many product like furl, offline browser...but, not satisfied with the performance. Tools like webcoppier, [Keepoint]("http://www.keepoint.com"), [Web content saver ]("http://www.macropool.com/en/")etc.. yet i need to try.
If u pple are aware of some web research, Internet research, Academic software, which allows to [save and organize web research(web pages)]("http://www.keepoint.com/prodinfo_personal.asp") for offline viewing, plse let me know.


[:shock: ]("http://www.keepoint.com/prodinfo_personal.asp")

[COLOR="Navy"]     This Time I tried "[[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp")" an advance web research software. Its Look pety Good in its performance. It has some infact most of the important features (like [[COLOR="Indigo"]save web page[/COLOR] ]("http://www.keepoint.com/prodinfo_personal.asp")with single click, Annoatate, Share web page, export web page ......) which i m looking 4.
Its Keetool feature is really good. 
It looks like [[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp") is the solution of all saving and organizing web research problem.

Is any body tried other tool...[/COLOR]

---

### Post by wyohermit on 2006-07-10
Maybe I missed something on there site but they don't seem to have a Linux version of this available.  And unless you buy the full version you are limited to 99 pages of storage

---

### Post by alex72 on 2006-07-12
> **Zikes said:**
> I think you should look into wget and crontab.  You can use wget to mirror entire sites with the -m option, and you can use a simple file full of URLs using the -i option.  Plus, crontab can be used to automatically run it every hour or so.  Using the -N option with wget will turn on timestamping so that only the newest files are grabbed in successive runs.  wget is also very efficient in that it doesn't have to disconnect and reconnect between files, it'll keep the connection alive for each file it retrieves.

More info on wget here: [http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
And cron/crontab: [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

One of the things I love about Linux, there's so much you can do without having to install new programs :D


Is WGET is a console base application for saving web page.

---

### Post by SigmaX on 2006-07-12
alex72, this site is for Ubuntu _Linux_ help -- Internet Explorer questions will bounce off us like rubber balls on bricks, because we assume you're using Linux (Thus the Firefox talk).

Yes wget is a console application, it's a standard Linux tool for downloading files and/or entire sites off the web or a network.  Crontab is an automated task scheduler, which would be useful for keeping a downloaded, offline repository of files up-to-date on Linux.

SigmaX

---

### Post by Dr. Nick on 2006-07-12
One of the best ways I know how to do this is using the previously mentioned scrapbook extension to Firefox, either in linux or windows. Most of the windows apps I see do this want to give you ads or charge you, Scrapbook is small, free, and unobtrusive. It saves the entire page structure so you cant tell a difference between on/offline

---

### Post by alex72 on 2006-07-14
> **alex72 said:**
> [:shock: ]("http://www.keepoint.com/prodinfo_personal.asp")

[COLOR="Navy"]     This Time I tried "[[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp")" an advance web research software. Its Look pety Good in its performance. It has some infact most of the important features (like [[COLOR="Indigo"]save web page[/COLOR] ]("http://www.keepoint.com/prodinfo_personal.asp")with single click, Annoatate, Share web page, export web page ......) which i m looking 4.
Its Keetool feature is really good. 
It looks like [[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp") is the solution of all saving and organizing web research problem.

Is any body tried other tool...[/COLOR]

Good peace of work by Keepoint pple
there product Keepad is really good tool for Internet researchers.

It allows me to
1) save web page with single click 
2) Annotate web page 
3) Export web page 
4) Share Web page 
5) Save only required information form web page 
6) Extract address etc...

Superb tool....

---

### Post by alex72 on 2006-07-27
> **alex72 said:**
> [:shock: ]("http://www.keepoint.com/prodinfo_personal.asp")

[COLOR="Navy"]     This Time I tried "[[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp")" an advance web research software. Its Look pety Good in its performance. It has some infact most of the important features (like [[COLOR="Indigo"]save web page[/COLOR] ]("http://www.keepoint.com/prodinfo_personal.asp")with single click, Annoatate, Share web page, export web page ......) which i m looking 4.
Its Keetool feature is really good. 
It looks like [[COLOR="Navy"]Keepad[/COLOR]]("http://www.keepoint.com/prodinfo_personal.asp") is the solution of all saving and organizing web research problem.

Is any body tried other tool...[/COLOR]

Hai Did any body tried Window live tool bar.
It's also a good technology for saving and organizing web research. I guess Microsoft had recently launched the Window live tool bar after Beta version.

---

