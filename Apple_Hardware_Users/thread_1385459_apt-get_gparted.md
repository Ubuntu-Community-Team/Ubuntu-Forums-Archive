---
title: "apt-get gparted"
date: 2010-01-19
forum: Apple Hardware Users
---

### Post by rlinsurf on 2010-01-19
Since this is the main thing I'm trying to install, and I can't currently get an internet connection up, will apt-get install gparted work without an internet connection or can I download gparted from their site and manually do the install?

---

### Post by Elfy on 2010-01-19
You can download it and burn it as an iso and boot with it.

Possibly better than having to use the ubuntu livecd, quicker to boot - at least for me it is.

---

### Post by rlinsurf on 2010-01-19
Ah, I tried this and it only boots to the point right after the command line. Then it just goes black.

Is there anything special you did to get this to work? 

I'm on a MacPro3,1.

---

### Post by jml on 2010-01-19
rlinsurf, did you really meaan that you want to install gparted on your system?  gparted is designed to be run as a live cd/distro.  It's my understanding that gparted can not repartition a disk drive that is actively being used.  So if you install gparted to your computer's HDD, you would not be able to repartition it if that is your intent.  You would be able to work on other drives connected to your system, however.

In answer to your question, apt-get install will work without an internet connection if your sources list includes CD's or DVD's (used for your initial install ,for example.)  If your sources list points to outside repositories, then apt-get will not be able to access them without an internet connection.  

How would you download gparted from their site if you can't get an internet connection up?  If you can use another computer to access the internet, then I would download an .iso image of gparted, burn it to it's own optical disc, and use it as a live CD/Distro.

Joe

---

### Post by rlinsurf on 2010-01-19
Hi, Joe--

I actually only need to use gparted, not specifically unbuntu -- however it does look fun in itself. I'm on a Mac Pro, and of course, from within that os I can download anything I need. It's needed not to re-partition, but to mount and then copy one drive to another. I have tried booting from the live CD, but it only gets to the end of command prompt section, and then just goes to a black screen. Since I have the live cd, and have downloaded gparted-0.5.0.tar.bz2, can I use either of those to do the install? If so, could you step me through that process?

---

