---
title: "Cannot restore Xserver"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by JefferyMcElroy on 2007-08-08
I was trying to manually configure dual monitors with the xorg.conf.  
I backed up my configuration, thinking I could play around with settings and values and restore anything that I messed up:  

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

X now crashes on boot, thanks to the change I made.
[I]1280x1024" is not a valid keyword in this section 
Fatal server error:
no screens found 
[/I]
Pretty cut and dry; the only problem is, can't seem to access the terminal to reload my backup file.

When I type the following command, nothing happens:   
[B]sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
[/B]
**sudo dpkg-reconfigure xserver-xorg**
doesn't do anything either.  

I am not asked to log in or anything.  How do I restore my backup file?

I wouldn't have otherwise asked such a noobish question, however I have a mission critical job that I need to finish this afternoon, and lack the knowledge or nomenclature to troubleshoot my problem. 

Best regards,
Jeff

---

### Post by bwtranch on 2007-08-08
Can you re-boot in recovery mode?

---

### Post by JefferyMcElroy on 2007-08-08
Thanks for the quick response.  Do I use the instillation CD for that?

---

### Post by bodhi.zazen on 2007-08-08
To access the terminal, Type :

ctrl-alt-F1 (or ctrl-alt-F2 if that fails)

Then log in and restore from backup

Then

sudo /etc/init.d/gdm restart

---

### Post by JefferyMcElroy on 2007-08-08
Okay, that did it!

When I attempt backup, it retorts "no such file or directory", but I can still reconfigure X, so no biggie.  

Thanks!

---

### Post by silent1643 on 2007-08-08
yeah i had a similar problem - just sudo pico xorg.conf and make your changes :D

---

### Post by JefferyMcElroy on 2007-08-08
You know, I panicked this time, even though I new it was something simple.  For the past four months, I have vowed never to directly ask for help.  I wanted to figure things out for myself; I must say this has been the most rewarding OS experience I have ever had (with a little help from google along the way).  :)

---

### Post by bodhi.zazen on 2007-08-08
> **JefferyMcElroy said:**
> Okay, that did it!

When I attempt backup, it retorts "no such file or directory", but I can still reconfigure X, so no biggie.  

Thanks!

Use tab completion. Start typing a file, hit the tab key

works for both commands and files

so 

cp /etc/X11/xorg.conf<tab> /etc/X11/xorg.conf

The tab will give you a list of options (you may have to hit it 2X if there are more then one).

---

