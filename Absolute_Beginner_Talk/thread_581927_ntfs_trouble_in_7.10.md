---
title: "ntfs trouble in 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by wrongopinions on 2007-10-19
Hey all,
   There are many threads on ntfs read/write support in ubuntu. I had it set up fine with ntfs-3g in feisty...
    Now, in 7.10, it has "native ntfs read write support". First off, where and how do you use this.... I installed ntfs-config and doesn't see all my ntfs drives nor does it mount the ones it does see. Ubuntu itself sees my ntfs drives (recognizes the partitions and names) within the file system... just refuses to mount them. 
  I am certainly not the most experienced, so I apologize if this post offends some. I could not find a correct answer (perhaps because 7.10 is so new). I am under the impression that Gutsy can "just see and mount" ntfs... but I havent a clue where...
..maybe some config file?

Thanks for your help, If you need more info from me, just ask.

---

### Post by benerivo on 2007-10-19
Partitions that are not already mounted might appear in nautilus. Type ```
computer:/
```in to the nautilus address bar, and see what drive icons appear. From here, i can mount my windows partition, with a right click, and have write permissions as a normal user.

---

### Post by wrongopinions on 2007-10-19
ok, well I had gutsy on an external hard drive...but I just set up up gutsy as a dual boot with xp on my internal hard drive.... it mounts the windows side ntfs just fine (thats fixed now)...BUT now it does not want to mount an ntfs partition on an external hard drive.

any ideas? (nautilus has always "seen" it, just wont mount it and give me access to it...)

thanks,
paul

---

### Post by dvarsam on 2007-10-20
> **wrongopinions said:**
> ok, well I had gutsy on an external hard drive...but I just set up up gutsy as a dual boot with xp on my internal hard drive.... it mounts the windows side ntfs just fine (thats fixed now)...BUT now it does not want to mount an ntfs partition on an external hard drive.

any ideas? (nautilus has always "seen" it, just wont mount it and give me access to it...)

thanks,
paul

Hi!
I just realized that I have the exact same problem like you!!!
On my HD1, I have 2 Partitions:

Partition 1 = Windows XP SP2 OS
Partition 2 = Ubuntu v7.10

Ubuntu auto-magically mounted that Partition just fine!

I then decided to add another HD (an external one) just like you :)
I could NOT mount that Partition at all, Gnome Crashed (a popup warning showed up), had to cold-reboot, and now I can't see any NTFS Partition icon at all, NOT even the HD1\Partition1 icon... ??? :(

I tried to mount the External Drive manually, and got ERROR...
See this post: [http://ubuntuforums.org/showthread.php?t=582519](http://ubuntuforums.org/showthread.php?t=582519)

Thanks.

---

### Post by wrongopinions on 2007-10-20
yep, exactly the same

-p

---

### Post by dvarsam on 2007-10-20
> **wrongopinions said:**
> yep, exactly the same

-p

Oh my Goodness, this version of Ubuntu seems to have the most bugs when compared to previous versions...

Another Example:
Right-click on your Top Panel & select "Add to Panel..."
Scroll down to find the "Disk Mounter", select it & click on the button named "Add".

Conclusion:
It does NOT get added to the Top Panel... :)

3 Serious Bugs till now & counting:

1. Can't mount NTFS Partitions
2. Can't add stuff to the Top Panel
3. Gnome crashes...

Thanks.

P.S. > Is this worse when compared to M$ or what?

---

### Post by wrongopinions on 2007-10-20
my disk mounter adds to the panel just fine actually....

...still cant mount the external ntfs partition

---

### Post by wrongopinions on 2007-10-20
SOLUTION 

force mount it by
```
mount -t ntfs-3g /dev/sdb1 /media/*'DRIVENAME'* -o force
```

it works for me...

---

### Post by ModeZt on 2007-10-21
maybe you hibernated your windows. try to boot in windows and shut it down instead of hibernating.

---

### Post by zeronothing on 2007-10-22
hello everyone,

For those that cannot seem to mount the ntfs partitions I would suggest installing the newest ntfs-3g from their website. I was having the same problems with an external hard drive, but I uninstalled the current ntfs-3g package using synaptic. Then I went to the ntfs-3g website, compiled the source and installed it, mounted the external hard drive with no problem. To compiled the source just make sure you have the build-essential, fuse-source, and libfuse-dev packaged installed first. The readme that comes with it is very easy to understand.  just to make it clear, the newest version of ntfs-3g was not included in Gutsy.

---

### Post by Axm3000 on 2007-10-22
> **wrongopinions said:**
> SOLUTION 

force mount it by
```
mount -t ntfs-3g /dev/sdb1 /media/*'DRIVENAME'* -o force
```

it works for me...

Does mounting with the -o force option entail any risks, or is it perfectly safe.  I'm experiencing similar problems, with my external USB drive, and I'd hate to risk losing all my data on it.

---

### Post by spinetingler on 2007-10-22
> **zeronothing said:**
> hello everyone,

 To compiled the source just make sure you have the build-essential, fuse-source, and libfuse-dev packaged installed first. The readme that comes with it is very easy to understand.  just to make it clear, the newest version of ntfs-3g was not included in Gutsy.

As a new user I have a concern about using this procedure. Will this break something else? and Are there dependencies I should be aware of?

---

### Post by zeronothing on 2007-10-22
spinetingler,

As a new user this can seem tricky but it's really not. if you uninstall ntfs-3g using synaptic it will only remove ntfs-3g unless you have ntfs-config installed. if this is the case when you uninstall ntfs-3g it will also uninstall ntfs-config because ntfs-config depends on ntfs-3g. That is the only dependencies issue when uninstalling ntfs-3g. As long as you have build-essential, fuse-source, and libfuse-dev install, compiling the newest ntfs-3g should go pretty smoothly. when I compiled it I ran into a Warning mentioning fuse was not compiled with a certain option enable. just ignore the message and proceed and it should work just fine. when compiling the source you will know if its going to work (most of the time) if the source compiles with no errors. when your compiling source remember you are just building not installing, you install after the building. so when you execute "make install" that is when you actually add files, libs, etc. to your system. if you need anymore help don't hesitate to ask.

---

### Post by wrongopinions on 2007-10-22
I forgot to mention this earlier...
while trouble shooting the problem, I discovered that the issue lie with windows. For anyone that is dual booting ubuntu and windows, you may encounter similar issues. 
  If I did not shut down or restart properly from windows (that is I used the system off button instead), ubuntu would have issue trying to mount that partition from the internal drive until I correctly shut down in windows.
  Similarly for my external hard drive, if it was not "properly disconnected" while in windows, ubuntu would refuse to easily mount it. 
   Of course there is no damage to either the internal or external drive (in most cases...) from actions like this. If you do not feel like booting back into windows to properly restart/shutdown or disconnect external devices then use the above mentioned force mount.

again, I am far from experienced, so anyone that finds issue with this, please correct me

---

### Post by User101 on 2007-10-25
> **ModeZt said:**
> maybe you hibernated your windows. try to boot in windows and shut it down instead of hibernating.

Thanks for the tip. Unfortunately, this on its own did not seem to help. I did manage to get my NTFS partition back into working shape in Gutsy, though -- please see my post at  [http://ubuntuforums.org/showpost.php?p=3633724&postcount=2](http://ubuntuforums.org/showpost.php?p=3633724&postcount=2) for the details.

---

