---
title: "Create a DVD"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-06-01
Hello,

I want to create a DVD for my hubby for Fathers' Day that incorporates photos and videos and is set to music.  What is the best program to create and burn it with?

---

### Post by Inxsible on 2007-06-01
you might wanna look into DeVeDe for creating the DVD menus and stuff and adding data. It also burns the DVD to disc
 
I personally prefer K3B to burn the DVD's but I don't think K3B allows you to create DVD menus -- atleast I dont know if it does

---

### Post by wrongo on 2007-06-01
I don't think DeVeDe can create menus.

Here is what I can do with DeVeDe--and, I should point out, it is the ONLY program that I can do these things with (at least that I have found so far).

I open DeVeDe, choose VIDEO DVD, browse for and select an .avi, .wmv, .flv (flash video)--and probably other video file formats; it's converted every format I've tried so far!--and then select NTSC (since I'm in North America--that's the region setting) then in ADVANCED OPTIONS go to the MISC tab and under "Extra Parameters for Mencoder" type: "-afm ffmpeg" - this fixes audio problems... select where to save and what to call the converted file

Uncheck the "Erase temporary files" (at the bottom of the main applet)

select "Only convert film files to compliant MPEG files"

and repeat

Now the reason all this is important is that the conversion takes quite a while and has been known to stall on more than one occasion, and you do NOT want to spend all that time converting only to lose your "temporary files" (i.e., the mpeg's you just created)

No, these files are very, very sweet creatures, the real gold if you ask me

because DeVeDe can take these files and (again, selecting NTSC and putting in the "-afm ffmpeg" info in the "extra parameters for mencoder" box!!!!) in a matter of just a few minutes it can burn them onto a playable DVD

OK?

But I still don't know how to get menus...although I heard there's a program for it...

Thank you DeVeDe!!!!!d Best program for making DVDs in linux yet (only program?)

nevermind the ones that people are SELLING...

---

### Post by wrongo on 2007-06-02
I FORGOT TO MENTION: When you have created the mpeg files, and you're ready to burn them into a dvd, look for and select the option something like "files are already mpeg compliant" - it's in the ADVANCED OPTIONS, i think, also under MISC

jerit

---

### Post by bean77 on 2007-06-05
This might be an even more basic question (sorry!) but what program should I use to actually create the movie from photos?  Open Office Presentation?

---

