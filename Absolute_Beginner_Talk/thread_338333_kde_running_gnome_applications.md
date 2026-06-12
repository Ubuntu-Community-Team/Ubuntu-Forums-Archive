---
title: "kde running gnome applications"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-01-14
Some articles I've read say to select the desktop you like the most and that applications will run on both kde or gnome.  When I look at the screenshots of kubuntu.  I like the layout better, yet I don't want to loose all the gnome applications.

While I'm looking at the screenshots, it seems that a lot of applications aren't there in kubuntu.  I'd love to run kubuntu, but afraid that just common applications like gimp aren't going to run?

Kind of wondering why some articals make it seem that an application will run on both, while reading some posts it makes it seem as if that's untrue

---

### Post by Iarwain ben-adar on 2007-01-14
Hiya,

Well, i can assure you that the Gimp will run on KDE :wink:

What programs are you unsure of?


Iarwain

---

### Post by bone2006 on 2007-01-15
I'm not exactly sure right off the top of my head about all the software, but Kiso was one that I was thinking about that I saw or mountiso  Thing that I use like gparted I think runs on both, but I don't want to get something that only runs on both.

I was looking for a daemon-tools replacement and wanted it to be gui, not command based and I saw at least two different emulators, but they said for KDE.

---

### Post by Henry Rayker on 2007-01-15
You may have to install some of the dependencies, but I haven't run into a KDE app that wouldn't run under Gnome (so I don't see why it wouldn't work the other way). I run all my gnome apps under e17. If you're that worried about gnome apps not running under KDE, though, you should install the GNOME version of Ubuntu and then install KDE on top of it (the package will be in synaptic).

---

### Post by chavo on 2007-01-15
Any app will run on any desktop. You may need to install some libraries and dependencies (which apt-get takes care of anyway) but after that you will have no problem.

---

### Post by bone2006 on 2007-01-15
I just tried to install mountiso and there's only one file install.sh and it failed during installation.

I guess if I feel that kde looks better that I should go with kubuntu then instead if it's true that any gnome and kde program can be installed on each other?

---

### Post by Zaffe on 2007-01-15
Yes, you can run programs of kde in gnome and gnome programs in kde. The thing is that, for example, i have gnome but i love amarok (kde), so when i start amarok for the first time its take longer than normal because its has to load kde libs before actually start the program.

---

### Post by Marsolin on 2007-01-15
> **bone2006 said:**
> I just tried to install mountiso and there's only one file install.sh and it failed during installation.

I guess if I feel that kde looks better that I should go with kubuntu then instead if it's true that any gnome and kde program can be installed on each other?

What failed when running install.sh? I have used [MountISO]("http://linuxappfinder.com/package/mount-iso") on Debian in the past and it worked. It runs as a Konqueror context menu.

Since you like the look of KDE better I would definitely recommend going with Kubuntu. I use a lot of "GNOME" programs on Kubuntu.

---

### Post by bone2006 on 2007-01-15
Thank you all for the help.
I do like the way kde looks over gnome, so I'll give it a try.  I actually instlled kde on ubuntu and I'm running ir now and I'm having the same installation problems.  Maybe I'm downloading an older version or something?

there's only a readme and install.sh and this is what I get when running it in terminal while in the directory fo the file:

:~/mount-iso-0.9.1$ ./install.sh
./install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort:

---

### Post by Marsolin on 2007-01-15
Try [this]("http://linuxappfinder.com/debian/pool/main/m/mount-iso/mount-iso_0.9-1_i386.deb").  It's a deb file I created a while ago for version 0.9 for my personal use.  I haven't run it in a while, but it should automatically do the install instead of requiring you to go to the terminal.

---

### Post by Oki on 2007-01-15
Hi bone2006

I have asked the same question as you did, and have learned that KDE applications works on GNOME, just as GNOME applications works on KDE. I have lots of KDE programs running on my Ubnutu OS. 

I have heard that mountiso dont work with Ubuntu Dapper Drake(are you using that version or Edgy?). If you are using Dapper Drake then you could search for the program called Kiso in Synaptic, witch will do the same. It works like Deamon tools, with GUI. 


I am running GNOME myself (Ubuntu), and today I also installed KDE(witch Kbuntu are using) just so I can easily shift and have a look at it; meaning; I have both GNOME and KDE installed. I must say – I really liked Kubuntu, it looks very nice imho. 

I followed this very easy guide here; [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)  
psychocats has a lot of good guides and tutorials at: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) You should take a look at it, I have learned a lot from him(thanks btw). He has also some images comparing Ubuntu and Kubuntu. 
 :-)

---

### Post by bone2006 on 2007-01-16
Marsolin thanks so much for the deb file, I'll give it a try when I get home.

Oki:
I already tried kiso before, but I didn't see anything when it came to actually mounting ISO when I opened up the gui.  It seemed to be a tool more similar to isobuster or ultraiso, in which you can open and convert and edit images, but I'm looking only for a utility to mount images and not just ISO images.

I installed kubuntu on another machine and the layout, the look and the feel to it is more impressive to me than gnome.   I'll install firefox and gaim, since it didn't come packaged with it, but KDE's file manager konqueror I like so much better than natilus, even though I guess you can install both.   I guess if I like the look and feel to KDE, I should stick with it.  I'll check out the links, you've provided as well.........thanks

Thanks for all the help

---

### Post by katabatic on 2007-01-16
I've read that if you stick to KDE, it's better to try to run KDE(QT?) apps as much as possible, because that will have less RAM usage, and the same thing for Gnome(GTK?). This is because they will use shared libraries, or something like that.

---

### Post by Oki on 2007-01-17
To mount a ISO file in Kiso: 
press the button in upper left corner called "CD image" and then choose "open image"; an window will pop up where you can find the ISO file. Just like Deamon tools. 

:-)

---

### Post by Mithrilhall on 2007-01-31
Just an FYI...UltraISO runs perfectly under Wine for me.

---

### Post by bone2006 on 2007-02-01
ultra iso does not mount images.  I've only been talking about mounting imaging.   Maybe I should word it as a virtual cd emulation, because it seems many people are confused when I say mounting a CD image.  Look at daemon-tools or alcohol software in windows.

I've been running kde applications in gnome, but they do start up so much slower.   I'm still trying to figure out why would a developer write a program for one environment and not have it independent.  I mean if only 1-5% of users use linux, why make an application that runs better in one environment over another one?

I honestly use these applications
gaim
firefox
filezilla
openoffice

because they are platform independent and when I move from windows to linux, I don't notice the difference.  It's a shame that some applications were written for KDE and some were written for gnome and that they run better in their own environment.

I really like KB3 the software burning utility and also I like ktorrent, but both applications start up soooooooooooooooooooo slow that you start to think it's not going to start up at all.  It's not my system as I have a fairly decent new system I put together, it's the KDE applications.

I can't see why linux user can get upset at those who develop applications that aren't platform independent and only write applications for windows.  I do see that the KDE applications can run on gnome, but these developers are writing software for KDE.

---

### Post by igknighted on 2007-02-01
I would avoid using Firefox with KDE.  It isn't a GNOME app per se, but KDE has a better app (konqueror) for web browsing and Opera is always available [note: I don't use Firefox at all because it is an unweildy beast of a program IMO, so take this with a grain of salt].  Konqueror is nice because it is blazing fast on KDE and it integrates very nicely.  Also, you could try Kopete of instant messaging.  I prefer Gaim as a program, but use Kopete normally because its KDE native (better performance).  Openoffice is also not a GNOME app as it is platform independant, but unless you need all the fancy features GnomeOffice or KOffice might better suit you as they are much more manageable (although KOffice is probably at least as featured as OpenOffice, plus comes with more apps (such as a visio clone)).

There is a fundamental difference between GNOME and KDE when it comes to libraries... Gnome libraries are smaller, but they don't share as much as KDE libraries do.  KDE libraries, while large to load at first, provide increasingly better performance the more apps/windows you open.  On a powerful enough system, these effects might not be noticed, but it is something to keep ni mind.

---

### Post by bone2006 on 2007-02-03
I actually go back and forth between windows and linux, so platform independent software I prefer.  It's why I prefer sticking with gaim, openoffice and firefox.  Regardless of the desktop or operating system there isn't much of a difference in the application itself.

I have two systems one with kde and one with gnome and slowly I'm starting to get used to the gnome more.  Seems more stable, faster and of course more support for gnome with ubuntu than kde, since ubuntu's default desktop is gnome.

---

### Post by igknighted on 2007-02-03
> **bone2006 said:**
> I actually go back and forth between windows and linux, so platform independent software I prefer.  It's why I prefer sticking with gaim, openoffice and firefox.  Regardless of the desktop or operating system there isn't much of a difference in the application itself.

I have two systems one with kde and one with gnome and slowly I'm starting to get used to the gnome more.  Seems more stable, faster and of course more support for gnome with ubuntu than kde, since ubuntu's default desktop is gnome.

Thats Ubuntu vs. Kubuntu, not gnome vs. KDE.  Kubuntu is (IMHO) not a good example of KDE, I have had nothing but trouble with it.  Installing kde-base and adding any further apps you need would be a better way to use KDE and ubuntu.

---

