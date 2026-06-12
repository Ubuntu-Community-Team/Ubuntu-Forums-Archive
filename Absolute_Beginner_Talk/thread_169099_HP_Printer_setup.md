---
title: "HP Printer setup"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by darquemeye on 2006-05-01
Ok I just wanted to share this info. I was having problems setting up my HP Officejet g85xi. I found this website [HPLIP]("http://hplip.sourceforge.net"). Go to the downloads and download the tar.gz file and save it in your home dir. then just follow the instructions for UBUNTU! It worked great for me! So glad i found it.

---

### Post by user1397 on 2006-05-01
You could also follow the guide in my signature :)

---

### Post by catlett on 2006-05-01
This was the post that did it for me.
> 
wondering_jew
	
 Re: Help installing HP PSC 1610 in Ubuntu
hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.
__________________
#373563

"Be a philosopher; but amidst all your philosophy, be still a man." - David Hume

---

### Post by Sef on 2006-05-01
I used wondering_jew's info to get my HP 1610 up and running when I was using Breezy.  With Dapper, I just went into the printer menu and it worked.

---

### Post by Brando569 on 2006-06-18
i have a hp psc 1610 also but nothing seems to work for me, i always get this:

Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1

---

### Post by z_diver on 2006-07-03
[quote=Brando569]i have a hp psc 1610 also but nothing seems to work for me, i always get this:

Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]
[COLOR=Red] invoke-rc.d: initscript hplip, action "start" failed.[/COLOR]
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1[/quote] 
I also had this issue on one of my Dapper machines.  I fixed it by running: ```
sudo aptitude purge hplip
``` which removed all of this.

The following packages are unused and will be REMOVED:
[COLOR=DarkRed]   brltty brltty-x11 festival festlex-cmu festlex-poslex festvox-kallpc16k
  gcc-3.3-base gnome-accessibility-themes gnome-mag gnopernicus gok
  gtk2-engines-highcontrast hplip-data landscape-client libbrlapi1
  libestools1.2 libgail-gnome-module libgnome-mag2 libgnome-speech3
  libstdc++5 screensaver-default-images tangerine-icon-theme
  tango-icon-theme tango-icon-theme-common ttf-gentium ttf-lao
  xcursor-themes[/COLOR]
The following packages will be automatically REMOVED:
[COLOR=DarkRed]   ubuntu-desktop[/COLOR]
The following packages will be REMOVED:
[COLOR=DarkRed]   hplip{p} ubuntu-desktop[/COLOR]

I then reinstalled hplip([COLOR=Blue]sudo aptitude install hplip[/COLOR]) and after there were no errors, I installed [COLOR=Blue]ubuntu-desktop[/COLOR] the same way.  Problem solved.

---

### Post by cowley on 2006-07-03
ubuntu is the best! i have a photosmart hp printer. with xp that can be a pain to set up. with ubuntu i plugged it in and turned it on, 30 secs later i was printing!  fantastic!

---

### Post by Brando569 on 2006-07-04
didnt help there still only 4 printers (LaserJet 1000, 1005, 1020 and 1500) listed under HP :( btw im using KDE 3.5.3 if that matters any (i dont think it would)

---

