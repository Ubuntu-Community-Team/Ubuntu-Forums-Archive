---
title: "Help with installing Ubuntu"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-17
I am currently on the Live CD 7.10. I was told I do not need to reformat my HDD to install Ubuntu, that is it why I wanted to be careful with this. 

Here is an image of available space I have on my HDD:

[IMG]http://i30.tinypic.com/28umu4k.png[/IMG]

When I am going through the installation process this is what shows up:

[IMG]http://i28.tinypic.com/2mi2izb.png[/IMG]

And I am not sure what to do, I do not want it to reformat my drive since I can not delete anything on it. Also I did not move that bar at all, that is what it was at. So if anyone knows please help me. 


Also is there any way to access my files on my HDD that were on windows through Ubuntu? I needed a few files and do not like switching back and forth.

---

### Post by sb12 on 2008-02-17
where it says resize that will be the size of your ubuntu partiton, the rest will be used for windows.  and yes you can access windows files frm ubuntu with ntfs-3g

---

### Post by aysiu on 2008-02-17
You do not need to reformat the *entire* drive, but you will need to resize one of those current Windows partitions to make room for a new Linux partition.

Resizing, 99% of the time, is non-destructive, but if your data is important to you, **back it up**. There can be no guarantees that resizing will leave your Windows installation intact, even if it *probably* will.

**Back up your data**.

---

### Post by Tyke91 on 2008-02-17
in this case you will probably have to delete some of your windows data. Dual booting is possible on such a small hard drive (I did it successfully on my friends laptop) but if you try to do it with this current setup, you will ruin both operating systems. 

ubuntu will want around 10 gigs to function properly, and windows will want at least 2 gigs of free space to play with (no free space will slow you to a crawl with both operating systems)

my advice is to either stick with windows on that computer, or save all your data, install ubuntu on the entire hard drive, and then transfer your data to your new ubuntu install.

---

### Post by erfahren on 2008-02-17
you have a pretty full disk there. how much did you want to allocate for Ubuntu? 

If you have critical data it would be a good idea to back it up first. shrinking patitions with the partitioner is pretty safe - but there are no guarantees. 

Windows needs some free space as well for the defrag to work. 

you should think about moving some stuff off there first.

Edit - others posted while I was, basically saying the same thing (I'm a little slow sometimes. - lol).

---

### Post by ImThatNerd on 2008-02-17
Yeah I know I don't have much to work with, but I am going to go through it later and delete a ton of stuff. I can probably get 15GB of free space if I really go through and uninstall programs I don't use and movies I don't watch. But with what I have now when I try to install I get this:

[IMG]http://i32.tinypic.com/345dlok.png[/IMG]

And when I click OK I get this:

[IMG]http://i31.tinypic.com/95viox.png[/IMG]


I suppose this is due to not having enough space, I didn't think I needed 10GB, but I will make sure I have more than that when I try installing later.

---

### Post by JohnnyBoy022 on 2008-02-17
You can't resize that becuase your windows partition is already taking up about 30 gigs of space. I'm not an expert but I would say use the first guided option and slide the bar to about 10 gigs. **Back up before you do anything.**

---

### Post by ImThatNerd on 2008-02-17
Sorry for the double post, but I was just curious what do you guys suggest for my first Linux? I am done with the slugginess of Windows on my PC and even running this CD it seems so fast. I plan on using Linux for programming and just firefox and other simple apps. But I hear XBuntu is good, but I am not sure what to try.

---

### Post by JohnnyBoy022 on 2008-02-17
If its your first time using Linux, Ubuntu/Kubuntu/Xubuntu is definately the way to go. It's extremely user friendly, easy to install, and the forums are great. After you get the hang of Linux then I would say just try a bunch of distros until you find the one you like. Ive tried quite a few and Ubuntu is definately my favorite. I tried Xubuntu off the live cd once and it was nice but I like GNOME better than Xfce.

---

### Post by erfahren on 2008-02-17
> **ImThatNerd said:**
> 
I suppose this is due to not having enough space, I didn't think I needed 10GB, but I will make sure I have more than that when I try installing later.
the paritioner needs to have free space to move data around, just like the defragger in Windows does.

again, move some stuff off there *before* doing it. If you don't know about [CCleaner](http://www.ccleaner.com/) already - use that as well. It removes stuff (crap) that the Windows cleanup utility doesn't (you'd be surpised!). - just run it with the default options.

Also - run the Windows "Scan Disk" (check disk) a couple times - in my experience it doesn't get everything the first time through. you can check the results of it through the [Event Viewer](http://www.housing.hawaii.edu/resources/support/chkdsk.htm) (that guide is for WinXP)

In any event - you can also defrag it with  [JKDefrag](http://www.kessels.com/JkDefrag/) - it does a better job then the Windows defragger. It's freeware, and is a standalone application (it doesn't need to be installed - just put the .exe somewhere and run it.) Exit as many running processes as you can when running it (firewall, antivirus, etc.).

---

