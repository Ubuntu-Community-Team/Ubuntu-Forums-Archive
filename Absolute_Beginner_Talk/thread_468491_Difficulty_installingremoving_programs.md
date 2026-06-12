---
title: "Difficulty installing/removing programs"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by fuwkej on 2007-06-08
Whenever I install/remove programs the terminal does this, I usually have to hit enter a few times and the program will install, but it is buggy sometimes. Also when I boot up my system there is an error message saying Module build failed. Below is what the terminal shows when installing/removing programs. There are many more problems I've been having with Ubuntu Feisty Fawn, but I'm willing to try to learn it since open source is better. Another is that I seem to have lost my trash can and cannot get it to reappear  ;)

Setting up driverloader (2.36) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.36

No prebuilt modules for: Ubuntu-7.04 linux-2.6.20-16-generic i686-SMP
Trying to automatically build the driver modules...
(this requires a C compiler and proper kernal sources to be installed)

Where is linux source build directory that matches your running kernal?
[/lib/modules/2.6.20-16-generic/build] dpkg: error processing driverloader (--configure):
 subprocess post-installation script killed by signal (Interrupt)

---

### Post by waggygee on 2007-06-09
When I got my feisty fawn the ride was a little bumpy too. Have you successfully run a system update? After I ran one things seemed to run better. To get your trash can back, right click the title bar you want it on. there should be something written "add to panel...." click that and a window will pop up, you should find the trash can there.

---

### Post by fuwkej on 2007-06-09
Thanks for the help, got the trash can back (had to click on top panel and drag to bottom panel). All the updates are installed, but everytime I try to install something it asks:

Where is the linux source build directory that matches your running kernel?
[lib/modules/2.6.20-16-generic/build]

I hit enter and it does this

Building modules for kernel 2.6.20-16-generic, using source directory
/lib/modules/2.6.20-16-generic/build. Please wait...

ERROR: Module build failed!


Then it goes on to earlier botched installations that I tried, and they just keep stacking up.

Other than that most things function normally, except mpgs/wmv/etc movie files which flicker on and off when I play them, seem to work most of the time when I put them fullscreen.

---

### Post by Michaelt74 on 2007-06-09
Your problems seem unusual, did you check for errors when you burnt your Feisty CD? A suggestion could be to burn it again and reinstall. I have found Feisty to be amazingly stable and have encountered no serious issues at this stage. I'm no expert and am a new user, so I can't offer any technical solutions.

Good luck!

---

### Post by waggygee on 2007-06-10
I'm no total expert either but could you post your source.list. Yo can find it in places/computer/filesystem/etc/apt
Use the file browser Im not what the commands would be if you use the terminal. Then open the source.list file as text (in my computer I'd use text editor) they highlight all the text and copy and paste it. Im not sure if I'll be able to spot something out of the ordinary but I'll try

---

### Post by Dedoimedo on 2007-06-10
Hello,

In order to compile programs, you will need gcc, make etc.

The first thing you should install:
sudo apt-get install build-essential

Dedoimedo

---

### Post by waggygee on 2007-06-10
> **Dedoimedo said:**
> Hello,

In order to compile programs, you will need gcc, make etc.

The first thing you should install:
sudo apt-get install build-essential

Dedoimedo

I tried this on my computer and got this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Dedoimedo on 2007-06-10
Hello,

Try these:

[http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html](http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html)

If it doesn't work:

apt-get --fix-missing
apt-get update

Dedoimedo

---

### Post by Eric_Jardas on 2007-06-10
@waggygee : first you must close synaptic or some programs that is run with sudo.

---

### Post by waggygee on 2007-06-10
> **Eric_Jardas said:**
> @waggygee : first you must close synaptic or some programs that is run with sudo.

Oops... I ddnt realise I was running it in the background. Anyway, I tried the command again after I closed the synaptic package manager... It downloaded some stuff but I still cant install multimedia codecs (It downloaded and installed Beryl and Wine successfully though)

---

### Post by waggygee on 2007-06-10
> **laverabe said:**
> Whenever I install/remove programs the terminal does this, I usually have to hit enter a few times and the program will install, but it is buggy sometimes. Also when I boot up my system there is an error message saying Module build failed. Below is what the terminal shows when installing/removing programs. There are many more problems I've been having with Ubuntu Feisty Fawn, but I'm willing to try to learn it since open source is better. Another is that I seem to have lost my trash can and cannot get it to reappear  ;)

Setting up driverloader (2.36) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.36

No prebuilt modules for: Ubuntu-7.04 linux-2.6.20-16-generic i686-SMP
Trying to automatically build the driver modules...
(this requires a C compiler and proper kernal sources to be installed)

Where is linux source build directory that matches your running kernal?
[/lib/modules/2.6.20-16-generic/build] dpkg: error processing driverloader (--configure):
 subprocess post-installation script killed by signal (Interrupt)

I just found something. Its amazing! I mean it put everything I've tried since I got Ubuntu in simple steps. I wish I found it earlier though, I would have saved me alot of time [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
Have a look through it

---

### Post by fuwkej on 2007-06-11
Wow, all that worked perfectly.  Thanks for the help guys, and that website is great, it's like a free 1000 page manual. Thanks!

---

### Post by malathia on 2007-06-11
> **waggygee said:**
> I tried this on my computer and got this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Waggy, this error occurs when you have both synaptic or some other GUI repository add/remove manager open and try to run a sudo apt-get. Close your instance of the GUI manager before running the sudo apt-get commands to sidestep that issue.




*edit* oops, that was already stated. Ignore me. hah

---

