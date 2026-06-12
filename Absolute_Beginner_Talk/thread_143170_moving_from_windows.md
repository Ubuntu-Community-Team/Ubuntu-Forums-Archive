---
title: "moving from windows"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by darkwarrior0404 on 2006-03-11
Hey everyone, I'm like fresh out of the ubuntu case new, and ran the live cd of linux, and it seemed pretty interesting, so I decided to install it to my HDD, and I'm on it now, and I wanna learn all the commands and everything I'm just kinda in the dark and everything sounds like spanish to me, I've been a hardcore microsoft guy the past 4-5 yrs and never even had to use anything that have to do with commands.. just curious if I could get some help lol I've looked on the site and everything is confusing to me, help plz? :mrgreen:

---

### Post by sapo on 2006-03-11
You could start reading this forum, especially the howto session, and this wiki:

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by aysiu on 2006-03-11
[This PDF](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf) is a good starting point:

---

### Post by darkwarrior0404 on 2006-03-11
wow fast responses lol thanks i'll check them out :) i love the layout and everything of this, and i really wanna learn, i'll keep it posted on if i need anything else, thanks :)

---

### Post by Mustard on 2006-03-12
[QUOTE=darkwarrior0404]Hey everyone, I'm like fresh out of the ubuntu case new, and ran the live cd of linux, and it seemed pretty interesting, so I decided to install it to my HDD, and I'm on it now, and I wanna learn all the commands and everything I'm just kinda in the dark and everything sounds like spanish to me, I've been a hardcore microsoft guy the past 4-5 yrs and never even had to use anything that have to do with commands.. just curious if I could get some help lol I've looked on the site and everything is confusing to me, help plz? :mrgreen:[/QUOTE]

It is a bit like learning a language.  At first you feel a bit confused and lost.  I can empathise with that feeling. :)  It does get easier and as the pennies drop it all starts to make more sense.

If you are an IRC type of person, you can also try the IRC support channel, which was where I learnt a lot of the basics of linux.

irc server: irc.freenode.net
channel: #ubuntu

The xchat client is available by default in your Applications>>Internet menu and should have the 'Ubuntu Servers' listed in the connection dialog.

---

### Post by nalmeth on 2006-03-12
Ubuntu is designed to be used with as little of the command line as possible, though at some point you'll likely need to use it.. If you're using gnome, just browse through the panel menus to get an idea where everything is. Devices networking users etc are all there.
It sounds like your not intimidated by the terminal, so this is good. You may find that for a lot of uses, you will rather use the terminal than a graphical interface, because it can do just about anything. 
This is personal preference though, I can't speak for anyone else.

Welcome to ubuntu

---

### Post by darkwarrior0404 on 2006-03-12
alright one more question, im just trying to do some basic stuff and, im trying to get gnomebreaker installed and ok well i installed it to a folder on the desktop, opened up the install instructions, and its giving me all of this stuff to type:        The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.


I know i probably seem kinda stupid for this, but I've been on windows and everything is just an "install or uninstall" and its definately confusing lol, but I'm trying to learn so just bare with me haha, can I get some help with this? Please and thank you :KS

---

### Post by Mustard on 2006-03-12
You can install gnomebaker via the Synaptic Package Manager after enabling the community supported repositories which are known as the 'Universe' and 'Multiverse' repositories.

The way you are doing it atm is the hard way.

Try reading this guide on enabling repositories

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

-edit-

If you like picture tutorials here is another link...

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

After you get those repositories enabled, and you have pressed the 'Reload' button in Synaptic to get the latest package lists, use the search function in Synaptic to look for the package 'gnomebaker', then right click on the package and choose install, then hit the 'Apply' button and it will download it and install it all in one.

---

### Post by darkwarrior0404 on 2006-03-12
ok i tried reading all 3 sites and im getting closer, but when i go to search for gnomebaker, it doesnt find it, do i need to download it to a specific location? also from all the places when i enter into the synaptic-repositories  there is no settings tab at the bottom at all, there is new, delete, cancel, and ok,   is this mostly because i am currently using v4.10 ubuntu? or? i am trying to get gnomebaker to work so i can copy the newer ISO image of ubuntu to a cd.. and its not working out lol helpppp :mrgreen:

---

### Post by animesh on 2006-03-12
just do

sudo apt-get install gnomebaker

no hassles at all ...i installed it today itself

---

### Post by darkwarrior0404 on 2006-03-12
alright i dumped the 4.10 ubuntu, and just installed v 5.10 ubuntu, (Hope that wasn't a mistake haha) is there any, oh i dont know, i'm not afraid of the text or anything, what would be good to learn on? something sorta simple to help get me more familiar with the commands, just reading this stuff is mind boggling, can anyone help? haha, i'm trying to install suse 10.0 on my laptop and its not reading the second disk for some reason... well hope i am able to get a little help with more text based and editing a little more, thanks all for the help its just taking a while to get used to:-k

---

### Post by Mustard on 2006-03-12
[QUOTE=darkwarrior0404]alright i dumped the 4.10 ubuntu, and just installed v 5.10 ubuntu, (Hope that wasn't a mistake haha) is there any, oh i dont know, i'm not afraid of the text or anything, what would be good to learn on? something sorta simple to help get me more familiar with the commands, just reading this stuff is mind boggling, can anyone help? haha, i'm trying to install suse 10.0 on my laptop and its not reading the second disk for some reason... well hope i am able to get a little help with more text based and editing a little more, thanks all for the help its just taking a while to get used to:-k[/QUOTE]

Ah..I didn't know you were using 4.10. :)  Using 5.10 would be much better as we would all be on the same page that way.

---

### Post by darkwarrior0404 on 2006-03-12
no wonder i was so lost when i was trying to find all that stuff ^.^

:Edit:

I bought a book "The Linux Bible" or something like that, and it came with a cd and dvd, and came with knoppix/fedora (which i installed on my labtop to play around with)/ and a whole bunch of others and in downloaded 5.10 off the net and put it on this pc. well the soundcard on my motherboard went out so i installed an older Riptide PCI audio/modem/joystick controller, and i downloaded the drivers for linux and, i try to type in what it tells me via the terminal and it tells me that it cant find it? Hope I'm not being too annoying with all of this just the change from windows to linux is a whole lot different lol.. i need a teacher :P

---

### Post by WoodyMahan on 2006-03-13
Hey,

I just had a long string on here concerning command lines myself.  I got this link from another user and it is a great starting tutorial.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

One newbie to another:  Be patient bro.  Give yourself time to adjust, this is a whole different world over her.

Good Luck

---

### Post by steve.horsley on 2006-03-13
[QUOTE=darkwarrior0404]
I bought a book "The Linux Bible" or something like that, and it came with a cd and dvd, and came with knoppix/fedora (which i installed on my labtop to play around with)/ and a whole bunch of others and in downloaded 5.10 off the net and put it on this pc. well the soundcard on my motherboard went out so i installed an older Riptide PCI audio/modem/joystick controller, and i downloaded the drivers for linux and, i try to type in what it tells me via the terminal and it tells me that it cant find it? Hope I'm not being too annoying with all of this just the change from windows to linux is a whole lot different lol.. i need a teacher :P[/QUOTE]

I think you need to be a bit more specific. You say the soundcard on the motherboard went out. Does that mean sound didn't work? What make is the motherboard? Do you know what chipset the on-board sound uses? Try these two commands, to write a hardware list to a file and then view the file (use "q" to quit viewing the list):
> sudo lshw > lshw.txt
less lshw.txt (or gedit lshw.txt if you prefer a GUI based editor to view the file)This should give some useful info. Post details here for more help.

As for not being able to compile drivers, you need to post the exact command and error message so people can see what's going on, but I'd leave that until you've had more of a try at sorting out the on-board sound.

---

### Post by jjf on 2006-03-13
Hi, darkwarrior.  Welcome to Linux, and to Ubuntu specifically.

It sounds like you're toying with a couple distributions of Linux at the same time (Suse, Fedora, Ubuntu).  This is the best way to find which distro suits you best, but for learning I would recommend picking one and sticking with it.  The Ubuntu community on these forums is the best tech support for any OS that I've ever come across, so I would suggest spending a month or two learning Ubuntu before venturing out into other distributions.

re. your earlier question about installing.  In general, there are three ways to install software.  

**1. The Easiest Way:** Use your distribution's package manager software.  For Ubuntu, this is Synaptic (menus: System > Administration > Synaptic Package Manager).  Synaptic is a program that searches lists of installable software (called "repositories") and lets you install it just by selecting it from the list and choosing "mark for installation."  To make more software available in that list, enable some extra repositories.  In the Synaptic menus, click Settings > Repositories.  Click the "Add" button.  Check the selections "Community maintained (Universe)" and "Non-free (Multiverse)."  Click "OK," "OK."  Synaptic will ask to reload the repositories (that is, update the list of software to include your newly added repositories).  Click "Yes."  Use the search button to find software (like "gnomebaker"), click the little box next to any item in the list to mark it for installation, and click the green "Apply" checkmark button to apply your updates.

**2. The Easy Way:** Use the command line.  Some people prefer the command line to Synaptic, I guess because it's faster.  If you know that a certain program (gnomebaker, for example) is in your repositories, you can type the following in the terminal:
```
sudo apt-get install gnomebaker
```
- sudo means "superuser do" -- basically telling Ubuntu, "I'm smarter than you think I am and I promise I know what I'm doing, so let me do this action that you have restricted for normal users."
- apt-get is a program just like Synaptic, but without the pretty interface (in fact, Synaptic may be nothing more than a GUI for apt-get -- I'm not sure).
- install gnomebaker is telling apt-get what to do

Sometimes you need to use the command line because your program was not in the repositories.  When you find a Linux program on the internet, download their Ubuntu package if they have one.  If not, get the Debian package.  (If they have neither, you must install with option #3).  Then go to the terminal and type:
```
sudo dpkg -i ~/Desktop/package_i386_0.9.1.deb
```
- dpkg is a program for installing Debian packages (.deb files), which Ubuntu uses.
- -i ~/Desktop/package_i386_0.9.1.deb tells dpkg to *install this package* which is right now sitting on your desktop.  Package names are usually long and complicated with lots of version numbers and architecture types.  Fortunately if you just get the first few letters and hit TAB, the terminal will fill in the rest of the name for you to make sure you get it right.

**3. The Hard Way:**  Compile the package yourself.  This is what the INSTALL instructions for gnomebaker that you posted were telling you how to do.  I avoid this whenever I can, and whenever I get it to work I feel like some minor miracle was achieved.  There are guides for doing this if you absolutely must.

---

### Post by dvarsam on 2006-03-13
Hello  & Welcome to the Ubuntu Community.

_Quote 1_:
"... I am trying to install suse 10.0 on my laptop and its not reading the second disk for some reason..."

If you want to install Suse 10.0, do NOT install it, by using the 5 CD's.
Go for the Suse 10.0 Evaluation DVD - only this one works!
I had the same experience (& problem) like you...
I just tried installing from the DVD Today !!!
At the same time, my screen was f*cked up...
I could NOT fix it & the Text was so small, I had to pull my eyes out to read the screen's stuff...

_Quote 2_:
"...wow fast responses lol thanks i'll check them out...".

Yes, this is what you are going to experience if you stay to the Ubuntu community!
Of course, like you, I was curious to see how Suse worked out...
But after I popped my eyes out, went to "www.suseforums.net" & made a post on my problems, I realized that the community was going TOO slow, that I would have to learn "Suse" in LAZY mode... (this means you will probably get one response in every 2-3 hours..., if you can cope with this... - I can NOT).
In this Forum, I can get a response in 10-30 minutes (tops), depending on how hard my question is...
Easy questions get answered instantly!!!

_Quote 3_:
Installing gnomebaker:
"... 3. The Hard Way: Compile the package yourself..."

Do NOT try to install it in this way. It is hopeless... I have NEVER EVER managed to install any program in this way... This is a total "scr*u up" situation...
By the way, when I tried to use Suse 10.0, I was curious whether program installations with ".rpm" files would be easier compared to ".deb" files.

_Outcome_:
".deb" files are MUCH MUCH better man !!!

Just try them out yourself & decide what you want...

But, yeah, stick on one Linux OS for a while, untill you really learn it well!
Then go look at other choices...

Good Luck !!!

---

### Post by Lord Illidan on 2006-03-13
[quote=dvarsam]Hello  & Welcome to the Ubuntu Community.



_Quote 3_:
Installing gnomebaker:
"... 3. The Hard Way: Compile the package yourself..."

Do NOT try to install it in this way. It is hopeless... I have NEVER EVER managed to install any program in this way... This is a total "scr*u up" situation...
By the way, when I tried to use Suse 10.0, I was curious whether program installations with ".rpm" files would be easier compared to ".deb" files.

_Outcome_:
".deb" files are MUCH MUCH better man !!!

Just try them out yourself & decide what you want...
[/quote]
It is NOT a total "scr*u up" situation. Compiling packages sometimes has to be done, when an app is not in the repos, or you need to install a more up to date version. Basically, you need to pay attention to the output of ./configure, and install new libraries based on what it is saying.
Otherwise, yes, apt/synaptic is faster, and much easier.
RPM vs DEB. I don't think there is much of an issue, over the packages themselves, more on the way they are distributed.

---

### Post by dvarsam on 2006-03-13
Dear "Lord Illidan",

If you believe that it is NOT a total "scR*p" situation, then you want to help me install the program "Gambas"?

Please see my **Article#: 143356**	- How can I run the program "Gambas"?

Thanks.

---

### Post by darkwarrior0404 on 2006-03-13
System Specs: 

description: CPU
          product: AMD Athlon(tm) 64 Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.4.10
          slot: Socket 754
          size: 1810MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz


--- *-memory:0
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 1GB


---        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits


--- *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list

--- *-disk
             description: SCSI Disk
             product: ST3160827AS
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@2.0:0.0
             logical name: /dev/sda
             version: 3.42
             size: 149GB
             configuration: ansiversion=5       (SATA Seagate HDD)

---*-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: Riptide PCI Audio Controller
             vendor: Rockwell International
             physical id: 8
             bus info: pci@01:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: ioport:df00-df3f irq:11
        *-communication UNCLAIMED
             description: Communication controller
             product: Riptide HCF 56k PCI Modem
             vendor: Rockwell International
             physical id: 8.1
             bus info: pci@01:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:fdfe0000-fdfeffff irq:11
        *-input UNCLAIMED
             description: Input device controller
             product: Riptide PCI Game Controller
             vendor: Rockwell International
             physical id: 8.2
             bus info: pci@01:08.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:fdfff000-fdffffff


--- All of above are on one card, Riptide, works with microsoft and i figured out how to get the drivers to work, and it says i need a version 2.4 kernel or something :( so i dont think its up to par with the newer versions of ubuntu? cause i finally figured out that i had to type in cd /home/desktop and so on and so forth to get me to the desktop in the terminal because i saved it to it, and well yeah its kinda a disappointment, the soundcard is really old tho, so i guess i'll have to break down and buy a new one but its no big deal..

---

### Post by darkwarrior0404 on 2006-03-13
I think this has turned out to be a good learning experience and I'm slowly getting the hang of it, I just wanted to thank everyone for helping  : ) the links were trouble at first but now that I'm getting to know what I'm looking at it's not to bad, just gotta have patience. I was kinda woried at first about hardware compatibility --using AMD Athlon 64 and everything was designed for microsoft lol.. but Ubuntu had no problem recognizing the hardware and I had it up and running in an hour or so. Thanks again for everyones help, just thought I'd tell that before posting any other questions :)

---

