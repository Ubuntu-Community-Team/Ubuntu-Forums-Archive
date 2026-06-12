---
title: "How to start gnome?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by RaicesRadicales on 2006-03-16
Ok... I know this thread may result in a newbie bashing around here, but I ran out of everything I had... I just can't start Gnome from the Dapper Drake release... Every since I had installed Ubuntu, it always boot me to the terminal screen and I can't get out of there. I'm not very familiar with sudo commands and alikes... so please, if anyone can help me I'll be much appreciated.. thanks..

---

### Post by Sutekh on 2006-03-16
- Firstly I wouldn't recommend running Dapper Drake as you day to day PC, especially since you are new to Ubuntu/Linux.  I would really recommend using the current release the Breezy Badger.

 - Ok, so how did you install Ubuntu, from a Dapper Drake CD?

[Or did you install from a Breezy CD then dist-upgrade (from what you've said I think this is unlikely so don't worry if you don't understand what I'm saying)]

 - When you installed Ubuntu, did you choose to do a normal install (just press Enter at the main installation screen)?

 - Or did you choose to do a server/expert install (type server/expert then press Enter)?

 - If you chose a server install then you would not have installed the desktop environment (GNOME) so we are going to have to do that now

 - If you use this command it will install the basic Ubuntu desktop (GNOME and applications)

```
sudo apt-get install ubuntu-desktop
```
 - When you are prompted for a password, use the one that is for your user.

 - A lot of downloading will begin and when you are finished you should be able to start GNOME.

 - If it doesn't start automatically, then use this code (one time) to start it
```
sudo /etc/init.d/gdm start
```

---

### Post by Buffalo Soldier on 2006-03-16
Please do not take this the wrong way. But if I may ask, why are you trying Dapper Drake? It's a development version. The latest stable version of Ubuntu is Breezy Badger (or sometimes refered to as Ubuntu 5.10).

It may be easier for you to try the stable version rather than the development version. Plus I believe there is more able and willing people to help if you use Breezy.

No matter running on Breezy or Dapper... here's a few command that might help you to give us more info about your computer:

**sudo lshw** give's a list of your computer hardware
**lspci** gives a huge list of components in your machine.
**cat /proc/cpuinfo** will tell you about your CPU.
**cat /proc/meminfo** tells abou memory.

Any command that starts with **sudp** will ask your for *your* password. It's the one and only password that you entered during installation. More on sudo -> [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

This two places is a good place to start digging around:
- [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
- [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

---

### Post by RaicesRadicales on 2006-03-18
Well, thank you guys for posting.
I'm using the dapper release cuz, if I'm not mistaken, is the only release that supports low memory installation. I'd tried the breezy badge but it always fails before the installation was completed. So, a member from this forum suggested me to try this release, which did install fine.
I tried to use the command "sudo /etc/init.d/gdm start" command but it returned "invalid command", so I supposed the gnome wasn't yet installed so I did the other command you posted "sudo apt-get..." and it didn't start to unpack some files and it was taking way long so I left the computer on and went to college. When I came back the monitor was on standby and wouldn't come back so I rebooted it. When ubuntu started I did the start command again, but again, it didn't work. However I ran the aptitude application and oddly enough I could see GNOME DESKTOP listed under INSTALLED PACKAGES and NOT-INSTALLED PACKAGED (or something like that)... anyway.. I tried to install again with the apt-get command and this is what it said "dpkg was interrupted. you must manually run dpkg --configure -a to correct" so I did and I got this then "setting up scrollkeeper (0.4.14-10ubuntu3) ...
Rebuilding the database. This may take some time.." and it does take a while and then says "out of memory. Killed process 4031 (dpkg)"
The thing is I'm not sure which memory is it referring to... is it the RAM or the hard disc? I think it is probably the RAM (64 mb shared with 8 mb for the inboard video card) since in the installation process I did partioned 10 gb for the linux thing (which I can't see when I'm at windows,l by the way, is it normal?)
wait for any tips... thanks..

---

### Post by steve.horsley on 2006-03-18
OK. ONce you are logged in, the command to atart x is **startx** . See what errors you get from that and post them here. 

It may be worth checking that the whole desktop has been installed. Try sudo apt-get install gnome-desktop and try to work out if it has problems, or if it says it's already installed you fool.

---

### Post by RaicesRadicales on 2006-03-18
I have said what I get when I do the apt-get thing... it tells me to configure manually by running "dpkg --configure -a" and when I do that it take a while only to tell me that I'm out of memory...
When I did the startx thing it told me "Xsession: unable to start x session --- no "/home/allen/.xsession file, no "/home/allen/.Xsession file, no  session manager, no window manager, and no terminal emulators found; aborting."
what can I do?

---

### Post by bonzodog on 2006-03-18
I think the big problem here is that X will struggle on much less than 128MB of memory. Low memory installations for linux are 128MB > 256MB of memory.
I really do not think you will ever get gnome to run on it - you might get fluxbox or something like that to run.I even think XFCE would be a bit much for it. look at fluxbox, blackbox, or windowmaker for it.

---

