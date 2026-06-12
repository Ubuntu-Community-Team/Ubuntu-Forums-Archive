---
title: "No viruses or spyware?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-26
It seems that "most" viruses and spyware are either for microshaft or apple.As a new Linux disciple do I need to worry about this? And what about crashes. I use to use xp hoe and it was (is)n the biggest ram and cpu hore ever!! Linux seems more kind (except for java 1.5.0_05 based frostwire 4.10.5) As a new disciple how can I "max" my system out.? I'm using a 2.0 ghz p4 512 ram sony viao.
The i686 kernal just seemed to use more ram so I switched back to i386.

---

### Post by BoneKracker on 2006-03-27
If it's a personal-use machine, I wouldn't worry about viruses currently, but I would back up important files.

Your other questions are very general, but I'll try to answer (also, because of the nature of the question, be aware you would get a different answer from any one person who responds).

Linux is as stable as you make it.  Generally speaking, it will take a little bit of trial-and-error and adjustment before achieving stability on any system you haven't built before.  Once you've tinkered a bit, I think you will find it highly stable (my stable box runs weeks, months).  

Same goes for performance.  There are lots of techniques, but they vary as widely as the use cases for computing.  You can discover several common ones by searching within these forums with keywords like "optimization" and "performance".  Search the internet too.  Remember, though, defaults are generally set by someone who knew at least what you know (not necessarily about your particular situation).  Accept risks in areas where you're different from the norm; go with recommendations where you're the same.

Stability:
- don't be afraid to go back and do your install over (and over) even weeks later, when you learn you laid a poor foundation somehow.  "No man knows better how to build his house than the man who just finished."
- back up important files, and useful configuration files (if it took you more than 10 minutes to figure out, create, or edit a config file, you might want to keep it in case you need to reinstall).
- make conscious decisions about the risk you are willing to accept in exchange for potential gains in performance or functionality (manage the sources from which you download/install software)

Performance:
- once you have mastered a basic install and are comfortable with the system, consider learning to compile your own kernel from source (get rid of drivers for hardware you don't have, modularize stuff you use less than half the time, eliminate features you don't use) 
- consider compiling selected applications from source: ones that you use a lot, that have a number of non-essential features that might be optional in a compile, or that can be optimized for your hardware)
- tweak your X11 configuration (are you able to get DRI?), could you make do with 16-bit depth instead of 24?
- eliminate what you don't need (use BUM to prune services, turn off unecessary daemons, customize your crontab, only autoload the kernel modules you need, only allocate the number of RAM disks you need, only initialize the number of tty's you are likely to concurrently use, etc.)
- make conscious decisions regarding the trade-offs between performance and features that you may not need (e.g., eye candy, plug-ins, etc.)

---

### Post by wolfee on 2006-03-27
wow thanx!! I just got ubuntu 3 days ago and I luv it!! I have it as my main os I dont want to ever use microshaft again!! Your info is allot to chew on THANX!!!

---

### Post by Sef on 2006-03-27
Well actually almost all viruses, trojans, worms, and spyware are made for Windows because of the way it is designed.   Apple is based on BSD, which is direct decendent of Unix.  Linux is a clone of Unix, so it is not a direct decendant of it.

---

### Post by wolfee on 2006-03-27
I've even heard that some viruses are written my unix and linux people who hate microshaft!!! ther is a program called Automatix are there anymore like it? I even got an iso for it!!!

---

### Post by jason.b.c on 2006-03-27
> Automatix are there anymore like it? I even got an iso for it!!!

Automatix isn't viral!   I don't know were you got that idea from!..:confused: 

Automatix is to aid in the installing of new software/applications..:) 

And as far as i know there are'nt any virues out there for linux. I've been through this conversation before in this forum..:) 

No automatix is just to make it easier on you ( the home user ) to install the stuff you want in your system. :D

---

### Post by wolfee on 2006-03-27
No No No I didnt meam Automatix is a virus software I ment viruses that windows gets!!!

---

### Post by jason.b.c on 2006-03-27
> No No No I didnt meam Automatix is a virus software I ment viruses that windows gets!!!

Oh sorry, I guess i just didn't understand what you meant there. Sorry my fault!:(

---

### Post by Sef on 2006-03-27
[Quote]I've even heard that some viruses are written my unix and linux people who hate microshaft!!![Quote] 

Actually today most of viruses are written for profit.  Steal bank passwords, credit cards, and other numbers that can make you money.  today, very few are written by people who dislike microsoft or for kicks.

---

### Post by wolfee on 2006-03-27
Thats cool all you guys have been cool and patient with me!!! I'm VERY compulsive!! I WILL make a perfect Ubuntu software bundle for my friends!!!anymore packages like automatix or easy ubuntu that I can get iso's of?

---

### Post by akiro.yamamoto on 2006-03-27
Well if you want here is an additional resource..
[** Ubuntu DVDs **](http://cargol.net/~ramon/ubuntu-dvd-en)
These DVDs have the multiverse repos (no downloading) packages for all those
who need to install on systems without Internet Access ;)

---

### Post by wolfee on 2006-03-27
Thanx!!!! I will spread this software to all my friends!!

---

