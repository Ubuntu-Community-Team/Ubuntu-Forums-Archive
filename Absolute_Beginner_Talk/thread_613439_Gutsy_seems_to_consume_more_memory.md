---
title: "Gutsy seems to consume more memory"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-11-14
In Feisty (just after starting or with some minor applications opened) when I opened terminal and typed top, it showed that around 450MB of RAM is being used; but in case of Gutsy it starts with more than 550MB. My memory is 643MB, so I do not have much room left after I open couple of major programs like firefox or evolution. Why is the difference? Is there a way out to hold the memory flow?

---

### Post by Inxsible on 2007-11-14
Are you subtracting the "cached" or "buffered" space from the total used?

---

### Post by sauravbhaumik on 2007-11-14
> **Inxsible said:**
> Are you subtracting the "cached" or "buffered" space from the total used?

No, perhaps I didn't; I give you the results verbatim:
```
top - 09:51:04 up 39 min,  2 users,  load average: 0.52, 0.49, 0.40
Tasks: 105 total,   3 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.0%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    643764k total,   636536k used,     7228k free,    21100k buffers
Swap:  1429736k total,    34736k used,  1395000k free,   258704k cached

```

---

### Post by Inxsible on 2007-11-14
So you have a total of about 512 MB RAM.

Remember the buffered is where it keeps all the applications it thinks that you might use. This is a good thing. Empty RAM is actually wastage !

So if you have them buffered, they can be accessed quicker.

---

### Post by sauravbhaumik on 2007-11-14
> **Inxsible said:**
> So you have a total of about 512 MB RAM.

I don't understand how you calculated 512MB. Please explain.

And why does the Swap remain almost unused? I like to use some Swap for my activities, can I do that?

---

### Post by Inxsible on 2007-11-14
> **sauravbhaumik said:**
> I don't understand how you calculated 512MB. Please explain.

And why does the Swap remain almost unused? I like to use some Swap for my activities, can I do that?you cannot dictate the usage of swap. The OS does it automatically if and when required.

---

### Post by sauravbhaumik on 2007-11-15
> **Inxsible said:**
> So you have a total of about 512 MB RAM.


Please explain how you got 512MB here. It is written that "Mem:643764k total" and even if you subtract the buffered memoru, 512MB doesn't come. Please explain.

---

### Post by insane_alien on 2007-11-15
try using 'free -m' that'll show how much is actually used without the cache which always expands to fill all RAM i've got 7GB of cache sitting in my RAM just now.

---

### Post by smartbei on 2007-11-15
Do you have visual effects (either normal or best) on? Visual effects (seen in top as comiz.real) will take up after several hours over 330mb of ram by itself on my computer. Workaround is to remove visual effects :D. You can put them back immediately, and the memory usage will be normal but it will start climbing.

---

### Post by insane_alien on 2007-11-15
> **smartbei said:**
> Do you have visual effects (either normal or best) on? Visual effects (seen in top as comiz.real) will take up after several hours over 330mb of ram by itself on my computer. Workaround is to remove visual effects :D. You can put them back immediately, and the memory usage will be normal but it will start climbing.

you sure, i haven't seen this at all. they've been on for weeks and they're at around 20MB just now, well, the were when i left and i can't ssh into my box from the internet just now.

---

### Post by sauravbhaumik on 2007-11-15
> **smartbei said:**
> Do you have visual effects (either normal or best) on?
No I have disabled the visual effects, I knew that it would contribute to the problem, so I didn't give it a room.

---

### Post by sauravbhaumik on 2007-11-15
> **insane_alien said:**
> try using 'free -m' that'll show how much is actually used without the cache which always expands to fill all RAM i've got 7GB of cache sitting in my RAM just now.

Here is the output:
```
saurav@saurav:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           628        583         45          0         11        200
-/+ buffers/cache:        371        257
Swap:         1396         33       1362
saurav@saurav:~$ 


```

---

### Post by jw5801 on 2007-11-15
> **sauravbhaumik said:**
> ...
And why does the Swap remain almost unused? I like to use some Swap for my activities, can I do that?

Actually you can configure this. Open up /etc/sysctl.conf ```
gksu gedit /etc/sysctl.conf
```and append```
vm.swappiness=*a-number*
```where *a-number* is an integer from 0-100. 100 meaning the system will greatly favour swap over RAM and 0 meaning the system will attempt to use RAM over swap. I find it better to have lower swappiness, but it depends how you use your system I guess. See [here](http://kerneltrap.org/node/1044) or [here](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43) for more info. You'll have to reboot for this to take effect.

---

### Post by louieb on 2007-11-15
New releases of and OS using more memory :KS of course they do. I had Ubuntu 5.04 running quite happily on a P2 400mHz 384MB memory. Gutsy need more than that. Oh had it installed and working but its kinda slow.

---

### Post by jw5801 on 2007-11-15
> **louieb said:**
> New releases of and OS using more memory :KS of course they do. I had Ubuntu 5.04 running quite happily on a P2 400mHz 384MB memory. Gutsy need more than that. Oh had it installed and working but its kinda slow.

The neat thing about Linux though, is that you can cut down on that (by using fluxbox or some other minimalistic interface). You'll probably find gutsy using a bit more RAM as it's using compiz as the default window-manager, and compiz is a bit more resource hungry that metacity (the old default) although it is alot flashier because of this.

---

### Post by SunnyRabbiera on 2007-11-15
> **sauravbhaumik said:**
> 
And why does the Swap remain almost unused? I like to use some Swap for my activities, can I do that?

well there are two possibilities, 1: you have a good amount of memory so having a swap will only take up so much room
or two (and this is a bad one): you dont have a swap partition...
did you format ubuntu the normal way or did you do a custom?
If you forgot to designate a swap partition, then the jig is up especially if you dont have a load of memory.

---

### Post by jw5801 on 2007-11-15
If you want to check for a swap partition and whether you're set up to use it post the outputs of the following two commands:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Inxsible on 2007-11-15
you might wanna read this link which gives good information about the top and free commands and why they report very less free memory
[U]
[Linux Memory Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management")

[/U]

---

### Post by por100pre1 on 2007-11-15
> **sauravbhaumik said:**
> Is there a way out to hold the memory flow?

You can try disabling Tracker startup if you don't use it. You can do so in Gnome Sessions:

```
gnome-session-properties
```

---

### Post by sauravbhaumik on 2007-11-16
> **SunnyRabbiera said:**
> well there are two possibilities, 1: you have a good amount of memory so having a swap will only take up so much room
or two (and this is a bad one): you dont have a swap partition...
did you format ubuntu the normal way or did you do a custom?
If you forgot to designate a swap partition, then the jig is up especially if you dont have a load of memory.

No I attached two swap partitions (actually I reformatted only one of them, 732MB in size); and I don't know why my system seems to prefer all of RAM to a stable share of RAM and swap.

---

### Post by rsambuca on 2007-11-16
> **sauravbhaumik said:**
> No I attached two swap partitions (actually I reformatted only one of them, 732MB in size); and I don't know why my system seems to prefer all of RAM to a stable share of RAM and swap.

You actually don't want the swap to be used except as a last resort.  It is designed to use RAM preferentially.

EDIT:  In looking back at the output of your 'free' command, you have 200MB of RAM available still (it is being used as a cache, but can be used for necessary stuff if you open another program).

Basically, your rig is working the way it is supposed to.

---

### Post by sauravbhaumik on 2007-11-16
> **jw5801 said:**
> If you want to check for a swap partition and whether you're set up to use it post the outputs of the following two commands:
```
sudo fdisk -l
cat /etc/fstab
```

fdisk -l shows that /dev/sda7 and /dev/sdb3 are swap partitions, and here is the /etc/fstab, in which I thought I could discern two swap partitions that I mentioned:
```
saurav@saurav:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=2b537f05-a786-443f-8dfa-0033942ec93b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=304C-19F9  /media/sda1     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=10DC-2B4D  /media/sda5     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=B815-6D93  /media/sda6     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=288dc04c-4f80-46dc-940e-87ae4eeceeca /media/sda8     ext3    defaults        0       2
# /dev/sdb1
UUID=9270A3B170A39A8D /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=c9a98b0a-81a7-48b3-a3a8-fd87ca96c432 /media/sdb2     ext3    defaults        0       2
# /dev/sda7
UUID=2764139c-3a90-440a-a796-13a70c870ba7 none            swap    sw              0       0
# /dev/sdb3
UUID=2051a46c-6bc5-419f-9298-c9374d5b42ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by sauravbhaumik on 2007-11-16
> **rsambuca said:**
> Basically, your rig is working the way it is supposed to.
Okay, then there was no problem. But I am rather sure that Gutsy is working slower than Feisty. I am in search of the cause, and I thought I should check whether the difference in memory usage is a one. 

Better, I should be more elaborate:
1. There is a problem in scrolling pages where some large pictures are there;
2. internet is a bit slower;
3. hard drive partitions (other than the one in which this OS is there) are not opening as fast as they did in Feisty;
4. the terminal opens quite slowly.

What might be the causes? Isn't the difference in memory use a worth noting point here?

---

### Post by jw5801 on 2007-11-16
> **sauravbhaumik said:**
> Okay, then there was no problem. But I am rather sure that Gutsy is working slower than Feisty. I am in search of the cause, and I thought I should check whether the difference in memory usage is a one. 

Better, I should be more elaborate:
1. There is a problem in scrolling pages where some large pictures are there;
2. internet is a bit slower;
3. hard drive partitions (other than the one in which this OS is there) are not opening as fast as they did in Feisty;
4. the terminal opens quite slowly.

What might be the causes? Isn't the difference in memory use a worth noting point here?

You are correct about you swap partitions and them being in use. If you think it's a lack of available RAM that's causing the slowness here, then have a play around with the swappiness (refer to my earlier post) and see if it makes a difference. As referenced [here](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43), you can run ```
sudo sysctl vm.swappiness=100
```to tell your system to use more cache than RAM. The number you set can be anywhere between 0 and 100. I have 1GB of RAM and find performance to be much better with a value of 0 (prefer RAM over cache), but have a play around and see if anything makes a substantial difference! If you find a value other than the default 60 that gives you better performance, then you can append vm.swappiness=*a* to /etc/sysctl, where *a* is this value.

---

### Post by sauravbhaumik on 2007-11-16
> **jw5801 said:**
> You are correct about you swap partitions and them being in use. If you think it's a lack of available RAM that's causing the slowness here, then have a play around with the swappiness (refer to my earlier post) and see if it makes a difference. As referenced [here](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43), you can run ```
sudo sysctl vm.swappiness=100
```to tell your system to use more cache than RAM. The number you set can be anywhere between 0 and 100. I have 1GB of RAM and find performance to be much better with a value of 0 (prefer RAM over cache), but have a play around and see if anything makes a substantial difference! If you find a value other than the default 60 that gives you better performance, then you can append vm.swappiness=*a* to /etc/sysctl, where *a* is this value.

Only disabling trackerd seemed to work a little; now at the starting point the output of top shows that 458MB of RAM is used; that is a good sign. But the slowness problems remained. And I put a value of 80 after the vm.swappiness, and ensured after reboot that there is a number 80 visible on the icon of the file /proc/sys/vm/swappiness, but no increase in swap use! Presently my swap is totally free, without use.

---

### Post by rsambuca on 2007-11-16
> **sauravbhaumik said:**
> Only disabling trackerd seemed to work a little; now at the starting point the output of top shows that 458MB of RAM is used; that is a good sign. But the slowness problems remained. And I put a value of 80 after the vm.swappiness, and ensured after reboot that there is a number 80 visible on the icon of the file /proc/sys/vm/swappiness, but no increase in swap use! **Presently my swap is totally free, without use.**

That is what you want.  Swap is really, really, slow.

---

### Post by Inxsible on 2007-11-16
> **sauravbhaumik said:**
> Only disabling trackerd seemed to work a little; now at the starting point the output of top shows that 458MB of RAM is used; that is a good sign. But the slowness problems remained. And I put a value of 80 after the vm.swappiness, and ensured after reboot that there is a number 80 visible on the icon of the file /proc/sys/vm/swappiness, but no increase in swap use! Presently my swap is totally free, without use.

Consider this: Swap is actually a hard drive, RAM is flash memory. Flash memory is much faster than hard drive. You definitely want to use RAM before you start using swap as a last resort.

So having a maxxed out RAM ans less of swap is a good thing.

Gutsy does have a few pre-installed apps, like trackerd (desktop search applet) that consume memory. You might also want to look at the system monitor or the top command, as was previously suggested and find out which application is using the most memory and try and triage from there.

---

