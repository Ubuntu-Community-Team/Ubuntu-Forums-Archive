---
title: "Nvidia Paradox"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-04-01
Im getting a little confused trying to install my Nvidia drivers..

I already tried using Envy, but it apparently isnt compatible with Feisty, as it crashed my X window and I had to reconfigure xorg.conf to get it back.

Ok, so here we go...

I type the command:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

and it starts to work, but comes up saying that I need to close the X window. So, I reboot into recovery mode for the command prompt and no X window. I try the command again:

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

and it tells me I need to be in runlevel 3 or it wont install right. So, then I type:

sudo telinit 3

and the dang X window loads! Obviously if I try to run it then, its going to say it detects the x window and wont go any further. So my question is, is there any way for me to get to runlevel 3 and have the X window down?? Im really wanting to get my OpenGL up and going so I can run some games... Any advice would be appreciated...

---

### Post by pppetter on 2007-04-01
you could start with installing the drivers in repositories instead, which is really straightforward and easy.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by astoltz on 2007-04-01
Just boot normally, then switch to a virtual terminal via "ctrl-alt-F1".  Once there, stop X by ```
sudo /etc/init.d/gdm stop
```Then you should be good to go with that NVIDIA shell command.

One thing, when you stop X it may leave you at tty7 (that's the terminal that X runs on top of) with nothing but a cursor.  Just switch back to tty1.  

PS, I don't think run level 3 has importance (you'll be at run level 2 if you do the above).  The installer just can't be in single user mode - run level 1 - which is why it was complaining.

---

### Post by infoseeker on 2007-04-01
Got mine running this way (substitute your kernel if not 386):
```
sudo apt-get install linux-386
```
```
sudo apt-get install nvidia-glx
```
backup your old xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo nvidia-xconfig --no-composite
```
and reboot (or shutdown/restart X ie. logout and CTRL+ALT+BACKSPACE)
Worked for me with nvidia 6600GT

Test it by:```
glxinfo |less
```

Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu:
> kdesu kate /usr/share/applications/NVIDIA-Settings.desktop (for KDE)
gksu gedit /usr/share/applications/NVIDIA-Settings.desktop (for Gnome)

Insert the following lines into the new file:

[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;


All this useful info was found here---->
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
(I'm using Feisty Beta but did the trick for me)

---

### Post by pppetter on 2007-04-01
infoseeker --> you didn't notice my answer? My link is to a very good guide in howto install the binary nvidia drivers. with troubleshooting and everything. It's always good to just check the wiki for guides and post them as answer, becouse chances are that you'll miss something when you make a little "quick guide". But that's just my opinion ;)

---

### Post by infoseeker on 2007-04-01
> infoseeker --> you didn't notice my answer?

Sorry, took some time to type my reply.

---

### Post by GSF1200S on 2007-04-02
Cool... I tried the howto and I THINK it might have worked. It was weird though, after I reloaded X I noticed that the letters where I type my login were larger than the box you type in..

Aside obviously from installing a 3d Open GL game, how do I tell if its working?

glxinfo |less

displays a huge list, which is promising, and I saw the NVIDIA icon not long after reloading X, so I guess it might be working...

**EDIT** I just tried the command "glxgears" and I got some gears working, as well as a framerate return.. It must be working, right? Let me know if im wrong..

---

### Post by GSF1200S on 2007-04-02
> **GSF1200S said:**
> Cool... I tried the howto and I THINK it might have worked. It was weird though, after I reloaded X I noticed that the letters where I type my login were larger than the box you type in..

Aside obviously from installing a 3d Open GL game, how do I tell if its working?

glxinfo |less

displays a huge list, which is promising, and I saw the NVIDIA icon not long after reloading X, so I guess it might be working...

**EDIT** I just tried the command "glxgears" and I got some gears working, as well as a framerate return.. It must be working, right? Let me know if im wrong..

Dangit! It WAS working, and then I reboot.. bam.. xwindow fails to load. Now Im back on NV drivers, and none of the open GL stuff works. Any ideas why it would start to work and upon reboot fail?? This is such a pain.. Ive been trying to get this to work for almost a week, and it still wont work..

**Edit** If I reinstall the restricted modules, reinstall kernel common, etc, and Ctrl+Alt+backspace, 3d open gl works. I can run GLX gears, I can even play torcs.. As soon as I reboot, the Xwindow crashes and I have to revert back to NV drivers to load the Xwindow. Heres the exact error:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9755. Please make sure that the kernel module and all NVIDIA driver components have the same version.

So what ups? I installed everything from the package manager, it actually WORKS when I ctrl alt backspace to reload X, but as soon as I reboot, I get this error after the X window fails to load.

---

### Post by GSF1200S on 2007-04-02
bump

---

### Post by go2dell on 2007-04-02
If you have a version mismatch, perhaps you tried to install both the nVidia driver from the repositories *and* the one you downloaded.

It's probably going to be helpful if you uninstall all versions just to clean things out.  Log out so you're at the GDM login screen, then go to a terminal (Ctrl-Alt-F1) and login.  Now stop GDM as you did before (sudo /etc/init.d/gdm stop).

Now that you've got X stopped, remove the various nVidia drivers.
```

sudo apt-get autoremove nvidia-glx

```
and you can also
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run --uninstall

```

This should remove all traces of the existing drivers,  if possible.  If you installed a different kernel, this is also part of your problem.  The nVidia driver you downloaded can use whatever Ubuntu kernel you have installed.  Only the one in the repositories is limited to a specific kernel version.  Remove extra kernels -- if your system starts in a different kernel, you'll get another mismatch, or even a completely missing nVidia driver.

At this point it's probably a good idea to reboot just so you can be certain you're running under the kernel you'll be using, and not on some kernel you installed previously.  If not, you'll be compiling the nVidia kernel in a spot you may never use again.

You can start the system in Maintenance mode just so you don't have to watch nasty messages about how X just failed.  The nVidia driver install will let you proceed just fine.

Now just do
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo nvidia-xconfig (add --no-composite if you need it)

```

You'll need to
```

sudo depmod
sudo modprobe nvidia

```
(or you could just reboot instead).

If you didn't reboot, try typing "exit."  Running system, hopefully.


If there's a problem, it might be your config file.  Instead of trying to edit by hand, you can let the system reconfigure -- assuming you know the specs on your monitor, etc.
```

sudo dpkg-reconfigure xserver-xorg
answer a bunch of questions, some of which may already be correct
sudo nvidia-xconfig (to get the nvidia config back)

```

Good luck!

---

### Post by GSF1200S on 2007-04-03
> **go2dell said:**
> If you have a version mismatch, perhaps you tried to install both the nVidia driver from the repositories *and* the one you downloaded.

It's probably going to be helpful if you uninstall all versions just to clean things out.  Log out so you're at the GDM login screen, then go to a terminal (Ctrl-Alt-F1) and login.  Now stop GDM as you did before (sudo /etc/init.d/gdm stop).

Now that you've got X stopped, remove the various nVidia drivers.
```

sudo apt-get autoremove nvidia-glx

```
and you can also
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run --uninstall

```

This should remove all traces of the existing drivers,  if possible.  If you installed a different kernel, this is also part of your problem.  The nVidia driver you downloaded can use whatever Ubuntu kernel you have installed.  Only the one in the repositories is limited to a specific kernel version.  Remove extra kernels -- if your system starts in a different kernel, you'll get another mismatch, or even a completely missing nVidia driver.

At this point it's probably a good idea to reboot just so you can be certain you're running under the kernel you'll be using, and not on some kernel you installed previously.  If not, you'll be compiling the nVidia kernel in a spot you may never use again.

You can start the system in Maintenance mode just so you don't have to watch nasty messages about how X just failed.  The nVidia driver install will let you proceed just fine.

Now just do
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo nvidia-xconfig (add --no-composite if you need it)

```

You'll need to
```

sudo depmod
sudo modprobe nvidia

```
(or you could just reboot instead).

If you didn't reboot, try typing "exit."  Running system, hopefully.


If there's a problem, it might be your config file.  Instead of trying to edit by hand, you can let the system reconfigure -- assuming you know the specs on your monitor, etc.
```

sudo dpkg-reconfigure xserver-xorg
answer a bunch of questions, some of which may already be correct
sudo nvidia-xconfig (to get the nvidia config back)

```

Good luck!

Awesome.. Now, not only does my Xwindow fail to start (and I followed these instructions to the letter), but my wireless card stopped working as well. I had to reboot just to get my hard line to work. And of course, Im back on NV drivers. Im not disgruntled with anyone, but I am frustrated at the puzzle called Linux..

What have I accomplished in 2 weeks? Ntfs3g. Yup thats it. Now, I have to figure out why messing with my VIDEO CARD CAUSED MY WIRELESS TO FAIL, and how to fix that. Then, im still left with the Video card issue, and I wont even begin to talk about the little **** that doesnt work.

Ive been really patient so far, but now its getting personal. Its like no matter what I try with Linux, it just doesnt work. Some serious strides need to be made with Linux, because contrary to this communities wishful thinking, people dont have 8 hours every day to "mess with Linux, and try to get it working." Hey, im not giving up, but dang, this is BS!

Any ideas on the wireless card? Oh, and after doing this suggestion, I had the same API error message saying that I had different versions (9755, 7184). So, any more ideas on the video card?

---

### Post by dr_dirk on 2007-04-03
I had a whole lot of trouble installing nVidia drivers.  Finally I got it to work and I made a document for my own future reference that I'll post for you.  I don't know what to say about your wireless but I hope this helps get your drivers working.  This is a copy of what I posted here in the ubuntu forums, so there will be a little repeat.

Re: nvidia-settings 

I finally worked through the problem and I'll write out what I did.

Eventually I stirred things up enough that I had to re-install, which is where I took off from. From a fresh install I followed the instructions of Artificialintelligence on another thread.

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```

From there I installed nvidia-kernel-common (from fitzy_oz in another thread) with

```
sudo apt-get install nvidia-kernel-common
```

Then I installed all available updates from the update manager and exited to the command prompt with: 

```
sudo /etc/init.d/gdm stop
```
*I don't recall when exactly I was asked to reboot, but do so as needed*

Press alt+F1 to escape the black screen, then log back in. I ran the driver installation with

```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
chose for it to automatically reconfigure xorg.conf, and crossed my fingers. *note* the install had to compile a kernel for me because the proper one was not available for download.

After the installation you return to the command prompt and restart the GUI with

```
sudo /etc/init.d/gdm start
```
Once logged back in, you should be able to go to Applications>System Tools>NVIDIA X Server Settings and have plenty of options.

---

### Post by GSF1200S on 2007-04-03
> **dr_dirk said:**
> I had a whole lot of trouble installing nVidia drivers.  Finally I got it to work and I made a document for my own future reference that I'll post for you.  I don't know what to say about your wireless but I hope this helps get your drivers working.  This is a copy of what I posted here in the ubuntu forums, so there will be a little repeat.

Re: nvidia-settings 

I finally worked through the problem and I'll write out what I did.

Eventually I stirred things up enough that I had to re-install, which is where I took off from. From a fresh install I followed the instructions of Artificialintelligence on another thread.

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```

From there I installed nvidia-kernel-common (from fitzy_oz in another thread) with

```
sudo apt-get install nvidia-kernel-common
```

Then I installed all available updates from the update manager and exited to the command prompt with: 

```
sudo /etc/init.d/gdm stop
```
*I don't recall when exactly I was asked to reboot, but do so as needed*

Press alt+F1 to escape the black screen, then log back in. I ran the driver installation with

```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
chose for it to automatically reconfigure xorg.conf, and crossed my fingers. *note* the install had to compile a kernel for me because the proper one was not available for download.

After the installation you return to the command prompt and restart the GUI with

```
sudo /etc/init.d/gdm start
```
Once logged back in, you should be able to go to Applications>System Tools>NVIDIA X Server Settings and have plenty of options.

Thanks for the try.. I actually thought it might work, because the installer didnt prompt me about the x window or what runlevel I was in. But, as soon as I attempted to run X, X window failed to load and I had to revert back to NV drivers. The BS part is that Ive actually had OpenGL working, but whenever I reboot I get the damn API mismatch...

---

### Post by dr_dirk on 2007-04-03
Sorry it didn't do the trick.  Each time I've tried to install these drivers it has been a royal PIA.  This seems like a silly question but instead of ```
/etc/init.d/gdm start
``` after the installation did you try just rebooting?  I have my doubts that it should make a difference, but I suppose it might.

As you would have read I followed those steps from a fresh install.  If I recall correctly I had trouble restarting X after the driver installation before I wiped the partition clean and re-installed Ubuntu.

If that doesn't do it then I'm out of ideas.  Unfortunately it seems like everyone's driver installation experience is different so some of the help can be limited.  Oh, if you haven't tried yet, look into Envy and/or Automatix.  I haven't heard anything negative about Envy, but I couldn't get the program itself to work for me (I think because of a lack of know-how on my part).   I got Automatix after I got my drivers working so I don't know how well it works.  Be advised though, there seems to be concern about how Automatix installs things.  If I'm not mistaken I just read earlier today that Ubuntu's official take on Automatix is unfavorable.  I think that is in part due to some upgrading complications that Automatix can cause.  I really don't know much about it and haven't really used Automatix so you would probably want to do a little research on the program itself before using it.

Ok, *now* I'm out of ideas.  Hope you get the problem resolved without too much more headache.

Derek

---

### Post by go2dell on 2007-04-03
The wireless driver problem is likely because I didn't think about "autoremove" also killing your restricted drivers, which may be needed for your wireless card.  I didn't notice in reading the previous posts that you had a wireless card, or what kind of card you have.  WOOPS!  Really sorry about that! :oops: 

For right now, you can get X working again with the "nv" driver.  Just do the "dpkg-reconfigure" step alone (it doesn't know anything about the "nvidia" driver).  That will get X up and running beautifully, although you won't have 3D.

I was also looking at your original post, and you don't mention which card you have.  In case you don't know, nVidia now has ***two***, count 'em, two legacy drivers, although they don't really call them both "legacy."  If your card isn't supported, you should get a message about that when you try to compile.  However, since you're new to Ubuntu, I would suggest that you just use the Ubuntu-packaged nvidia-glx if you can.

At this point it's sounding like you've done a lot of things to this system.  Are you early in the system's life?  If so, would you be willing to wipe the system clean and reinstall?  That may be easier for you.

I feel fairly certain that the version mismatch problem is because you have more than one kernel installed, and you did part of the installation under one kernel and other parts under another kernel, probably after rebooting.

The problem is not Linux;  it's conflicting advice.  There's a great wiki page on exactly how to get the nVidia drivers working:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

Whatever you do, pick a method and stick with it.  If you use Automatix, stick with that.  If you do things from the wiki page, stick with that.  Switching methods is a sure way to hose your system beyond repair.

---

### Post by GSF1200S on 2007-04-04
> **dr_dirk said:**
> Sorry it didn't do the trick.  Each time I've tried to install these drivers it has been a royal PIA.  This seems like a silly question but instead of ```
/etc/init.d/gdm start
``` after the installation did you try just rebooting?  I have my doubts that it should make a difference, but I suppose it might.

As you would have read I followed those steps from a fresh install.  If I recall correctly I had trouble restarting X after the driver installation before I wiped the partition clean and re-installed Ubuntu.

If that doesn't do it then I'm out of ideas.  Unfortunately it seems like everyone's driver installation experience is different so some of the help can be limited.  Oh, if you haven't tried yet, look into Envy and/or Automatix.  I haven't heard anything negative about Envy, but I couldn't get the program itself to work for me (I think because of a lack of know-how on my part).   I got Automatix after I got my drivers working so I don't know how well it works.  Be advised though, there seems to be concern about how Automatix installs things.  If I'm not mistaken I just read earlier today that Ubuntu's official take on Automatix is unfavorable.  I think that is in part due to some upgrading complications that Automatix can cause.  I really don't know much about it and haven't really used Automatix so you would probably want to do a little research on the program itself before using it.

Ok, *now* I'm out of ideas.  Hope you get the problem resolved without too much more headache.

Derek

I might try your method again, as I didnt have any restricted drivers installed. Like I said, the installer didnt complain about my run level or anything, it just failed to load the Xwindow. I am new to Ubuntu, so maybe I messed up somewhere. I also hear what the person said who posted after you- I would be better off not switching methods all the time. Im going to stay away from Automatix.. I need to learn the Linux way of doing things... Thanks for the help though- I really do appreciate it.

---

### Post by GSF1200S on 2007-04-04
> **go2dell said:**
> The wireless driver problem is likely because I didn't think about "autoremove" also killing your restricted drivers, which may be needed for your wireless card.  I didn't notice in reading the previous posts that you had a wireless card, or what kind of card you have.  WOOPS!  Really sorry about that! :oops: 

For right now, you can get X working again with the "nv" driver.  Just do the "dpkg-reconfigure" step alone (it doesn't know anything about the "nvidia" driver).  That will get X up and running beautifully, although you won't have 3D.

I was also looking at your original post, and you don't mention which card you have.  In case you don't know, nVidia now has ***two***, count 'em, two legacy drivers, although they don't really call them both "legacy."  If your card isn't supported, you should get a message about that when you try to compile.  However, since you're new to Ubuntu, I would suggest that you just use the Ubuntu-packaged nvidia-glx if you can.

At this point it's sounding like you've done a lot of things to this system.  Are you early in the system's life?  If so, would you be willing to wipe the system clean and reinstall?  That may be easier for you.

I feel fairly certain that the version mismatch problem is because you have more than one kernel installed, and you did part of the installation under one kernel and other parts under another kernel, probably after rebooting.

The problem is not Linux;  it's conflicting advice.  There's a great wiki page on exactly how to get the nVidia drivers working:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

Whatever you do, pick a method and stick with it.  If you use Automatix, stick with that.  If you do things from the wiki page, stick with that.  Switching methods is a sure way to hose your system beyond repair.

Yeah, Im not afraid of losing X anymore... Im familar with the sudo dpkg-reconfigure -phigh server-xorg command, so its as simple as reverting back to NV drivers. This video card thing ticks me off, because im really trying to break my windows dependency. 

Heres a question.. while im fairly expierienced with windows, I dont know much about the life of laptops. How bad is a reboot/shutdown/startup for a laptop? I reboot this computer a lot, whether its trying to get my video drivers working, or switching to XP for my games. Is this a bad thing? This laptop is about a month old, so its pretty new. I even chose my processor based on personal expierience. Ive personally had 2 Athlon processors go out on me, yet the intel pentium I had never gave me a problem. Thats why for this computer, I decided to go with the intel coreduo vs. the athlon equivalent... Intel seems to run cooler. My athlons would get hot enough to make my hands uncomfortable..

The problem isnt Linux, and I dont think its conflicting advice either. Its the fact that corporations dont back Linux, so we as users have to figure out how to trick there crap into accepting our OS. But hey, I was pretty damn effecient with Windows, and getting your ______ kicked by some new world can get frustrating... Im still here..

Anyways, no biggie on the wireless thing.. I thought about the restricted drivers thing yesterday. I reinstalled them before I went to bed, and tonight when I logged on, my wireless was up and running... Im going to check that Wiki, but I believe I already did that. I think I need to install the drivers that Ive downloaded off the nvidia website and  then uninstall the nvidia common kernel as someone else suggested. The problem with that before was if I tried to uninstall the common core, it would remove my GLX drivers, which defeats the purpose. If I do it via the d/l ed drivers, I should be good. Ill let you guys know how it works out... Thanks for all the help and take it easy...

---

### Post by GSF1200S on 2007-04-04
I have figured out my problem to the tee.

I installed the NVIDIA drivers from the website, and then used the synaptic package manager to remove the nvidia kernel common. I reboot, and it works perfect- BUT neither my wired nor wireless internet work. As soon as I try to install the restricted modules to get my internet back up, it shows the nvidia common kernel as a requirement. Installing these restricted modules, I reboot, Xwindow fails to load and I revert back to NV drivers- once X loads, bang, my internet loads. So, im caught in a catch 22. I have to have the restricted modules to make madwifi work, but with them comes the nvidia common kernel, which wont allow my X window to load. 

At this point, it seems to me I have 2 options:

1) figure out how to uninstall solely the nvidia common kernel without uninstalling the restricted modules supporting my wireless/wired internet (anyone know a terminal command to do this?) --or--
2) Ditch madwifi as the method to get my wireless working, and try to use ndiswrapper. At this point, my wired network wont work, but wireless will, and my NVIDIA drivers will work because I wont have the common kernel/ restricted modules to cause X window to fail.

I really hope theres a way to pull off number one without messing stuff up. Anyone have any ideas? Any advice on which route to take? Thanks for the help.. I wouldnt have figured this crap out without this forum, or even this thread...

---

### Post by GSF1200S on 2007-04-04
bump

---

