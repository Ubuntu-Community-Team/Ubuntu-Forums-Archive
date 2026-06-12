---
title: "[SOLVED] cannot remove turboprint package - error"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by scb0206 on 2007-10-29
Hello All.

I'm completely new to Linux, so please forgive newb errors/ignorance.

I was trying to find a driver for my printer (Cannon Pixma iP1500), and I came across TurboPrint.  I installed the package, and it printed fine, but it put this huge logo on everything I printed because it wants me go give it money, so I decided to remove it and find another option.  I cannot remove it.  Here's the code:

```
steven@steven-desktop:~$ sudo apt-get remove turboprint
[sudo] password for steven:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  turboprint
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 22.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93405 files and directories currently installed.)
Removing turboprint ...
/var/lib/dpkg/info/turboprint.prerm: 3: /usr/share/turboprint/lib/uninstall-pre: not found
dpkg: error processing turboprint (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/turboprint.postinst: 3: /usr/share/turboprint/lib/install-post: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 turboprint
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try to remove from Synaptic, I get this error message:

```
E: turboprint: subprocess pre-removal script returned error exit status 127
```

Also, whenever I try to install any other new package I get an error message that mentions turboprint, and has the same "/usr/bin/dpkg returned error code (1)" (sorry I don't have the exact error message).  I know turboprint is causing this problem because it mentions turboprint in the error message.  

In the TurboPrint properties, it shows all installed files; I've tried to go and manually delete some of those, but they're all on system root, and when I try, it says I don't have the permissions to modify the folder.  I've not figured out how to get the permissions yet, but I haven't really looked, either, because I don't think that will fix my problem.

Is there anything I can do to get this off my machine other than reformatting and reinstalling?

Thanks,
Steven

---

### Post by Partyboi2 on 2007-10-30
U could try:
```
 apt-get autoclean
```Or
You could look in  /var/lib/dpkg/info/ for turboprint.prerm if you see it there then delete it (or any other files relating to turboprint)
```
 sudo cp /var/lib/dpkg/info/turboprint.prerm /var/lib/dpkg/info/turboprint.prerm_bkp
```then:
```
 sudo rm /var/lib/dpkg/info/turboprint.prerm
```might work

---

### Post by scb0206 on 2007-10-30
Thanks for the reply.

I was able to delete all turboprint-related files in the directory you gave, including turboprint.perm (and two others in the same directory).  I tried again to remove from the terminal and I got this message:

```
steven@steven-desktop:/$ sudo apt-get remove turboprint
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  turboprint
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 22.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `turboprint' missing, assuming package has no files currently installed.
92830 files and directories currently installed.)
Removing turboprint ...
steven@steven-desktop:/$ 
```

I searched in Synaptic again and it was still there.  I marked for complete removal and applied.  It seemed to work fine.  The removal dialog came up and it gave no error messages.  It can no longer be found in synaptic.  

However, the turboprint setup and config menu items are still listed in administration and preferences, respectively.  When I click on config, I get an error message and it does not work - a good thing.  If I click on setup, however, the turboprint dialog still pops up, but is not fully operational (I cannot add a printer - when I click "add" the window simply closes.

What now?  Can I get the rest of it off my computer and remove the menu items?  I have not tried to install any new packages to see if it will work...

Thanks a lot.

---

### Post by scb0206 on 2007-10-30
Actually, I just had this thought...

I don't know what turboprint.perm exactly is, nor the other two files I deleted.  Could one of the files I deleted have been the list that tells Ubuntu what files were installed with the package so it knows which files to delete?  In my eagerness to get it off my computer, I emptied trash after I deleted them (not wise, in retrospect).  Otherwise I would restored the other two files and tried again.  

What if I try to install the package again, then try to uninstall it again - maybe it will work?:confused:  I would go ahead and do it, but I figure you know more about this stuff than me, so I'll wait to see what you think.  

Thanks again

---

### Post by Partyboi2 on 2007-10-30
Try:
```
sudo apt-get --purge remove turboprint
sudo apt-get update
```You could also try installing deborphan, which is a program that finds orphan packages. 

```
sudo apt-get install deborphan
``````
sudo deborphan
```Then if it shows any dependencies left:
```
sudo apt-get --purge remove ***dependencies***
```* dependencies being what ever there might be listed, if any.
And with the '--find-config' option, you could see if there's any configuration files left

```
sudo deborphan --find-config
```If any config files are found for turboprint, remove the config file with dpgk and the purge option:
```
sudo dpkg --purge ***file name***
```* File name being the name of the file(s)
Hope this helps

---

### Post by scb0206 on 2007-10-31
Installed deborphan. No problems on install.  Here's what happened when I ran it like you said.  

```
steven@steven-desktop:~$ sudo deborphan
libdb4.3
steven@steven-desktop:~$ sudo apt-get --purge remove libdb4.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdb4.3*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 995kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92992 files and directories currently installed.)
Removing libdb4.3 ...
steven@steven-desktop:~$ sudo deborphan --find-config
steven@steven-desktop:~$ sudo deborphan --find-config
steven@steven-desktop:~$ 

```

Didn't seem to do anything.  I'm assuming that since it didn't return anything on the find config that it didn't find anything.

Any other suggestions?  

Thank you for helping me.

---

### Post by Partyboi2 on 2007-10-31
Can you delete the turboprint setup and config files manually? In other words go to the directory that they are in and remove them?

```
cd ***directory***
```*directory being where the files are.
```
sudo rm -r ***folder name***
 
``` to remove a folder
or if it just a file
```
 sudo rm ***file***

```*name of file

---

### Post by scb0206 on 2007-10-31
I had already thought about that, but I cannot find any of the files.  I opened up the program's .tgz file that I downloaded from the website and there is an "uninstall" file there.  I opened it up - this is it:

```
#!/bin/bash
#
# Turboprint deinstallation script
#
# must have root permissions
#

# get dirs

if [ ! -e /etc/turboprint/system.cfg ] ; then
	echo "Configuration file "etc/turboprint/system.cfg" not found!"
	exit 1
fi

eval $(cat /etc/turboprint/system.cfg)

echo
echo "Turboprint deinstallation"
echo "========================="
echo "Will delete the following directories:"
echo "$TPPATH_CONFIG"
echo "$TPPATH_SHARE"
echo
echo "And the following files:"
echo "$TPPATH_BIN/tpprint"
echo "$TPPATH_BIN/tpsetup"
echo "$TPPATH_BIN/xtpsetup"
echo "$TPPATH_BIN/tpconfig"
echo "$TPPATH_BIN/xtpconfig"
echo "$TPPATH_BIN/turboprint"
echo "$TPPATH_MAN/man1/tpprint.1"
echo "$TPPATH_MAN/man1/tpsetup.1"
echo "$TPPATH_MAN/man1/tpconfig.1"
echo "$TPPATH_MAN/man7/tpfilter.7"
echo "$TPPATH_MAN/man7/turboprint.7"
echo "$TPPATH_LOG/turboprint.log"
echo "$TPPATH_LOG/turboprint_lpr.log"
echo "$TPPATH_LOG/turboprint_cups.log"
if [ -e "$TPPATH_CUPSDRIVER/turboprint" ] ; then
	echo "$TPPATH_CUPSDRIVER/turboprint"
fi
echo
echo -n "Start deinstallation now? "
read ANSWER

if [ -z $ANSWER ] ; then
	exit 0
fi
if [ $ANSWER != "y" ] ; then
	exit 0
fi

# call script to remove dynamic data (also called by rpm %preun)

lib/uninstall-pre

# call script to remove static files

lib/uninstall-static --tgz

echo "Deinstallation complete"

exit 0
```

Now, while I don't know how to read all that (I have only one semester's worth of programming in Java), I do see that it lists files and directories that will be removed if uninstalled.  I tried searching for "tpprint" in Nautilus, and it didn't work.  I started the search this morning, but had to hurry and leave for class.  I just got back and nautilus was still searching.  I just used the search button that's built into nautilus and typed in "tpprint" and hit enter.  Apparently it searched for 6 hours and still was not done - I don't know why it would do that.  Could I be searching wrong somehow?

Thanks

---

### Post by Partyboi2 on 2007-10-31
> **scb0206 said:**
> I had already thought about that, but I cannot find any of the files.  I opened up the program's .tgz file that I downloaded from the website and there is an "uninstall" file there.  I opened it up - this is it:

```
#!/bin/bash
#
# Turboprint deinstallation script
#
# must have root permissions
#

# get dirs

if [ ! -e /etc/turboprint/system.cfg ] ; then
    echo "Configuration file "etc/turboprint/system.cfg" not found!"
    exit 1
fi

eval $(cat /etc/turboprint/system.cfg)

echo
echo "Turboprint deinstallation"
echo "========================="
echo "Will delete the following directories:"
echo "$TPPATH_CONFIG"
echo "$TPPATH_SHARE"
echo
echo "And the following files:"
echo "$TPPATH_BIN/tpprint"
echo "$TPPATH_BIN/tpsetup"
echo "$TPPATH_BIN/xtpsetup"
echo "$TPPATH_BIN/tpconfig"
echo "$TPPATH_BIN/xtpconfig"
echo "$TPPATH_BIN/turboprint"
echo "$TPPATH_MAN/man1/tpprint.1"
echo "$TPPATH_MAN/man1/tpsetup.1"
echo "$TPPATH_MAN/man1/tpconfig.1"
echo "$TPPATH_MAN/man7/tpfilter.7"
echo "$TPPATH_MAN/man7/turboprint.7"
echo "$TPPATH_LOG/turboprint.log"
echo "$TPPATH_LOG/turboprint_lpr.log"
echo "$TPPATH_LOG/turboprint_cups.log"
if [ -e "$TPPATH_CUPSDRIVER/turboprint" ] ; then
    echo "$TPPATH_CUPSDRIVER/turboprint"
fi
echo
echo -n "Start deinstallation now? "
read ANSWER

if [ -z $ANSWER ] ; then
    exit 0
fi
if [ $ANSWER != "y" ] ; then
    exit 0
fi

# call script to remove dynamic data (also called by rpm %preun)

lib/uninstall-pre

# call script to remove static files

lib/uninstall-static --tgz

echo "Deinstallation complete"

exit 0
```Now, while I don't know how to read all that (I have only one semester's worth of programming in Java), I do see that it lists files and directories that will be removed if uninstalled.  I tried searching for "tpprint" in Nautilus, and it didn't work.  I started the search this morning, but had to hurry and leave for class.  I just got back and nautilus was still searching.  I just used the search button that's built into nautilus and typed in "tpprint" and hit enter.  Apparently it searched for 6 hours and still was not done - I don't know why it would do that.  Could I be searching wrong somehow?

Thanks
I am running out of ideas here lol Just wondering did you type tpprint or tppath? 
Also which one did you download? .deb one or the .tgz?
To uninstall a .deb
```
 sudo apt-get uninstall turboprint
```to uninstall .tgz  u  use the uninstall script in its directory
```
 cd turboprint-1.96-3 
sudo ./uninstall 
```

---

### Post by scb0206 on 2007-10-31
I downloaded both of them because I didn't know what I was doing at the time, and I didn't know which one I was supposed to have.  When I opened them only the .deb file actually installed it, so I went with it.  After that, I deleted the .deb file, but the .tgz file was still on my desktop because I didn't know if I was still supposed to do anything with it (I'm still learning).  I just happened to look around in the .tgz file and found that uninstall file.

I searched for tpprint.  I'll try tppath now.

---

### Post by scb0206 on 2007-10-31
tppath is coming up with nothing as well.

I'll probably just end up reformatting my drive and re-installing.  I completely expected to do this  several times, because I have no clue what I'm doing with Ubuntu, and I knew I would mess something up while learning.  This is a machine that I just built and I don't have anything else on it, so it's not a big deal.  I have a laptop that all my schoolwork is on.  I'll keep learning and fooling with things on this install of ubuntu, and when I think I know enough (or I've messed it up beyond repair), I'll reformat and reinstall.  It's going to have to happen eventually because I need to repartition to make some room for windows when I get it (I'm planning on a dual-boot).  I'm reading the official ubuntu book and i'm reading online about several things, including mythtv (my main purpose of this computer is a pvr for my room), and i'll eventually learn my way around it.

in fact, if you know of any good resources other than the book and this forum, please share!!!  for a little more info about my background, I'm completely new to linux, but have a strong working knowledge of windows, java programming, and hardware (obviously, since i built my own desktop).  Any good resource for someone with my background would be awesome!

thank you very much for helping me!!! :D

---

### Post by Partyboi2 on 2007-10-31
You could trying to reinstall turboprint .deb and then try and uninstall again, don't have a clue if that would work. But then again whats the worse could happen a reinstall? 
Here are some links that might be of interest:
[http://www.intelligentedu.com/blogs/post/best_new_training_sites/3530/ubuntu-linux-video-tutorials](http://www.intelligentedu.com/blogs/post/best_new_training_sites/3530/ubuntu-linux-video-tutorials)
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

:)

---

### Post by scb0206 on 2007-10-31
Thank you very much!!!!!!
):P

---

### Post by scb0206 on 2007-11-01
Just to keep you informed, I reinstalled and uninstalled and it seems to have worked fine!!!  If only we had tried that first!  Only problem is that the menu items are still there, but they are completely nonfunctional.  I'll have to teach myself to remove them.

Thanks again for all the help!

---

### Post by Partyboi2 on 2007-11-01
sometimes the answers just stare us in the face :lolflag:
Atleast we learnt something.

---

