---
title: "Deleting everything off my ipod"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Evegan on 2007-11-21
Something happened a few weeks ago with the ipod. After I ejected it all the titles and artist and genres were all kinds of mixed up. Songs would come up as Alternative/Alternative/Alternative without an artist or album name. Very odd. Thing is, all this songs in my music folder are still correct. So what I've done is delete Banshee, which is what I was using to manage the ipod, and now I'd like to clear the ipod and reinstall everything.  

Any idea how I would do this without access to a windows or mac? The ipod is a 5th gen 30gig if that matters.

Thanks for the help

Evan

---

### Post by daimaru on 2007-11-21
first find out where your ipod is mounted
should be under /media/ipod  or something like that.
then you could delete everything on the ipod by changing into the /ipod directory and executing the remove command using recursive option. but I really don't want to give you this advice unless you are sure that you are in the right directory. I don't have an ipod so i don't know if it shows up just like a usb or external hardisk does under /media ...

---

### Post by tdrusk on 2007-11-21
> **daimaru said:**
> first find out where your ipod is mounted
should be under /media/ipod  or something like that.
then you could delete everything on the ipod by changing into the /ipod directory and executing the remove command using recursive option. but I really don't want to give you this advice unless you are sure that you are in the right directory. I don't have an ipod so i don't know if it shows up just like a usb or external hardisk does under /media ...

no no no no no

if you delete that your ipod won't start.

use rhythmbox or bansheee and delete all the files that it shows. Now resync.

---

### Post by daimaru on 2007-11-21
> **tdrusk said:**
> no no no no no

if you delete that your ipod won't start.

use rhythmbox or bansheee and delete all the files that it shows. Now resync.

as i said i don't have an ipod so i don't know where the music is stored. [COLOR="Red"]Listen to drusk and don't delete anything in your root ipod directory[/COLOR] since i guess now that there are more folders in your ipod :)

---

### Post by tdrusk on 2007-11-21
> **daimaru said:**
> as i said i don't have an ipod so i don't know where the music is stored. [COLOR="Red"]Listen to drusk and don't delete anything in your root ipod directory[/COLOR] since i guess now that there are more folders in your ipod :)
yeah if you delete the ipod_control folder you are stuck because it boots the firmware off that.

---

### Post by Evegan on 2007-11-21
Thanks, that was much easier than I had expected. I usually assume that doing everything on the linux takes more steps. 

Thanks for the help

Evan

---

