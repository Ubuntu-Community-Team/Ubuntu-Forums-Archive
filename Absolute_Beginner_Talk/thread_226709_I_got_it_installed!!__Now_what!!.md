---
title: "I got it installed!!  Now what??!!??"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by mattatkins on 2006-07-31
OK ok..  I know this is the place for beginners to feel safe, and I know that they say there is no such thing as a stupid questions.... butttt......

I have decided to try out Linux, and I decided on Ubuntu.  I downloaded the install disk, and much to my surprise, everything went as planned, without a hitch.  I couldn't believe it.  I was so excited that I booted up the PC, and waited for a pretty GUI..  waited.. waited.. but all I see is white text on a black background!!  I can get logged in, but what the heck do I do next?  I have not the slightest clue on Linux commands, and I was definitely expecting to see at least a little bit of a GUI...  

Please be gentle..  I was born and raised on Microsoft...

Thanks. 

Matt Atkins

---

### Post by Nano Geek on 2006-07-31
Did you download the server disk or the desktop one?

---

### Post by aysiu on 2006-07-31
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Tomosaur on 2006-07-31
Interesting. You should indeed be seeing a GUI. Please let us know what hardware you're using (particularly your graphics card). Ubuntu uses X to render its GUI, and as with any software, it occasionally needs additional setup, or has bugs which need ironing out. If you tell us your hardware we may be able to see what's going on.

In the meantime, try logging in using the terminal (or, the white text on black background :P), and type 'startx'. This should theoretically start up the x server, and allow you to see a GUI. It should generally just start automatically though, especially since this is a clean install.

Ah yes, if you downloaded the server disk, it's easy to see why you could have this problem. Double check which one you downloaded.

---

### Post by cantormath on 2006-07-31
you installed the server version.

install the gui.
type this into terminal


~$ sudo apt-get update

~$ sudo apt-get install ubuntu-desktop

type y if prompted.

reboot 

If you have a gui-windows like interface, then you did right.
If it's still screwed up, just get the right disk.
you want the Desktop CD, not the Server CD.
go here
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)
reinstall the ubuntu, and it will start you with the gui.

Speaking of easy, ubuntu is way easy, but its also more powerful, so there can be more to do if you choose to do more.  

The first thing you are gonna want to do being a post windows user is get your web-broswer stuff working right, ie, playing flash, and java apps for certain websites.  You are also gonna want to get your dvds playing right without having to read a million howtos.

For this I will turning you to AUTOMATIX.  Automatix is the easiest way to get all of your stuff installed correctly.  Go here

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

All you gonna do here is add the automatix repository to your sourcelist.
the you are gonna update your source list and install automatix.  
Follow the instructions on getting automatix installed.  Then run automatix and click on the programs you want.  I recommend:
Acrobat
archiving tools
AUD-DVD codecs
Azureus (if you use bittorent)
ctrl-alt-del (since you are a windows guy)
flashplayer
media players
Mplayer & FF plugin
Multimedia codecs
opera  (just a cool web browser)
Sun Java 1.5 JRE (not jdk)
Swiftfox browser
swiftfox plugins
vVIDIA DRIVER  (only if you have a nVidia card)


I would not install 
wine 
(if your new to linux, dont mess with this yet, and if you are going to try crossover office, which uses and configs wine for you)
NDISWrapper 
(only use this if you have no choice, sometimes your wireless will work but you just arent doing it right.)
GnomePPP
(this is for dialup)
Gaim 2.0 beta3
(gaim is included with ubuntu, if you want to add more fuctionality, add some of the plugins for gaim through synaptic)
GFTP
(ubuntu can do that stuff without this program, PLACES>Connect to server)

---

### Post by givré on 2006-07-31
Yeah, say me if i'm wrong, but you was probably confuse by the stupid description of the server CD: > The server install CD allows you to install Ubuntu permanently on a computer.
If it's the case, you're not the first one, and not the last.
I filled a bug against that few weeks ago, and they changed it, but it seams that the return to the original version. :x.

---

### Post by cjwatson on 2006-07-31
I did fix it, and the files on the master site still have the fix, but unfortunately the Swedish mirror is out of date and its administrator is currently on holiday so there isn't much I can do about it. I recommend that people use releases.ubuntu.com rather than mirrors such as se.releases.ubuntu.com for the moment.

---

### Post by Lord Illidan on 2006-07-31
What video card do you have?

---

### Post by mattatkins on 2006-08-02
Thank you all!!  I did indeed download the Server instead of the Desktop.  I now see the pretty GUI.  Well, can't wait to start playing.  Thanks again for all of the suggestions.

---

