---
title: "G4 as File Server"
date: 2008-03-04
forum: Apple PPC Users
---

### Post by fireman biff on 2008-03-04
Hi, I have an old Power Mac G4 which is just sitting around and I'm thinking of using it as a file server for my small home network which consists of about 4-6 computers running Ubuntu and Windows (2000/XP).

I'm trying to decide what OS to put on the computer. It currently has OSX 10.3.9 I think (panther). I figure that another OS could probably use less resources (which are very limited), especially if I keep in command line only.

Should I use Ubuntu 6.06 or should I look for a more recent non-Ubuntu distribution? If you think I should go the non-Ubuntu way please suggest an alternative (I'm open to a BSD-type OS also).

Or should I just forget the whole idea cause the computer is old?

---

### Post by bogoliubov on 2008-03-04
Hello. The G4 might work very well for this task. It depends a bit on which G4 you have, and how much RAM you have. I'd suggest Ubuntu for this task, but if you really want it to use few resources, perhaps you can install Ubuntu Server. 

This won't provide you with a GUI, but if you're comfortable with the command line, you should be OK.  If you want a GUI though, you can still install Ubuntu server, and the install the XFCE desktop environment through apt-get or aptitude. XFCE is what Xubuntu uses, and it requires less memory than Gnome or KDE.

On the other hand, you can surely use some other Linux distro, or BSD. But in my experience Ubuntu is very good since one can easily get help through the forums, at least better than for BSD and some of the other Linux distros.

If you can wait a month or so, you can install Ubuntu 8.04 when it comes out in april. This will be a LTS (Long Term Support) release, which may be nice for a server. But the current version of Ubuntu  will work as well, and it's usually easy to upgrade to the newer version when it comes out.

---

### Post by fireman biff on 2008-03-04
> **bogoliubov said:**
> If you can wait a month or so, you can install Ubuntu 8.04 when it comes out in april. This will be a LTS (Long Term Support) release, which may be nice for a server. But the current version of Ubuntu  will work as well, and it's usually easy to upgrade to the newer version when it comes out.

Are you sure about this? I was under the impression that 6.06 (Dapper) was the last release to support PPC. I'm not extremely familiar with Macs, but I'm pretty sure the one I have is PPC.

If I could use the server version Gutsy or Hardy (possibly with XFCE) I would gladly do so, I just didn't think it was an option.

---

### Post by bogoliubov on 2008-03-04
> **fireman biff said:**
> Are you sure about this? I was under the impression that 6.06 (Dapper) was the last release to support PPC. I'm not extremely familiar with Macs, but I'm pretty sure the one I have is PPC.

If I could use the server version Gutsy or Hardy (possibly with XFCE) I would gladly do so, I just didn't think it was an option.

Yes, all Macs between the first G3s and the G5s are PowerPCs. 
It is correct that Dapper was the last release to officially support PPC, but the UBuntu community still create PPC versions of the Ubuntu releases. Have a look at [this]("http://ubuntuforums.org/showthread.php?t=427714") thread.

By the way, what G4 do you have and how much RAM?

---

### Post by fireman biff on 2008-03-04
> **bogoliubov said:**
> By the way, what G4 do you have and how much RAM?

From looking at the Wikipedia page I would say its a Graphite G4. Let me know If that's not what you meant, I can pull it out and look for any information that might be useful.

If I remember correctly it has around 190 MB of RAM. Definitely less than 256.

---

### Post by bogoliubov on 2008-03-04
> **fireman biff said:**
> From looking at the Wikipedia page I would say its a Graphite G4. Let me know If that's not what you meant, I can pull it out and look for any information that might be useful.

If I remember correctly it has around 190 MB of RAM. Definitely less than 256.

Nah, it's not that important. Just to know what the system may be able to do...
But 192 MB should be OK with Xubuntu I think, at least if you do the server install. However, I'm not sure if all these different discs are available for the PPC nowadays. It might be so that there is simply and Ubuntu disc, and one has to go from there. Have a look in the link I showed.

If it's a Graphite G4, then it will have at least 400 MHz CPU. These specs are about the minimum for Xubuntu I think. If you can live without a GUI, then try that. If you just need it as a file and printer server, it might work very well.

But if you have a more recent than the first graphites, it might be OK for heavier work..., trying is best I guess.... :)

---

### Post by fireman biff on 2008-03-04
K, well I think I'll try the alternate install cd for Xubuntu Gutsy. Once I get it running I'll decide if to use XCFE or skip the GUI.

Thanks a lot for your help :) (and fast responses)

---

### Post by stream303 on 2008-03-04
The good news is that it looks like Hardy will once again offer a ppc server install.

In the meantime, you can try Feisty server

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

and if you wish to just bring up a very simple X environment, do your administration in a few xterms, and then shut down X to conserve resources, check this out:

[http://ubuntuforums.org/showthread.php?t=685324](http://ubuntuforums.org/showthread.php?t=685324)

It could be as simple as doing

```
sudo aptitude install xorg twm
```

Then edit a new file called **.xinitrc** in your home directory and add these lines:

xterm &
exec twm

and use startx at the commandline to bring it up.  When done administering, just hit Ctrl-Alt-Backspace or Ctrl-Alt-Delete to stop X.  If you need more xterm terminals at the start, just add them to your .xinitrc file, and drag them off of each other when X starts.  (or set your xterm geometry settings in .xinitrc, but this will get you started - just do a CTRL-right click on an xterm and choose Large or Huge fonts for right now. )

---

### Post by fireman biff on 2008-03-04
> **stream303 said:**
> The good news is that it looks like Hardy will once again offer a ppc server install.

In the meantime, you can try Feisty server

As mentioned I was thinking to use the alternate install CD for Xubuntu Gutsy. Are there any advantages in using the server CD for Xubuntu Feisty/Hardy instead?

---

### Post by stream303 on 2008-03-04
The main advantage to using the server install is that you will get a kernel optimized for server usage, (100hz kernel freq vs 250hz desktop among other things) and it will ask you if you want to install a dns server, or lamp stack (or both) during installation and do the heavy lifting of installing these things for you.

With the alternate install images, you will usually end up with a desktop Xubuntu, along with a desktop kernel.  The alternate is just a text-graphics installer, and not a full blown gui / live-desktop like the standard installer.  Either way you end up with a gui desktop, probably something you don't want with a server.  (unless you do the super simple xorg / twm / xterm thing...)

I'd definitely recommend the server install for server use.  If you do run with this, you can immediately update it:
```

sudo aptitude update

sudo aptitude upgrade
```

If you find newer kernels being held back when you do this, you can force apt-get to install them.

---

### Post by fireman biff on 2008-03-04
Thanks for the advice stream303. I'm now also downloading the server version of Fiesty. I'll give the two a try and see which one works better for me.

---

