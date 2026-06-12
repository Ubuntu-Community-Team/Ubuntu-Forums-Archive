---
title: "Xubuntu 7.10 freezes at startup"
date: 2008-12-08
forum: Apple Hardware Users
---

### Post by doctorbighands on 2008-12-08
I followed the directions here ([https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)) and was able to get the Live CD to boot and get the OS installed, but now I can't get the installation to boot from the hard disk. I tried booting into the live CD and appending the /etc/initramfs-tools/modules file according to directions, but it still won't go.

What should I do?

---

### Post by meg23 on 2008-12-08
It sounds like boot loader "yaboot" probably didnt install correctly. I have had similiar problem. In my case it happened because of a format problem with the hardisk. Yaboot is kind of testy. I had much better luck with Xubuntu 7.04. You might want to install that.

---

### Post by doctorbighands on 2008-12-08
Is there a way to reinstall yaboot without redoing the whole OS?

Also, I can't find a download mirror for 7.04.

---

### Post by meg23 on 2008-12-08
I feel your pain. You first need to run the livecd and run gparted to determine if yaboot partition is missing. If it is, theoretically what you need to do is get a yaboot and load it into the partition via the livecd. However, I was never able to fix this problem on my own. The last option you have is try to install xubuntu on a smaller partition and import your settings. 

I am a little surprised that you can't find Ubuntu 7.04, I am going to put out a call to swarm the torrent file on the forums. Check back at this post.

---

### Post by doctorbighands on 2008-12-08
Smaller partition is funny - my whole drive is 3.3GB! :) As it happens, that's the main reason I chose xfce over Gnome.

That's mighty generous of you to put out that call. I hope, for the sake of others struggling with this problem, that it finds its way here!

I'm working on installing 8.10 right now. We'll see how that goes...

Thank you for being so helpful!

---

### Post by tiresia on 2008-12-08
Can you please post more informations about your Hardware?
What happens, when you reboot after the installation?

---

### Post by doctorbighands on 2008-12-08
It's an iBook G3 "clamshell" style laptop. 300MHz CPU, 288MB RAM, 3.3GB HDD. I'm not sure about other hardware, but it hasn't been tinkered with, so it should be whatever factory specs say it is.

I turn it on, I get the Yaboot screen which seems to load the kernel just fine, and then the screen goes black and all motion stops. That's as far as it'll go.

I installed Intrepid, but that's giving me a whole new set of problems. Gah!

All I want is to get some kind of lightweight (because of the HDD size, mainly) distro running on this thing, and I can't seem to do that.

---

### Post by tiresia on 2008-12-08
You should be able to access the desktop environment, typing at the yaboot prompt
```
Linux video=ofonly nosplash
```
After that, if it works, you need to edit your /etc/xorg.conf file, in order to configure a correct video. Have a look in this forum, you will find a few threads dealing this issue.
Let us know, if you still have problems

---

### Post by doctorbighands on 2008-12-08
I went ahead and installed the server version of 8.04 and installed xubuntu-desktop on top of it. Now I have a beautifully functioning iBook with (so far) no bugs!

Hardy must be the most bug-free release of all of them. I don't think I've ever had an issue with it on any platform.

Anyway, problem solved for now, and hopefully for good! Thanks to everyone for your help.

---

### Post by stream303 on 2008-12-08
> **doctorbighands said:**
> I went ahead and installed the server version of 8.04 and installed xubuntu-desktop on top of it. Now I have a beautifully functioning iBook with (so far) no bugs!

That's a rockin' way to do it!  Can you post your /etc/X11/xorg.conf and /etc/yabot.conf for other clamshell owners?

Don't forget that you are running with a kernel tuned for server use.  You may want to go into synaptic, apt-get etc to see if you want to install the desktop kernel.

But first, enjoy your new box for a few days! :)

Glad to see you got that worked out.

---

