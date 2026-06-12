---
title: "[SOLVED] AWN in Feisty"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by jamiehendrich on 2008-03-22
  I have tried all afternoon to install AWN in Feisty.  Here are the instructions I followed, the  e ones for Feisty, of course:  [http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)


I did the first step , added the two lines.  Saved and exited.  Imported the key.  Then I did sudo aptitude update and got the following screenshots.

What am I doing wrong?  Thank you for any assistance.

---

### Post by saj0577 on 2008-03-22
Your asking it to read a file "damaged_file_bzip2" which most liekly wont exsist to use that program you need to type.

bzip2recover damaged.tar.gz2


Saj

---

### Post by jamiehendrich on 2008-03-22
thank you very much.

---

### Post by saj0577 on 2008-03-22
Problem fixed?

---

### Post by jamiehendrich on 2008-03-23
**[SOLVED]**

Saj, thank you for your input.  

My sources.list was wrong.  It originally said something about "feisty avant-window-navigator on the last two lines.  My friend, oseph Millikan -- Linux expert --  figured it out and had me change the last two lines as follows and it works absolutely beautifully.    

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz(-Fusion), AWN and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

You should see my applets on  my AWN dock.  They spin if you click on system/preferences/AWN manager and then the "General" tab  and change "hover" to          "3D spotlight turn."   I love this.  It's just terrific.

Thank you, Joseph.

---

### Post by jamiehendrich on 2008-03-23
And it's "Joseph Millikan" not "oseph."  Tsk.....tsk.....tsk.  My fingers must be tired.

---

### Post by saj0577 on 2008-03-23
Good to hear.

Please mark thread as solved thank you.

Saj

---

### Post by moonbeam on 2008-03-23
> **jamiehendrich said:**
> **[SOLVED]**

Saj, thank you for your input.  

My sources.list was wrong.  It originally said something about "feisty avant-window-navigator on the last two lines.  My friend, oseph Millikan -- Linux expert --  figured it out and had me change the last two lines as follows and it works absolutely beautifully.    

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz(-Fusion), AWN and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

You should see my applets on  my AWN dock.  They spin if you click on system/preferences/AWN manager and then the "General" tab  and change "hover" to          "3D spotlight turn."   I love this.  It's just terrific.

Thank you, Joseph.

I believe that Treviño's repo has 0.2.1 of AWN.  Which is unstable.  At the very least it is old.  Anyway, do not be surprised if there are a variety of issues.

As of this time awn devs do not recommend that package:  [http://wiki.awn-project.org/DistributionGuides#Trevi.C3.B1o.27s_Ubuntu_Feisty_Repository](http://wiki.awn-project.org/DistributionGuides#Trevi.C3.B1o.27s_Ubuntu_Feisty_Repository)

The only recommended (by awn devs) Ubuntu repos are awn-testing, reacocard's, and the Ubuntu repos(only has awn core not extras)  themselves . 

I know reacocard no longer supports Feisty.  Our awn-testing repo has more recent (than 0.2.1) packages for Feisty:  [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)   They are bit of out date but should be a better bet than what you are using.

---

### Post by jamiehendrich on 2008-04-13
I have had no problem with my AWN dock until today.  There is a white vertical line that appears sometimes on the bar and it will not let me add an icon to the dock/bar.    Has my configuration file become corrupted?  Please advise if there is an easy fix.  I do not want to have to begin again from scratch.  That would not be a good thing.  Thank you in advance.

---

### Post by jamiehendrich on 2008-04-13
I have had no problem with my AWN dock until today. There is a white vertical line that appears sometimes on the bar and it will not let me add an icon to the dock/bar. 

Has my configuration file become corrupted? Please advise if there is an easy fix. I do not want to have to begin again from scratch. That would not be a good thing. Thank you in advance.

This is a new question.  The one above was marked "solved" and it is not quite solved yet.

---

