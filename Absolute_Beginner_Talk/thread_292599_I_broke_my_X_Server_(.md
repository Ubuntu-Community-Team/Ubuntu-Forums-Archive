---
title: "I broke my X Server :("
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2006-11-04
I recently rebooted my desktop only to discover that the Xserver no longer loaded.  It now gives me an unintelligable error (at least to me) about how it can no longer load.  The only thing I did was stick a wireless card in...and even when I remove it, it still doesn't work.  

My only guess is that when Easy Ubuntu was editing something video related that would allow me to see 3d with my video card and I had to abort the program in the middle of the installation, it corrupted some config file that  resulted in the breaking of my X server.  Is there any way I can recover it without having to reformat my desktop? ](*,)

---

### Post by steven8 on 2006-11-04
I found these two possible solutions aftering doing a search for reconfigure x server:

> drop into a console, alt+ctrl+f1 and then try typing in
sudo dpkg-reconfigure xserver-xorg

> Happened to me and i had to type "sudo apt-get install xorg", dunno why the update 'forgot' to install the xorg server, but it worked after that

I have never had this happen, but give these a try and see how it goes.

---

### Post by StormGuy on 2006-11-04
Thanks, that first option seems to have worked.  Unfortunately, when I boot the graphical server now, it gives me the same garbled mess it used to give me when my Nvidia drivers weren't installed...which is weird because when I reconfigured it...I set it to nv and Gforce 6600 (both were options on the list).  Is there a way I can grab and install the Nvidia drivers inside of the console?  I'd love to do it graphically, but I don't have another video card handy at the moment.

---

### Post by steven8 on 2006-11-04
[http://ubuntuforums.org/showthread.php?t=242295&highlight=nvidia+terminal]("http://ubuntuforums.org/showthread.php?t=242295&highlight=nvidia+terminal")

---

### Post by StormGuy on 2006-11-04
Hmm...when I change it it just breaks my X Server again. :\

---

### Post by StormGuy on 2006-11-04
When I attempt to apt-get the Nvidia drivers, I get the following error

Err [http://archive.ubuntu.com/ubuntu/pool/restricted](http://archive.ubuntu.com/ubuntu/pool/restricted) nvidia-glx 1.0.8762+2.6.15.11-1
  Temporary failure resolving 'archive.ubuntu.com'
"Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762+2.6.15.11-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762+2.6.15.11-1_amd64.deb) Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Is it possible that I'm not getting the proper files?  I tried it with the --fix-mising and update...but no luck with either of those :(

---

### Post by steven8 on 2006-11-04
The last part said this:

> ok, decided to wipe the server installation and install desktop edition. followed your steps after the reinstall and everything went smoothly. thanks.

Do you have server or desktop installation?

---

### Post by steven8 on 2006-11-04
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

See if this guide by tseliot will help.

---

### Post by StormGuy on 2006-11-04
I have the desktop edition, I believe.  I'm not sure...so I'm just assuming.

---

### Post by steven8 on 2006-11-04
Did you burn your own disk from the iso download?  These are the filenames:

ubuntu-6.06.1-server-i386.iso

ubuntu-6.06.1-desktop-i386.iso

Give that guide a try and see how it goes.

---

### Post by StormGuy on 2006-11-04
I used the Live CD

I used this guide before, but had to resort to using another videocard for the installation so I could download the package offline.  For whatever reason, my apt-get rarely works and I have to grab most of my stuff from sites instead.  It's not a HUGE problem, but it is a little annoying since it means I can't fix this tonight and have to wait till the morning.  Is there any reason my apt-get wouldn't be able to get the correct files?

Oh, well...no biggie.  Thanks a ton for all your help.

---

### Post by justifier on 2006-11-04
to get graphical interface back, when it boots to terminal try this

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf

try that and see if it fixes it, i allways make a copy of xorg.conf on my desktop just incase it breaks before changing anything

justifier

---

### Post by StormGuy on 2006-11-04
Wow...I'm amazingly dumb and you should all laugh at me.  I finally got it working.  The problem?  My modem wasn't plugged into my desktop ](*,) 

Thank you so much for your patience...I'm going to go hide my face under something for a while now.

---

### Post by steven8 on 2006-11-04
That's fine.  I'm just glad you got it working.  I am a total newbie, and things like this help me to learn as well.  I discovered command line information I didn't know before.

Maybe it's time to get some sleep!!  :-)  You've earned it.

---

### Post by StormGuy on 2006-11-04
Sounds like a good idea :)

Thanks again

---

### Post by steven8 on 2006-11-04
You're welcome.  g'nite.

---

