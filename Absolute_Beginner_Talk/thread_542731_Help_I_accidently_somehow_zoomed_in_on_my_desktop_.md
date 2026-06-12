---
title: "Help I accidently somehow zoomed in on my desktop and dont know how to zoom out!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Azerial on 2007-09-04
OK, I have no earthly idea how I did this!

I was in the login screen on Ubuntu 7.10 Tribe 5. (Had to use the beta of gusty due to hardware incompatibility issues on 7.04 with my dvdrw/cdrw combo drive)


Anyway I pushed my keyboard drawer in on my desk that has my keyboard and mouse on it and when I did my screen zoomed in, I restarted and my desktop is still zoomed in when I move my mouse to the corner of the screen it moves to areas of the desktop and open window I cant see.  I cant figure out how to make it normal again!!!

Also ontop of making it normal how can I disable it from ever doing this again?

---

### Post by marco123 on 2007-09-04
Could be Compiz.  Try holding down the windows key and using the mouse scroll wheel to zoom in and out?

---

### Post by nowshining on 2007-09-04
you do know that 7.10 is not officially out yet - it's in development - IN OTHER WORDS _ BUGS GALORE.. and Problems galore..feisty fawn 7.04 is the only latest official version out...

---

### Post by Azerial on 2007-09-04
> **marco123 said:**
> Could be Compiz.  Try holding down the windows key and using the mouse scroll wheel to zoom in and out?

that didnt work, any other ideas?

---

### Post by Azerial on 2007-09-04
> **nowshining said:**
> you do know that 7.10 is not officially out yet - it's in development - IN OTHER WORDS _ BUGS GALORE.. and Problems galore..feisty fawn 7.04 is the only latest official version out...

Well I cant use 7.04 because it refuses to recongize the existance of my CDr/rw/DVDr/rw combo drive because of hardware imcompability and Linux being fussy over SATA drives.

since it was my only disk drive and 6.06 refused to isntall on my machine I had no other options but to do 7.10.

---

### Post by marco123 on 2007-09-04
Is there an Auto-Config option on your monitor?  You could try that, if not you might have to reconfigure xorg . "sudo dpkg-reconfigure xserver-xorg" and accept most of the defaults.

---

### Post by nowshining on 2007-09-04
you could of been patient and waited a month - october is when it is suppose to come out and be officially stable.. but i'm glad you know that..

---

### Post by Azerial on 2007-09-04
> **nowshining said:**
> you could of been patient and waited a month - october is when it is suppose to come out and be officially stable.. but i'm glad you know that..

Yea wait a month, a month with a computer where I cant use my ONLY Disk drive.... Id rather switch to windows for EVERYTHING.  at least my XP partition recognized my Drive.


So aside from telling about 7.10 being in beta and such.... How about telling me how to fix this problem.

---

### Post by SOULRiDER on 2007-09-04
Theres no point in lecturing him about not using beta software, he clearly knows that.

AFAIK, the problem could be a resolution problem, try reconfiguring xorg.

---

### Post by Azerial on 2007-09-04
> **marco123 said:**
> Is there an Auto-Config option on your monitor?  You could try that, if not you might have to reconfigure xorg . "sudo dpkg-reconfigure xserver-xorg" and accept most of the defaults.

Uhhh I tried that and got confused by the questions and was too afraid of messing something up by answering them.

IM Sure I hit some kinda keyboard shortcut here I jsut want a fix, so I can see my desktop normally and not zoomed in this is bullcrap I'll reformat my linux parition before I'll deal with this any longer its sooooo annoying!  not like I care to do that if I cant get an answer all my data is backed up.

---

### Post by marco123 on 2007-09-04
> **Azerial said:**
> Uhhh I tried that and got confused by the questions and was too afraid of messing something up by answering them.

IM Sure I hit some kinda keyboard shortcut here I jsut want a fix, so I can see my desktop normally and not zoomed in this is bullcrap I'll reformat my linux parition before I'll deal with this any longer its sooooo annoying!  not like I care to do that if I cant get an answer all my data is backed up.

If you don't want to reconfigure xorg, and all your data is backed up, just reinstall.  Unlike Windows it only takes about half an hour to reinstall, tick all the programs you want reinstalled in add/remove etc...

Try making a seperate /home partition so you don't lose settings or files when you reinstall.  e.g 160gb HD = 10-15GB root, 1GB swap and the rest for /home.  Then when you reinstall just don't format the /home partition and you'll still have your settings/files etc...

See - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Edit: Or - [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by UbuntuniX on 2007-09-04
Check System ~> Admin ~> Screens & Graphics for the resolution setting.
It seems to be bugged, because the settings sometimes reset.

---

