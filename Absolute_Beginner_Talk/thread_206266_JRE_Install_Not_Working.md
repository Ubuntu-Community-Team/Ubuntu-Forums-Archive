---
title: "JRE Install Not Working"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by ravenproject_two on 2006-06-29
[B]I just got done installing JRE before bed last night-the goal was to install Limewire Basic on my sys...I got into adept and changed my repos settings so that Multi-verse is included and even then I still had problems...a cat named Sas bailed me out by having me try a command in konsole:

sudo apt-get update && sudo apt-get install sun-javba5-bin

Or something to that affect-I cannot find the thread we were talking on last night but anyways-it worked and sun-java5-bin was installed on my os...now I downloaded limewire...created a debian pckg with the alien utility, installed that dpkg amd it does not work-it says that I don't have a valid JRE and that I need to go to sun.com and get one...what the #####???   What do I have to do now?  Can anyone help?  I searched for some time for answers on my own-I am new to the forum thing but I didn't get results-either the inst. were for the wrong dist or thtey didn't work or did not apply...I need help-all I want is my music back and I refuse to go crawling back to Windows-I set up a single boot configuration for a reason; Me and Linux are going to ride win or lose-I refuse to give up until I have it mastered....any help is greatly appreciated...sorry I am such an incompetent little dumbass everyone....The RavenProject:confused: [/B]

---

### Post by woedend on 2006-06-29
try this
sudo apt-get install sun-java5-jre

if it fails/doesnt find it, skip that, it may not be a valid package anymore OR it may already be installed(i dont have ubuntu to look at it).  Then, importantly, run
sudo update-alternatives --config java

and select the one you just installed

---

### Post by ravenproject_two on 2006-06-29
Dude, You f'in rock man--worked!!!  I put in
Code:

sudo apt update-alternative --config java

and it gave me three options, the default was set on the wrong one so I switched and Limewire is working now...Can you explain what I did?  I mean I do not want to bother you but would just like to know so that I can learn?  Thank you dude...Lifesaver

The RavenProject=D> =D> =D>

---

### Post by woedend on 2006-06-29
If im not mistaking(then again I usually am), ubuntu comes with some sucky free implementation type java(openoffice uses it I think).  Most java programs you would use want sun's java.  For some reason beyond me this isn't changed automatically(or at least an option?) when you install sun's java.

---

### Post by ravenproject_two on 2006-06-29
So by using the command that you gave me- that is how I access the options for how my system uses java?  Or better-which java my sys uses?

---

### Post by woedend on 2006-06-29
exactly.

---

