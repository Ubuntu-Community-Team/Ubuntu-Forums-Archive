---
title: "Some newbie questions...curious about some stuff"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Senses on 2008-02-08
Hi, I've been with linux world ...quite some months, and have bit some experiences with Linux, especially Fedora. [I installed fedora on completely separate machine]...I'm interested to try out ubuntu, after heard about it from friends for quite some time.

But there's some stuff that I'm bit curious, and wanna to know something...

1. I want to install ubuntu in this machine, and it uses SATA hdds, will ubuntu detects it?

2. If it does, do I need to manually allocates free spaces, in this case, new partition for it? Is 10GB will be enough?

3. Will my machine with Radeon 9200 SE will able to run? I've heard some of my friends that they faces blank screen issues?

I think thats the questions from me now, I might have some more questions in the future.

Thanks for reading my questions, and again, thanks in advance =D.

*Still downloading ubuntu *.iso image file currently.*

---

### Post by kesman on 2008-02-08
SAta disks will be detected correctly. If you have empty space in the disk, you can either choose ubuntu to partition it for you, or do it yourself. 10gb will be enough. I think radeon 9200 will work. When you put the cd in for the first time and boot, select safe graphics mode just to be sure it works.

---

### Post by Paqman on 2008-02-08
> **Senses said:**
> 
1. I want to install ubuntu in this machine, and it uses SATA hdds, will ubuntu detects it?

Absolutely, yes.

> 
2. If it does, do I need to manually allocates free spaces, in this case, new partition for it? Is 10GB will be enough?

You can tell the installer to do this automatically, or if you feel confidant creating partitions then you can do it manually. 10GB would be ok for an Ubuntu install. Certainly the base system will fit comfortably on that, but if you added a lot of applications and data you might run into problems.

> 
3. Will my machine with Radeon 9200 SE will able to run? I've heard some of my friends that they faces blank screen issues?

You'll be fine. I used to have a 9200SE that ran Ubuntu fine. Some of the desktop effects were a bit jerky, but you can easily customise that to suit what works on your hardware.

---

### Post by hyper_ch on 2008-02-08
> **Senses said:**
> 2. If it does, do I need to manually allocates free spaces, in this case, new partition for it? Is 10GB will be enough?

If you have done partitioning before in windows and feel more confortable with it, then do it there.

Just resize the current partitions and leave those 10 gb UNPARTITIONED.

During install you have an option "use largest continousu FREE space"!

Be careful not to select "Use entire disk"!

It will then use those UNPARTITIONED 10gb and create partitions itself within it.

**NOTE: BEFORE PLAYING AROUND WITH PARTITIONS, MAKE A BACKUP!**

---

### Post by Senses on 2008-02-08
Thanks for the replies guys, definitely will give ubuntu a try =D

@ **hyper_ch**:- Thanks for the tip! Noted that down.

Oh, another question, can ubuntu reads my NTFS partitions? And also, can I access my ubuntu partition while in Windows mode?

Thanks!

---

### Post by jonabyte on 2008-02-08
You will be able to "see" your windows partition from Ubuntu, not sure about Windows "seeing" Ubuntu, never tried it.

You may want to try using the Live CD first to make sure things like the video card work to your satisfaction.

Good Luck

---

### Post by Senses on 2008-02-08
> **jonabyte said:**
> You will be able to "see" your windows partition from Ubuntu, not sure about Windows "seeing" Ubuntu, never tried it.

You may want to try using the Live CD first to make sure things like the video card work to your satisfaction.

Good Luck

Sure! Right now I'm burning the images, and gonna tests if it can run properly in this system.

Thanks for the replies guys, really appreciate it. Might wanna tests if I can read my NTFS partitions.

---

### Post by aeiah on 2008-02-08
you'll be able to see your ntfs partition (specify its mount point during installation (eg /media/windows, its easier than messing with fstab later on). there are ntfs-3g drivers that you can download that will enable you to write to your ntfs partition, but ubuntu ships with read only drivers. windows wont be able to see your linux partitions (ext2, ext3 etc), although there is software that lets you do this. the one i used to use didnt make windows treat the linux partitions like normal drives though, but they were accessable.

---

### Post by kesman on 2008-02-08
don't worry about reading your windows partitions, ubuntu 7.10 did a shortcut on my desktop to browse the contents of the windows partition and it works great. Also, there's tools that you can use in windows to access your ubuntu files. But play with the liveCD first for a while, it gives you a good image of the system.

---

### Post by Senses on 2008-02-08
Yes, it can reads my ntfs partitions flawlessly, and also there's no problem with the display, yay =D...

Right now I'm using the LIVE CD to navigate through the system before I install it afterward!

Anyway, I've 15GB free spaces [non-partitioned yet] allocated for the installations, so what I do next is just point to the INSTALL icon @ the desktop and choose the unallocated free spaces to install?

And it will auto detect my Windows as boot options too, right?

Thanks for the replies everyone =D.

---

### Post by seventhc on 2008-02-08
Yes, click on the icon that says *Install* then during the *install* you will choose to use '*largest continuous free space*' then when it finishes and you reboot you should have a menu to choose either windows :( or Ubuntu. :)

---

### Post by Senses on 2008-02-08
Ok, sure, thanks!

---

### Post by Senses on 2008-02-08
Bit curious about this part:-
[COLOR="Magenta"]**- Guided - Use Largest continuous free space**[/COLOR]

When on the next step [after I've imported some of my settings such as firefox's settings], I come across this part, where I've highlighted:-
[[IMG]http://img172.imageshack.us/img172/1310/screenshotxi4.th.png[/IMG]](http://img172.imageshack.us/my.php?image=screenshotxi4.png)

Does this mean it will uses the free unallocated space, or?

Thanks in advance!

---

### Post by Senses on 2008-02-08
> **Senses said:**
> Bit curious about this part:-
[COLOR="Magenta"]**- Guided - Use Largest continuous free space**[/COLOR]

When on the next step [after I've imported some of my settings such as firefox's settings], I come across this part, where I've highlighted:-
[[IMG]http://img172.imageshack.us/img172/1310/screenshotxi4.th.png[/IMG]](http://img172.imageshack.us/my.php?image=screenshotxi4.png)

Does this mean it will uses the free unallocated space, or?

Thanks in advance!

/requoted again, due to spammer above :(

---

### Post by seventhc on 2008-02-08
That screenshot looks normal, as long as you chose [COLOR=Magenta][COLOR=DarkSlateBlue]**Guided - Use Largest continuous free space**[/COLOR][COLOR=Black], then you shouldn't have a problem. It obviously detected your windows since it was able to import the settings, so you should be fine. :)[/COLOR][/COLOR]

---

### Post by Senses on 2008-02-08
@ **seventhc**:- Thanks for your reply.

Only the warning part makes me feel bit uneasy :x

---

### Post by seventhc on 2008-02-08
you're welcome,
 it isn't really a warning so much, it's just saying..."hey, look what I'm about to do' :D

---

### Post by Senses on 2008-02-08
Sure, will do!

Now its still installing necessary files, can't wait to see it in action :p...

Any links of software, or something to read, especially for media players and such?

Thanks!

---

### Post by hyper_ch on 2008-02-08
[http://www.psychocats.net](http://www.psychocats.net)

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

that should answer a lot of questions.

---

### Post by seventhc on 2008-02-08
Once it's installed you can go to *Applications>Add/Remove* and you will find tons of software to choose from. You can also find a bunch in [I]System>Administration>Synaptic Package Manager
[/I]and you might also want to have a look at [http://getdeb.net/](http://getdeb.net/)
There are a lot of media players available, but one you should definitely install is VLC.

---

### Post by Senses on 2008-02-08
Thanks!

It's installed flawlessly, now I'm still downloading the updates, thanks everyone!

---

