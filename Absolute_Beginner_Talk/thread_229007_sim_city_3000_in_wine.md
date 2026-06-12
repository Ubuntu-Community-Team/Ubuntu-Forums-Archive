---
title: "sim city 3000 in wine"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by uraliss on 2006-08-03
Hi Folks,
Im pretty new to ubuntu but its fantastic!
I have a problem running simcity 3000 in wine though at the moment.

it installs ok but when i click on the sc3.exe using winefile i get this message in the terminal window;

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


Not sure how to fix it. Any ideas?

---

### Post by cantormath on 2006-08-03
test audio in wine
Code:

winecfg

Go to the Audio tab.
If it crashes follow the instructions here.
[http://www.ubuntuforums.org/showpost...65&postcount=7](http://www.ubuntuforums.org/showpost...65&postcount=7)

---

### Post by cantormath on 2006-08-03
This is how I do it from start to finish:

The easiest way to install wine is with Automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)


If you want to do it more manually.....
I think wine is in the normal repos. If not, uncomment the Universe repos in your /etc/apt/source.list

1 Install wine
Code:

sudo apt-get update
sudo apt-get install wine


2 Setup disc drives in wine
Code:

winecfg

Go to the Drives tab.
Press the Autodetect button.
Press the Show Advanced button.
Change the type of your CD drive(s) to CD-ROM.

3 Test audio in wine
Code:

winecfg

Go to the Audio tab.
If it crashes follow the instructions here.
[http://www.ubuntuforums.org/showpost...65&postcount=7](http://www.ubuntuforums.org/showpost...65&postcount=7)


NOTE
here are the bleeding edge repos for wine.

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

