---
title: "New Install"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by StanRedfish on 2007-02-15
Hi;
I am a long time Windows user by necessity.  I am a programmer and with the advent of the OOS programs have decided to start the switch to Linux.  I also give away a couple of computers a year to young students who can't afford them.  With out having to purchase office and windows I can now afford to give away 3 instead of 2.

However on my first trip down this slope I experienced the following:
HP dx2200, 
     Video wouldn't install properly found solution
     Sound won't work don't understand solution
     download AVG anitvirus .rmp file, can't open it.

In all cases, solutions to the above are extremely cryptic and confusing.  I realized the problem is between my ears.  I think one very useful ingredient would be for solutions (such as the Realtek High Definition Audio drivers package) include very explicit examples.  I'm sure I will eventually figure this out as there is no doubt in my mind this is the way to go and so my information is offered constuctively.

If anyone can direct me to help that includes examples I would appreciate it.  Overall, I am very impressed by the work you all have done and am in your debt.  Hopefully, one day I will be able to be a contibutor as well.

Thanks,
Stan Ralph

---

### Post by renzokuken on 2007-02-15
ok, for the high def Realtek drivers, i had no sound either. to get it working i compiled the latest alsa-driver from source and my sound immediately started working upon reboot.

go here [ftp://ftp.alsa-project.org/pub/driver](ftp://ftp.alsa-project.org/pub/driver) and download the latest 0.1.14rc2 file to your Desktop. then run the follwing commands to compile the latest driver from source

```

sudo apt-get install build-essential
cd Desktop
tar xjf alsa*
cd alsa*
./configure
make
sudo make install

```

reboot and see if it works

as for .rpm files, these are packages more specifically for Red Hat and Fedora, ubuntu uses .deb (its a similar thing)

rpms can be converted to deb using Alien

```

sudo apt-get install alien
sudo alien name_of_file.rpm

```

this will create the deb file in the same place....to install the deb run

```

sudo dpkg -i name_of_file.deb

```

---

### Post by StanRedfish on 2007-02-19
thank you very much.  Your instructions worked perfectly.  In the mean time I set up another computer with Nvidia video.  The computer kept lock up and I installed 6.10.  That was a smooth install and everything has been working for 2 days with out incident.

Again, thanks for your help.

Stan Ralph

---

### Post by mikewhatever on 2007-02-19
Here is howto install AVG
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

the version in the howto is an older one, so enter the file name you actually have.

---

### Post by renzokuken on 2007-02-19
> **StanRedfish said:**
> thank you very much.  Your instructions worked perfectly.  In the mean time I set up another computer with Nvidia video.  The computer kept lock up and I installed 6.10.  That was a smooth install and everything has been working for 2 days with out incident.

Again, thanks for your help.

Stan Ralph

glad to be of service, happy ubuntuing!

Rob

---

