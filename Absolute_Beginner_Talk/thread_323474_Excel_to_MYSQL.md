---
title: "Excel to MYSQL?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by uncreative on 2006-12-22
Does anyone know how to convert Excel to Mysql?

I'm going nuts over here...

---

### Post by gvoima on 2006-12-22
[removed] chit chat, nothing else :P move along [/removed]

---

### Post by uncreative on 2006-12-22
Believe me, I googled.  But all that stuff is payware for Windows.

I was kind of curious if there was a linux answer to this question...

---

### Post by gvoima on 2006-12-22
Well you always could run some of the trial (full featured) versions in vmware, or wherever you got the excel sheet from?

---

### Post by gvoima on 2006-12-22
This could work too [http://sourceforge.net/projects/qtexcel-xslt/]("http://sourceforge.net/projects/qtexcel-xslt/")
or this [http://sourceforge.net/projects/excel2mysql/]("http://sourceforge.net/projects/excel2mysql/")

---

### Post by uncreative on 2006-12-22
checking links now -- thanks

---

### Post by jvc26 on 2006-12-22
I'd say it fits to beginner talk, if you are a beginner! It could be done by using the MYSQL GUI tools i think- I'm not 100% sure, but the way I used to push Excel sheets into MYSQL tables on windows was by Saving the excel info as a .txt file and then using the command to copy the information from the .txt file to the table. - That info is all in the MYSQL reference manual. I also think, again its been a while since I worked with MYSQL, that the GUI tools allows you to import takes from excel (don't quote me on that on) again more info I'm sure will be on the MYSQL site/reference manual (which is also on the site). Finally, GUI tools I believe are available from the repo (check out [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) as I think there is a HOWTO on there)  and if not, you can download a LINUX version from the MYSQL site.
Hope that goes some way to helping :),
Il

---

### Post by uncreative on 2006-12-22
Ah thank you.  Yeah, this database is absolutely huge so I probably should have mentioned that.  I'll give it a go and see what happens!


> **Illuvator said:**
> I'd say it fits to beginner talk, if you are a beginner! It could be done by using the MYSQL GUI tools i think- I'm not 100% sure, but the way I used to push Excel sheets into MYSQL tables on windows was by Saving the excel info as a .txt file and then using the command to copy the information from the .txt file to the table. - That info is all in the MYSQL reference manual. I also think, again its been a while since I worked with MYSQL, that the GUI tools allows you to import takes from excel (don't quote me on that on) again more info I'm sure will be on the MYSQL site/reference manual (which is also on the site). Finally, GUI tools I believe are available from the repo (check out [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) as I think there is a HOWTO on there)  and if not, you can download a LINUX version from the MYSQL site.
Hope that goes some way to helping :),
Il

---

### Post by jvc26 on 2006-12-22
No problem mate - I know the problems of getting huge tables into MYSQL - nightmare if you had to do each line by the command line ;) Iv just have a brief re-run of my methods:

To put things in via command line, save the excel sheet as a tab delimited .txt file and then follow the instructions here I think:
[http://dev.mysql.com/doc/refman/5.0/en/loading-tables.html](http://dev.mysql.com/doc/refman/5.0/en/loading-tables.html)

To do them via GUI (now Im pretty sure you can do that - I'm sure there was an import excel sheet one on the GUI database viewer) get yourself the GUI tools and connect to the db, select the table you want (presuming you've made the tables) and then import data souce .xls I think - I'm less sure about this one as I used to always use the command one with the 
```

LOAD DATA LOCAL INFILE '/path/to/newtable.txt' INTO TABLE newtable;

```
command. (Was a big command user until I discovered the GUI tools which was at the end of my project ;) so never used them widely enough to know most of the ins and outs - they definitely make the MYSQL accessing and loading data steps so much easier its nice to 'see' what you're going)

Best of luck mate,
Il

---

