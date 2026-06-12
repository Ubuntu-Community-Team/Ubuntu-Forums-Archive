---
title: "[SOLVED] HP LaserJet 1020 Recognized by Ubuntu 7.10, but does not print"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bconverse on 2007-11-04
Hi,

I've been trying to read about this problem, but most of the stuff I've found is regarding earlier versions of Ubuntu. Anyways, Ubuntu recognizes my printer fine, but, whenever I try and print something, nothing happens.  The job appears to have gone though, as the printer icon appears in the notification area, but no printing.  The jobs are backing up too, as I've tried to print a test page a few times, and it adds it as job number 5 or 6, indicating that there are other jobs still in the printer queue. I am puzzled by this whole problem, so any help would be appreciated.

Thanks

---

### Post by DutyDuty on 2007-11-04
I've had a similar problem with my Officejet. 

also, bump.

---

### Post by elmagno on 2007-11-04
I installed one of these on Feisty on Friday. At first, it displayed like yours but wouldn't print anything either. I'm away from the machine and the information right now, but I was using a foo...something driver available on the net. It would configure and make, but no printing. I discovered it was not creating some needed directories, even when I ran the install as su. Luckily it has an uninstall with it. 

That foo... driver may work for you (it has for a lot of people), though it didn't work for me. Then scouring Google, I found a deb for download in a forum--made by an individual and not in repositories. It worked like a charm. Hope you can find it.

From what I understand HP Imaging can't install this one as it has no onboard firmware in the printer.

---

### Post by bconverse on 2007-11-04
> **elmagno said:**
> I installed one of these on Feisty on Friday. At first, it displayed like yours but wouldn't print anything either. I'm away from the machine and the information right now, but I was using a foo...something driver available on the net. It would configure and make, but no printing. I discovered it was not creating some needed directories, even when I ran the install as su. Luckily it has an uninstall with it. 

That foo... driver may work for you (it has for a lot of people), though it didn't work for me. Then scouring Google, I found a deb for download in a forum--made by an individual and not in repositories. It worked like a charm. Hope you can find it.

From what I understand HP Imaging can't install this one as it has no onboard firmware in the printer.

I think I read something about that, but I haven't had any luck finding anything yet. That driver you said you were using though that didn't work is the one that was automatically set up for me.  I am still new to Ubuntu, so I think I need some help installing the new driver (if I can locate it)

---

### Post by bconverse on 2007-11-04
Any suggestions? I really don't want to keep Windows around for printing.. ha.

---

### Post by bconverse on 2007-11-05
bump

---

### Post by drs305 on 2007-11-05
I have a HP Laserjet 1000 which had the same problem in gutsy (worked in edgy and feisty). I found that the new Gutsy driver didn't seem to work. The solution for me was to get different drivers, which can be found at:
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)
which was referenced by this thread:
[http://ubuntuforums.org/showthread.php?t=583143#4](http://ubuntuforums.org/showthread.php?t=583143#4)

For the LJ1020, change the applicable line in the instructions to  

```
./getweb 1020
```

The thread involved more steps but I found that I didn't have to complete them all. You can read the previous posts if the way I did it doesn't work for you.

Good luck.

---

### Post by bconverse on 2007-11-05
> **drs305 said:**
> I have a HP Laserjet 1000 which had the same problmen. I found that the Gutsy driver didn't seem to work. The solution for me can be found at:
[http://ubuntuforums.org/showthread.php?t=583143#4](http://ubuntuforums.org/showthread.php?t=583143#4)

Change the applicable line in the instructions to  

```
./getweb 1020
```

The thread involved more steps but I found that I didn't have to complete them all. You can read the previous posts if the way I did it doesn't work for you.

Good luck.

Great, thanks! I am having some trouble though. When I get up to the 'make' step i get his:
```
#
# Dependencies...
#
# ... OK!
#
cc -O2 -Wall -o foo2zjs foo2zjs.o jbig.o jbig_tab.o
/usr/bin/ld: cannot open output file foo2zjs: Is a directory
collect2: ld returned 1 exit status
make: *** [foo2zjs] Error 1
brandon@brandon-desktop:~/foo2zjs$ sudo ./getweb 1020
sihp1020.img

```

however, if i put in the ./getweb 1020
 i then get this...

```
(c) Copyright Hewlett-Packard 2005

```

and then with 'make install'

```
#
# Dependencies...
#
# ... OK!
#
cc -O2 -Wall -o foo2zjs foo2zjs.o jbig.o jbig_tab.o
/usr/bin/ld: cannot open output file foo2zjs: Is a directory
collect2: ld returned 1 exit status
make: *** [foo2zjs] Error 1

```

I installed the hotplugs, and CUPS as well, but the printer still does not work

Is it not installing correctly?

---

### Post by drs305 on 2007-11-05
When I ran the script exactly as it was posted it ran perfectly. 

Did you cut & paste each line to prevent mistakes.It is possible I have a typo in my post so I'd try to use the same steps but off the original post. You shouldn't get any errors. 

And I'm not surprised that your's didn't work - with the foo2zjs errors you wouldn't get the right drivers, which is why we were having problems in the first place.

I'll try to analyze your output but I'm pretty new at this stuff and hopefully someone else will chime in.


Added: The link references aren't that clear as to where to start.

Here are the notes I took and the commands I followed (change 1000 to 1020). Make sure when you cd/ you are going to the location of the foo2zjs folder. In my case, I was at the ~/ prompt when I began running the commands in terminal. You want to be inside the foo2zjs directory when you run the MAKE command.

```

		sudo apt-get install build-essential
		wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
		tar zxf foo2zjs.tar.gz
		cd /home/<yournamehere>/foo2zjs
		make 
		./getweb 1000
		sudo make install
		sudo make install-hotplug
		sudo make cups

```	
	
Remainder wasn't necessary for me and I selected the recommended printer from the gutsy printer install and everything worked. There were 3 choices, a recommended and two others. Even though the recommended hadn't worked before, that is the one I selected and which worked this time.

This is the part of the script I didn't have to get to. If you have to go further, substitute 1020 for 1000
```
gksudo gedit /etc/hotplug/usb/hplj1000
```	
		    # Set $DEV to, e.g. /dev/usb/lp0, to force the device you want
		    # Else, leave it null to automatically detect the device
		    #
		    DEV=/dev/usb/lp0
		    #DEV= ""
```
	sudo gnome-cups-manager	
```

---

### Post by bconverse on 2007-11-05
Ok, so I ran it again, and this time everything worked. Not sure why it didn't the first time around, I copied and pasted.  But, now, when I use the gutsy printer setup, I also get the recommended foo driver, plus the three new ones.  However, still no dice.  I guess I'll try the other three new drivers it installed? See what happens.

---

### Post by drs305 on 2007-11-05
> **bconverse said:**
> Ok, so I ran it again, and this time everything worked. Not sure why it didn't the first time around, I copied and pasted.  But, now, when I use the gutsy printer setup, I also get the recommended foo driver, plus the three new ones.  However, still no dice.  I guess I'll try the other three new drivers it installed? See what happens.

I edited my post to say that I had three drivers listed but the recommended one works. Since it didn't for you, I guess it wouldn't hurt to try the others. If they don't work, I'd have to wonder what the result would be if you tried using the 1000 drivers? 

A problem I had with another computer was that the address of the HP usb printer was never correct. It always ended with ....serial  something. On my current setup, the Device URI reads:  usb://HP/LaserJet%201000

Those are about the only inputs I have left so I hope when you come back you had success!

---

### Post by alienexplorers on 2007-11-05
Your printer is listed as OK under Linux.  Are you running the right drivers and hplip.
> Monochrome (B&W) LaserJet Printers
Model Name 	Min. HPLIP Version 	Parallel 	USB 	Network1 	Print Class 	Scan3 	Photo4 	Fax5 	Copy6 	Services/Status7
LaserJet 1010	0.9.5 	No	Yes	No	LJFastRaster 	No	No	No	No 	Yes
LaserJet 1012	0.9.5 	No	Yes	No	LJFastRaster 	No	No	No	No 	Yes
LaserJet 1015	0.9.5 	No	Yes	No	LJMono 	No	No	No	No 	Yes
LaserJet 1018	2.7.10 	No	Yes	No	LJZjsMono 	No	No	No	No 	Yes
LaserJet 1018s	2.7.10 	No	Yes	No	LJZjsMono 	No	No	No	No 	Yes
LaserJet 1020	2.7.10 	No	Yes	No	LJZjsMono 	No	No	No	No 	Yes

---

### Post by bconverse on 2007-11-05
Hmm, I still can't get it to work.  In the Gusty printer setup thing, every time I try and print a test page it adds to to a quene that started when i first installed Gutsy. Even if I uninstall the printer and start from scratch. It just keeps adding the test pages as jobs (its up to like 12 or 13 now) So I don't know.

How can I reset all the defaults and try this from scratch?

---

### Post by bconverse on 2007-11-05
> **alienexplorers said:**
> Your printer is listed as OK under Linux.  Are you running the right drivers and hplip.

I beleive so. The new drivers are all installed, as well as the recommended one. When I run the gusty setup, it shows my printer and the information says " hplip software driving a printer, or the printer function of a multi-function device. " So I am guessing everything is installed? I am new at this so I apologize for ignorance. At this point I want to start over from scratch though I think.  And try this fix again.

---

### Post by drs305 on 2007-11-05
For what it's worth, I got up to 35-40 jobs in the queue before I got mine working. Did you try powering off and on the printer?

By the way, on another printer the problem was that the Device URI was never correct, always ending with ..."serial..." something when it was a usb printer. The correct address on mine is  usb://HP/LaserJet%201000

Alienexplorers, the 1000 isn't on the list but the symptoms bconverse has are exactly the same ones I and many others had. I don't remember if any of the complaints I read were from 1020 owners. I don't have HPLIP installed on my machine any longer.

---

### Post by bconverse on 2007-11-05
hmm i think you may have just discovered the problem.. mine does have the serial thing after it. how can i change that manually?  thanks again for all this help.

---

### Post by bconverse on 2007-11-05
or rather, how to I determine what the correct location is on mine, and then change it?

---

### Post by bconverse on 2007-11-05
ok, I got the test page to print! I managed to figure out how to get the printer to the correct location, so things are dandy, at least for now. Thanks for all the help once again. I think I only have 2 major problems left to tackle at this point.

---

### Post by himuraken on 2007-12-09
You last post indicates that you figured out how to change the address of the printer. What did you do to find and correct the address? I am getting the same exact issue.

---

### Post by drs305 on 2007-12-09
When you go to System, Admin, Printing, Setting tab, what do you see in the Device URI field?  

On my LJ1000 I kept getting a serial address which didn't work and the address had 'serial' somewhere in actual address. I had to manually enter the usb address [ usb://HP/LaserJet%201000  ].  I don't recall how I found the location of the printer but believe it was off an old forum post - which means the address would be pretty standard.   As you can see, my printer's address is not very complicated (the %20 is just to simulate/replace a space). You would change the 1000 to 1020, assuming it's a usb printer. 

If that doesn't work, hopefully someone with a 1020 will post what address they see in the Device URI block and that same address will work for you.

---

### Post by himuraken on 2007-12-09
Here is the address detected by the add new printer wizard: 
**hp:/usb/HP_LaserJet_1020?serial=JL1TMWF**. 

When I plug in my device syslog shows:

[B]Dec  9 14:31:58 navi NetworkManager: <debug> [1197228718.852408] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_2b17_JL1TMWF_usbraw'). 
Dec  9 14:31:58 navi /usr/sbin/hplj1020: foo2zjs: Missing HP LaserJet 1020 firmware file /usr/share/foo2zjs/firmware/sihp1020.dl[/B]. Hopefully this helps. 

I am unsure if this makes a difference but I added a second monitor/reconfigured X this morning and have been unable to print since.

Thanks

---

### Post by drs305 on 2007-12-09
> **himuraken said:**
> Here is the address detected by the add new printer wizard: 
**hp:/usb/HP_LaserJet_1020?serial=JL1TMWF**. 


That's about what I recall I had. I deleted everything after 1020 ( ' ?serial....'  ), recycled the power on my printer and it started working. This might work assuming your's is a usb printer.

Edit: I just read the second part of your post. Did you run the steps listed in post 9? The 1020 is supposed to be supported but it looks like the system is searching for the foo2zjs files. Your post seems to indicate the foo2zjs files haven't been installed.

---

### Post by Orbital75 on 2007-12-15
Gave that a try but still in the same boat

---

### Post by zhkent on 2008-01-07
I got my HP 1020 printer working by following a link from drs305 in this thread.
Here's what worked for me:
Go to the link  [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")
Scroll down and you will see a spot for donations. 
 Down a little further and there is this:
"The INSTALL file contains more detailed instructions; please read it now"
Click on INSTALL and a read me file opens.   Scroll down about half way and there is a very simple guide on installing printer support for the 1020 in  ubuntu, just follow the guide.

---

### Post by sofamensch on 2008-03-09
I tried the Packages from the latest Hardy Repositories, but "by default" with no manual settings it is not working.

No way for automation for this?

---

### Post by sofamensch on 2008-03-19
I LOVE YOU UBUNTU Community !

I just updated the latest Hardy Rep's and without any configuration it starts printing :-)

THX

---

### Post by sofamensch on 2008-03-25
Edit: For Some reason.. it doesnt work by itself again.

---

### Post by goutas on 2008-04-20
New to Ubuntu and had the same problem. Followed the guidelines at: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and the printer works fine. Thank you for the hints.

---

### Post by PhantomNJ on 2008-04-26
Count me as another who was helped by this thread.  Nice to have my printer working in Hardy.

Thanks again!

---

### Post by danpos on 2008-04-26
@All

On **Hardy Heron** isn't more necessary to install the drivers from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) since that the it installs the correct drivers and hp programs. It's only necessary to download the printer's firmware since that Ubuntu can't delivery it cause of license and/or patent restriction. At terminal and as root (or using sudo), just type:

```
# hp-setup (as root)
```

OR

```
$ sudo hp-setup (as sudoer)
```

and follow-up the wizard. It's straightforward. :)

Regards,

Danpos.

---

### Post by roman.lange on 2008-07-03
Thanks Danpos, your solution worked just fine!

---

### Post by ocdude on 2008-07-19
> **danpos said:**
> @All

```
# hp-setup (as root)
```OR

```
$ sudo hp-setup (as sudoer)
```and follow-up the wizard. It's straightforward. :)

Regards,

Danpos.

Thanks! This solved my problem. I thought the printer itself was dead, because I couldn't get it to work with my OS X machine either (long story involving HP discontinuing driver support).

---

### Post by Sprax on 2008-07-24
"hp-setup" did it! Thanks!

---

