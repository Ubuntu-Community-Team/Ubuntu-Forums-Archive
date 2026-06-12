---
title: "Installed a GeForce 7300, and a fresh install will not log in"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by vuarra on 2008-03-14
I had upgraded my video card from the built in Radeon X200 to a PCI-e GeForce 7300GS.  I checked for power connectors, and there were none built-in on the card.  Windoze eXtra Poopy, of course, has no problems with the card.

The system is a HP a1350n, 1.5 GiB of memory, and a 4200+ Athlon 64 X2, and a Samsung SyncMaster 941BW through DVI connection.

When I did a fresh install of 64-bit 7.10 Ubuntu, I get a login error, where the login lasts for 10 seconds, and Ubuntu suggests that I might have a problem.

I also get the feeling that the video card might be a red-herring, as I can boot from the CD.

Any recommendations?

---

### Post by drdrewdown on 2008-03-14
can you provide any more info such as the errors its giving you?

also i'm not sure why you would want to mess with 64bit os when you only have 1.5gb of ram...  if its just to explore 64bit thats kewl, but other then that its a pita

---

### Post by smurphy_it on 2008-03-14
I'm assuming you reloaded Ubuntu 64-Bit 7.10 after installing the new Nvidia Card.  Guess it won't matter much as video isn't working properly now.

did you try reconfiguring your xserver video to it's defaults to see if that will let you in ?  If so, you can always try the Restricted Drivers Manager for the Nvidia Card or download them through either Nvidia's website or say try something like Envy.

In a terminal type:

sudo /etc/init.d/gdm stop

Hit Ctrl-Alt-F2 and login to the terminal then type the following:

sudo dpkg-reconfigure xserver-xorg

Afterwards, type:
sudo /etc/init.d/gdm start

Might have to hit Ctrl-Alt-F7 to get back into X-windows

That should allow you to login.  Once logged in, go to System, Administrator, Restricted Drivers Manager and see if you can "enable" the firmware for your Nvidia Video Card.

If not, you can always use Envy by going [Here.]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by vuarra on 2008-03-14
I really cannot provide any more info, as I login, the screen clears, then it tells me that my login lasted less than 10 seconds, and there may be a problem with my system.  It will not let me go any further in X or Gnome... it even does that in safe mode.

@smurphy_it:  I'll do that when I get more chance, and follow up on this thread... gotta love it when the boss springs instant overtime for me :)

---

### Post by vuarra on 2008-03-15
Problem solved.

Video card seems to have been a red herring, I'm guessing (and probably should be hitting myself on the head, too) that when I re-installed Ubuntu, I did not set a / folder - or at least not properly - and could not login because the files required were not in a recognized place.

Thank  you to all who responded.

---

