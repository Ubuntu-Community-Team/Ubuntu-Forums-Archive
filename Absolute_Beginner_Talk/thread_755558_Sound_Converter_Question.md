---
title: "Sound Converter Question"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Spline64 on 2008-04-15
K...I downloaded sound converter -1.0.0
Is in my Home directory and also the desktop (lol old windows habbit) and when I run:

[I]pat@daddy:~$ sudo apt-get install soundconverter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package soundconverter[/I]

Look I know I am stupid, (spent 2 hours reading and messing around) just tell me what I am doing wrong!! Tried using synaptic as well doing a search and can't add. God please tell me I am an idiot and give the solution.:confused: I really want to adopt this OS. 

running Gutsy Gibbon 7.10

thanks,
Spline64

---

### Post by cm.squared on 2008-04-15
Don't be so hard on yourself.  Everyone starts out as a noob.  You probably don't have all of the repositories you need.  You can enable these in Synaptic with by going to Settings > Repositories and checking the Multimedia (universe) box.  You should then be able to find soundconverter and install it.

It sounds like you downloaded the source code, which would require you to compile it.  If you enable the repositories from the package manager you shouldn't need to do this.

---

### Post by Sinkingships7 on 2008-04-15
yup. after you enable the multiverse repos (as stated in above post), just run
```
sudo apt-get install sound-converter
```

---

### Post by Spline64 on 2008-04-15
thanks for the quick reply but same deal. Did enable the universe in synaptic and used the same command. any ideas?

---

### Post by Spline64 on 2008-04-15
thanks but using the dash gives me

pat@daddy:~$ sudo apt-get sound-converter
E: Invalid operation sound-converter

---

### Post by Sinkingships7 on 2008-04-15
EDIT: nevermind. you answered my question while i was posting ;D

EDIT of the EDIT: the error you got was because you said;
```
sudo apt-get sound-converter
```
you should have said:
```
sudo apt-get install sound-converter
```

---

### Post by Spline64 on 2008-04-15
damn thought you had it lol...I still get:

pat@daddy:~$ sudo apt-get install sound-converter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sound-converter

---

### Post by cm.squared on 2008-04-15
When I search for sound converter the package has no hyphen.  It's just called "soundconverter".

---

### Post by Sinkingships7 on 2008-04-15
let's see if this makes a difference:

System -> Administration -> Software Sources
Click the tab that says "Third-Party Software".
Make sure those two boxes are checked.
Press close and agree to reload.

Open a terminal and run:
```
sudo apt-get update
```
and then run:
EDIT: i was wrong about the dash... this is the code you need to run:
```
sudo apt-get install soundconverter
```

---

### Post by Mellon on 2008-04-15
yup, seems like you missing the update part.

---

### Post by Sinkingships7 on 2008-04-15
i've got to go to bed lol

if what i just said didn't work, then i have one more idea for now:

extract the tar.gz onto your desktop, if not already done.

rename the folder to "soundconverter" without the quotes (just for ease of typing with the following commands lol)

open a terminal and navigate to that folder using this command:
```
cd ./Desktop/soundconverter
```

that command assumes that you renamed the folder appropriately.

next, type these commands, in this order, into the terminal:
```
./configure
make
make install
```

hopefully you get no errors.

---

### Post by Spline64 on 2008-04-15
sinkingships7!!!

you rock...that did it thanks much for going the extra mile with me!

spline64

---

### Post by Sinkingships7 on 2008-04-15
> **Spline64 said:**
> sinkingships7!!!

you rock...that did it thanks much for going the extra mile with me!

spline64

no problem :D

for future readers, can you tell me (them) which method worked?

---

### Post by Spline64 on 2008-04-15
Sweet!!

Yes this would have saved much time...thanks again all of ya and for all here is the solution provided by Sinkingships7


Le[B][I]t's see if this makes a difference:

System -> Administration -> Software Sources
Click the tab that says "Third-Party Software".
Make sure those two boxes are checked.
Press close and agree to reload.

Open a terminal and run:
Code:

sudo apt-get update

and then run:
EDIT: i was wrong about the dash... this is the code you need to run:
Code:

sudo apt-get install soundconverter
[/I][/B]
I then saw:
pat@daddy:~$ sudo apt-get install soundconverter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gstreamer0.10-plugins-ugly gstreamer0.10-lame gstreamer0.10-ffmpeg
The following NEW packages will be installed:
  soundconverter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.4kB of archives.
After unpacking 438kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe soundconverter 0.9.6-1 [67.4kB]
Fetched 67.4kB in 3s (17.6kB/s)        
Selecting previously deselected package soundconverter.
(Reading database ... 92148 files and directories currently installed.)
Unpacking soundconverter (from .../soundconverter_0.9.6-1_all.deb) ...
Setting up soundconverter (0.9.6-1) ...

pat@daddy:~$ 

hope this helps everyone

spline64

---

### Post by Ripfox on 2008-04-15
For future reference you must always reload or update your repos after changing or adding new ones before you attempt to install new software. :)

---

### Post by Spline64 on 2008-04-15
a painful lesson....I sure hope other newbies read this. 

thanks!

Spline64

---

