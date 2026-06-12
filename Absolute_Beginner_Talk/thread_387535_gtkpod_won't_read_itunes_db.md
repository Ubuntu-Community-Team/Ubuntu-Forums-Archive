---
title: "gtkpod won't read itunes db"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by squig on 2007-03-18
Question... 

I've followed the directions here [http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu) 
get gtkpod set up.

iPod mounts automatically, shows up on desktop as AMY GROSHEK, and mounts as/in /media/ipod

When I open gtkpod and select read iTunes DB

I get an Warning window, which reads: The following has occurred:

Then the box is blank!? 

I have backtracked through the directions to make sure I didn't flub anything. Reinstalled gtkpod, mounted and unmounted ipod several times, and ran the script suggested at the end of the link I supplied above: 
```
sudo dosfsck -a /dev/sdc2
```

Except that I changed it to
```
sudo dosfsck -a /dev/sdb2
```

because that's what mine shows up as in /etc/mtab 

I'm not sure what else to try at this point. If I have to manually import all mp3 files and start over, what is the smoothest way to accomplish this? Are there any shortcuts? 

Many thanks for any assistance!
~A

---

### Post by Kobalt on 2007-03-18
You need to go in the configuration of gtkpod and set up manually the name of your iPod for the mount point, that should look like something like this : > /media/AMY GROSHEK
If you gave a name to your iPod under Win or OS X it will be used as a label for the mount point.

---

### Post by squig on 2007-03-18
Okay, did that. But now... gtkpod won't start up at all...

```
amy@amy-laptop:~$ sudo gtkpod
*** glibc detected *** realloc(): invalid next size: 0x0853b150 ***
Aborted
amy@amy-laptop:~$

```

I have tried to uninstall and reinstall gtkpod... 

any hints? 

~A

---

