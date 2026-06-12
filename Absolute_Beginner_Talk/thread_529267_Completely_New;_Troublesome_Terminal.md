---
title: "Completely New; Troublesome Terminal"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Adamaeus on 2007-08-19
Hey there. I'm trying Ubuntu out mainly out of curiousity; I had an old MIllennium Edition PC from way back in 2000, and wanted to see if Ubuntu (6.06) would run on it. I'd heard Linux-based OSes are easy on memory--to my immense satisfaction, this is true. With ME this was a nearly-useless box collecting dust in my closet. It has a massive (</sarcasm>) 20 gig hard drive and runs off a 750 megahertz Intel processor, and on this old machinery, Ubuntu runs passably well. It's certainly not the Road Runner, but I have a feeling that as it runs usably well on such an old machine, on something new, it'd run lickety-split. 

I managed to install Flash; too bad, Flash games and .flv files don't run too well. 

I'm liking what I'm seeing, though. Ubuntu performs all the major things I do from my Windows machine, and with this Wine thing, I think there won't be much of a reason -not- to switch.

Oh, but I am having some trouble installing Beagle, Amarok, and VLC. When I use the terminal I enter the following code: 
apt-get install beagle
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


I have no idea what the heck that means. 

I try using sudo, and voila: 

sudo apt-get install beagle
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beagle: Depends: mono-jit (>= 1.0) but it is not going to be installed
          Depends: libgconf2.0-cil (>= 2.7.90) but it is not installable
          Depends: libglade2.0-cil (>= 2.7.90) but it is not installable
          Depends: libglib2.0-cil (>= 2.7.90) but it is not installable
          Depends: libgmime2.1-cil (>= 2.1.19) but it is not installable
          Depends: libgmime2.1-cil (< 2.1.20) but it is not installable
          Depends: libgnome2.0-cil (>= 2.7.90) but it is not installable
          Depends: libgtk2.0-cil (>= 2.7.90) but it is not installable
E: Broken packages


?_? I realize I am a total newbie, but I figured this was the most appropriate forum for that. I have never used Linux before. 

Any ideas?

---

### Post by thevictor390 on 2007-08-19
Wow, shows how good ME was.  I have XP on a 366 MHz laptop with a 10 GB HDD and it runs fine.  not enough room for a dual-boot though.

I'm not sure what's going on with Beagle, but in all honesty, I don't see why not install Ubuntu 7.04, since in my experience it is much easier to install.  Do you have the package manager or the add/remove programs list on that old version? Those are both graphical interfaces to install programs and packages.  I had no problem with VLC (following the instructions on the website), so that might work with beagle as well.

and FYI, I'm posting from a 300 MHz iBook Clamshell, just to show that you can easily run 7.04.  ubuntu seems to be very easy on the hardware.

EDIT: Unrelated question: for the last year or so, whenever I install a flashplayer from adobe it has gone PAINFULLY slow, whether its the Windows version (which took 5 hours to d/l 5 MB) or the linux version (which I'm working on now, 38 kb so far).  Does this happen to you or anyone else for that matter? If not how did you do the install?

---

