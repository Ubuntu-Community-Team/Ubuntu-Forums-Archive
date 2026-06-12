---
title: "display outta wack and can't see other drives"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-02-17
I got linux up and running and so far so good. D/led a bunch of codecs and stuff with automatix and what not. When I d/led the Nividia video card driver thing, my display moved about 5-10 pixels to the left. My monitor's pretty good about auto positioning but it's just bugging me. Is there any way I can fix it through linux so I don't have to readjust every time I switch from linux to windows? 

Also, I can't see my other drives. I think it's because I didn't mount it or whatever after partition. I didn't really know what it meant or did so I just put ubuntu on a 54gb partition and a 5gb swap on one of my harddrives and that's all I can see. Is there an easy way to see my other drives?

---

### Post by G Morgan on 2007-02-18
What other partitions do you have in terms of format. Fat32 is relatively painless, NTFS will require a little work but isn't difficult.

---

### Post by old_geekster on 2007-02-18
Here is a link to help you install the latest nVidia drivers (1.0-9746):

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

Once the drivers are installed, you will find "NVIDIA X Server Settings" in Applications/System Tools.  From there you can set the "Refresh Rate", which is what causes my screen to be out of line.  After I have the "Resolution" and Refresh Rate" set where I want them, then I manually align the screen.  I have a CRT monitor.

---

### Post by Yellowbelly on 2007-02-18
> **G Morgan said:**
> What other partitions do you have in terms of format. Fat32 is relatively painless, NTFS will require a little work but isn't difficult.

the other partitions are fat32 with all the stuff that I want/need. The only ntfs partition I have is for my windows with a few games and other applications. 

Thanks.

---

