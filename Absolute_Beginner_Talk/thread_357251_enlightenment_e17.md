---
title: "enlightenment e17"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-02-09
well i found the how-to on this and im gonna check it out....but for some reason i cant make the file that i need in /usr/share/xsessions.  i dont understand why i dont have the permissions to make a file.

---

### Post by taurus on 2007-02-09
Because you are not root.  If you want to create or edit something outside your $HOME directory, you need to use either sudo or gksudo.

Applications -> Accessories -> Terminal
```
gksudo gedit /usr/share/xsessions
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dragnazz5.0 on 2007-02-09
when i type that i get an error that says "cannot open file /usr/share/xsessions"

but i know it exists because i can get to it through the file browser

---

### Post by taurus on 2007-02-09
What's the output of this command from a terminal?

```
ls -la /usr/share/xsessions
```

---

### Post by dragnazz5.0 on 2007-02-09
total 16
drwxr-xr-x   2 root root 4096 2006-10-25 09:29 .
drwxr-xr-x 248 root root 8192 2007-02-09 01:05 ..
-rw-r--r--   1 root root 2948 2006-10-02 18:46 gnome.desktop

---

### Post by taurus on 2007-02-09
/usr/share/xsessions is a directory and you cannot edit a directory.  However, there is a file, gnome.desktop, in /usr/share/xsessions so you can edit that.

```
gksudo gedit /usr/share/xsessions/gnome.desktop
```

---

### Post by dragnazz5.0 on 2007-02-09
well the instructions say to add a file named e17.desktop to /usr/share/xsessions. and it seems that everyone else can do this except me.

---

### Post by taurus on 2007-02-09
```
gksudo gedit /usr/share/xsessions/e17.desktop
```

---

### Post by dragnazz5.0 on 2007-02-13
well...now that i have that figured out i get this error when i sudo aptitude install e17

Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%

---

### Post by taurus on 2007-02-13
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by tcrroadie on 2007-02-14
> **dragnazz5.0 said:**
> well...now that i have that figured out i get this error when i sudo aptitude install e17

Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%

What guide (instructions) are you using to install Enlightenment E17?  

Also, can you post the full aptitude install error message that you recieve before you select "Do you want to continue? [Y/n?]"

Thanks.

---

### Post by dragnazz5.0 on 2007-02-16
> **tcrroadie said:**
> What guide (instructions) are you using to install Enlightenment E17?  

Also, can you post the full aptitude install error message that you recieve before you select "Do you want to continue? [Y/n?]"

Thanks.

i followed your instructions that you posted back in december.  here is the install message i get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon 
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot 
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock 
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan 
  emodules0-all 
The following NEW packages will be automatically installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white eutils 
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 
The following NEW packages will be installed:
  enlightenment-theme enlightenment-theme-cthulhain 
  enlightenment-theme-darkness enlightenment-theme-kor 
  enlightenment-theme-milky enlightenment-theme-simply-white eutils 
  libecore1 libecore1-con libecore1-config libecore1-dbus libecore1-desktop 
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job 
  libecore1-txt libecore1-x libeet0 libevas1 libevas1-loader-eet 
  libevas1-loader-gif libevas1-loader-jpeg libevas1-loader-png 
  libevas1-loader-svg libevas1-loader-tiff libevas1-loader-xpm 
  libevas1-loaders-all libexml1 
0 packages upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.0MB of archives. After unpacking 22.8MB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment but it is not installable
  emodule0-wlan: Depends: enlightenment but it is not installable
  emodule0-language: Depends: enlightenment but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment but it is not installable
  e17: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-photo: Depends: enlightenment but it is not installable
  emodule0-deskshow: Depends: enlightenment but it is not installable
  emodule0-taskbar: Depends: enlightenment but it is not installable
  emodule0-flame: Depends: enlightenment but it is not installable
  emodule0-moon: Depends: enlightenment but it is not installable
  emodule0-mixer: Depends: enlightenment but it is not installable
  emodule0-rain: Depends: enlightenment but it is not installable
  emodule0-cpu: Depends: enlightenment but it is not installable
  emodule0-uptime: Depends: enlightenment but it is not installable
  emodule0-mem: Depends: enlightenment but it is not installable
  emodule0-net: Depends: enlightenment but it is not installable
  emodule0-tclock: Depends: enlightenment but it is not installable
  emodule0-snow: Depends: enlightenment but it is not installable
  emodule0-winselector: Depends: enlightenment but it is not installable
  emodule0-slideshow: Depends: enlightenment but it is not installable
  emodule0-alarm: Depends: enlightenment but it is not installable
  emodule0-weather: Depends: enlightenment but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy, edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy, edgy)]

Score is -128

Accept this solution? [Y/n/q/?] 


that is the first y/n/q part.


Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon 
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot 
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock 
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan 
  emodules0-all enlightenment enlightenment-data enlightenment-theme 
  enlightenment-theme-cthulhain enlightenment-theme-darkness 
  enlightenment-theme-kor enlightenment-theme-milky 
  enlightenment-theme-simply-white eutils libecore1 libecore1-con 
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas 
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt 
  libecore1-x libeet0 libevas1 libevas1-loader-eet libevas1-loader-gif 
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-svg 
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1 
The following NEW packages will be installed:
  e17 emodule0-alarm emodule0-cpu emodule0-deskshow emodule0-flame 
  emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon 
  emodule0-net emodule0-photo emodule0-rain emodule0-screenshot 
  emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock 
  emodule0-uptime emodule0-weather emodule0-winselector emodule0-wlan 
  emodules0-all enlightenment enlightenment-data enlightenment-theme 
  enlightenment-theme-cthulhain enlightenment-theme-darkness 
  enlightenment-theme-kor enlightenment-theme-milky 
  enlightenment-theme-simply-white eutils libecore1 libecore1-con 
  libecore1-config libecore1-dbus libecore1-desktop libecore1-evas 
  libecore1-fb libecore1-file libecore1-ipc libecore1-job libecore1-txt 
  libecore1-x libeet0 libevas1 libevas1-loader-eet libevas1-loader-gif 
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-svg 
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all libexml1 
0 packages upgraded, 55 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.1MB of archives. After unpacking 28.9MB will be used.
Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%


and thats the second part

---

### Post by dragnazz5.0 on 2007-02-16
> **taurus said:**
> Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

## E17 Repository "e17.dunnewind.net"
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) edgy e17

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

---

### Post by tcrroadie on 2007-02-16
Hi dragnazz5.0.

First question.  Are you using an apt preferences file?  /etc/apt/preferences

```
ls -l /etc/apt/
```

If so please check your apt preferences file for pinning of Enlightenment packages.  Please remove any listing of enlightenment pinning from your apt preferences file. 

What looks like is happening is apt is trying to install E16 in place of E17 because it thinks the E17 package (e17 16.999) is not available.

```
e17: Depends: enlightenment (>= 0.16.999) but it is not installable
```

Second.  Please only use one of the available repositories for E17.  They are both mirrored, so you only need one.  You can just comment out one of the repositories if you prefer.  For example, you can make it look like this. 
 
```
## E17 repository "edevelop.org"
#deb http://edevelop.org/pkg-e/ubuntu edgy e17
#deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

## E17 Repository "e17.dunnewind.net"
deb http://e17.dunnewind.net/ubuntu edgy e17
deb-src http://e17.dunnewind.net/ubuntu edgy e17
```

Then after you have checked the above, run these commands.

```
sudo apt-get update
```
```

sudo apt-get install e17
```

Please post back with your results.

---

### Post by dragnazz5.0 on 2007-02-16
Reading package lists... Done
E: Invalid record in the preferences file, no Package header

thats what i get after i did everything you said.  i removed all e17 stuff from my preferences file and uncommented one of the repos.

---

### Post by tcrroadie on 2007-02-16
One more thing before my head hits my pillow. 

Please post your apt preferences file.

```
cat /etc/apt/preferences
```

I'll get back with you tomorrow sometime. 

zzzzzzzzzzzzzz

---

### Post by dragnazz5.0 on 2007-02-16
there is nothing in that file actually

---

### Post by tcrroadie on 2007-02-17
Remove it. 
```

sudo rm /etc/apt/preferences
```

Then. 

```
sudo apt-get update
```

```
sudo apt-get install e17
```

Please post back with your results.

---

### Post by dragnazz5.0 on 2007-02-17
well i think it worked.  it installed everything and set it up.  so ill see what happens.  thanks for the help

it works.....and i love it.  now i just cant decide between this and fvwm-crystal.

---

### Post by tcrroadie on 2007-02-17
Great.  I'm glad you stick with it and got E17 installed.   

Thanks for posting back.  :-D

---

