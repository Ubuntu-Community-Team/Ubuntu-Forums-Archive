---
title: "Stalling on MTA sendmail. Please help!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by sambando on 2007-12-13
Hi everybody,
                       I've got some serious issue on start up: system is stalling at Starting Mail Transport Agent MTA sendmail. It all began when I install kalarm, and then sendmail, it screw up everything... Ok, I'am a absolute begginner...  System is freezing frequently too.

PLEASE, HELP ME TO DISABLE SENDMAIL, MTA whatever, and boot normally again... 



thanks in advance

---

### Post by hfranco on 2007-12-13
Have you tried uninstalling sendmail?

sudo apt-get remove sendmail

---

### Post by Dr Small on 2007-12-13
My sendmail is rather sluggish too. Is that the nature of sendmail ?

---

### Post by sambando on 2007-12-14
Yes, I've tried before to remove sendmail... all the same... freezing all the time now... could not get back to work normally... 

I have dual boot on my machine, but I don't want to use crappy Windows anymore, I'am pretty happy with Ubuntu...

How can I disable MTA? He is the bad guy I think...

Buy the way, compiling the kernel would solve this issue, is it dangerous and/or difficult??? 

thanks in advance

Bruno

---

### Post by maestrobwh1 on 2007-12-31
I had a similar issue, but could get to my desktop.  It just hung for a while on MTA, then some errors flashed by, then the desktop loaded.  I fixed this by searching Adept pakcage manager for "MTA" and found 4 associated files that were installed.  I then requested them to be reinstalled and not everything works.  

From command line, perhaps try
[INDENT]
sudo aptitude reinstall exim4 exim4-base exim4-config exim4-daemon-light[/INDENT]

---

### Post by sambando on 2008-01-03
Hi, maestrobwh1,

                              wow, to be honest, now that I used your command line, it's freezing all the time!!! It's not the case of recompilling the kernel?? Please, someone help, can not go back to work!!!

VERY VERY disappointed with this issue in Ubuntu!!

thanks in advance

---

### Post by maestrobwh1 on 2008-01-17
sudo apt-get remove exim4 exim4-config exim4-base exim4-daemon-light

you could use  "aptitude purge " in place of "apt-get remove," but it tends to be more aggressive and might try to remove other things.  Probably not in this case.

If you can open synaptic, you can do a search for mta, and these are the files that show up as installed.

If you did the apt-get remove thing: open synaptic and go to the status option then to "residual configuration" and purge that stuff.

I started having issues again, and did some research.  If you don't plan on using this variety of mail (to be honest, I could not figure out why it is part of the base distribution), just get rid of it.  If you check your mail via a program (thunderbird, kmail, whatever gnome uses, etc) you don't need exim4.

---

### Post by sambando on 2008-01-18
Thanks maestrobwh1!

It worked! But Ubuntu continues to freeze several times a day. Any idea?

thanks a lot, you've solved my problem!

Bruno

---

### Post by hyper_ch on 2008-01-18
kalarm is missing sendmail or rather an MTA... I guess that's the freezing problem you encounter. I prefer postfix over sendmail.

---

### Post by sambando on 2008-01-18
I've made aptitude purge on sendmail and kalarm. Perhaps it will fix the problem. 

thx!

---

