---
title: "Installing Ubuntu on 128mb Computer"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by dmpolska on 2007-05-26
Hey all, I just clean installed Ubuntu 7.04 on a computer with 128mb... but, after logging in the only thing that shows up is the background image and nothing else. 

So I am guessing that the computer doesn't have enough ram... which is pretty disappointing. Anyway, any solutions to this problem, or is there another version I can install? 

Thank you

---

### Post by taurus on 2007-05-27
With only 128MB of RAM, try Xubuntu or Fluxbuntu.

[http://www.xubuntu.org](http://www.xubuntu.org)
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

---

### Post by drakos on 2007-05-27
I believe 256mb is the minimum for an Ubuntu install. I recommend using Xubuntu, which uses the Xfce desktop environment and is designed for older and slower machines. I use Xubuntu 7.04 myself, and I've been very happy with it.

---

### Post by dmpolska on 2007-05-27
Thanks for the suggestions. Whats the different between Xubuntu and Ubuntu? Is Xubuntu worse? And what's the difference between Xubuntu and Fluxbuntu? Seems like a lot of different versions.

---

### Post by taurus on 2007-05-27
Ubuntu uses Gnome window manager (heavy on system resources--RAM).
Kubuntu uses KDE window manager (heavy on system reources--RAM).
Xubuntu uses XFce4 window manager (light on system resources--less RAM).
Fluxbuntu uses fluxbox window manager (light on system resources--less RAM).

---

### Post by confused57 on 2007-05-27
You probably should the alternate install cd(Xubuntu) with only 128 mb ram.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

If you have an internet connection on the computer you're installing to, you might consider Ubuntu Lite:
[http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite)

---

### Post by ryanVickers on 2007-05-27
Yes, use xubuntu.  You could also add some ram - I think that most programs won't run that great on so little, even on xubuntu.

Another solution is add a *really, really* fast harddrive partitioned 100% as swap :p

---

### Post by voided3 on 2007-05-27
I once ran WinXP on a 200mhz comp with 64mb, but it was horrendously slow, so it should be possible for Xubuntu to make things work out. I have used Xubuntu on comps ranging from 192mb of RAM to 1.25 GB and it consistently only uses about 66-80mb at boot, so you should be fine for basic programs like Gaim and Abiword, but you'd have to use a pretty light weight web browser, maybe a simplified configuration of Opera or Seamonkey. What kind of system is it exactly? Chances are pretty good that you could get it up to at least 256mb or more for next to nothing, which would be much better. Otherwise, Puppy Linux would be a good choice as it uses even less than Xubuntu. You also can disable services to save some RAM; one of my comps running Xubuntu is a 713mhz OCed Celeron with 384 of ram and I disabled cpu frequency scaling and printer services since i don't use one with it and it shaved off about 12mb at boot. You also could do a server install and then download the ICEwm or fluxbox wndow manager if you really want to test your hand at tweaking. Good luck!

---

### Post by RedSquirrel on 2007-05-27
Here is a quotation from the [Xubuntu website]("http://www.xubuntu.org/get#requirements"):

> Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.
So, it may work on your system, but it may not be really fast.

As mentioned above, you could install the server edition and then a lightweight window manager on top of that. 

You can do this with the following guide, which uses the net installer:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

or you could download the server edition CD from [www.ubuntu.com]("http://www.ubuntu.com") and install that and then just do:

```
sudo nano -wB /etc/apt/sources.list
```Comment out (put a # in front of) lines with **cdrom: **in them, otherwise you'll be asked to insert the CD each time you want to install something.

Then

```
sudo apt-get update
``````
 sudo apt-get install xorg xterm gdm fluxbox firefox gksu synaptic

```Configure the X server:
```
 sudo dpkg-reconfigure xserver-xorg
```
Generate a basic Fluxbox menu:
```
sudo update-menus 
```
Start X so you can login to Fluxbox:
```
 sudo /etc/init.d/gdm start
```This will be a very lightweight system.

---

### Post by DJ Wings on 2007-05-27
Xubuntu is definitely the choice for a decent desktop on an old system. Fluxbuntu is still under development, and XFCE is more complete anyways.

---

### Post by houstonbofh on 2007-05-27
I have run Ubuntu, with full Gnome support, in 128 meg.  You need to install with the alt-install disk.  You need a very big swap file. (I used 1 gig)  It will be slow, but usable.  If you have installed it, and can not log in, you have a different problem.  Changing flavors may or may not help.

---

### Post by SteveHoffmanUK on 2007-05-27
I have a older Dell Latitude CSx laptop that I bought used, with 128Mb, and I have run Dapper, Edgy and Feisty on it, both with Gnome Ubuntu and XFCE Xubuntu without any problem. It's a bit slow, but everything works OK on it. It has a Belkin wireless PCMCIA card that works well with my home broadband network, and have even used it as a remote terminal for my networked desktops. I have always used the Alternate CD install method. I can view BBC video clips with sound without any problems.

128 Mb isn't a serious limitation for Ubuntu unless you want to do something really whizzy or cutting-edge. That's my experience, anyway.

---

### Post by ebs16 on 2007-05-28
> **RedSquirrel said:**
> 
```
sudo apt-get update
``````
 sudo apt-get install xorg xterm gdm fluxbox firefox gksu synaptic

```Configure the X server:
```
 sudo dpkg-reconfigure xserver-xorg
```
Generate a basic Fluxbox menu:
```
sudo update-menus 
```
Start X so you can login to Fluxbox:
```
 sudo /etc/init.d/gdm start
```This will be a very lightweight system.

This worked perfectly on a clean ubuntu fiesty server install. Thanks!

---

