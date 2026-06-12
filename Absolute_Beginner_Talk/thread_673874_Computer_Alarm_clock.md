---
title: "Computer Alarm clock"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-21
Hi there, I'd like to set up my laptop to work as an alarm clock.  One that I can set different alarm times for different days, and have my computer speakers wake me up in the morning.  Anyone know if there are any programs to do what i'm asking?

---

### Post by CasperRed on 2008-01-21
I'm going to post here so I can watch, because I am VERY interested in the same thing. 8)

---

### Post by erginemr on 2008-01-21
Did you try kalarm? It is a KDE app but should work under Gnome.

```
sudo aptitude install kalarm
```

---

### Post by whitethorn on 2008-01-21
Hi all, I use this called alarm clock it's for gnome.  You can get it here.

[http://www.getdeb.net/app/Alarm+Clock](http://www.getdeb.net/app/Alarm+Clock)

or if you feel like it you can use cron. It's Ubuntu's built in clock/ update manager, you can also use this to schedule different tasks.  

[http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm](http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm)

Here's an intro to using cron.  I prefer using alarm clock 0.5 and have it start audacious -p

---

### Post by jordank on 2008-01-22
i don't really know what you mean by cron.  is what you're describing what I'm looking for?

---

### Post by BobCFC on 2008-01-22
Cron is used by the system to run programs at certain times of the day... such as run the backup script at midnight etc. 

It's not very friendly to use and not meant for desktop use.

---

### Post by CasperRed on 2008-01-26
> **whitethorn said:**
> Hi all, I use this called alarm clock it's for gnome.  You can get it here.

[http://www.getdeb.net/app/Alarm+Clock](http://www.getdeb.net/app/Alarm+Clock)

Here's an intro to using cron.  I prefer using alarm clock 0.5 and have it start audacious -p

I'm checking out Alarm Clock now. I've used Cron in an intro to Linux class I took a few years ago (Red Hat 9 days) and frankly I'd rather have a tooth pulled. 

But Alarm Clock looks like what I'm looking for. I like the GetDeb site as well. First time I've seen it. Thanks for posting. :)

---

### Post by wolfvorkian1 on 2008-01-26
> **CasperRed said:**
> I'm checking out Alarm Clock now. I've used Cron in an intro to Linux class I took a few years ago (Red Hat 9 days) and frankly I'd rather have a tooth pulled. 

But Alarm Clock looks like what I'm looking for. I like the GetDeb site as well. First time I've seen it. Thanks for posting. :)

If you change your mind, here is good thread on crontabs. At least for setting up alarm clock type of events, it is quite easy. No need to lose any more teeth. 

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

A couple of things. In the thread you are shown how to change your editor to something sane for this type of lite weight editing and don't worry when the editor says it is saving the file as a tmp. Somehow it gets it to the right place which is /var/spool/cron/crontabs/your_username. They are actually sort of fun to dink around with.

---

### Post by t3k on 2008-02-05
I've been trying to use alarm clock to run "rhythmbox-client --play" and it works when I hit test but It never works in the morning. I keep rhythmbox open and I have alarm clock set to also pop up a dialog box which it does not do leading me to beleive that the issue is with alarm clock. I also have it set to do the same thing twice within two minutes. I hoped that this would wake the display and allow it to work but this failed as well. I had it set for seven AM pst, but I just woke up and wrote this.

---

### Post by geordie on 2008-03-03
Thanks guys this is awesome! I've got my computer set to wake me up to loud happy hardcore Space Odyssey Remix every morning :D Anyone know how I can get my computer to boot at the scheduled times, or maybe just resume from standby?

Oh yeah I'm using the gnome alarm clock 0.9.1 on an hp dv9774ca with Gutsy 64bit.

---

### Post by big dizzle on 2008-04-11
> **erginemr said:**
> Did you try kalarm? It is a KDE app but should work under Gnome.

```
sudo aptitude install kalarm
```

this worked 4 me! many thanks!

---

### Post by Sim777 on 2008-04-16
> **whitethorn said:**
> Hi all, I use this called alarm clock it's for gnome.  You can get it here.

[http://www.getdeb.net/app/Alarm+Clock](http://www.getdeb.net/app/Alarm+Clock)
-p

Good stuff. Exactly what I was looking for. It has an option to run terminal command at particular time...so I can run totem with wake-up mp3.  :cool:

---

