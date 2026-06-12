---
title: "want progz without terminal installs"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by koganinja89 on 2007-07-21
1. don't have good internet on MY computer.

2. neighbor has dedicated connection, DLs at 500+ KB/s (Awesome).

3. no good sites with packages by the masses for Debian.

4. I have a 2g thumb drive and need KDE and stuff.

5. Not a noob; just when it comes to debians lack of do-it-your-selfness.

---

### Post by koganinja89 on 2007-07-21
please help

---

### Post by forestpixie on 2007-07-21
what is it that you actually want?

---

### Post by koganinja89 on 2007-07-21
I don't want one program, I want a way to find/get/DL debian progz and put them on my thumb drive to install on my linux machine via someone else's internet and none of this terminal crap :) NO GOOD INTERNET

---

### Post by por100pre1 on 2007-07-21
You can try to get a Kubuntu CD, if you have Ubuntu already installed it will detect the CD as a local repo. Then you can install kubuntu-desktop or kde.

I'm just assumin'... I didn't understand much neither :confused:

---

### Post by forestpixie on 2007-07-21
you could look here but not really sure what programs you're looking for

[http://linuxappfinder.com/](http://linuxappfinder.com/)

[http://www.getdeb.net/](http://www.getdeb.net/)

[http://www.freesoftwaremagazine.com/blogs/weekly_tip_finding_installing_deb_files](http://www.freesoftwaremagazine.com/blogs/weekly_tip_finding_installing_deb_files)

and don't shout

---

### Post by kavon89 on 2007-07-21
> **koganinja89 said:**
> I don't want one program, I want a way to find/get/DL debian progz and put them on my thumb drive to install on my linux machine via someone else's internet and none of this terminal crap :) NO GOOD INTERNET

Rough translation to English.

> I want someone to tell me how to download the .deb packages & programs, possibly from the repositories, with my neighbor's PC to my USB drive. Then I want to install them on my Ubuntu PC, which lacks the proper bandwidth for the download, without using the terminal. :) 

Are you using the Debian based Ubuntu, or just straight Debian?

---

### Post by koganinja89 on 2007-07-21
> **por100pre1 said:**
> You can try to get a Kubuntu CD, if you have Ubuntu already installed it will detect the CD as a local repo. Then you can install kubuntu-desktop or kde.

I'm just assumin'... I didn't understand much neither :confused:

I tried that and for some reason it would not let me install anything off of the CD and now my computer is having troubles with file permissions I will probably reinstall

---

### Post by koganinja89 on 2007-07-21
> **kavon89 said:**
> Rough translation to English.

thax I am just frustrated, it just seems like there are no tolerations to people with no internet now adays

---

### Post by annda on 2007-07-21
[http://packages.ubuntu.com](http://packages.ubuntu.com)

you will have to download the dependencied too (they are listed). you probably have most of them installed, but there is no way of telling except going through the install precess.

i suggest going to synaptic, checking the program you want to install and noting down the dependencies it says it needs. download them all and install (simple double-click) from the thumb drive - start with the dependencies.

kde is huge, so i suppose downloading kubuntu at your friend's, burning and adding the cd to the repositories is the easiest way to install that.

---

### Post by Old Pink on 2007-07-21
Go to your neighbours house, boot a Ubuntu live CD, stick in a pen drive, use ```
cd /media/USB-NAME
sudo aptitiude download <application>
```Download the .debs to your memory stick, go next door, plug in and install. :) 

Or buy the Ubuntu DVD, $9.99 add it as a repo and use the apps on there?
[http://www.amazon.com/Canonical-Ubuntu-7-04-PC-Edition/dp/B000PSWZSC/ref=pd_bbs_1/103-8062989-8637455?ie=UTF8&s=software&qid=1185055310&sr=8-1](http://www.amazon.com/Canonical-Ubuntu-7-04-PC-Edition/dp/B000PSWZSC/ref=pd_bbs_1/103-8062989-8637455?ie=UTF8&s=software&qid=1185055310&sr=8-1)

---

### Post by koganinja89 on 2007-07-21
thax for all of your help, and that last bit of shell script.

---

