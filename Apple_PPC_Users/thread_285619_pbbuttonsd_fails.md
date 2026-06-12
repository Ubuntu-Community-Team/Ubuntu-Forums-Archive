---
title: "pbbuttonsd fails"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by silouette747 on 2006-10-27
I managed to install Ubuntu on my iMac G5 using the alternate cd. However when I try to boot it fails when pbbuttonsd tries to boot. Is there anyway to bypass this or get into ubuntu somehow?

---

### Post by stmiller on 2006-10-27
pbbuttonsd takes care of some important parts of mac hardware, so it is needed. Unfortunately, it is probably trying to load laptop sleep/suspend support for a hardware part that doesn't exist on your desktop computer. 

One possible way to fix this is to boot again from the alternate CD and press tab at the boot prompt. I think there's a rescue mode to choose there. After you are booted in rescue mode, you can then navigate to edit the file /etc/pbbuttonsd.conf (I think that's it) and comment out lines of the hardware that it is trying to load.

Or just rename that file to pbbuttonsd.conf.bkup or something different. That would prevent it from loading.

Either that, or you can turn off the service of pbbuttonsd from loading. It would be a sym link in one or many of the /etc/rc.***
folders. You could find it, and just remove (or temporarily move) that sym link. You could do that in rescue mode.

---

### Post by silouette747 on 2006-10-27
I got into rescue mode and I couldn't get to the file /etc/pbbuttonsd.conf I want to try the other method you suggested but I don't know how, could you provide some instruction?

---

### Post by stmiller on 2006-10-28
Okay yeah give me a second and I'll find exactly what you need to do. I need to poke around my system first.

On a side note, here is a program (sysvconfig) to help you pick what starts/stops. This might be good to poke around with, after you've got a bootable system.

[http://ubuntuforums.org/showthread.php?t=263932](http://ubuntuforums.org/showthread.php?t=263932)

---

### Post by stmiller on 2006-10-28
Okay this is kind of nitty gritty, but here you go:

There are folders here:

/etc/rc0.d
/etc/rc1.d
/etc/rc2.d

thru
/etc/rc6.d

Each represents a different run level. The folders contain a sym link of which service to start for each run level. So you must delete or move the sym links for pbbuttonsd which in ubuntu are:

/etc/rc0.d/K12pbbuttonsd
/etc/rc1.d/K12pbbuttonsd
/etc/rc2.d/K12pbbuttonsd
/etc/rc3.d/K12pbbuttonsd
/etc/rc4.d/K12pbbuttonsd


So, once booted up in rescue mode,

$ cd /etc/rc0.d/

$ mkdir disable

$ mv K12pbbuttonsd disable/

Then go to the next one,

$ cd /etc/rc1.d

$ mkdir disable

$ mv K12pbbuttonsd disable/


Repeat for the rest of the run level folders with pbbuttonsd.

Then restart, and pbbuttonsd will not load.

Check out that program sysvconfig, or just remove pbbuttonsd once you are all up and running. Good luck! There might be a more elegant way to do this, if anyone wants to chime in.

---

### Post by silouette747 on 2006-10-28
no luck it pbbuttonsd still fails. Maybe I'm doing it wrong? I excute a shell once I'm in rescue mode and I typed in the commands you said. on rc2.d-rc5.d it told me that pbbuttonsd was not found. For the others it just went to the next line. Did I do something wrong?

---

### Post by stmiller on 2006-10-29
For those steps, you are moving the file to a folder you made called disable. If it just went to the next line, that means it successfully moved the pbbuttonsd link.

How are your *nix command skills? You can list what is in a directory by typing 

$ ls

so poke around and see if you see anything that says pbbuttonsd in those rc*.d folders. It might have a different letter at the beginning, than the filenames on my system. And then move it or delete it! Sorry you are having such a mess. This is a pretty technical problem.

---

### Post by silouette747 on 2006-10-29
This is my second time using linux. First time I installed ubuntu on my PC no problem. Now I'm trying to get it on my imac and I'm running into problem after problem ](*,) but hopefully I can figure it out with your help. I'll try your suggestion.

---

### Post by silouette747 on 2006-10-29
Success! It worked. The problem was in /etc/rc2.d/ to /etc/rc5.d/ the file was named S12pbbuttonsd. I rebooted and the message no longer came up. However after everything finished loading fine, the computer screen went black as if it failed again. Any ideas?

---

### Post by silouette747 on 2006-10-29
I think I might have found the root of the entire problem. Ubuntu is fine, the problem is the video. On a hunch I tried doing a complete reinstall including erasing the entire hard drive. After the install was completed and the screen went blank, I heard a sound then I entered my username and password and I heard another sound that sounded like it had successfully booted into Ubuntu a completion kind of sound. So what I'm thinking is that maybe it just isn't supporting the monitor maybe because of the widescreen or the high resolution. So if anyone can tell me how to like manually get the video working it just might work.

---

### Post by seatea on 2006-10-29
I just installed edgy, but I get a black screen up until the time just before login. Formerly, I got a screen with the ubuntu logo and a series of messages before the  login prompt. I got the pbbuttonsd failed message during that time. I was able to stop the  pbbuttonsd,  since I don't have a laptop, by running the following in terminal:

```
sudo start-stop-daemon --verbose --stop --exec  /usr/bin/pbbuttonsd
``` 

This took care of the daemon running pbbuttons. I didn't notice any problems after that except that I can't put my  computer to sleep. I ran this command  again in edgy, even though I don't know if it is giving the  failed message, and once again got the  confirmation "Stopped /usr/bin/pbbuttonsd (pid 3562)". Now, what to do about the black screen?

---

