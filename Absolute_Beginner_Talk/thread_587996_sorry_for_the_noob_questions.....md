---
title: "sorry for the noob questions...."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by leeb1977 on 2007-10-23
Hiya folks,

Im a Vista 64 ultimate user at the moment and im looking for a change. No real reason for it - infact for me at the moment Vista is working perfectly well - but i still fancy trying out linux to see what i may be missing!

I plan to partition off a section of my hard disk and use that as a dual boot system so that once im used to linux i can choose if its better for my needs than windows.... or not.

Anyway - at the moment im a 100% noob..... Ive never even seen a version of a linux based OS running before - let alone used one.

Before i take the plunge i was wondering if one of you kind folks would answer me a few questions....

1) After spending some time looking around the net - the one thing ive noticed is how many different variations there are of linux O/s.... can someone give me a very quick rundown of the better known one and what i should be looking for as far as a linux OS goes. Ive been looking at one called Freespire - is that any different to ubuntu 7.10??

2) on the ubuntu homepage there are several different versions of the OS for download - can someone explain the differences?

3) I have a pretty decent pc - is there a version of the OS thats functional yet seriously heavy on eye candy?

4) Obviously theres a load of Linux alternatives for windows apps - but is there a way to get windows apps running under your os for the ones i can live without?? (mainly newsleecher, quickpar and dbox2 flashing apps etc).

5) Is there a guide somewhere that will give an old windows user like me a gentle introduction into the world of linux? I dont want to sit at a desktop and not know how to install an app!!

6) whats the driver support like for linux? my system is as follows (please let me know if im going to run into any problems with driver support):

core 2 duo 6600
2gb ram
320gb Sata 2 hdd
Nvidia 8500GT 512mb PCI-E graphics
onboard sound and lan
19" w/s monitor

etc etc.....

7) Hows the 64bit version of ubuntu stack up against the 32bit... are there any major advantages to it??

8) What does the ubuntu download come with as standard? (games, office, antivirus etc....)


finally, a big thanks in advance - i know youve probably seen a million posts like this before... but i have searched the forums and cant get any def' answers.

thanks again all

Leeb.

---

### Post by renzokuken on 2007-10-23
welcome to the forums,

1. the better known distros are probably ubuntu, debian, opensuse, fedora, mandriva and pclinuxos. as far as beginner distros go i would recommend sticking to Ubuntu, OpenSUSE or PCLinuxOS, due to their excellent community support and ease of use. (check out [www.distrowatch.com](www.distrowatch.com) for linux distros). try the livecds first if you are unsure. you can test the distro from the CD without having to install anything

2. Desktop - normal LiveCD/Installer version for everyday desktop use
Server - for a server, no GUI, server stuff (LAMP) comes ready to use
Alternate - plain installer (no livecd) that just installs the same as the Desktop version

3. not sure which ones come preinstalled with eye candy (Compiz Fusion etc) but Ubuntu 7.10 has Compiz ready to go

4. a whole range of windows apps will run under Wine ([www.winehq.org](www.winehq.org)), available in the repos

5. [www.google.com](www.google.com) - although diving in and getting practical experience is always the best bet

6. all looks supported to me, nvidia driver is available through the Restricted Drivers Manager in Ubuntu

7. 64 bit debatebly gives a small performance increase but various things are tricky to get working such as flash and codecs. i'd strongly recommend 32bit if you're a first time linux'er

8. ubuntu comes with various games, office apps, media apps preinstalled and hundreds/thousands of alternative apps available in the repos for easy installation

good luck....hope that all helped

---

### Post by leeb1977 on 2007-10-23
its helped loads yeah - ta!

---

### Post by bumanie on 2007-10-23
I will answer what I can of your questions. I have not yet got gutsy on my computer, but use feisty and plan to upgrade to gutsy (ubuntu 7.10) soon.

1. Have never used freespire so I can't tell you what the differences are. What I can say with reasonable certainty is that Ubuntu is generally regarded as the most user friendly distro for former windows users.

2. Without explaining the differences, it would be best for you get the 64 bit ubuntu 7.10 based upon your next question regarding eye candy.

3. Ubuntu 7.10 has serious eye candy enabled by default. Upon loading the OS, your system is analysed and if you have the architecture to run it, the eye candy is automatically enabled. (At least that is what the documentation says).

4. There are two programs that I know of. They are called wine and crossover. Suggest you google and read. Some windows games also work under wine. Another game emulator is cedega, however I believe it costs a small monthly fee to use this. In regards to wine, it is apparently fickle and sometimes works well, whilst at other times it doesn't.

5. Again, google for guides to using ubuntu, there are a multitude out there. Also this forum is of great help. Check out this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
If enabling repositories that mention feisty, just insert gutsy instead and the commands should work.

6. In gutsy, graphics card drivers are now enabled via GUI prompt. HP and epson support linux but canon don't. This doesn't mean it is impossible to get canon printers working, but it can be more difficult. In gutsy, printers are meant to be configured automatically once they are plugged in. For media players you have to enable certain repositories and load proprietory codecs etc. Refer to the above guide for info on this. A good all round player is vlc player - it has never failed playing anything I have tried.

The best thing you can do is try ubuntu out and see how it goes. Keep in mind that it works differently than windows and a number of functions are performed via command line in the terminal. It is not necessarily harder than windows, just different. Best to be prepared to have frustrating times on occassions, but the longer you try and the more you read and ask questions on this forum, the easier things get.

PS: May be best to stick with the 32 bit as suggested by renzokuken.

---

### Post by LaRoza on 2007-10-23
> **leeb1977 said:**
> 
1) After spending some time looking around the net - the one thing ive noticed is how many different variations there are of linux O/s.... can someone give me a very quick rundown of the better known one and what i should be looking for as far as a linux OS goes. Ive been looking at one called Freespire - is that any different to ubuntu 7.10??



There are thousands of distros, for a new user: Ubuntu (Debian Based), PCLinuxOS (Mandriva based), or Pardus might be easier to use.

I recommend staying away from Freespire, and if you want KDE install it on Ubuntu or get Kubuntu.

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by steve.horsley on 2007-10-23
> **leeb1977 said:**
> 
1) After spending some time looking around the net - the one thing ive noticed is how many different variations there are of linux O/s.... can someone give me a very quick rundown of the better known one and what i should be looking for as far as a linux OS goes. Ive been looking at one called Freespire - is that any different to ubuntu 7.10??

This is an Ubuntu forum - what kind of reply do you expect? I recommend Ubuntu.
They all differ in the collection of software they supply on top of the Linux kernel. One major difference is in the desktop - some use KDE and some use Gnome. These are GUI systems and they tend to look as different as say Windows and Mac do, and they have their own set of utility programs. However it's still Linux underneath, and all applications work in both GUIs whichever they were written for. Mixing the two may result in applications that look slightly different - different fonts, different button borders but thats about all. Both desktops have their zealots, both are very useable and there are others too. Ubuntu uses Gnome, Kubuntu uses KDE and Xubuntu uses XFCE. I recommend you start with Ubuntu because it's the default so more users use that so you will find help in the forums slightly easier to come by. You can install KDE into Ubunto later and then get a choice as you log in.

I also recommend Ubuntu as a starter for 2 reasons. It seems to have a reputation of being beginner friendly - most likely to work out of the box although there is constant competition between distros for this crown. And the Ubuntu help forums are vastly more friendly and helpful than other forums that I have tried to use. I wonder if the forum is not a major reason for Ubuntus current success rate.
> 
2) on the ubuntu homepage there are several different versions of the OS for download - can someone explain the differences?

There is a server edition. You don't want this - it has no GUI - servers sit in racks with no-one looking at them.
There is a 64-bit version. I suggest you avoid this as a beginner. I gather it's getting better, but there are still minor issues with availability of some proprietary codecs, drivers etc, and again there are fewer users to answer any issues in the forums. Go 64 bit later once you have some experience.
There are 2 x86 32-bit installers. The "Desktop" one is a full Ubuntu system running from a CD. Good for trying things out, and a GUI installer too. But sometimes has problems with odd hardware, in which case you must use the "alternate" installer which is text-mode like WIN98 was - less memory and graphics requirements. They both install the same system though - the difference is only the installer. I suggest you try the "Desktop" installer as you can get a flavour without installing (although it's slow from CD), nad play mahjongg while you wait for the installer.
> 
3) I have a pretty decent pc - is there a version of the OS thats functional yet seriously heavy on eye candy?

They are all getting eye-candy these days, mostly the same. Ubuntu has it. Puts vista to shame. You will want to install gnome-compiz-manager for the widest range of useless effects.
> 
4) Obviously theres a load of Linux alternatives for windows apps - but is there a way to get windows apps running under your os for the ones i can live without?? (mainly newsleecher, quickpar and dbox2 flashing apps etc).
[QUOTE]
There is a package called wine that can run a variety of windows apps. I've never heard of those you mention though.

5) Is there a guide somewhere that will give an old windows user like me a gentle introduction into the world of linux? I dont want to sit at a desktop and not know how to install an app!!
[/QUOTE]
Off the top of my head:
[http://www.psychocats.net](http://www.psychocats.net)
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
Please always look in Synaptic (System->Administration->Synaptic) before considering downloading sw from the web. Most stuff is 3 clicks away (two of those being "Apply").
> 
6) whats the driver support like for linux? my system is as follows (please let me know if im going to run into any problems with driver support):

core 2 duo 6600
2gb ram
320gb Sata 2 hdd
Nvidia 8500GT 512mb PCI-E graphics
onboard sound and lan
19" w/s monitor

etc etc.....
Looks OK. USB modems and wireless can be problematic.> 
7) Hows the 64bit version of ubuntu stack up against the 32bit... are there any major advantages to it??
As above, avoid it unti you have at least a little experience.> 
8) What does the ubuntu download come with as standard? (games, office, antivirus etc....)

Yes, yes, yes. Look in Synaptic.

Antivirus - what's that? Actually, there are a couple in Synaptic, but they're only useful if you run a server that handles files passing between windows machines. You can do their washing for them.

Good luck. Be warned that Linux is different to Windows, in ways that you don't imagine. For users it's much the same, but system administration will require some learning curve. 

I suggest you leave some unpartitioned space on the hard drive (not an empty partition, but real un-partitioned space), and then tell the installer to go Guided (means auto) and use the largest free space. This lets it create its own partitions and format them how it wants.

---

### Post by leeb1977 on 2007-10-23
thanks folks, 

Ive posted the same questions on other forums and had no real joy in terms of getting answers.... so the fact that ive had reply's already fills me with confidence!

I'll get the 32bit version of ubuntu 7.10 then and see how i fare from there on in. Im looking forward to this :)

---

### Post by TheLions on 2007-10-23
:confused::confused::confused:
I have some noob questions to:

1. I installed program over synaptic but it isn't on my desktop/program toolbar, how to put it there
2. Why i cant see my NTFS partitions from wine and some other programs
3. how to install programs which aren't in in synatic  from terminal ?
4. Which video player supports subtitles below the movie (not overlayed)
5. Where are stored Ubuntu fonts, and how to copy fonts from M$ Vista folder to ubuntu?
6. How to install AMD dual core drivers?

:-\"

---

### Post by leeb1977 on 2007-10-23
sorry folks - just one last question....

Ive read through the installation guide on this site, and while working with command lines etc doesnt phase me (i remember the days before windows and i write command line based programs for a living), i was wondering how user freindly it is to complete PC novices??

My wife and kids use my pc all of the time, and if i make the switch a permo one will they cope ok with it.

I know i can just install and find out, but im at work at the moment and once i get an idea in my head.... well.... you know what its like - you want to know everything now!! lol!

---

### Post by steve.horsley on 2007-10-23
Please start your own thread instead of hijacking other peoples. But quick answers anyway:

1: Right-click the Ubuntu sign and click Edit Menus. You can add a new launcher there, but you need to know the name of the executable to launch. Synaptic can show a file list in the properties of a package if you are in doubt.
2: You need to mount the NTFS partition into the filesystem tree. Then applications will be able to see it. Wine uses a dummy drive_c file hidden in the directory .wine in your home folder. But by default, the rest of the Linux filesystem is visible as Z:
3: That depends on how they are distributed. See [http://www.psychocats.net](http://www.psychocats.net)
4: Dunno
5: Dunno
6: No drivers needed. These processors are supported by the kernel.

---

### Post by steve.horsley on 2007-10-23
Users don't have to use the command line if they don't want to. But it's sometimes necessary for system administrators. Do you expect your wife and kids to regularly use regedit? How friendly is that?

The fact is that  even when a GUI method is possible, it's generally quicker and more accurate to tell other people the command-line way when your helping out. And command-line commands (and the corresponding error messages) can be copy/pasted to/from the forums quickly and efficiently. In one line I can tell you things that would take a whole essay in click this, select that, find X in the list etc.

---

### Post by TheLions on 2007-10-23
thank you very much!:)

---

### Post by leeb1977 on 2007-10-23
> **steve.horsley said:**
> Users don't have to use the command line if they don't want to. But it's sometimes necessary for system administrators. Do you expect your wife and kids to regularly use regedit? How friendly is that?

The fact is that  even when a GUI method is possible, it's generally quicker and more accurate to tell other people the command-line way when your helping out. And command-line commands (and the corresponding error messages) can be copy/pasted to/from the forums quickly and efficiently. In one line I can tell you things that would take a whole essay in click this, select that, find X in the list etc.

cool, as long as theres ways around the os by using the GUI im sure they'll be happy.

to be honest the only thing they'll use is the internet, email and the odd desktop game anyway!

---

### Post by renzokuken on 2007-10-23
> **leeb1977 said:**
> thanks folks, 

Ive posted the same questions on other forums and had no real joy in terms of getting answers.... so the fact that ive had reply's already fills me with confidence!

I'll get the 32bit version of ubuntu 7.10 then and see how i fare from there on in. Im looking forward to this :)


i'd say that is the single biggest reason for beginners to use Ubuntu......Ubuntu's **AWESOME** forums.....by far the single greatest and friendliest support i have ever come across......the people here are brilliant

> sorry folks - just one last question....

Ive read through the installation guide on this site, and while working with command lines etc doesnt phase me (i remember the days before windows and i write command line based programs for a living), i was wondering how user freindly it is to complete PC novices??

My wife and kids use my pc all of the time, and if i make the switch a permo one will they cope ok with it.

I know i can just install and find out, but im at work at the moment and once i get an idea in my head.... well.... you know what its like - you want to know everything now!! lol!

there is absolutley no reason for kids/wives to use the command line with a working ubuntu desktop. all the apps, menu's systems will be very familiar and easy for surfing, media playing etc.

---

### Post by leeb1977 on 2007-10-23
> **renzokuken said:**
> i'd say that is the single biggest reason for beginners to use Ubuntu......Ubuntu's **AWESOME** forums.....by far the single greatest and friendliest support i have ever come across......the people here are brilliant



there is absolutley no reason for kids/wives to use the command line with a working ubuntu desktop. all the apps, menu's systems will be very familiar and easy for surfing, media playing etc.


Wives...:eek:......dont wish that one on me.... one's enough! ;)

---

### Post by mb01915 on 2007-10-23
> **leeb1977 said:**
> sorry folks - just one last question....

Ive read through the installation guide on this site, and while working with command lines etc doesnt phase me (i remember the days before windows and i write command line based programs for a living), i was wondering how user freindly it is to complete PC novices??

My wife and kids use my pc all of the time, and if i make the switch a permo one will they cope ok with it.

I know i can just install and find out, but im at work at the moment and once i get an idea in my head.... well.... you know what its like - you want to know everything now!! lol!

If your wife and kids are going to do email and websurfing, Ubuntu is 100% friendly.  Just put a shortcut to the programs on the desk top and away they go.

If my 87 year old mother in law could do it anyone can.  She thought the screen looked different but had no idea that a new operating system was on her old computer.

---

### Post by LaRoza on 2007-10-23
> **leeb1977 said:**
> 
My wife and kids use my pc all of the time, and if i make the switch a permo one will they cope ok with it.


If it is already set up, extremely easy.

Installing Windows is more of a pain, but most people don't know that because it is usually preinstalled. If someone has a ready-to-go system, it is usually perceived as being easy.

What do they do on the PC?

If it is Internet, Movies/Multimedia, word processing, and such, they will have no problem. In fact, you can have different DE's for each one if they have preferences.

---

### Post by leeb1977 on 2007-11-02
Hiya chaps,

riiight, first ive got to say that my home PC is now dual boot and Gutsy is now running a treat! im loving it - just seems much free-er than the Vista enviroment!! great stuff!

to start off with i used Vista to create a 50gb partition and installed ubuntu onto that, but i do have a couple of quick questions if i may....

1) when i boot into ubuntu and look at my available hard drives i cant actually see my windows partition.... is there anyway i can gain access to this from within ubuntu - as ive got various documents and pics etc that i wish to transfer across (i dont really want to have to waste blank dvd's). I then wish to shrink the size of my vista partition and increase the size of my linux one - as i plan to use ubuntu as my main O/S from now on.

2) This is a silly little question - when using SMF forums around the net, for some strange reason i cant view Youtube videos - ive installed the plugins and restarted - yet all i see is a white box where the vid' should be... any ideas on howto get this working?

3) does anyone know where i can find a version of spider solitare?? My mrs will kill me if she cant play it!!!

apart from that - im as happy as a pig in muck - thanks all for your superb help so far... i think im gonna like it here. Add another 1 to the converted list ;)

---

