---
title: "Help installing dangerdeep pl."
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-17
Hi

I have downloaded a game called Dangerdeep(looks very good! [http://dangerdeep.sourceforge.net/download.php](http://dangerdeep.sourceforge.net/download.php), and I downloaded this file: [http://prdownloads.sourceforge.net/dangerdeep/dangerdeep_0.1.1-1_i386.deb?download)](http://prdownloads.sourceforge.net/dangerdeep/dangerdeep_0.1.1-1_i386.deb?download)), and have a file on the Desktop called dangerdeep_0.1.1-1_i386.deb witch I want to install. To do that I typed this in the terminal; sudo dpkg -i dangerdeep with no luck then I tried sudo dpkg -i dangerdeep_0.1.1-1_i386.deb and with no luck](*,) 

I get this error:
dpkg: error processing dangerdeep (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 dangerdeep

What are the noob(me) doing wrong? 


And btw; the game x-moto in synaptic is very fun:-D

---

### Post by gareththegeek on 2006-11-17
Are you in your desktop folder in the terminal?

If I were installing it I would move the deb file to my home folder, and then open a command prompt and type

sudo dpkg -i dangerdeep*.deb

The * saves you typing all that version number junk :D

HTH
G!

---

### Post by Oki on 2006-11-17
Thanks:-)

I wrote dksudo nautilus and moved the folder to Home, then I entered your command witch gave me an error message. Then I typed sudo apt-get install -f And after that everything worked(I am new, so I dont know what I did he he).

The grafic in dangerdeep is very good!

---

