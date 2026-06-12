---
title: "gusty server + gui ... NOT"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by lazyart on 2008-01-14
This past weekend I was tasked to put up an alternative solution for a currently running Windows FTP server which was giving cruddy throughput even after multiple tweaks.  This was for a financial company so security was a concern.

So, I put together Gutsy Server in a VM hosted on a Windows Server 2003R2 blade.  I went with the gosh-its-so-simple OpenSSH setup and I hit the ground running.  After spending all of Saturday getting it going (had to do it all remotely, including transferring the .iso, so it was time consuming).  After getting close but not quite, I decided I would install a GUI to help me along.  Sunday morning I jumped out of bed at 4:30, started the```
sudo apt-get install ubuntu-desktop
``` process and went back to sleep.  At 9:30 I woke up and things went all wrong.

First there was a corrupted file in the download.  Eventually I had to clear the /var/cache and download again, but things started installing.  I typed startx got into the desktop and installed the VMware tools.

That would be the last time I saw the desktop as it should be.  When rebooting I started getting messages that the greeter app was crashing.  Reconfigured X, no luck.  Then somehow I couldnt get online anymore.  A few hours of that and I decided it would be quicker to just build another server.  And I did.  Got it running, SSH was doing it's thing, so I tried installing a GUI.  This time I tried xubuntu-desktop (which I have done on my LAMP server at home), or so I thought, but when it finally came to the desktop I got the familiar brown background, but no icons.  Restarting I foudn I had a problem with the "default font 'fixes'" or something to that effect.  Found the answer here on the forum. but then again started getting the greeter app crashing message.  Got to the command line and installed xdm instead.  Got me to the brown desktop with no icons.  So then I tried installing ubuntu-desktop.  It did it's thing but the greeter app would crash again.  So I tried to remove ubuntu-desktop.  apt-get tells me it's not installed.  AAARGH!  I tried Synaptic from the command line and messed something up because the next time I tried to fetch packages I got a Segmentation fault. WTF!?!  Finally cleared that up by clearing the /var/cache again.

So I removed gdm and xdm.  Got me to the command line.  From there I told myself forget about the gui.  It's 6:30 now I have gotten NOTHING accomplished.

I then make 4 ssh connections to the server.  With nano running in different windows I could edit the files I needed to and test the results from another connection.  Finally was able to map drives for different user connections to facilitate backups.  Found that by default Ubuntu will let you look at anyone's home directory, so I fixed that with a CHMOD 700.  It took about an hour and a half of true work to get it done but I spent so much time trying to create a gui.  I don't know what happened.

So my question is,

Is there a secret to getting a GUI on Gutsy Server running on a VM?

The good news here is that we replaced a Windows Server with an Ubuntu Server.  I like it.

---

### Post by Dr Small on 2008-01-14
May I ask, why do you need a GUI on a server, anyways ??
I normally just install xorg, and then IceWM along with a few little applications that I need, such as pcmanfm, and then I'm done.

But, if you are running a server, why would you want a GUI on it, when you have SSH ?

Dr Small

---

### Post by lazyart on 2008-01-14
I just wanted the gui up to get things configured... it was going away once I had everything in place.  Webmin would have been nice but wasn't an option in this setting.

---

