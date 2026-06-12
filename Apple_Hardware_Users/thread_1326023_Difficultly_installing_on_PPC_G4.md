---
title: "Difficultly installing on PPC G4"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by zobo1942 on 2009-11-14
Hello,
 
Just a quick question: When I'm installing Kubuntu, I get to the login screen, and then have no idea what to do. 
 
Thoughts? I'd LOVE to get this machine up and running!

---

### Post by linuxopjemac on 2009-11-14
might sound silly what I say now, but at login screen you have to login with a user name and a password. During the installation you created a user with a password associated to it. You should enter these details there.

---

### Post by zobo1942 on 2009-11-14
The funny thing is, during the installation process, I didn't enter anything... 
 
I booted from the CD, and loaded the live-nosplash-powerpc kernel.
 
Then I waited about 20 minutes.
 
Got to a screen, double clicked on the 'install kubuntu' icon.

Login screen popped up and... ?
 
Am I missing something really obvious?

---

### Post by B_Free on 2009-11-14
Which G4 are you installing Kubuntu? Which version of Kubuntu?

---

### Post by zobo1942 on 2009-11-14
Hello,
 
G4/450, 80gigHD, 256MB RAM - and I've FINALLY gotten to the login screen again... but I have no login information to enter.
 
Is there a default login - like kubunto/kubunto or something?
 
I'm trying to install Kubunto 9.10 - the kernal loaded from yaboot is 'live-nosplash-powerpc', which I burned to DVD to make the install.
 
I really appreciate and help you could give me!
 
Geoff

---

### Post by zobo1942 on 2009-11-14
Back at the login screen (with no input from me)
 
there are the two fields - (top) person sillouette and a blank area (I'm assuming user name) and the second field with a key beside it (I'm assuming password)
 
There are two buttons to the lower left of the dialogue box - one with three horizontal lines, which, when pressed, the options of default, KDE, and failsafe (None selected)
 
and the second - with a 'power' icon - options, when pressed, switch user, restart x server, remote login, console login, shutdown.
 
Any ideas?

---

### Post by zobo1942 on 2009-11-15
Maybe I should try installing another version?

---

### Post by zobo1942 on 2009-11-15
Anyone? Anyone?

---

### Post by zobo1942 on 2009-11-15
download the iso from here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
 
NOT from here:
[http://cdimage.ubuntu.com/kubuntu/ports/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/ports/daily-live/current/)
 
80% done!!

---

### Post by B_Free on 2009-11-17
If you are successful, please share your success with us. If there was no place to add your name and password when you installed the software, try return, return or tab, tab.
I have not found any distribution installable except 5.10 and 6.06 on my Mac 450 G4. These "distros"were developed closer to the time the Mac was made. If you need help i'll check here tomorrow morning (Mountain time).

---

### Post by zobo1942 on 2009-11-17
Successful installation of Ubuntu 9.10!
 
Burning the .iso I mentioned previously, I just burned a DVD on my PC, stuck it in the drive on the mac and booted from the disk and followed the instructions. Easy!
 
I think the trouble I was having was the distro I was trying to install was kubuntu, not ubuntu, and the rage128 with 16MB of video ram couldn't handle it (I'm guessing).
 
I love this OS! I'm starting to think that the next machine I buy will run this OS. It's got some pre-OS X 'mac-ism's I really like, and some other parts that remind me of windows. Great stuff!
 
However, the age of the machine is rather apparent in a few places - launching apps takes quite a bit of time, and the lack of a flash player is a pain. Also, watching media across my network from my PC to it is quite bad - choppy, and the sound seems to be a bit of a mess overall. 
 
That said, I was going to throw this machine out last week, and now, I think it will be  up and running for me to use for emailing, writing, etc... (I already use openoffice on my PC), so that's great!
 
Any thoughts on how I could improve the video playback? I'm thinking of throwing in another video card with 128 MB of RAM would help... and if I can find more PC100 RAM, I may try to throw some more of that in it as well, just to try to see if it helps.
 
Any advice? Thanks for your interest!!

---

### Post by B_Free on 2009-11-22
Try going to [http://www.medibuntu.org/](http://www.medibuntu.org/) for CODECS. Also, go to [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/).

---

### Post by linuxopjemac on 2009-11-23
The problem with this is that you have a PPC Apple. Proprietary drivers are closed binaries written for x86 and they won't work on a PPC. You have to always use the open source drivers....

---

