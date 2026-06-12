---
title: "Disabled wireless adapter, switching desktops"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Jeff Rage on 2007-02-10
I was getting tired of the issues I was having with XP, so I installed Kubuntu.  So far, this has been very frustrating.  I've been looking through documentation and searching the forums, but I'm not finding the answers I'm looking for. 

1. My Linksys PCI Wireless G adapter is showing disabled.  If it enable it, it goes back to being disabled.  Could this be a driver issue?  Is there the equivalent of Device Manager in Kubuntu?

2. How do I switch to the GNOME interface?

---

### Post by Happy_Man on 2007-02-10
1. Is there an exact model number you can give us for the router?

2. Kubuntu uses the KDE desktop environment, which is (in my opinion) more powerful but harder to grasp for the first-time user. To get a GNOME interface, I believe you can type 

```

sudo apt-get install gnome

```

into the Terminal to get it. You can then choose which dekstop you want when you log in. I'm not sure if that's the exact command to install, though, so try it. If it doesn't work, come back here and post. Welcome to Ubuntu!

---

### Post by Jeff Rage on 2007-02-10
1. Router is Linsys WRT54G
Wireless Card is Linksys WMP54G

2. Where is the Terminal that I can type this code?


Thanks for the welcome!  Wow, I feel like it's my 1st day on a computer today!

---

### Post by Happy_Man on 2007-02-10
Your terminal is helpfully located at Applications --> Accessories --> Terminal. 

And, guess what? You've got the same router as me! Yay! :) I'm typing this from my desktop that is wired into the router, but my laptop works fine too. There are a lot of great Howto's and tutorials on these forums for wireless cards and router problems, so try searching for a fix. If you still can't find one, come back here. Sorry I can't help more, but my laptop's being cranky and won't load itself up. Hope this helps!

---

### Post by Jeff Rage on 2007-02-10
OK, found Ternimal.  However, it didn't find gnome.

Is the thread you're referring to the " How to install WUSB54G for Dapper Drake"?  If not, I'll keep searching.

I've been at this for than 3 hours, I better take a break!

---

### Post by Happy_Man on 2007-02-10
Try this howto and see if it works: [http://www.ubuntuforums.org/showthread.php?t=241565]("http://www.ubuntuforums.org/showthread.php?t=241565") It seems to work fine, and if it does, congratulations! If not, try putting 

```

lspci

```

into your terminal and post the output back here.

---

### Post by Jeff Rage on 2007-02-11
As far as switching desktops, I found this on the Xubuntu  download page.

> If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. There you are! Next time you login, you can choose Xubuntu from the Session menu on the login screen.

However, using the Adept installer, I don't see a xubuntu-desktop package or a ubuntu-desktop package.

Do you need an internet connect for this to work?

EDIT: do you also have to be on the net to update that driver?

---

### Post by Jeff Rage on 2007-02-11
The computer I'm setting this up on normally connects to the net via wireless.  Will I need to have a connection to update the driver and to switch to Ubuntu/Xubuntu?

Just wanted to know before I haul my computer up to the second floor. :)

---

### Post by Jeff Rage on 2007-02-11
OK, i tired updating the driver, suing

sudo apt-get install build-essential linux-headers-$(uname -r)

Is said something about not finding the package

I went on anyway, doing
ote:
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz), but that gave me an eroras well

*Do I need an internet connection to do this?*

---

### Post by Jeff Rage on 2007-02-11
OK, I set up a direction connection, and am on the internet (yAy!)

When I run
sudo apt-get install build-essential linux-headers-$(uname -r)
I get
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential

When I go in the Adept Package Manager, I cannot find the ubuntu-desktop or Xubuntu-desktop.

It appears these problems may be related in that I'm not fidning packages?

---

### Post by Jeff Rage on 2007-02-12
Still working on this! :)  I reread the instructions from that thread and saw I overlooked something.

When running lshw, I see my card is a BCM4306, and not a Rt2500
I found this guide [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
The directions for adding Universe to the Package Manager must different for Kutuntu - the options they talk about aren't there.

Time for bed! :)

---

### Post by Jeff Rage on 2007-02-14
Just to follow up:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
This worked for adding repositions.  Using the column on the left, I added the gnome and xfce desktops, as well as firefox.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
This sucessfully got my wireless working.

---

### Post by MCSE_Crossover on 2007-02-14
> **Happy_Man said:**
> 1. Is there an exact model number you can give us for the router?

2. Kubuntu uses the KDE desktop environment, which is (in my opinion) more powerful but harder to grasp for the first-time user. To get a GNOME interface, I believe you can type 

```

sudo apt-get install gnome

```

into the Terminal to get it. You can then choose which dekstop you want when you log in. I'm not sure if that's the exact command to install, though, so try it. If it doesn't work, come back here and post. Welcome to Ubuntu!

You will actually want to type "sudo **aptitude** install ubuntu-desktop"

Always use aptitude, it makes removing it later much easier because it removes all dependencies as well. apt-get, synaptic, or adept remove the core application but leaves all dependencies.

---

### Post by MCSE_Crossover on 2007-02-14
Once you get internet, make sure to run "sudo apt-get update" to update your respository listing. Also, is your wireless card pci or usb? You can use "lspci" or "lsusb," respectively, to list the output for what is actually plugged into your computer. Post those outputs here if you can.

Part of the problem may be that there is a kernel driver already loaded with your operatig system that may be for your card, but, may not be functioning correctly. You will have to disable that driver once we figure out what it is by added a line to /etc/modprobe.d/blacklist and then possibly having to load a windows driver by using ndiswrapper.

paste the output of those commands so we can keep working on diagnosing the issue :)

---

### Post by Jeff Rage on 2007-02-14
My fellow MCSEr, I apologize if I was unclear, but I have solved all of the issues I was having! :)


From running, lspci, I found that my wireless card is a BCM4306
I installed NDISwrapper using this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) and that resovled the issue.

Using the instructions from the column on the left of that page, I installed grome and xcfe (which instructed to use sudo aptitude install)

I will make sure to run the updates using sudo apt-get update



Thanks for your help!

---

