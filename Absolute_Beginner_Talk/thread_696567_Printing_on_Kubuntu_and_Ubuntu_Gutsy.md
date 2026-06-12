---
title: "Printing on Kubuntu and Ubuntu Gutsy"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by steve.t on 2008-02-14
Hi everyone,
I have a Canon i560 on which I have been trying to print from Gutsy. I initially installed Kubuntu Gutsy, and could not find a driver for the printer. I tried all of the relevant gutenprint packages, updating the relevant CUPS packages. No luck.
I then installed Ubuntu Gutsy, and hey presto, there's the driver, printer installed and operating perfectly.
But I like KDE, so I installed kubuntu-desktop. I was monitoring the installation, and to my horror, the kubuntu-desktop installation installed/updated the cups-driver-gutenprint package. The Canon i560 driver no longer available for selection and installation in the KDE Print Add Printer Wizard.
Fortunately, the installed printer is still operational and works perfectly, which leads me to believe that the driver file/s remains somewhere on the system.
So, my question is in two parts:
1. What's the fundamental difference between Ubuntu Gutsy and Kubuntu Gutsy in the area of print drivers and printing; and
2.  What do I have to do to make Kubuntu behave itself and do what Ubuntu does.
I have posted a similar question in other forums, and I am posting this thread on Kubuntuforums as well.
I refuse to believe that nobody else has experienced this problem, and that nobody has an answer.  There must be someone out there in forum world who knows.

Thanks and cheers,
Steve Terek

---

### Post by kernel tom on 2008-02-14
okay, seeing how all ubuntu distros use the same repositories you should be able to find it. 

Also, Ubunut/Kubuntu should handle printing relatively similar if not exactly the same way.

You could use a live Ubuntu CD and boot from that, find the printer driver on the CD's filesystem and copy it to you're Kubuntu hard drive.

-kt

---

### Post by buntu_hugenewbie11 on 2008-02-29
I have a similar problem where the printer settings in Kubuntu do not show any drivers.
So when I go to install a printer I use a downloaded ppd for my printer. Problem is that when I need to quickly print on a printer in a different office (I am on a laptop) finding the driver via the command window and locate command becomes a time consuming process. Does anybody know how to get the list of drivers on to my printer system settings screen?

---

### Post by zukakog on 2008-03-03
Same problem. KDE doesn't list any of the Gutenprint drivers.

---

### Post by luceerose on 2008-03-04
I have this same problem with a Canon MP780 on Kubuntu 7.10
This is what I had to to;
1) Install gutenprint
2) Install Xfce (xubuntu-desktop)
3) Use the Xfce print wizard thingy to set it up
At this stage printing worked in Xfce
4) Uninstall xubuntu-desktop (which took gutenprint with it)
I could then see the drivers listed in print setup thru KDE, but printing no longer worked.
...so on to last step,
5) Re-installed gutenprint packages.

And everything worked.

PS If you try this using Ubuntu or Xubuntu as a temporary desktop, install with aptitude NOT apt-get.
Using apt-get will make it a pain in the **** to uninstall & get back to kde.

Oh and also, I installed Kubuntu 8.04 the other day and it installed the printer without my intervention. Unfortunately 8.04 is still a little buggy & I couldn't get Hardy working well enough to use full-time and had to go back to Gutsy.

I have now switched from 32bit gutsy to 64bit gutsy so after a fresh install, I am looking for a way to install the printer without having to do those 5 steps I mentioned.

Obviously I'm looking forward to Hardy Herron next month.
But for now, I'd like to find a way that doesn't involve changing desktop then uninstalling & reinstalling stuff.

---

### Post by luceerose on 2008-03-04
I compared the installed packages on my Xubuntu PC to the ones on my Kubuntu installation.

Results:
the difference is >>> "hal-cups-utils" package

I installed just that one package, rebooted & it worked. The printer was recognized, installed & working.

My MP780 must use what is called a HAL UDI which means that cups needs the hal-cups-utils package to know how to communicate with it.

See if this fixes the problem with your i560, steve.

1st - make sure you have all 5 gutenprint packages installed. They are;
cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2
libgutenprintui2-1

2nd - install hal-cups-utils

3rd - Reboot

If that doesn't fix your problem it probably means that your printer is not in the gutenprint driver database.

---

### Post by steve.t on 2008-03-04
Thanks mate, I'll give that a go over the next few days and let you know how I got on.  I've now read so many posts about printing, that between all the suggestions or a combination of two or more, I may actually get it working.  That's what long weekends are for, right?
Cheers,
Steve

---

### Post by steve.t on 2008-03-11
Just following up. I didn't bother re-installing Kubuntu. Ubuntu works, but it just isn't as pretty as Kubuntu.  I'll wait until Kubuntu Hardy is released and try again. BTW, do you know if Kubuntu Hardy comes with i560 support?
Cheers,
Steve

---

