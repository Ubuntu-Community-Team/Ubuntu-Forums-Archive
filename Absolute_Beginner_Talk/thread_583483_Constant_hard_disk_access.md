---
title: "Constant hard disk access"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by jcarlton on 2007-10-20
I'm brand new to Linux and Ubuntu, with limited (and ancient) Unix experience.  I've installed Fiesty on a Dell Latitude D400 as the only OS.  I allowed the installer to auto-partition and format the drives.  This system is intended as a non-critical music server, but I installed the desktop version so I could learn the OS from a desktop POV.

It's been up an running for about 36 hours.  About 18 hours in, the system began to hit the hard drive and hasn't stopped.  I'm wondering why.

Checked the documentation and searched the forum, but haven't found an answer that fits.  Or at least that I can make fit my problem :confused:

Running TOP doesn't show any odd processes and I don't see trakerd running at all.  Any ideas?  Do you need a log file or screenshot to help with this?  If so, point me to what you need -- but be gentle, I'm still very new to this!

Thanks in advance for any help.

---

### Post by jcarlton on 2007-10-26
*bump*

Ok, so I know everyone is slammed with 7.10 issues, but does anyone have an answer?  Rather than let the hard drive run unabated, I shut down the system (normally).  I decided to give it another try, and, sure enough, I'm watching the drive light right now and it's almost constant access.  There are no obvious processes (running TOP) that would be causing this...  I see an occassional HALD pop up near the top of the processes list (I'm sorting by CPU %).

If no one has any ideas, I guess I'll be giving up on Ubunutu and moving to a different Debian distro so I'm hoping I can at least get an idea of where to look to find out what's going on.


-=> Jim

---

### Post by drinkpepsi on 2007-10-26
Do you have something called prelink.bin running? If so kill it and see if that fixes it.

I found this in a search, not sure if it applies.

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

In that guide someone stated to add

```
/dev/sda {
apm 254
}

to /etc/hdparm.conf and to add a startup link with

sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

---

### Post by jcarlton on 2007-10-27
> **drinkpepsi said:**
> Do you have something called prelink.bin running? If so kill it and see if that fixes it.

I found this in a search, not sure if it applies.

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

In that guide someone stated to add

```
/dev/sda {
apm 254
}

to /etc/hdparm.conf and to add a startup link with

sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

Thanks, I tried this but with no change.  I'm really baffled, since there are virutally no processes showing when I run TOP.  It has to be a process somewhere, and I'm sure someone far more experienced than I am would know how to find it.

At this point, I'm just going to have to uninstall Ubuntu.  When 7.10 is a bit more stable, I'll try installing that to see if the problem goes away.

Thanks, though,for your help.  I appreciate it.


-=> Jim

---

### Post by Mr_Cynical on 2007-10-29
> **jcarlton said:**
> At this point, I'm just going to have to uninstall Ubuntu.  When 7.10 is a bit more stable, I'll try installing that to see if the problem goes away.

I have 7.10 installed and I have the same problem, so I don't think it'll help you any.

---

### Post by logos34 on 2007-10-29
> **Mr_Cynical said:**
> I have 7.10 installed and I have the same problem, so I don't think it'll help you any.

Fresh install or upgrade?

Because, for me, an upgrade didn't fix it.  Blink blink blink goes the hdd every two secs.  Not a big deal, but it's baffling little things like this that just drive me up the wall...

---

### Post by Inxsible on 2007-10-29
I had a similar problem that my cpu fan kept running constantly in Feisty. not the same, i know, but i think there are some issues with Feisty. My suspend and hibernate never worked in Feisty. Since I did  a fresh install of 64 bit Gutsy, my system is amazingly quiet. Suspend and hibernate work out of the box. 


I was actually afraid, the life span of my cpu would go down because of Feisty. No issues with Gutsy though. 

A lot of improvements seem to have been made in Gutsy with respect to hardware. If you are not averse to it, maybe you should give Gutsy a whirl.

---

### Post by Octagonal on 2007-10-29
Is beagle installed by any chance? perhaps it's indexing if it is...

---

### Post by Inxsible on 2007-10-29
> **Octagonal said:**
> Is beagle installed by any chance? perhaps it's indexing if it is...
No I never installed beagle. Surprising thing is, Gutsy comes with tracker pre-installed. Feisty didn't. Still Gutsy is mush quieter than Feisty.

---

### Post by volksman on 2007-10-29
Might be related:

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

---

### Post by jcarlton on 2007-10-29
Wow... talk about threadjacking :eek:

My problem is not the "every 2-5 seconds my drive spins and makes a sound like the heads are being parked."

This one is one where the hard drive is being accessed virtually non-stop with reads and/or writes.

I'd guess it was related to indexing software, but as far as I know I'm not using any.  No odd processes show up when I run TOP either.  There are generally only 3-4 running apps while it is happening...  slimserver, top, and xorg.  Periodically, I see cupsd, gnome-cups-icon, and hald, but that's it.

Despite the lack of processes that show up in TOP, there's got to be something back there causing the hard disk to get slammed.  I'd just like someone to point me in the direction of how to find it.


-=> Jim

---

### Post by Innernet on 2007-10-29
Hi.
Try  System > Preferences > Indexing preferences > Tracker preferences

> General - disable indexing ; disable watching ...

And come back with results.

---

### Post by Mr_Cynical on 2007-10-30
> **Innernet said:**
> Hi.
Try  System > Preferences > Indexing preferences > Tracker preferences

> General - disable indexing ; disable watching ...

And come back with results.

Hmm I'll try that before I do a complete wipe/reinstall.

> **logos34 said:**
> Fresh install or upgrade?

Because, for me, an upgrade didn't fix it.  Blink blink blink goes the hdd every two secs.  Not a big deal, but it's baffling little things like this that just drive me up the wall...

I'm an upgrade too (done via the Updates Manager if there's more than one way to upgrade). If disabling Tracker doesn't work I have the Gutsy ISO downloading just now :P

**EDIT:** Tried disabling and then uninstalling Tracker, didn't seem to  solve the problem. Could there be any other culprits or should I just do a fresh install of Gutsy? (PS: I opened System Monitor and the only process using any CPU time was System Monitor itself). Could this be a problem with ext3, and if so would choosing ext2 on a clean install solve it? Finally, my system isn't running in laptop mode (I checked) so I don't think it can be the mount/unmount bug that has been in the news lately

---

### Post by Mr_Cynical on 2007-11-01
*bump*

I tried doing a fresh install of Gutsy from the install CD (which I downloaded and burned). I also partitioned the drive into separate root and home partitions so I could do future reinstalls without losing data.

The result of that is that the system now won't boot. It gets past Grub no problem but then a black screen with the system still on and the hard disk access light flickering (as in not even getting to fully 'on' before going off again.) Is this a corrupted install or is the hard disk dead? (I have the smaller, original one somewhere that I could put in if the latter is the case)

---

### Post by Shrav on 2007-11-02
My sons machine is doing the same thing. Boots fine to desktop and then the hard drive starts thrashing non-stop. The system slows to a crawl and is pretty much unusable. If he boots into Windows it runs fine. The problem just appeared out of the blue upon booting one day. I'd love to know what is causing this because I'm the one who convinced him to set up a Ubuntu dual boot in the 1st place!

---

### Post by smurphy_it on 2007-11-02
Do you have laptop mode enabled ????

cat /etc/default/acpi-support and check the 2nd last line.

enable_laptop_mode = false / true

By default it should be false which wouldn't explain your hard drive access, (unless it is doing it anyways) however, if it was set to true then you are ruining your hard drive because of aggressive hard drive access (not a ubuntu bug).

Check out this link to see what I am talking about and the fixes/workarounds.

[https://launchpad.net/bug59695.html]("https://launchpad.net/bug59695.html")

---

### Post by Shrav on 2007-11-06
I fixed it. I turned on his machine and let it run overnight. When I rebooted all was as it should be (no drive thrashing). I have no idea what was happening with the hard drive but it seems fine now. Upgrading that box to Gutsy now and I'll see how that works out!

---

### Post by davidomundo on 2008-01-31
Most likely, the problem was caused by updatedb, an application that indexes all the files of your harddrive so you can locate them quickly using the command 'locate'.

The problem you and others are facing is that updatedb is scheduled to run daily with cron jobs. If you look at /etc/crontab, you'll see that it runs /etc/cron.daily/* every day.

One of the scripts that runs daily is /etc/cron.daily/find which runs updatedb. Ubuntu adds that file by default.

This is not much of a problem if you don't have much files on your harddrive, or you can spare the Disk IO, but if you're fed up with the disk access, or never use locate, you can just ```
sudo rm /etc/cron.daily/find
``` or just comment out everything in that file.

---

### Post by mikael_rev on 2008-02-10
> **Innernet said:**
> Hi.
Try  System > Preferences > Indexing preferences > Tracker preferences

> General - disable indexing ; disable watching ...

And come back with results.

I just installed Ubuntu 7.10 and experienced periodically constant hard disk access. This  reduced my system's performance dramatically, not allowing enough resources to programs (which window became gray and unresponsive).

Disabling indexing and watching seems to have solved my problem.

Thanks!

Mikael

---

### Post by mekoche on 2008-07-24
MythTV was my problem

---

