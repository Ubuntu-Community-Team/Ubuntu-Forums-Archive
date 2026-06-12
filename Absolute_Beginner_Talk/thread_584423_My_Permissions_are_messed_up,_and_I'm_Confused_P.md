---
title: "My Permissions are messed up, and I'm Confused :P"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by jonnymongoose on 2007-10-21
First of all, Hello everybody!
Second of all this has been a long week for me trying to install/use/understand this thing called Linux.
I have solved everything up to this point(installing on a raid and setting up the bootloader), but now I have to admit that I'm stuck. I wanted to try out World of Warcraft by means of Wine and I may have screwed up my permissions. I did a sudo chroot / somewhere and then did my winecfg. I just copied and pasted my WoW install over and opened the .exe with wine. It didnt fire up at first until I fix some mistakes I made in winecfg. Hopefully you see a trend here that I have mucked up every step since I started :) I got WoW to work and it started the update, which didn't finish because my "temp" folder in wine was locked in ROOT along with all the rest of the .wine files. So, from root I started the Patch. and it went on to start the game. The game froze up, and I had to reboot. I checked my WoW folder to find all my .exe files had a big red padlock. Then I found the command  gksudo nautilus, which I then gave permission back to me for my    
Wow files, and started to open up my .wine stuff. Still WoW was a no go and I checked in nautilus and every folder in my File System has a padlock on it(that's the part that confuses me, I cant remember if that is the way it should be). I got the error on log in "User's $HOME/.dmrc is being ignored", but I fixed that one. Now I have no sound at all, and I'm lost. 

Am I just confused or has my "file system" been write protected?
If yes, how do I fix it?
If no, is there an easy way to give permission back to me for all my .wine files?

Thanks
jonnymongoose

---

### Post by ruibernardo on 2007-10-21
Hi jonny,

> **jonnymongoose said:**
>  I did a sudo chroot / somewhere 

Why did you did chroot? to run wine you don't even need to be root. Run wine as a usual user, no need to run it as root or with chroot.

> **jonnymongoose said:**
> and then did my winecfg.

If you run wine as root/chroot, the owner of the files created are owned by root, not in your usual username.

From here I believe that the .wine directory in your personal directory, where you installed WoW, (sudo != root, but if you run as sudo, then they have root ownership) are owned by root, so your usual account can't change them. Remove your ~/wine (~/ stands as your personal folder, /home/username/) with sudo and start over again.

```
 sudo rm -rf ~/.wine
```

---

### Post by sloggerkhan on 2007-10-21
A lot of us screwed up our first installs within a few days of trying ubuntu doing things we didn't really understand or shouldn't have done.

In anycase, start with using your local .wine directory for windows apps.

---

### Post by jonnymongoose on 2007-10-21
> Why did you did chroot? to run wine you don't even need to be root. Run wine as a usual user, no need to run it as root or with chroot.

Why?.......
........Putting the terminal in the hands of a twit like me can only lead to certain doom!  :lolflag:

---

### Post by duanerobertson on 2007-10-21
I got some interesting messages about permissions when I was setting up City of Heroes on my  brand new Ubuntu install last night. I ended up removing the copied files from my Wine C folder and installing CoH from the disk. Then, instead of letting the patcher run, I copied my old program files to the correct directory (with nautilus) and used nautilus to change the permissions for the owner (now me) to read/write/execute/etc. After that it worked fine.

---

### Post by ruibernardo on 2007-10-21
It's normal to make this mistake when you come from a one user OS like windows. 

In Linux or ubuntu only use sudo/root if you want to set something to the whole system. It's not the case here, wine is installed on the system, but each user can and have their settings on their ~/.wine directory and each one have a different C drive on their account).

---

### Post by jonnymongoose on 2007-10-21
Yeah I was thinkin' I should install WoW then paste the updated version over top of it, but I was just trying it out to see how it worked. I'll do that from now on.

I got my .wine folder looking much better, thanks for the fix epimeteo, but my sound is still missing in game and at the desktop(no sound when I play a media file). I checked my "Sound Preferences", and everything looks like it did from before. I have a Audigy2 ZS using the ALSA mixer.

any ideas?

---

### Post by ruibernardo on 2007-10-21
I don't know about WoW, but you can change your ~/.wine audio settings just by running (as normal user)  winecfg in a terminal and selecting the "Audio" tab.

```
winecfg
```

---

