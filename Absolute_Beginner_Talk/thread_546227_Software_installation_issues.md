---
title: "Software installation issues"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Norm24 on 2007-09-08
I'm new to this Ubuntu/Linux.Been a Windows guy for way to long.Anyway...a few questions for the more knowledgeable.

First I've tried installing the ClamTk AV scanner but when I go to use it I'm notified that I don't have any definitions and when I try to download definitions I'm notified that I must be logged in as root.From what I've gathered that's impossible as I don't know the password and am not supposed to know.I've also discovered that root can't be logged in from the login screen.

The other AV,Aegis installs just fine but can't find it in order to launch it,Its supposed to be in the accessories menu but its not.

Lastly how on Earth do I install software that's not on the add/remove list or Synaptic package manager list?And doing it through terminal is a pain in the ***.I really would like to use newer and or better versions of a lot of the software on these lists.A perfect example would be Avira's free AV,best free av going.Avira has a Linux version but I can't figure out how to install it.

I've read ALL of the documentation I could find before I posted here.I would appreciate all the help any here can give me......and patience with a newbie.Thanks.

I REALLY don't want to go back to Windows.

---

### Post by marco123 on 2007-09-08
Firstly, relax,- you don't have to worry about viruses or spyware anymore.:) (Or filesystem fragmentation.)

Lots of newer versions are available in .deb installation packages.  Try - [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Norm24 on 2007-09-08
15 years of Windows and you get set in your ways:).

---

### Post by bodhi.zazen on 2007-09-08
Ubuntu uses sudo, so 

sudo <command>

Enter you login password (you will not see anything on the screen as you type)

to log in as root

sudo -i

see [uwiki]Rootsudo[/uwiki]

And for security issues : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by cotcot on 2007-09-08
First of all welcome.

The software available through synaptic is pretty up to date, at least when you update the package list from time to time. (it is in synaptic)

Have you enabled the "multiverse" and "universe" repositories as mentions in the docs ?
There are also other repositories (not supported by ubuntu but possible to use) where you might find more recent software.  (marillat)

After all I am a little bit surprised with you search after more recent software. Please know that you are asking for software that might be unstable. If you want you can compile source code (.tar) by yourself to install the software you want.

Giving a couple of examples (other than virus scanners) might help to understand what you are missing.

---

### Post by marco123 on 2007-09-08
> **Norm24 said:**
> 15 years of Windows and you get set in your ways:).

I was exactly the same.:)  Now I wonder why I wasted all that time scanning my PC, defragmenting and reinstalling when I could have been just been using my computer.

My Linux maintenance consists of shutting my PC down every few months and cleaning the dust out from inside it. :lolflag:  I don't even need to restart it.:)

Edit:  Sometimes new .debs can be found on the forums as well.

---

### Post by Norm24 on 2007-09-08
> **marco123 said:**
> I was exactly the same.:)  Now I wonder why I wasted all that time scanning my PC, defragmenting and reinstalling when I could have been just been using my computer.

My Linux maintenance consists of shutting my PC down every few months and cleaning the dust out from inside it. :lolflag:  I don't even need to restart it.:)

Edit:  Sometimes new .debs can be found on the forums as well.

All the maintenance with Windows really does get old and its one of the main reasons I need to get away from it.That and the fact that some of the solutions for bizarre error codes are absolutely insane.

---

