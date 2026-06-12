---
title: "installing wine"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-12-17
I want to install wine on my computer, any help?

---

### Post by Rackerz on 2006-12-17
Get automatix, [http://www.getautomatix.com](http://www.getautomatix.com) then run winecfg after it's installed.

Then to run a program with Wine do this:
> sudo wine ~/Desktop/install.exe

---

### Post by lordvolo on 2006-12-17
can i install it via terminal in the repositories? the automatix database is down

---

### Post by meng on 2006-12-17
Yes you don't need to use automatix. In fact wine is in the official repositories, I can't remember if you need universe or multiverse enabled though. It's not THE latest version, but you can enable yet another wine-specific repository (budgetdedicated) for the bleeding edge version.

sudo aptitude install wine

---

### Post by arnieboy on 2006-12-17
> **lordvolo said:**
> the automatix database is down
no. it isnt. only the home page is down.

---

### Post by a.v.l on 2006-12-17
> **Rackerz said:**
> Get automatix, [http://www.getautomatix.com](http://www.getautomatix.com) then run winecfg after it's installed.

Then to run a program with Wine do this:

Apologies for butting in here but I'm also trying to use wine from the repositories.  I've downloaded and installed wine from the repository and when I type in wincfg in the terminal  I  get a wine configuration window open.  The Wine configuration window opens, with Windows 2000 version selected.   When I click OK this is the terminal response.

" wineserver: could not save registry branch to /home/joe/.wine/system.reg : Permission denied"   

I'm lost at this point, can someone help please.I'm hoping to install Photoshop 7

---

### Post by meng on 2006-12-17
> **a.v.l said:**
> Apologies for butting in here but I'm also trying to use wine from the repositories.  I've downloaded and installed wine from the repository and when I type in wincfg in the terminal  I  get a wine configuration window open.  The Wine configuration window opens, with Windows 2000 version selected.   When I click OK this is the terminal response.

" wineserver: could not save registry branch to /home/joe/.wine/system.reg : Permission denied"   

I'm lost at this point, can someone help please.I'm hoping to install Photoshop 7
I'm not sure of the reason for that error message, perhaps you could show the result of:
ls -l .wine
ls -l .wine/system.reg

BUT on another point, are you aware that many users have reported difficulty in getting Photoshop 7 to work with wine? I've never tried this myself, but I get the impression that any version newer than 5 is a b*tch to run. Perhaps if it all doesn't work out, and you need to use Photoshop (i.e. GIMP is not an option) then look into Crossover Office, you may have better luck there and there is a free trial available.

---

### Post by a.v.l on 2006-12-17
> **meng said:**
> I'm not sure of the reason for that error message, perhaps you could show the result of:
ls -l .wine
ls -l .wine/system.reg

BUT on another point, are you aware that many users have reported difficulty in getting Photoshop 7 to work with wine? I've never tried this myself, but I get the impression that any version newer than 5 is a b*tch to run. Perhaps if it all doesn't work out, and you need to use Photoshop (i.e. GIMP is not an option) then look into Crossover Office, you may have better luck there and there is a free trial available.
------------------------------------------------------------------------------------------
The results  of pasting
ls -l .wine
ls -l .wine/system.reg can be seen below.


 ls -l .wine
total 280
drwxr-xr-x 2 root root   4096 2006-12-03 18:49 dosdevices
drwxr-xr-x 4 root root   4096 2006-12-03 18:49 drive_c
-rw-r--r-- 1 root root 246625 2006-12-17 15:33 system.reg
-rw-r--r-- 1 root root   2277 2006-12-17 15:33 userdef.reg
-rw-r--r-- 1 root root  17897 2006-12-17 15:33 user.reg

 ls -l .wine/system.reg
-rw-r--r-- 1 root root 246625 2006-12-17 15:33 .wine/system.reg

Thanks for the tip about Photoshop 7..... I would still like to get wine to work if possible. Can anyone help me do that please.

---

### Post by arnieboy on 2006-12-17
u ran
```
sudo winecfg 
```
which was not a good idea (it changed your directory permissions)
do the following to set it back:
```
sudo chown -R **jack**:**jack** /home/**jack**/.wine
```
and replace jack with your user name
then run
```
winecfg
``` to configure wine the right way

---

### Post by jvc26 on 2006-12-17
Photoshop wise, again haven't had time to try this one myself but will soon found it yesterday [http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)
may be worth a shot if you have CS2.
Il

---

### Post by a.v.l on 2006-12-17
> **arnieboy said:**
> u ran
```
sudo winecfg 
```
which was not a good idea (it changed your directory permissions)
do the following to set it back:
```
sudo chown -R **jack**:**jack** /home/**jack**/.wine
```
and replace jack with your user name
then run
```
winecfg
``` to configure wine the right way

No I didn't use Sudo winecfg,  I just typed in winecfg and pressed enter. Have I  still goofed up and should I  do as you've recommended to recover?

---

### Post by arnieboy on 2006-12-17
if you are not running Ubuntu as root (I hope you are not), then yes you should.

---

### Post by a.v.l on 2006-12-17
> **arnieboy said:**
> u ran
```
sudo winecfg 
```
which was not a good idea (it changed your directory permissions)
do the following to set it back:
```
sudo chown -R **jack**:**jack** /home/**jack**/.wine
```
and replace jack with your user name
then run
```
winecfg
``` to configure wine the right way

Having followed the advice above I have been able to install Photoshop 7 it seems, at least I went throught the  whole installation procedure using the Photoshop7 CD.  Unfortunatly I didn't notice where it was installed, I think the default programes folder as in windows.  I cannot see the installation now and would like to reinstall it somewhere else. Where is the recommended location to install this software to please?
Thanks for the advice above it has allowed me to progress with Wine.

---

### Post by arnieboy on 2006-12-17
look under **.wine** in nautilus (file manager, press ctrl-H to make hidden files visible). you should see "drive_c" under that. Under that you will see the usual windows tree (program files, windows, and the other usual windows directories). Photoshop will be in program files.
double click the correct exe to get photoshop running.

---

### Post by bsell on 2006-12-17
> **a.v.l said:**
> Having followed the advice above I have been able to install Photoshop 7 it seems, at least I went throught the  whole installation procedure using the Photoshop7 CD.  Unfortunatly I didn't notice where it was installed, I think the default programes folder as in windows.  I cannot see the installation now and would like to reinstall it somewhere else. Where is the recommended location to install this software to please?
Thanks for the advice above it has allowed me to progress with Wine.

WINE treats the Linux partition as the Windows C drive. Aysui has a [nice Ubuntu tutorial]("http://www.psychocats.net/ubuntu/wine") on WINE and where to install progams. Check it out. 

WINE is updated frequently and the repos don't usually have the latest release. If you want to run the lastest release, you can add ```
deb http://wine.budgetdedicated.com/apt edgy main 
```to your repositories.

---

### Post by a.v.l on 2006-12-17
> **arnieboy said:**
> look under **.wine** in nautilus (file manager, press ctrl-H to make hidden files visible). you should see "drive_c" under that. Under that you will see the usual windows tree (program files, windows, and the other usual windows directories). Photoshop will be in program files.
double click the correct exe to get photoshop running.

I've found Photoshop 7 folder by doing as you sugged but can't open the program?  When I click on the folder name it opens and I can see all the files but where do I go from there please. I'm sure I'm very close now.

---

### Post by arnieboy on 2006-12-17
look for files with extension **.exe** in that folder. there shouldn't be too many. one of them is the photoshop executable. double click that.

---

### Post by a.v.l on 2006-12-17
> **arnieboy said:**
> look for files with extension **.exe** in that folder. there shouldn't be too many. one of them is the photoshop executable. double click that.

I did try .exe files but the only one which opened was "Image Ready.exe"  but its appearance was missing some tool bars.  Photoshop 7.exe refused to open at all.  Does that mean the end of my chances of being able to use it in Ubuntu?

---

