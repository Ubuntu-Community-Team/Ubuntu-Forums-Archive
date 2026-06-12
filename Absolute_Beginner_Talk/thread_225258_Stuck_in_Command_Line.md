---
title: "Stuck in Command Line"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Village on 2006-07-29
New Linux user here, and already I've hit a bit of a problem. 

After reading somewhere on the Internet that by pressing ctrl+alt+f1 I would be able to bring up the command line I decided to see what it looked like, after getting into the command line (and not typing anything I tried to get out of the command line and back to the GUI, but ctrl+f7 does not seem to be working. It looks like curiosity has killed the cat, any suggestions?

Thanks

---

### Post by Seaman on 2006-07-29
**ctrl+alt+F7** it is.

---

### Post by Village on 2006-07-29
Tried that a number of times still nothing;

the text that is up now is saying something about 
"An automatic file system check of the toot filesystem failed.
A manual fsck must be performed, then the system rebooted. 
This fsck can be performed in maintenance mode. 
Please not that the root filesystem is currently mounted read-only. 
The fsck should only be performed whilst the root filesystme is mounted read-only. However, the command to remount it read writes is:
In order to exit from the maintenance shell, press control-D and the system will reboot"
# mount -n -o remount,rw /
In order to exit from the maintenance shell, press control-D and the system will reboot.
"

---

### Post by rowanparker on 2006-07-29
What happens after a reboot?
Does it load the GUI again?

To reboot from the command line, login and use ```
sudo shutdown -r now
```


Rowan.

---

### Post by Village on 2006-07-29
tried that it still takes me back to the command line.

Basically it gets about 70% though doing a check on /dev/hda3 and then says Unexpected Inconsist4ncy, run fschk manually

I don't know how to do this. I can't understand why this is happening, I just loaded up the command line to take a look at it and then tried to get back to the GUI but it wouldn't let me, so i rebooted it and I'm stuck in this loop.

---

### Post by rowanparker on 2006-07-29
You could do ```
sudo apt-get install ubuntu-desktop
``` to make sure it's alright.

---

### Post by Village on 2006-07-29
Would that reinstall Ubuntu?

---

### Post by Village on 2006-07-29
its saying;

"bash: sudo: command not found

---

### Post by rowanparker on 2006-07-29
It wouldn't reinstall ubuntu but it sounds like you need to if it can't find sudo.

Unless anyone else has got any ideas?

---

### Post by DirtDawg on 2006-07-29
Forgive me if this is obvious, but as you're new, maybe you don't know. The command line can be accessed in a window without disregarding the rest of the desktop. I believe it's under applications>terminal (that may be wrong, but it's in the menu system somewheres).

Again, sorry if this is obvious. I did the same thing as you once, thinking ctrl+shift+F1 would open a new window.

---

### Post by rowanparker on 2006-07-29
But now he's done that, he can't seem to get out of it.

---

### Post by Loffe_ on 2006-07-29
> **Village said:**
> its saying;

"bash: sudo: command not found

That is not good. To me this sounds like your filesystem is bad. (I suppose you did not erase your files on purpose :p). If you are running on an old harddrive it may have crashed.

Switching to the console *should* not give you this problem..

---

### Post by rowanparker on 2006-07-29
Should we reccommend a reinstall?

---

### Post by Loffe_ on 2006-07-29
> **rowanparker said:**
> Should we reccommend a reinstall?

I would recommend the live cd.
It should contain some tools to check (and maybe fix) the disk. Hopefully it is only the filesystem that is corrupt...

/Loffe

---

### Post by Village on 2006-07-30
Thanks for the advice, I found I could assess the terminal and still run the GUI (before hand my problem was getting my wifi card to work). 

Basically I read somewhere that you could go to the command line and being curious I thought that I would just do that to see what it looks like. I hit the buttons, looked at the screen and remembered why MS Dos went away, namely simple people like myself like a GUI, its easier to understand. Anyway I then tried to hit the buttons to take me back to the GUI and it wouldn't work, so I went to the different command line screens (f2, f3 and so on) and then back to f1 and tried to access the GUI. Again nothing. 
So I switched my Laptop off, came back to it later and still the command line, I've tried booting in safe mode, still command line. now its coming up with the fault as reported earlier, and I'm still stuck. 

By the sounds of it I might have to reinstall. I was going to do that anyway as currently I'm dual-booting with windows xp, and I thought that I would just run Ubuntu and nothing else on this laptop (OK maybe another version of Linux, like I said I'm curious). I guess that this has just forced my hand a little.

Just for the record I'm running Ubuntu on a 5 year old Laptop, P3 1ghz, 320mb Ram and a 30gb hard drive. I didn't think that there were any problems on my original install but if your saying the file system is corrupt then maybe there was?

Thanks for you help,

Village

---

### Post by rowanparker on 2006-07-30
No problem, happy to help.

---

### Post by Village on 2006-08-01
I've reinstalled it and during the setup I saw something flash across the screen about "RAND" and FAIL. I'm not sure what RAND is but could it be the reason for my problems.

Like I said I have reinstalled Ubuntu and so far it seems to be working, although I don't know if I'll ever enter the command line again. 

I think I know my limits.

Village

---

### Post by Tomosaur on 2006-08-01
Are you sure it didn't say 'RAID'?

---

### Post by steve.horsley on 2006-08-01
> **Village said:**
> I've reinstalled it and during the setup I saw something flash across the screen about "RAND" and FAIL. I'm not sure what RAND is but could it be the reason for my problems.

My lappy says that too. It's something to do with not being able to initialise the random number generator from a hardware random number generator, I think. Which means any random numbers you generate might not be as random as they could have been. Nothing serious.> 
Like I said I have reinstalled Ubuntu and so far it seems to be working, although I don't know if I'll ever enter the command line again. 

I think I know my limits.

Village
As others have said, switching to one of the text consoles should not have done that. It is possible however, that switching off instead of shutting down cleanly did it. It's worth remembering that from a text console (or from Alt-Ctrl-F1 at least) you can reboot with Alt-Ctrl-Del, which does a clean shutdown, and you can turn off while the BIOS is starting up again. Or use the command **reboot** or **sudo init 6** (**sudo init 0** shuts it down).

---

### Post by Village on 2006-08-04
Thanks for that, and yes I think that it might have been RAID instead, it only flashed up for a second.

---

