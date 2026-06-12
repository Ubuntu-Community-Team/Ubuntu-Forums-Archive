---
title: "Problems when installing NDISWRAPPER"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by d00derino on 2007-09-26
Please, let me start off by saying I'm an absolute Linux newbie. I have no idea what's going on, and have basic knowledge of UNIX commands, all stemming from either class, or DOS. 

That said, getting NDISWRAPPER to work is THE hardest thing I've done in my life...and it shows, because it doesn't work.

Let me run you through my terminal commands:

1) tar -zwvf ndiswrapper-1.48.tar.gz -- EXECELLENT this works! 


2) cd /home/user/ndiswrapper-1.48 -- Works again, a simple change directory command, I get that!


3) make distclean -- Whole bunch of stuff I don't get. Probably writing and setting permissions, cause it kinda looks like what you when you CHMOD. Cool, that worked. 


4) make -- Runs for a while...but then I get so many errors I dunno what to do with myself! Here's the first one: "gcc -g Wall -I../driver -o loadndisdriver loadndisdriver.c (next line) loadndisdriver.c:15:20: error: stdlib.h: No such file or directory"

After that, I get more of the same kind of errors. At the end, however, I get this:

"loadndisdriver.c:590: warning: implicit declaration of function 'closelog'
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory 'home/user/ndiswrapper-1.48/utils'
make: *** [all] Error 2"


5) make install -- I figured, I might as well go for the next step anyway. I get the same kind of errors, except the directories are different.


6) ndiswrapper -l mn510.sys -- Ok, this is where I figured, let's just run the end of this thing baby! But I got "Error: no versions of ndiswrapper found!"



-----
Can anyone help? FYI, I used the installation guide found [here](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/).

Alternatively, are there any cheap wireless adapters I can just buy and install on Linux easier? I looked at Best Buy, asked the Geek Squad, and none of them know Linux.

Please help...I'm donating this PC to a community center, and they wanted it all bare-bones only with internet access and a text editor on it. I suggested Linux because this way the kids can't really download any viruses and keep a P3 running as fast as it can without all the junk Windows loads up on startup. 

Thanks for any and all help

---

### Post by dca on 2007-09-26
What kind of wireless card is it because you may have to blacklist existing drivers...  For instance I have to blacklist 'ath_pci' and use ndiswrapper to load Atheros Windows drivers because the card won't work w/ MadWifi...

---

### Post by Kobalt on 2007-09-26
If you are new to Ubuntu then the best way to install ndiswrapper is to go into System > Admin. > Synaptic package manager. Search for ndiswrapper, select it and apply the changes. 
Here you go, it's installed.

About your wireless chip: search the cheapest you can find (pick 2 or 3) and come back here to search for feedback about that hardware. That should help :)

---

### Post by d00derino on 2007-09-26
I have ndiswrapper-common and util, but I think I'm doing the right thing.

I have a MS MN-510 wireless adapter, I took the drivers from the CD and they are the ones that are listed on the site to work. 

Ok, it installed it, but what dir do I need to be in?

Edit: Ok, let me do this again...I have MN150.inf and MN150-50.sys in my /home/user/ndiswrapper-1.48 dir. 

So I did:

cd /home/user/ndiswrapper-1.48
nsidwrapper MN510.inf

And I got: Couldn't create etc/ndiswrapper/mn150: Permission denied at /user/sbin/ndiswrapper-1.9 line 146

Help again please?

---

### Post by Kobalt on 2007-09-26
Try ```
sudo ndiswrapper -i /home/user/ndiswrapper-1.48
```

---

### Post by d00derino on 2007-09-26
Ok, I ran:

sudo ndiswrapper -i /home/user/ndiswrapper-1.48/MN120.inf

and it installed it...now what?

Edit: Ok, I ran the list function, and I get this:

mn120: invalid driver!
mn120-50.sys: invalid driver!
ndiswrapper-1.48: invalid driver!

What the heck is going on?

---

### Post by d00derino on 2007-09-27
I should probably also mention that I have a Microsoft MN-510 wireless adapter I'm trying to install.

It's not under the lists, but the CD it comes with has the same exact drivers as the one on the list. Basically, I'm just putting the driver CD in, taking the .inf and .sys files, and putting them into the ndiswrapper-1.48 folder, and trying to run it like that.

And I get the invalid driver sequence. Although the MN120 ones ARE supported in ndiswrapper.

---

