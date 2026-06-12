---
title: "Steam problems"
date: 2014-06-01
forum: Any Other OS
---

### Post by Mazate on 2014-06-01
I just installed Mint 17 Mate  version and I'm trying to install Steam.  I've tried installing in the  software center and I've tried installing from the steampowered.com site  and either way my results are the same.  It appears to install fine but  when I go to double-click the icon on my desktop, nothing happens.  It  doesn't respond in any way.  My hard drive does nothing.  When I go into  the menu and launch it from there, same thing.  Any help would be most  appreciated.

---

### Post by Joel_Ross on 2014-06-01
open a terminal session and run steam from there. See if it opens/logs any errors

---

### Post by Mazate on 2014-06-01
Sorry, I'm not real proficient in the terminal. I would have no idea how to find the right directory or type the right command but I'm open for following instructions.

---

### Post by sammiev on 2014-06-01
Found [this]("https://github.com/ValveSoftware/steam-for-linux/issues/1386") quickly, give it a read.

---

### Post by Joel_Ross on 2014-06-01
> **Mazate said:**
> Sorry, I'm not real proficient in the terminal. I would have no idea how to find the right directory or type the right command but I'm open for following instructions.

Open your Start Menu like you would in Windows go to Accessories > find Terminal and click on it, then just type steam in the terminal window, its that easy :) All output will be display in this terminal, so if you encounter any errors it will be displayed here.

---

### Post by Mazate on 2014-06-01
Sorry, I may have given a false impression of being more inept than I really am with the terminal.  I can do basic stuff and what I don't know how to do I can usually find instructions for, this current issue being an exception.  Here is the output when I type Steam into the terminal.

```
$ steam
Running Steam on linuxmint 17 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140601061935_1.dmp
/home/david/.local/share/Steam/steam.sh: line 755:  8608 Segmentation fault      $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/david/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/david/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on linuxmint 17 64-bit
STEAM_RUNTIME has been set by the user to: /home/david/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140601061937_1.dmp
/home/david/.local/share/Steam/steam.sh: line 755:  8733 Segmentation fault      $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-28040f0e-2719-4f19-bd19-6f9002140601
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-0b88badb-ed87-4bc0-a729-dc9442140601
```

---

### Post by Joel_Ross on 2014-06-01
Run this from terminal:

```
locate libGL.so.1
```

And post output here

There is a resloved issue here [https://github.com/ValveSoftware/steam-for-linux/issues/3020](https://github.com/ValveSoftware/steam-for-linux/issues/3020) regrading the location of the libGL.so.1

Also a new issue here [https://github.com/ValveSoftware/steam-for-linux/issues/3340](https://github.com/ValveSoftware/steam-for-linux/issues/3340) it's worth signing up with github if not already as this is where alot of open source projects are moving too, keep an eye on this post as it may be resloved correctly. 

Hope this helps

Joel

EDIT: Just noticed an update for steam, might be worth updating and see if that fixes it.

---

