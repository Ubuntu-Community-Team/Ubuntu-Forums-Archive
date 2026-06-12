---
title: "KDE apps on GNOME"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by devils3cups on 2006-11-02
Can you put kde apps on a Gnome environment?

---

### Post by skierkegaard on 2006-11-02
Yes, but it will require you to have many of the packages that KDE apps depend on.

---

### Post by devils3cups on 2006-11-02
ok so case in point. I wanted to install this app called kleansweep and when it tries to load it states "Details: Failed to execute child process "kdesu" (No such file or directory)". im assuming bc im not running a KDE desktop. what can i do?

---

### Post by bsussman on 2006-11-02
> **devils3cups said:**
> Can you put kde apps on a Gnome environment?

Install the normal way (synaptic, usually) and the needed parts of kde will be installed as well.

---

### Post by devilsadvocate1987 on 2006-11-02
sure. I have a nice mix of kde and gnome apps. while gnome looks nice with some neat font rendering, i prefer kde apps. synaptic or aptitude will be able to handle the dependancy correction 

sudo aptitude install <kdeapp> 

should do the trick

---

### Post by bsussman on 2006-11-02
I think you need to install kdesu - it is needed since kleansweep will want to act on files you might not own.

If you had installed all of kde, kdesu would be there.  But you need not install all of kde just to use kleansweep.

---

### Post by devils3cups on 2006-11-02
I installed kleansweet using synaptic. Kdesu is not listed in synaptic so can i just go get the installer files and install it. This is my first attempt to put a KDE app on my system i guess i got confused that there would be compatibility problems but i guess i ran into one of the rare situations where synaptic didnt put all the nessessary librarys on

---

### Post by kerry_s on 2006-11-02
> **devils3cups said:**
> ok so case in point. I wanted to install this app called kleansweep and when it tries to load it states "Details: Failed to execute child process "kdesu" (No such file or directory)". im assuming bc im not running a KDE desktop. what can i do?
 
Make link from kdesu to gksu. Open a terminal->
cd /usr/bin
sudo ln -s gksu kdesu

That should take care of that.

---

### Post by Sef on 2006-11-02
> I think you need to install kdesu - 

If it is a dependency, it should automatically be downloaded.  I installed K3b, and it downloaded all the depencies.

Installing K3b

It is also available in Add/Remove (Under Applications at the bottom.)

If you use the terminal, do it this way first:

sudo aptitude update

sudo aptitude install <app>

Note: Aptitude is better than apt-get since the former will remove all the depencies if you decide to uninstall it.

---

### Post by skierkegaard on 2006-11-02
kdesu should be part of kdebase-bin, so look for that package.

edit: My advice is the worst and the slowest...

---

### Post by Brownedwg89 on 2006-11-02
> **kerry_s said:**
> Make link from kdesu to gksu. Open a terminal->
cd /usr/bin
sudo ln -s gksu kdesu

That should take care of that.

that would work nicely... except its gksudo, not gksu
also, you could just replace kdesu in the shortcut to kleansweep with gksudo

so if the shortcut is "kdesu kleansweep" change it to "gksudo kleansweep"

---

### Post by devils3cups on 2006-11-02
kraig@kraig-laptop:~$ sudo aptitude install kdesu
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?


??? whats up

---

### Post by Bartender on 2006-11-02
Have you got some room on your HDD?  Did you know you can install the entire Kubuntu desktop via Synaptic?  Do a Search for the Kubuntu-desktop package in Synaptic and download.  Then you swap back and forth via Sessions button at log-in screen.  Take a look at [this]("http://www.linuxjournal.com/article/9369") guide.  Once you've logged into Kubuntu it'd be easier to take a look at these "k" packages you're interested in.

---

### Post by devils3cups on 2006-11-02
that seems alittle bit excessive but the gksudo tip worked. THX guys.

---

### Post by FreakinSyco on 2006-11-02
> **Bartender said:**
> Have you got some room on your HDD?  Did you know you can install the entire Kubuntu desktop via Synaptic?  Do a Search for the Kubuntu-desktop package in Synaptic and download.  Then you swap back and forth via Sessions button at log-in screen.  Take a look at [this]("http://www.linuxjournal.com/article/9369") guide.  Once you've logged into Kubuntu it'd be easier to take a look at these "k" packages you're interested in.

Wow that is sooo tempting to do. Any kind of performance hit having these sort of things? Any disadvantages other than used HD space?

---

### Post by kerry_s on 2006-11-02
> **Brownedwg89 said:**
> that would work nicely... except its gksudo, not gksu
also, you could just replace kdesu in the shortcut to kleansweep with gksudo

so if the shortcut is "kdesu kleansweep" change it to "gksudo kleansweep"

Here's a picture for ya->

---

### Post by Brownedwg89 on 2006-11-02
i did not know that... im so using gksu from now on :D

---

### Post by 3rdalbum on 2006-11-03
> **devils3cups said:**
> kraig@kraig-laptop:~$ sudo aptitude install kdesu
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?


??? whats up

It looks like you're running another package manager at the same time. Check that Synaptic is not open.

---

### Post by bsussman on 2006-11-03
> **FreakinSyco said:**
> Wow that is sooo tempting to do. Any kind of performance hit having these sort of things? Any disadvantages other than used HD space?

The main technical hit is the disk space and, theoretically, the very slight hit to memory when running a foreign app (a kde app in gnome or verse-visa).  But the whole perf hit is probably very very minor.

I think the chaos of deciding which desktop to run today is the serious downside.  Both can do most anything, sometimes a little differently in appearance.  All have irritating limitations or cumbersome workarounds (different backgrounds for different gnome workspaces comes to mind).  

Each has its fans, convinced theirs is better.  And they are right.  For them :)

And we haven't even mentioned the 64 zillion other desktops available :) .  Like MWM, FVWM, xfce, bzzt and whhhhp.  (some of those are made up but I am sure they will be released soon anyway)

I think it is a really good idea to settle on one rather quickly and get used to it, adding apps from the other family as needed or desired.

---

### Post by mat1t on 2006-11-29
> **devils3cups said:**
> ok so case in point. I wanted to install this app called kleansweep and when it tries to load it states "Details: Failed to execute child process "kdesu" (No such file or directory)". im assuming bc im not running a KDE desktop. what can i do?

I've filed a bug on this issue, as it affected me as well. Could you please go [here]("https://bugs.launchpad.net/distros/ubuntu/+source/kleansweep/+bug/73859") to validate it?

Regards,
Mat

---

