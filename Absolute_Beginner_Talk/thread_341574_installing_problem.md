---
title: "installing problem"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by cairo on 2007-01-18
at the partition part, i choose second option (erase entire disk: IDE master (hda)-20gb samsung) i wanna replace the window with linux (crash window xp inside this hardisk)

during my first time for installing system step, i put in install and i away, when im back, this error message prompt out.

traceback (most recent call last)
File "/usr/ubiquity", line 166, in ? main()

file "/usr/bin/ubiquity", line 161, in main install(sys.argv[1])

file "/usr/bin/ubiquity", line 57, in install ret=wizard.run()

file "/usr/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run self.process_step()

file "/usr/ubiquity/ubiquity/frontend/gtkui.py", line 856, in progress_step self.progress_loop()

file "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 631, in progress_loop raise RuntimeError, ("install failed with exist code %s; see")

RuntimeError: install failedwith exist code 139; see /var/log/syslog





i have no idea what is going on here, so i go install again for second time, and still the problem exist, it hang at 54% for long period,  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

anyone please help me for this issue :(
thanks in advanced !

---

### Post by Shatrat on 2007-01-18
I don't have any particular insight into why it failed, but since you were gonna erase the whole disk anyway there isnt anything at risk here.  You could just try it again a couple more times.

Also, judging by your hard drive size this seems to be an  older machine?  Maybe you could ry using the Alternative install disk or boot the live one in 'safe' mode?

---

### Post by cairo on 2007-01-18
errr... only the hardisk is old, this computer spec is pentium 4 2.4 HT, 768 ram, i got another 80 western digital hardisk, seem im stil beginner, so i decide to choose 20gb for linux
should i got try Alternative install disk or boot the live one in 'safe' mode again ?

---

### Post by Sef on 2007-01-18
1) Did you md5sum the download?

2) Did you burn at 4x or less?  (More can corrupt the burn.)

3) Try the alternate cd, if the live cd fails.  The former can work where the latter one fails.  The alternate cd is a text based installer, but mostly common sense.   Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for installing from the alternate cd.  If you are not dual booting, just skip the part about the FAT32 partition.

---

### Post by cairo on 2007-01-18
yes, i did the checksum step, both is the same, the lowest speed in my combo drive is 12x, so i choose 12x, i also check integrity for my cd, there is no checksum error
nop, im not dual booting, i just want linux in my hardisk
thanks for ur website i will go through and  have a read

---

### Post by cairo on 2007-01-19
no idea ?

---

### Post by louieb on 2007-01-19
Well at least the problem is consistent. Due to the fact that  that you can boot the CD and start the install at least we know you don't have to play with boot codes. Is it the Live or alternate CD ? Not that for a machine with 3/4 gig of ram it would make a difference.
My wild as guess of the day:  Bad CD burn. It just take a few scrambled bit in the wrong place to turn a CD into a coaster.

---

