---
title: "ubuntu speed and VmWare"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by howbag on 2006-05-24
Hello!
I am currently using Ubuntu breezy with gnome, and I run windows on a virtual server. it seems that this virtual windows is Extremely slow, and is getting slower and slower after I started it.
So I have two things I wanna try out, but need some info on forehand.

1. I want to strip ubuntu of unusual programs running in the background (which and how?) to make the machine run faster. (i.e. removing gnome and using a faster windows-viewer?)

2. I want to try another Distribution, to see if it runs faster, but without removing the virtual machine. (where is it, and how can I load it in a new vmware on the other distrib?) 

Thanks!

---

### Post by JELaVallee on 2006-05-24
Okay... so... give us this info:
1. Your Ubuntu system's hardware config.  Processor, bus speed, memory size, swap page size, etc.
2. Your version of VMWare.
3. Your VMWare virtual partition configuration (memory, disk allocations, etc.)
4. What version of Windows you're running.

Beyond that, I use the gnome-system-monitor app to give my "vmware" process a nice value of -2 or -4 This significantly speeds up my Win2k Pro VMWare virtual machine when I'm using it, but allows the system to rebalance when I come out and work in the linux/gnome desktop.  The upside of this is that you don't have to go stripping down your Ubuntu install to accomodate Windows...

For reference, I use Photoshop, Illustrator, Flash MX and MS Office 2003 Pro all in that virtual environment with no problems or slow downs what so ever.  But I also have  zippy machine with 2Gb of system ram.

cheers,
Etienne

---

### Post by aysiu on 2006-05-24
You don't need to remove Gnome to a get a lighter graphical environment.

Just add in IceWM or Fluxbox.

```
sudo apt-get update
sudo apt-get install icewm
``` Log out. Select **Session** and then **IceWM**. Log back in again.

Virtually nothing will be running in IceWM. Go to an xTerm and then type ```
vmplayer
``` or whatever command you use to launch WMWare.

You may also want to try ```
sudo apt-get update
sudo apt-get install bum
gksudo bum
``` to disable some unnecessary services.

---

### Post by Robgould on 2006-05-24
I use VMWar 5.5....the newest version available for download....whatever it is.  I am running Dapper and have VMWare running both XP and server 2003.  Both perform very well for me.  In fact, I am using Dapper because my nirtual machines perform much better from linux then from windows XP.  I am not sure why and don't really care.   My point is just that VMWare works very well for me in Dapper with Gnome running server 2003.  
 
My only complaint is that bridged newtowrking does not work from Linux.

---

### Post by Burgresso on 2006-05-24
JELaVallee,

What do you mean by gnome-system-monitor app and how do you set it to -2 or -4?

Thanks,
Burgresso

---

### Post by JELaVallee on 2006-05-24
[QUOTE=Burgresso]JELaVallee,

What do you mean by gnome-system-monitor app and how do you set it to -2 or -4?

Thanks,
Burgresso[/QUOTE]

Open a terminal window, type the command gnome-system-monitor and enter.

This opens a nice looking system monitor not unlike the Task Manager in Windows but much more functional.

Go to the "Processes" tab, select Menu->View->My Processes just to view your processes.  Find the "vmware" process and right-click on it.  Select the "Change priority..." option from the right-click menu.  This opens a priority dialog that lets you set the "nice value" of the process.   Nice values run -20 to +19 with 0 being the default nice priority value (i.e. everything gets the same priority when launched unless otherwise specified).  I usually set mine to  -4 which does a nice job of speeding up the VM w/o clobbering the rest of my system.

To do this from the command line you'd type "ps aux|grep vmware" and enter.  This would give you a list of all your processes that are running with "vmware" in the process name... You want to find the one with the process execution path of /usr/lib/vmware/bin/vmware and find the second number from the left of the output which is the process ID number (a.k.a. PID).  That number is different every time.  To nice down the value for that process, just type "sudo renice -4 -p {PID}" and enter.  This will prompt you for your system password and then renice the value to what you set (in this case, -4).

I prefer the gnome-system-monitor method because it's pretty and I'm a sucker for a good gui... 8^)

cheers,
Etienne

---

### Post by JELaVallee on 2006-05-24
[QUOTE=aysiu]You don't need to remove Gnome to a get a lighter graphical environment.

Just add in IceWM or Fluxbox.

...
[/QUOTE]

While that's useful for slimming down the WM/DM... I think it's a bit overkill for getting a speed boost when you can just adjust priority on the vmware process...

See my other posts.

Also, if you're trying to run VMWare on a 256Mb machine, you're going to have trouble no matter what... hence it being useful to know the system configs of the original poster.

word,
Etienne

---

### Post by aysiu on 2006-05-24
Makes sense.

Using BUM to turn off unnecessary system processes isn't a bad idea, though, is it--even in Gnome?

---

### Post by howbag on 2006-05-25
Thanks for the replies!
I am using an old machine (pentium 4, 512mb RAM, etc.)
I have the most recent version of VmWare Server console, but cant find the version number. But it is just downloaded.
but since I use a game in windows (which is the only thing I use it for), wouldn't it be better to diable things in gnome rather than setting the priority down on vmware?

---

### Post by howbag on 2006-05-27
I installed fluxbox, and everything worked perfectly! Some problems figuring out where this and that is under flux, but got it working after a while. Now I run my game in Windows under vmware, and both gimp, MMX and webbrowser in linux without problems! Thanks everyone!

---

