---
title: "I just installed Ubuntu."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-04-29
A few simple questions that I bet anyone can answer. 

1.- Where can I find a list of MUST HAVE software, so I can download a anti-virus, a VLC player, etc.

2.- I tried to install my motherboard drivers because I thought I needed them to use the internet, somewhat like Windows, but apparently I can use the internet without any driver. So are my driver automatically installed through the internet? <----I REALLY NEED AN ANSWER TO THIS.

3.- How the heck do I open .exe files? Does Ubuntu even support .exe file extensions?

---

### Post by xmastree on 2007-04-29
1. you don't need antivirus
2. you don't need them, everything should just work.
3. you don't. .exe files are for windows

---

### Post by papuccino1 on 2007-04-29
So where can I find a list of must have programs? 

I'm really, I mean REALLY newbie at Ubuntu.

---

### Post by Wiebelhaus on 2007-04-29
[automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation")

A nice list with explanations and simple installation scripts.......dude , like Michael Dell uses it.

---

### Post by Nythain on 2007-04-29
what do you want to accomplish... must have software is kind of relative really... i must have the stuff that kubuntu installs default... with the added must have of firefox, kftpgrabber, synaptic and xine-ui...

everything you must have can usually be found using apt-get or synaptic...

---

### Post by riminicat on 2007-04-29
Hey papuccino1 welcome to the linux community, I'm a noob too, well kinda.  But any way, if you google ubuntu programs you should find most of them, and a tip, get to know the terminal

---

### Post by Wiebelhaus on 2007-04-29
> **riminicat said:**
> Hey papuccino1 welcome to the linux community, I'm a noob too, well kinda.  But any way, if you google ubuntu programs you should find most of them, and a tip, get to know the terminal

lol , like your mothers face...

---

### Post by Tomosaur on 2007-04-29
You don't need an anti-virus. To get your hands on VLC player, click Applications, then Add/Remove. Do a search in that program for VLC player, and then select it and click apply. The password it asks you for is your user password. This is how you install software in Ubuntu, you do the same process to remove software, but you deselect programs rather than select them. Fairly obvious really :P

The LiveCD is there for you to check whether your hardware works. If it doesn't, post here with make and model of the offending hardware, and we'll see what we can do. Most things should just work, sometimes you need to install the drivers yourself.

There are no .exe files on Linux. In fact - Linux doesn't need file extensions at all. It knows what opens which file by reading the contents of the file. Extensions are for humans to understand - most programs and some files you come across will have no extension at all. Those files which do have an extension have one for your sake, not the computer's. On Ubuntu, the equivalent to the Setup.exe on Windows is <program name>.deb. You double click these, then click 'install' to install software. Program launchers do not normally have an extension - you just either launch the program from the menu by clicking it's name, or you type the name of the program in the 'run' box (hit alt+f2), or in the terminal (applications > accessories > terminal).

---

### Post by riminicat on 2007-04-29
P.S. When you install stuff, make sure you can uninstall it without your computer going nuts.  I assume you actually plan on using your computer.

I just got Ubuntu for a new challenge, and I love it!!

---

### Post by lluisanunez on 2007-04-29
Most of the must-have programs are already in your system: explore the menus. For more programs, open Applications >> Add/Remove... you'll find them classified by areas, such as multimedia, internet, office. Use always this Add/Remove...  or System >> Admin >>synaptic to install programs.

---

### Post by mikewhatever on 2007-04-29
> **papuccino1 said:**
> A few simple questions that I bet anyone can answer. 

1.- Where can I find a list of MUST HAVE software, so I can download a anti-virus, a VLC player, etc.

2.- I tried to install my motherboard drivers because I thought I needed them to use the internet, somewhat like Windows, but apparently I can use the internet without any driver. So are my driver automatically installed through the internet? <----I REALLY NEED AN ANSWER TO THIS.

3.- How the heck do I open .exe files? Does Ubuntu even support .exe file extensions?

Ubuntu comes with a lot of 'must have' software pre-installed, so that most of the users are covered. Search for whatever else you need, or ask. AV apps are available for Ubuntu, check the links:
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)
[http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)

I do not think you want to mess with driver installation at this stage.

EXE files are not supported in Linux. Ubuntu uses the DEB extension instead.

---

### Post by papuccino1 on 2007-04-29
I'm scared sh-tless of the terminal. Hahahaha I guess I'll get used to it though. I kinda have to! No friggin' way I'm changing OS now. 


So here's what I'd like to be able to do:

1.- Use a P2P software, like Limewire or Ares.

2.- I'd like to watch some .avi .wmv movies. What program should I use? Do codecs download automatically?

---

### Post by riminicat on 2007-04-29
use torrents in Ubuntu!!

---

### Post by mikewhatever on 2007-04-29
You can learn a lot on how to install stuff from [www.ubuntuguide.org](www.ubuntuguide.org)
Just search for the program you need.

---

### Post by papuccino1 on 2007-04-29
You've all been a great help.

Just one more thing.I installed a program called Envy, which is supposed to download a driver for my video card. So, I run it and it found that my hardware/os was not supported. Whatever I say, it still works fine. 

So I wanna uninstall it. But when I search for the program on the add/remove thingy, I can't find it anywhere. 

Any help?

---

### Post by papuccino1 on 2007-04-29
BUMP because I can't even turn on desktop effects without uninstalling this piece of crap program called Envy.

HELP

---

### Post by mikewhatever on 2007-04-29
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

To remove envy open the terminal (Applications>Accessories>Terminal) and type
> sudo aptitude purge envy

If that does not work, tell more about how you have installed it.

---

### Post by mikewhatever on 2007-04-29
> **papuccino1 said:**
> BUMP because I can't even turn on desktop effects without uninstalling this piece of crap program called Envy.

HELP

I am sorry, this is very impolite. Envy is an excellent program and you really do not know what you are talking about. It can also be the case, that you do not know how to use it.

---

### Post by papuccino1 on 2007-04-29
> **mikewhatever said:**
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

To remove envy open the terminal (Applications>Accessories>Terminal) and type


If that does not work, tell more about how you have installed it.

OK I did that, but I can't type in my password. WTF? I get beeping noises and crap. Maybe I should restart my computer like some windows program requires you to.

---

### Post by ludileptir on 2007-04-29
Ok..didn't want to open new post so i'll ask here..also just installed ubuntu 7.04...new to this system and I have trouble with wireless networking..my provider uses VPN conection an ubuntu recognized I have a wireless network but only web page I can open is my providers homepage..tryed to insert an IP but my provider didn't gave me a direct IP adress..can anyone help..

---

### Post by mikewhatever on 2007-04-29
> Ok..didn't want to open new post so i'll ask here..also just installed ubuntu 7.04...new to this system and I have trouble with wireless networking..my provider uses VPN conection an ubuntu recognized I have a wireless network but only web page I can open is my providers homepage..tryed to insert an IP but my provider didn't gave me a direct IP adress..can anyone help..
Reply With Quote
There is absolutely no reason not to open a separate thread for your question. Your topic is different, hijacking another thread is not very nice, and lastly, not too many will look at the end of this one.

---

### Post by ludileptir on 2007-04-29
OK sorry i asked..

---

### Post by jrlii on 2007-04-29
There are viruses, worms, trojans and other malware for Linux. Neither as many of them nor in as wide a circulation as those for Windows, but I understand they can be pretty nasty if you DO get one. Of course security holes are generally plugged faster than they are for Windows.

Since I'm still running dialup, I haven't bothered to configure the firewall, but with a broadband connection I figure it would be essential. As I understand it, Firestarter is a good GUI tool for setting up/managing the firewall.

f-prot is a good anti-virus, and for non-commercial use on Linux workstations is available free of charge. There is even a .deb package. The user interface, however, is pretty primitive: It is pretty much the same command line interface as the version of f-prot I used back in the 80s when the floppy disk was virtually the only vector and 1200 baud modems were fast. . .

---

### Post by Swab on 2007-04-29
> **ludileptir said:**
> OK sorry i asked..

Don't be sorry,  it's fine.  Just post a new topic with your issue.

---

### Post by bulldog on 2007-04-29
> **jrlii said:**
> There are viruses, worms, trojans and other malware for Linux. Neither as many of them nor in as wide a circulation as those for Windows, but I understand they can be pretty nasty if you DO get one. Of course security holes are generally plugged faster than they are for Windows.

Since I'm still running dialup, I haven't bothered to configure the firewall, but with a broadband connection I figure it would be essential. As I understand it, Firestarter is a good GUI tool for setting up/managing the firewall.

f-prot is a good anti-virus, and for non-commercial use on Linux workstations is available free of charge. There is even a .deb package. The user interface, however, is pretty primitive: It is pretty much the same command line interface as the version of f-prot I used back in the 80s when the floppy disk was virtually the only vector and 1200 baud modems were fast. . .

You only should be concerned if you run your ubuntu as a root on a daily basis.
If you use ubuntu as it was mend, the change you get a working virus is minimal.
I ran Linux distro's for some time now,and I have a broadband connection for over 7 years,I use a router between my computer and my modem,and I never been infected by what so ever,not even in windows.

Safety starts with the user!

---

