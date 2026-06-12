---
title: "apt-get error (and other issues)"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by aethernaut on 2006-09-16
First of all I'm (more or less) crossposting this from the Server Talk forum...after I posted it over there I realized that this might be the better place to ask such noobish questions; so this is a longer version of the first post.  If a mod could delete the first post (or tell me how to do it myself) I'd appreciate it.

  My story so far:

  I ran the install 'LAMP Server' option from the Server CD (this took some doing as I ended up needing to hit F6 and add "ide=nodma" at the end of the line before running the install; I still have no freakin' idea WHAT that command means or does, other than that it let me run the install!).

  The LAMP install ran smoothly but, as you might guess, left me stranded in The Command Prompt Wastelands with no idea what to do.

  After fighting with the command line for a day and a half (all of the tutorials that I've found tend to tell you to do something like type "vi <whatever>" and change such-n-such; but w/o telling you WHAT vi is nor HOW IT WORKS!!  Now, I've rooted around enough over the last few days to find the Vi Man page and I at least understand that it's a built in text editor...but since the book I'm reading "Beginning PHP5,Apache,and MySQL by Wrox" assumes that you're running everything from a desktop I decided to take the path of (HA!) least resistance and just install a desktop; assuming I could either uninstall it or just disable it at startup after everything was up and running.

  No dice: when I try to update apt-get I see an error that reads (in part): "Temporary failure resolving 'us.archive.ububtu.com' "

 ](*,) 

  I tried to sudo apt-get Kubuntu-desktop anyway (hope springing eternal and all that) but get this: 

"reading package lists...done"
"building dependancy tree....done"
"E: couldn't find package Kubuntu-desktop"

  Since this is an old box that had just been sitting here collecting dust for a few years I thought that it might just have a bad connection/network card; but I ran the Kubuntu Live CD to test that w/o any problems whatsoever (it didn't even take very long to load even on the piddly 250mb of RAM) and I even used the Konkeror(sp?) browser to surf here...in fact I'm making this post FROM the same machine using Kubuntu Live!!

  Does anyone have any idea why the Kubuntu Live CD would allow me to access the net but the LAMP set-up refuses to apt-get update?

  I'm neither lazy nor stupid...but my ignorance in this area is pretty profound; so very specifically what I'm trying to do is to set up a web server on my old system to run behind a router.  It might or might not eventually connect to the web as an http server (I haven't cleared it with my ISP although they do offer a plan with a static IP addy "for gaming") in the long term...in the short term I'm just trying to get the silly thing set up so I can work my way through this book and set up a few simple dynamic websites (if that's not oxymoronic) BEFORE I go to the trouble of registering a domain and looking for hosting ect ect.

  I'd really like to set this up correctly and I'm given to understand that that means a LAMP server w/o a GUI (less being more on a server) and then access it via another machine on the same router (in my Googling I saw several things mentioned, such as phpmyadmin, that looked like they might do the trick...but first I'd have to be able to actually ADD the apps to the server install!). 
 
  The machine I'm trying to use for this is an old AMD 750mhz with 250 mb RAM and a 10 gig HD behind a Linksys 4 port router.

I can't imagine that this is an unusual project but I've not seen anything in my wandering to baby-step me through it so any advice would be welcome.

:-)

---

### Post by bulldog on 2006-09-16
I did it with this HowTo.

Maybe it get's you out of the dark.

[http://ubuntuforums.org/showthread.php?t=223410&highlight=HowTo+install+LAMPP](http://ubuntuforums.org/showthread.php?t=223410&highlight=HowTo+install+LAMPP)

[It's LAMPP btw]

---

### Post by aethernaut on 2006-09-16
Thanks for the quick reply!

I looked through the thread you posted but it's not exactly what I'm looking for.  I don't want to download yet another install when I ALREADY have the Ubuntu LAMP Server installed and running...I just can't do anything with it as is o_o

I saw this link in the thread you posted (towards the end): 

[http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)

and that's more or less exactly what I'm after: setting up the server on one machine to be accessed by others on the same network...however the same problem as in the title of this thread still applies: I cannot apt-get the desktop!!!!

---

### Post by bulldog on 2006-09-16
Well installing a desktop isn't that hard to do.

I'm not sure if you want to install the kubuntu on your system,because,well let's face it,it's not that state of the art.

But to install the ubuntu desktop just do

sudo aptitude install ubuntu-desktop

This should do the trick.

If you get an error try to switch your us to something else [I use nl and works fine]
It all depends where you live offcourse but only to take a look if it works for now.

---

### Post by aethernaut on 2006-09-16
I ran both the ubuntu and kubuntu live CDs just to get the feel of them and I liked the KDE interface much more than the GNOME interface; but that's nither here nor there : )

I tried to run what you suggested and it is still telling me that it "couldn't find any package whose name or discription matched "ubuntu-desktop" so aptitude doesn't work any better than apt-get does ::::sigh:::

](*,) 

How do I change the us to nl? (other than reinstalling the whole thing and telling it I live in Amsterdam?) :::I don't, I live in the USA, but I'll claim I'm in Botswana if it'll make the commands work like they should!:::

---

### Post by bulldog on 2006-09-16
Did you unlock your repositories in synaptic,Universe and Multiverse?

If you didn't do so,I think you have only the security update's unlocked.

Go to administration--synaptic and tab configuration.
There should be something about your repositories and click them all [not the cd]

Then do 

sudo aptitude update

sudo aptitude install kubuntu-desktop

It should work.

When I read
No dice: when I try to update apt-get I see an error that reads (in part): "Temporary failure resolving 'us.archive.ububtu.com' "
it did me think your repositories where at maintanance or otherwise not reachable.

---

### Post by aethernaut on 2006-09-16
> **bulldog said:**
> Did you unlock your repositories in synaptic,Universe and Multiverse?

<<snip>>

Go to administration--synaptic and tab configuration.
There should be something about your repositories and click them all [not the cd]

  You're forgetting the whole thing started with my trying to add a desktop :biggrin: 

  How would I do this from the commandline; because I don't have any tabs to click at present?

> 
When I read
No dice: when I try to update apt-get I see an error that reads (in part): "Temporary failure resolving 'us.archive.ububtu.com' "
it did me think your repositories where at maintanance or otherwise not reachable.

  I noticed this as well...but I've tried several times over the last two days and gotten the same error message; so I suspect you're correct in that I need to unlock something first; the only question now is how to do so?

and thank-you, btw,  for taking the time to help.

---

### Post by bulldog on 2006-09-16
Stupid me,yes I forgot :-\" 

Okay I think you can get to your sources.list by doing

sudo nano /etc/apt/sources.list

Make a backup first.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

You can put my repo's in there so it should work.

When you've got your desktop you can replace everything with your own.




####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main #restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

But they should be in your sources.list.
If so you just can uncomment them [remove the # in front]

Then do  sudo aptitude update
and      sudo aptitude install kubuntu-desktop

---

### Post by aethernaut on 2006-09-16
nope...I copied the file and edited it in Vi (and then checked to be sure that I had made the changes) but it still throws the same errors:

"Temporary failure resolving 'archive.ububtu.com' "

<a whole string of these>

  Of course I made my list match exactly what you have posted above (meaning I deleted the "us." at the front of most of the URLs)....I'm going to go back and add in "nl." in front of them just to see if it makes any differance (can't hurt).

---

### Post by aethernaut on 2006-09-16
...and that doesn't work either.

How can I be connected to the net (remeber that I posted the first part of this thread FROM the computer in question via the Kubuntu Live CD's browser) but apt-get refuses to connect??

  I've just changed every url to read: as follows: 'nl.archive.ubuntu.com' (adding 'nl' where 'us' was before); I also tried simply killing the prefix as in the examples posted above.

:::much wailing and gnashing of teeth::::#-o 

ah well...I learned how to copy/duplicate a file and I can get into and out of Vi without it BEEPING at me more than a half dozen times or so...I guess it's not a total loss :frown:

---

### Post by aethernaut on 2006-09-16
OK I reinstalled the LAMP Server over the top of the first install and now it works fine!!

Here is the only thing I can figure: when I ran the first install the old system wasn't connected to the net (didn't have an extra cable at the time).  I hooked it up later when I tried to apt-get the first time and although that failed it WAS connected when I ran the Kubuntu Live CD...so apparently there is/was something that I would have needed to fiddle with to tell the system to recheck the connections before apt-get could see the net?

At any rate it took less than 30 min to re-install and now I can apt-get myself silly! =D> 

I feel a little foolish having not thought to post this at the very start but hopefully someone else will see this and not make the same silly mistake :roll: 

Thank-you again for your help!

---

### Post by Biker45 on 2006-09-16
Well I'm glad everything is turned allright for you.

---

