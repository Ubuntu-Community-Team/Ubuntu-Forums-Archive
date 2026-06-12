---
title: "Cannot free up disk space - 40GB too small?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Brian9000 on 2007-07-13
**[COLOR=red]EDIT: Solved! Thanks trak87![/COLOR]**
 
 
Hi everyone. I'm on my first attempt at using linux/unbuntu. I took a spare Dell box I had (GX280) with a 40g HD and installed directly off a kubuntu live cd. It is the only install on the box, no dual boot. So far I've only been using it to surf via firefox and sometimes listen to streaming music via amarok. I do not get email, create documents, or download torrents, etc. on this box. 
 
Yesterday it prompted for updates which I installed and rebooted. I could not login. After typing my password it would dump me back to the login page. I searched these forums and found that it may be a disk space issue since I could log in via the CLI. I knew I had copied some large (300MB) movie files on my desktop so I browsed to those files and deleted them. After rebooting I was able to login. 
 
I then went into adept and removed other items such as open office etc. that I was not using. 
 
Another search of these forums on "disk space" prompted me to do a "dh -H" which showed:
/dev/sda1 (size)36G (Used)34g (Avail)0 (use)100%
varrun (size)248M (Used)96k (Avail)248m (use)1%
varlock (size)248M (Used)0 (Avail)248m (use)0%
procbusb (size)248M (Used)100k (Avail)248m (use)1%
udev (size)248M (Used)100k (Avail)248m (use)1%
devshm (size)248M (Used)0 (Avail)248m (use)0%
lrm (size)248M (Used)33m (Avail)215m (use)14%
 
I then did a sudo apt-get autoclean. Now df -h says:
/dev/sda1 (size)36G (Used)34g (Avail)88M (use)100%
...
 
I then found this thread: [http://ubuntuforums.org/showthread.php?t=184435](http://ubuntuforums.org/showthread.php?t=184435)
which suggested:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
 
as well as 
$find ~/.thumbnails -type f -atime +7 -exec rm {} \;
 
Now df -h says:
/dev/sda1 (size)36G (Used)34g (Avail)2.3M (use)100%
...
 
Questions: is it normal for a clean kubuntu install to need larger than a 40gb drive to operate?
If not, is it possible to see what's taking up so much space? 
Is there a process that can start growing a file out of control?
I'm concerned at this point as it seems that something is taking up space as quickly as I can free it. If I reboot, I might not be able to get back in and don't have anything more I can remove.
Thanks for your help!

---

### Post by Happy_Man on 2007-07-13
Hmmm.... I've got Kubuntu, Ubuntu, Fluxbox, and Openbox all on the same 10GB partition, and they barely crack 3 GB. So Kubuntu's gotta be smaller than that. Perhaps clearing the /tmp folder will help a bit... I can't think of anything else that could clog up an HDD. Although, at this point, I suggest getting an external HDD to put your files on, so that you don't have this problem every other day. 4GB is too restrictive for any OS other than a server.

---

### Post by Brian9000 on 2007-07-13
Thanks for the info.  I'm totally new to this.   Is there a simple command for clearing the tmp file, or do I just browse to it and move everything to the trash?

If I have to have an external drive just to use this... back to XP for me ;)  Especially since I'm not saving any files.  Just surfing.  Oh, also it's a 40GB drive not 4.  

Thanks!

---

### Post by Papi-KB7VGW on 2007-07-13
Wow!  I have a 40 G on this notebook with windows 12G, /boot 100M, swap 1.5G, / 10G and /home 13G.  None of them is over 40% used.  I have noticed that swap is never used.  I have heard that Kubuntu/KDE is fat but 40G worth is amazing.  Open the System Monitor and look at the resources tab.  Maybe that will give you an idea where it all is.  :(

---

### Post by avik on 2007-07-13
Run baobab in the terminal, then scan the filesystem.  Wait and see what's taking up so much space.

---

### Post by Rocket2DMn on 2007-07-13
navigate to the /tmp directory in terminal and run
```
rm -r *
```
in order to empty your temp files.

---

### Post by Happy_Man on 2007-07-13
> **Papi-KB7VGW said:**
> Wow!  I have a 40 G on this notebook with windows 12G, /boot 100M, swap 1.5G, / 10G and /home 13G.  None of them is over 40% used.  I have noticed that swap is never used.  I have heard that Kubuntu/KDE is fat but 40G worth is amazing.  Open the System Monitor and look at the resources tab.  Maybe that will give you an idea where it all is.  :(
EDIT: Don't listen to me, I'm stupid. My tips, though, should still apply.

---

### Post by Brian9000 on 2007-07-13
Thank you Rocket.  That freed up another .1M of space :)

I now have 2.4M of space free!

Thank you Avik.  When I ran that it said: baobab is not installed you can install it by typing "sudo apt-get install gnome-utils."

I tried that, but I'll bet you can guess the rest: "Need to get 4202kb of archives.  After unpacking 18.5MB of disk space will be used....

eh..... help?

---

### Post by Happy_Man on 2007-07-13
Wow. At this point, I'm not sure running commands like 'sudo apt-get autoclean' or 'sudo apt-get autoremove' will help. You can try them, but the way this is going, they may not help too much. My earlier suggestion stands: get another HDD to put your data in.

---

### Post by Brian9000 on 2007-07-13
> **Papi-KB7VGW said:**
> Wow!  I have a 40 G on this notebook with windows 12G, /boot 100M, swap 1.5G, / 10G and /home 13G.  None of them is over 40% used.  I have noticed that swap is never used.  I have heard that Kubuntu/KDE is fat but 40G worth is amazing.  Open the System Monitor and look at the resources tab.  Maybe that will give you an idea where it all is.  :(

It could be that I'm using KDE, but I don't see an icon for "system monitor" just "system settings".  Is there a command I can run to launch the monitor?

thanks!

---

### Post by Happy_Man on 2007-07-13
> **Brian9000 said:**
> It could be that I'm using KDE, but I don't see an icon for "system monitor" just "system settings".  Is there a command I can run to launch the monitor?

thanks!
In KDE, it's under System --> KSysGuard.

---

### Post by Papi-KB7VGW on 2007-07-13
In Gnome it is under >System>Administration although it may be called something else in KDE.

Edit:  too late again!

---

### Post by trak87 on 2007-07-13
Try this at the command line:

```
sudo du -c --max-depth=1 | sort -n
```

Whatever directory is taking up the most space will appear at the bottom of the resulting list. Then cd (change directory) into that (largest) directory and run the above command again. Keep doing that until you drill down to what's taking up the most space. Periodically do a 'ls -lSr' to see what files are in there and you'll find what's taking up the space.

---

### Post by Papi-KB7VGW on 2007-07-13
@trak87  Way cool.  That is definitely a command for me to save.  I take it that the number to the left represents sizein Bytes?

---

### Post by Brian9000 on 2007-07-13
> **trak87 said:**
> Try this at the command line:

```
sudo du -c --max-depth=1 | sort -n
```

Whatever directory is taking up the most space will appear at the bottom of the resulting list. Then cd (change directory) into that (largest) directory and run the above command again. Keep doing that until you drill down to what's taking up the most space. Periodically do a 'ls -l' to see what files are in there and you'll find what's taking up the space.

Perfect!!!
This is exactly what I needed.  (this has been pretty frustrating 'cause this would take me seconds to figure out in a win enviroment)

so it lead me down the trail to:

./.mozilla
./firefox
./yugm0u3e.default
./browserstate-logs

where there are two >16GB files with names such as log-20070710-094116-304.txt

....any firefox experts in the house? :)

Seriously, thanks trak87!

---

### Post by trak87 on 2007-07-13
> **Papi-KB7VGW said:**
> @trak87  Way cool.  That is definitely a command for me to save.  I take it that the number to the left represents sizein Bytes?

Right. Size in bytes.

---

### Post by Brian9000 on 2007-07-13
So after googling "browserstate-logs" I found a bunch of stuff concerning unbuntu and google's browsersync plugin in firefox (which I've now disabled).  After deleting those two log files I'm using 11% of sda1.  

Thanks everyone for your quick and acurate advise!

---

### Post by avik on 2007-07-14
> **Brian9000 said:**
> 
Thank you Avik.  When I ran that it said: baobab is not installed you can install it by typing "sudo apt-get install gnome-utils."

Really sorry.  I forgot you were using KDE. :oops:

---

### Post by YandaPanda on 2007-07-27
> **trak87 said:**
> Try this at the command line:

```
sudo du -c --max-depth=1 | sort -n
```

Whatever directory is taking up the most space will appear at the bottom of the resulting list. Then cd (change directory) into that (largest) directory and run the above command again. Keep doing that until you drill down to what's taking up the most space. Periodically do a 'ls -lSr' to see what files are in there and you'll find what's taking up the space.

Thanks for the suggestion! Worked wonderfully. 

As a hint to anyone who is doing any CD/DVD burning and coming across this issue - keep an eye on /var/archive! The above helped us to trace into the right directory and found 35G of data just hanging around doing nothing! Turns out they were the temp files from the prior days of DVD burning - but none of the programs I used gave any indication of this directory as a 'temporary' location.

---

