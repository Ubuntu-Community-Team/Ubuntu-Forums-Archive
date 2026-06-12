---
title: "Help me ...now moved from windows to linux."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by new on 2006-09-03
Hi ... i have jus recently ...installed linux .ubuntu dapper drake. I have found a program to use my msn and to play mp3s ... but i still really dont know much about linux. I downloaded some programs from off of the internet and i got the files on the desktop but i cant get them installed cause it says linux doesnt use exe files...How do u install programs??? with Ubuntu. 

Also what are good P2P programs for ubuntu... and how do i install them ??

---

### Post by BatteryCell on 2006-09-03
First of all welcome to ubuntu :D 

Now then, onto buisness.  The first step is to figure out what os you installed (amd64 or i386 ?).  This is because some programs take extra configuration to get working on a64 systems.  Second, I would advise that you go to the HOWTO tips and tricks part of this forum, and click on the Automatrix thread.  Follow the directions there and run automatrix, this will install most of the most commonly used apps.  

Ubuntu is a distro baised off of the debian distro, therefore whenever you want to download something look for files named with the .deb extension
These are packages, a package is everything needed to run a program.  For instance lets say that you want firefox, go to a package manager (for example synaptic which can be obtained by opening up a terminal and running "apt-get install synaptic", without the quotes) and search for firefox, then once the results have come up, click on it and tell it to install, then click apply.  This downloads the firefox .deb file and then installs from it.  Note that if the program is already installed the square next to the name will be green.

The p2p client that I personally use is frostwire (a limewire clone). Depending on your architecture you have to install it differently though.
This probably doesnt answer all your questions, and if you have any more just post again and I'm sure someone will help :)

---

### Post by Omnios on 2006-09-03
First off Ubuntu has the synaptic package manager Menu / system / administration / synaptic package manager. WHich has like 18873 software packages very well organized into groups so you can look through them. Also you can download deb packages and tarballs and install them.
Here is alink to some guides on deb packages and tarballs
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)

 You might also want to read on adding extra repositories and backports for synaptic there is a lot of post on the forum and even a section with backports.

 I second Automatrix it will install some stuburn programs

---

### Post by GuitarHero on 2006-09-03
Go to applications> add/remove programs.  You can search for and easily install programs from there.  If you want more programs available in there you need to do this:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Frostwire is the best p2p program in my opinion.  Its in the repositories for easy installation.  The only way to install .exe's is using wine, but that doesnt always work.  Your best bet is to find linux equivilents.  I suggest Listen for mp3's and gaim for IMing.

---

### Post by orb9220 on 2006-09-03
[https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=gnome-panel](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=gnome-panel)
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by aysiu on 2006-09-03
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by *Zebedee* on 2006-09-03
Hi,
I am also new to linux and ubuntu. I recently installed ubuntu 6.06, downloaded from the net, over windows!
I do know that exe files are dos / windows, NOT linux, so they don't seem to work.
However, if you go to ...  Applications,  there is an option  'Add/Remove',
click it and you will find a table of available things to install, which are compatible with linux. They just arrive under 'Applications' when you confirm your choices.
I have used Xfmedia, it plays dvd's, seems to work ok!
I downloaded everything from the 'sound and video' section under 'Add/Remove', and clicked through them till one worked...  :) 

Hope this helps a bit, keep trying...

Regards Zebedee

---

### Post by new on 2006-09-03
Thank you for replying ... I am starting to love linux.... i will read some of your tips...i am not finding frostwire in my repositories ... anymore ideas ?

---

### Post by BatteryCell on 2006-09-03
Yea frostwire isnt in the repositories, to install it you have to go [here]("http://www.frostwire.com/") and click on the ubuntu/debian link, this will download the frostwire.deb to your desktop (assuming that firefox is set up to download to the desktop).
So then, in a terminal type:
```

cd /home/<YourUser>/Desktop
dpkg -i <nameofdeb>.deb 

```
Replace <YourUser> with the user that you downloaded the file as, and replace <nameofdeb> with the name of the downloaded .deb file.

Then you should be able to type "frostwire" into the terminal and it should start frostwire.

---

### Post by GuitarHero on 2006-09-03
oops sorry thought it was in there.  you can also just double click the deb file just like you would an exe file.

---

### Post by new on 2006-09-04
ammm i installed the frostwire by double clicking the .deb file and it is in my applications but it is not opening ! why is this ?? i really like linux but installing stuff sometimes is proving to be rather tideous ....

---

### Post by new on 2006-09-05
please help me ...i installed java runtime for the frostwire to work...since it isnt opening ... but it still not working ?? how do u configure it .... please help me this is getting rather fustrating ...

---

### Post by new on 2006-09-06
please help me ... ive tried everything and i cant get it configured ...my frostwire wont open at all ...

---

### Post by Tomosaur on 2006-09-06
You need to add the java installation directory to your PATH environmental varible. I don't know exactly how you installed java, but you should be able to modify this easily enough to reflect how where you have it installed:
1: Open a terminal
2: Type 'nano ./.bashrc'
3: Add this to the end of the file:
```
export PATH=$PATH:/bin/java/jdk1.5.0_07/bin
```
  but make sure to modify it for wherever you actually installed java
4: Log out and log back in again.

You say you installed the java runtime. I just use the jdk since I program in Java from time to time, and this is how I got frostwire to work. I would recommend you download the jdk since the runtime has given me nothing but trouble in the past.

---

### Post by redDEADresolve on 2006-09-06
Try Easy ubuntu: [http://easyubuntu.freecontrib.org](http://easyubuntu.freecontrib.org)
Helps set up Java, flash, mp3/DVD support and other cool stuff to get you started.

Made my install much easier.

---

### Post by new on 2006-09-07
Thank You...frostwire worked ...i guess the easy ubuntu installed everything i needed ... thanks alot ..i really am glad that i got it to work. Ubuntu rocks and it has a really good support community ..thanks alot guys ! So far my switch from windows is 2 weeks now and i am enjoying every minute of ubuntu with no regrets so far.

---

