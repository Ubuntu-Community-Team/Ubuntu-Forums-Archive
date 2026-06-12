---
title: "Request: How to back up Evolution made simple"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2005-09-12
Hello,

I've just lost an hour trying to find out how to back up my Evolution data (the calendar and emails). Does anyone know of a method?

I've already tried

---------------
[http://ubuntuforums.org/showthread.php?p=265526](http://ubuntuforums.org/showthread.php?p=265526)
--------------
conftool-2 --shutdown
evolution-2.0 --force-shutdown
cd ~
tar -cvzf evolution.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution
--------------------

Did not work. Couldnt find the directory.

I also tried "copying all stuff in /home/youruser/.evolution should do the trick." as suggested in:

[http://ubuntuforums.org/showthread.php?t=46153&highlight=backup+evolution](http://ubuntuforums.org/showthread.php?t=46153&highlight=backup+evolution)

Is there any simple method? I'm actually ready to ditch Evolution now as there doesnt seem to be any newbie way to export and backup files (or at least there's no mention of it in the help files).

Thansk for any advice

Dafydd

---

### Post by aysiu on 2005-09-12
[QUOTE=Dafydd]
I also tried "copying all stuff in /home/youruser/.evolution should do the trick." as suggested in:

[http://ubuntuforums.org/showthread.php?t=46153&highlight=backup+evolution](http://ubuntuforums.org/showthread.php?t=46153&highlight=backup+evolution)

Is there any simple method? I'm actually ready to ditch Evolution now as there doesnt seem to be any newbie way to export and backup files (or at least there's no mention of it in the help files).[/QUOTE] So you tried this method... and? What happened? What went wrong? Why do you believe it didn't work? I don't see what can be more simple than copying a folder.

If you're talking about exporting, does that mean you're migrating to a new email client? If so, maybe these links will help:

[http://email.about.com/cs/evolutiontips/qt/et110103.htm](http://email.about.com/cs/evolutiontips/qt/et110103.htm)
[http://www.linux.com/article.pl?sid=04/09/10/1446217](http://www.linux.com/article.pl?sid=04/09/10/1446217)

---

### Post by davmac on 2005-09-12
Have a look at Mark Wilde's Evolution backup script at [http://markwilde.com/linux/](http://markwilde.com/linux/)

HTH,

Dave Mac

---

### Post by Dafydd on 2005-09-12
[QUOTE=davmac]Have a look at Mark Wilde's Evolution backup script at [http://markwilde.com/linux/](http://markwilde.com/linux/)
HTH,
Dave Mac[/QUOTE]


Thanks for your comments and help. But I don't have a "/home/${USERNAME}/" directory?

I just installed Ubunto 5.04 and like the calendar at the top. So I clicked it and thought aobut using it as an agenda/planner. But now I realize it's not so simple to backup the date. Does Evolution store the data for the calendar (ie. appointments etc) elsewhere? Also, if I can't back up my emails then I'll try installing sth else.

Best
Dafydd

---

### Post by aysiu on 2005-09-12
What you're looking for is a hidden folder. All the settings for programs are in /home/username/.programname, and all the .folders are hidden. Open up the file browser, and then press control-H to view hidden folders.

---

### Post by Dafydd on 2005-09-12
[QUOTE=aysiu]What you're looking for is a hidden folder. All the settings for programs are in /home/username/.programname, and all the .folders are hidden. Open up the file browser, and then press control-H to view hidden folders.[/QUOTE]


Thanks a million. I'm sorry for the stupid question. 

Now I can see the .evolution folder (in /home/dafydd/.evolution). But how do I backup my calendar data? Also, I'd like to copy it to my other machine once in a while.

Sorry, I've only been using Linux (Ubuntu for about a month). I don't understand scripts and all that. This is the first Linux distribution that has worked (relatively well) for me so far. But these little things are frustrating.

How should I change this script so that it works for me (and backs up my calendar data, not just emails)? 

[http://markwilde.com/linux/evolution-backup.cron.html](http://markwilde.com/linux/evolution-backup.cron.html)

Thanks anyone who can help.
daf

---

