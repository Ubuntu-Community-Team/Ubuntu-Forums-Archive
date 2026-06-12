---
title: "desktop installation on dell optiplex gx1p"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by gldvxx on 2007-02-26
hi i feel like a total re-re.  anyways, i found this old dell optiplex gx1p and thought it would be a prime candidate for installing ubuntu on it.  i was able to install the server just fine and the command line stuff all seems to be working great.  when i installed the desktop, it looked like it was doing fine downloading everything, when suddenly the monitor screen went black.  the cd wasn't spinning, nothing was happening with the hard drive.  i left it like that for awhile and nothing happened.  i rebooted and attempted to install the desktop version of 6.06 LTS on the other hard drive.  at 51% in the Installing System, the machine hangs.  is there some kind of verbose install option or something so i can see what the problem is?  I'm worried there might be some kind of video card incompatibility or i dunno what.  Any ideas are welcome, thanks.

Server install: Ubuntu 6.10
Desktop install: Ubuntu 6.06 LTS

Hardware: Dell Optiplex GX1p (whatever the standard configuration for those are..)

---

### Post by poohbear1616 on 2007-02-26
Here's what dell shows for specs
> The OptiPlex GX1p managed PC is designed for today's business power users with aggressively priced, robust configurations featuring high-end peripheral components that help maximize the performance features of the Microsoft Windows NT Workstation operating system. Prices for the OptiPlex GX1p featuring the Pentium III processor at 450MHz start at $2,050 including 128 MB ECC SDRAM, 10 GB 7200RPM EIDE hard drive, integrated 3Com 10/100 Wake-up-On LAN networking, integrated 2X AGP video with 8 MB integrated video memory, integrated audio, 17X/40X CD ROM drive, Microsoft Windows NT Workstation 4.0:

---

### Post by poohbear1616 on 2007-02-26
Hit the wrong tab before I was done typing.....lol
6.06LTS disk won't work with that small a ram size, would have to do alternate disk.
Did the system hang during boot? which it should have.

---

### Post by tronica on 2007-02-26
when your at the black screen command prompt, the screen with go black after some time, just press space to wake it, if thats the case.

---

### Post by gldvxx on 2007-02-26
i guess it's not the default system config then because i meet the minimum ram requirements, it's 256 + some extra from the video card.  i can boot from the Live CD just fine and everything works great.   I went to the device manager to make sure everything was being recognized properly - i have a 3D Rage Pro AGP 1x/2x showing up.

when i click "install" and start the installation process, it hangs right after the disks have been partitioned.

when i had installed 6.10 server, the initial install went smoothly, but the screen went blank and the computer was unresponsive about halfway through the desktop install.  i did the desktop install using sudo apt-get install ubuntu-desktop or whatever the command is.  

in both cases the installs started fine, but part way through the gnome installation (i'm assuming it was installing gnome stuff) the computer hung and was unresponsive.  before i write it off as some nasty hardware issue (which is possible) i wanted to make sure there wasn't anything else i could try first..

---

### Post by gldvxx on 2007-02-26
it's still not working.. i reformatted the hard drive and ran the install again.  again it froze at 51%.  if anyone has any tips on ways to check the hardware or anything i can do to troubleshoot further i would realllllly appreciate it.. i really hate old computers..

EDIT: i re-formatted then re-ran the server install (it worked fine).  i ran sudo apt-get install ubuntu-desktop and tronica, you were right, the screen was just asleep.  i guess i didn't hit the space bar hard enough the first time hehe.  so i got everything installed np.

the only thing i'm confused about is why the Live CD (6.06 LTS) didn't work properly when the server install (6.10) has?  strange.  maybe i was too impatient.. :P

---

