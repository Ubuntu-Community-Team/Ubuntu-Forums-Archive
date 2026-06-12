---
title: "Ubuntu 6.06 LTS on iMac DV-SE"
date: 2006-07-08
forum: Apple PPC Users
---

### Post by arsche on 2006-07-08
I am trying to get Ubuntu 6.06 LTS for Mac working on a iMac DV-SE G3 400 MHz with Mac OS 9.04, videocard ATI 128VR, 640MB ram, 12GB harddrive.

After loading succesfully all packages from the CD, I get a prompt for a very short time and after that the screen turns black, the whole machine stops
being usable.
Before installing it on my machine, I first want to see whether it's worth the hassle in the first place. 
So I want to know how I can remedy these problems.

AvS

---

### Post by RHTopics on 2006-07-08
> Before installing it on my machine, I first want to see whether it's worth the hassle in the first place.


If this means you are trying to use the Live CD, then you are experiencing a common problem with slot-loading G3 iMacs.  The Live CD does not properly setup the xorg.conf file.  This file controls how the X server is configured which affects the graphical display.

Below is a link to a thread which discusses this problem along with solutions to fix it.  This problem exists in both Ubuntu 5.10 and Ubuntu 6.06 

[http://www.ubuntuforums.org/showthread.php?t=75604&highlight=imac+g3+live+cd+blank](http://www.ubuntuforums.org/showthread.php?t=75604&highlight=imac+g3+live+cd+blank)

---

### Post by arsche on 2006-07-08
>Below is a link to a thread which discusses this problem along with >solutions to fix it.  This problem exists in both Ubuntu 5.10 and Ubuntu >6.06 
-Thanks for that link.
I've read it and it would mean that each time I use the Live CD I have to type these lines, cause you can't save them on the CD itself of course.
So the alternative is installing everything, which I'm not sure whether I would like to right now. 
So if there are other ways to bypass this problem for the time being, I would very pleased to hear them.

AvS

---

### Post by RHTopics on 2006-07-09
After reading your reply, I investigated a new feature available with Unbuntu 6.06, it is called *Live CD persistence*.

*Live CD persistence* provides for the automatic savings of your activities while using the Live CD.  In essence, through the use of storage device like an USB pen drive, your Live CD behaves as though it is writable.

Using *Live CD persistence* allowed me to permanently fix the iMac G3 blank screen problem.  When I now boot up my iMac using the Live CD, it now goes into the X session with no intervention.

Below is a link to the Ubuntu documentation, which describes how to use *Live CD persistence*.  

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

That document does not describe how to boot a Mac computer with the persistent option.  So, when you boot your iMac, type the following at the **boot:** prompt

   ```
live persistent
```

Also, even with *Live CD persistence*, the Live CD boot process will rename your modified "xorg.conf" and build the faulty one.

To overcome this, you will need to make a backup copy of the modified "xorg.conf".  I copied "/etc/X11/xorg.conf" to "/etc/X11/xorg.conf.good".

And then you will need to find a place to copy the backup copy of "xorg.conf" back to "/etc/X11/xorg.conf" when the Live CD boots up.  I modified "/etc/init.d/gdm" which is the script file used to bring up the display manager.  Below is a partial listing of the modified "/etc/init.d/gdm".

```
#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001

set -e

cp /etc/X11/xorg.conf.good /etc/X11/xorg.conf

# To start gdm even if it is not the default display 
```


Using *Live CD persistence* allowed these changes to be automatically saved and ready for the next boot up with the Live CD.  The boot up process does take longer when using *Live CD persistence*.  It takes about 5 minutes to boot up my iMac G3 350mhz with 384 RAM.

Another note about the Ubuntu documenation on *Live CD persistence*.  I used a new USB 512MB pen drive and it did not required to be partitioned because it showed it did not have any partitions on it.  I just formatted it as instructed and it worked fine.

---

### Post by arsche on 2006-07-10
>After reading your reply, I investigated a new feature available with >Unbuntu 6.06, it is called *Live CD persistence*.
-Thanks for that informative reply.
  As soon as I've got the time, I'll continue to investigate the matter further.

I'll let you know what the outcome is.

Thanks,
AvS

---

