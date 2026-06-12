---
title: "Ubuntu on Acer Aspire laptop"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by handinglove on 2006-09-29
Hello, my gentle friends!

I'm yet another Windows user curious to try Ubuntu, so if this isn't the right place for this thread, please feel free to move it to where it belongs.
I’ve downloaded the ISO of the 6.06 LTS version and burned it to a CD, then tried to boot it on my laptop (Acer Aspire 1690, with a 64 MB X700 ATI card) to the point where I could see the welcome screen (as seen in the GraphicalInstall thread) and choose to ‘Start or Install Ubuntu’. Then would ensue a long list of what I suppose to be the components of the OS charging into the memory, all followed by an OK, until I’m finally greeted with a sound akin to the one you hear at the welcome screen during Windows start-up. I suppose this would be the point at which the desktop screen would appear, but the screen remained black, with no activity either of the CD in the drive or of the HDD. I always ended up having to shut the computer down pressing the laptop’s start button after a while.
Could anyone please let me know if I’m doing anything wrong? I’d really appreciate any input on this, thanks!

Cheers!

---

### Post by jorn on 2006-09-29
Your screen is probably black becuase the installer can't identify your graficcard or monitor.
Will you come to a text screen by pressing "Ctrl+Alt+F2"?
Enter username and password. Then:
sudo dpkg-reconfigure xserver-xorg
And choose the correct values. Not always easy.
I'm nor sure if you have to restart after that?

---

### Post by handinglove on 2006-09-29
> **jorn said:**
> Your screen is probably black becuase the installer can't identify your graficcard or monitor.
Will you come to a text screen by pressing "Ctrl+Alt+F2"?
Enter username and password. Then:
sudo dpkg-reconfigure xserver-xorg
And choose the correct values. Not always easy.
I'm nor sure if you have to restart after that?

Thanks Jorn, that was a fantastic start! At least with 'Ctrl+Alt+F2' I now can interact with the OS, to the point of being able to reboot the machine. Now, could you please be a little more specific on what 'sudo dpkg-reconfigure xserver-xorg' means? Would there be a place where I could find a list of commands I could use to explore things further? Thanks a lot!

Cheers

---

### Post by jorn on 2006-09-29
Hmm..
There is a certain file that's configures your graficcard and monitor.
It's placed in: etc/X11/xorg.conf
You can see it with the command:
> sudo vi etc/X11/xorg.conf
I think. This file is alteret to the values you give in by using the command:
sudo dpkg-reconfigure xserver-xorg
I just used it a long time ago.
You can find useful knowledge by searching this forum.
Edit: no, its:
> sudo vi /etc/X11/xorg.conf

---

### Post by jorn on 2006-09-29
I searched the Wiki and found this:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer?highlight=%28screen%29%7C%28resolution%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer?highlight=%28screen%29%7C%28resolution%29)
Now, I don't know the last name of your laptop.

---

### Post by handinglove on 2006-09-29
Thanks a lot! Working on it, I'll let you know how it worked.

---

