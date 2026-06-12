---
title: "Swap is not used"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-11-16
Hello.

I'm not sure whether this is normal or only me having this problem. I have 512 MB of RAM and 1GB of swap memory. But the swap memory has never been used more than 50 MB. Even thought 70% of my RAM is being used, only about 20 MB of RAM is used. I heard the swap memory size should be double than the RAM but I think it's just a waste if it is not used. Oh, I'm running Dapper.

---

### Post by kerry_s on 2006-11-16
I've got a gig of ram & have never seen my 1 gig of swap used for normal use. I have plenty of space so i just leave it, even windows will set space for swap even tough its not needed. With 512 you should keep it just in case.

---

### Post by TheTux on 2006-11-16
Thanks for your reply.

So I guess it's normal for Linux, not just Ubuntu. Can I configure the swap space so it is always used, not matter how much RAM is being used? Or is it better if it is not used until the system run out of RAM. Well I'm from Windows and that's why I think it it's weird when the swap is not used.

---

### Post by skwillz on 2006-11-16
AFAIK, you do not want to use your swap space unless necessary since it runs off a hard disk, so it's much slower than actual RAM.

---

### Post by SZorg on 2006-11-16
I don't know why, but I gave Linux a 1 gig swap. 2 gigs of ram (thanks to windoze's ability to eat the stuff.). Unecessary.

(With 660GB total HDD space, though..)


Never seen it used at all.

---

### Post by mush on 2006-11-16
Wasn't the old standard for swaps double your ram? I thought that used to be the standard until such larger amounts of ram were available, so it may not still apply to modern applications.

Also, its been my understanding that the swap space in linux is just about the same as virtual memory in microsoft's...using it only when all ram is used up. is that right?

---

### Post by marx2k on 2006-11-17
On one of my computers I have 1GB of RAM and 5 hard drives at 200GB each in it.

When installing Ubuntu, I dedicated 1GB of HD space to swap.

I see now that that was pointless but hey... better to have it and not need it... :)

I wonder if Linux sees multiple hard drives on separate buses having swap and can somehow utilize them efficiently?

Even on the laptop Im on now, with 756MB of RAM, I havent seen the swap used at all.  You definitely want all of your RAM used up before beginning to use swap.  XP seems to use swap even if all RAM isnt used up.  Looking to my right, the XP box with 1GB of RAM shows:

Total 1048048
Available 185320
System Cache 499412

Of course, im reading this at separate times and it changes around but the general idea is there.

Also what I've noticed is that linux RAM levels seem to be a lot more stedy than XP when the desktop is just sitting there.  Like, in XP the desktop can be sitting there and the RAM and CPU usage will jump all around.  In Linux, the CPU usage jumps a bit too but nothing like in XP.

---

### Post by Delkster on 2006-11-17
> **TheTux said:**
> Can I configure the swap space so it is always used, not matter how much RAM is being used? Or is it better if it is not used until the system run out of RAM. Well I'm from Windows and that's why I think it it's weird when the swap is not used.

It is possible to configure Linux so that it's more prone to swap stuff out onto the disk, but I believe the defaults are generally quite fine. (There's no fancy graphical interface for configuring that but it's possible)

---

### Post by kerry_s on 2006-11-17
> **TheTux said:**
> Thanks for your reply.

So I guess it's normal for Linux, not just Ubuntu. Can I configure the swap space so it is always used, not matter how much RAM is being used? Or is it better if it is not used until the system run out of RAM. Well I'm from Windows and that's why I think it it's weird when the swap is not used.

Yes,it can be changed. The file is called swappiness & is usually set to 60. It's a common tweak to lower it to 10 to keep the working applications in ram longer so there faster, the oldest apps would be pushed off to swap when the ram starts to get full & more room is needed for the current working apps. If you want to play with it, in terminal->

gksu gedit /proc/sys/vm/swappiness

I run a minimal system so i use very little resources from the get go->

---

### Post by anaconda on 2006-11-17
It is good to have some swap available, even if it isn't needed very often.

The reason is that if you run out of RAM then OOM -killer starts to  randomly kill your running aplications! IF you have enough swap then the OOM-killer doesn't do anything.

Another thing where swap is needed is with laptops if you want to use the suspend -feature (or was it hibernate?), where RAM is copied to swap, and machine shuts down.

But I like swap files more than swap partitions. Their size is easier to change as needed..

---

### Post by az on 2006-11-17
> **anaconda said:**
> 
Another thing where swap is needed is with laptops if you want to use the suspend -feature (or was it hibernate?), where RAM is copied to swap, and machine shuts down.

But I like swap files more than swap partitions. Their size is easier to change as needed..

But you cannot hibernate onto a swap file - it must be a seperate partition.

Also, any machine can hibernate.  Not just laptops.  You may want to hibernate (suspend to disk) your desktop and cut down on boot time.

---

### Post by TheTux on 2006-11-17
Linux can use swap file? I thought it can't. But swap file gets the hard disk fragmented more easily right? Correct me if I'm wrong. Anyway, I can't use both the suspend and hibernate features.

---

### Post by anaconda on 2006-11-17
> But you cannot hibernate onto a swap file - it must be a seperate partition.

I didn't know that.

> But swap file gets the hard disk fragmented more easily right? Correct me if I'm wrong.

Yep. you are wrong. The swap file is fixed, so you create it once, and it is mounted and used just as a partition. (same way than you can mount cd images)
So whatever happens inside the swap-file doesnt affect the other files or disk fragmentation at all..

---

### Post by Prodrive on 2006-12-06
When I was installing Linux, I did not have the proper space allocated to create a swap partition at the time, so I just did not create one and installed anyways because I was eager to start working with and learning Linux.  I told myself I could go back later and configure the swap partition.

I have now created a partition I intend to use for the swap, but I do not know of any way to configure and use it as my swap partition.  Is this possible to do after Linux has been installed or can it only be done when installing?


Thanks!

Edit: I did a search for swap and found this thread and did not even think to check the date on it before posting...

---

### Post by Delkster on 2006-12-06
> **Prodrive said:**
> I have now created a partition I intend to use for the swap, but I do not know of any way to configure and use it as my swap partition.  Is this possible to do after Linux has been installed or can it only be done when installing?

This requires a bit of command-line magic.

I assume that you've created the partition so that it's of type Linux swap. If you haven't, and you're having trouble doing that, please ask about that before continuing.

The *mkswap* command prepares an file or partition for use as a swap area:
```
sudo mkswap <partition>
```
Replace <partition> with the device node of your swap partition. For me it's /dev/hda5 but on your system it's probably different. Be careful to target the correct partition!

You can then enable the swap area with the *swapon* command:
```
sudo swapon <partition>
```
EDIT: I forgot the *sudo* part earlier. I fixed it now. The command requires root privileges.

You can check if the swap area is in use by using the *free* command or any system monitor to check the amount of usable swap.

However, this only applies to the current session and doesn't make your system use the swap partition automatically on the next boot. For that you'll need to add it to /etc/fstab. As an example, my line for the swap partition in /etc/fstab is as follows:
```
UUID=b9fed8c9-4f69-4f54-a5f7-1585f3d6bce3 none swap sw 0 0
```
It uses the UUID of the device rather than an old-fashioned device node (the Ubuntu Dapper -> Edgy upgrade did that), but if you don't know the UUID of the partition, you can just use the traditional device node instead. In my case that would be /dev/hda5, so the line would be:
```
/dev/hda5 none swap sw 0 0
```

After /etc/fstab has been saved, the system should use the swap partition on next boot.

---

### Post by Prodrive on 2006-12-06
Wonderful!  Thanks so much!  That worked just fine!  Is there like an encyclopedia of all of the linux commands and properties?

---

