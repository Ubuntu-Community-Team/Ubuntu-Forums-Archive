---
title: "Partitioned on my own.. now what?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by krunk on 2007-02-23
OK I used Gparted to partition my drive myself, because the ubuntu install couldn't do it. 

Now it looks like this

/dev/hde1 ntfs : size : 50.44gb                                                       boot
/dev/hde3 linux-swap : size : 996.23mb
/dev/hde2 ext3 : size : 5.86gb

have i done this properly? was i supposed to make the linux-swap partition myself or no?

also, when Im installing ubuntu and get to the part about partitioning, do I click on "partition this myself?" or what?

Thanks!

---

### Post by BarfBag on 2007-02-23
That looks correct to me.  Just go through the setup normally and hit "Partition Drive Manually."  I can't be any more specific about this, but there should be options there where you can tell it which partitions to use.

---

### Post by Shatrat on 2007-02-23
Well, you could use Manual Partitioning and then not change anything, on the mount points screen set the swap to the swap partition and / to the ext3 partition.
Those look decidedly small though, youll probably quickly run out of space if you install games or other large programs.

---

### Post by BarfBag on 2007-02-23
Looking back, Shatrat is right.  Ubuntu can easily run on that amount of space, but it will fill up faster then you think.

---

### Post by orb9220 on 2007-02-23
Yep that will work just use manual and assign / to the 5.83gb and make sure there are checkmarks to format / and swap only. And the ntfs should already be deselected for formating. But it always good to verify visually.

---

### Post by krunk on 2007-02-23
Ok I should re-size then, one problem.. I deleted the 5.86gb associated to ext3 so i could make it bigger, but now it is just unallocted space.. so I created another 5gb of unallocted space, hoping I could combine the 2 and have 1 ext3 partition about 10gb in size.

How can I combine these 2 partitions? or just put them back in the original hde so I can create a bigger ext3 partition. Thanks!

---

### Post by linux_kid on 2007-02-23
> Those look decidedly small though, you'll probably quickly run out of space if you install games or other large programs.
Your partitions are not too small, although if that is your hde (focus on the e, not an a) drive, you may have some free space somewhere else if needed.

EDIT: 
You don't need to change your partitioning unless you plan on using wine on lots of games.  Change them back :D

---

### Post by geezerone on 2007-02-23
You could always create a partition for your /home directory just to confuse you.

---

### Post by krunk on 2007-02-23
Ok, so now I wish I had just gone ahead with the installation when I had it right.. lol, but heres where im at.

/dev/hde1 ntfs blah blah
unallocated 5.86gb
/dev/hde3 linux-swap
unallocated 5.86gb


I have 2 unallocated spots, how do I combine these so I can make one 10+gb ext3 partition?

---

### Post by linux_kid on 2007-02-23
In Gparted, I think you drag the partition over and click make changes, I'm not exactly sure, but it wouldn't be any harder than that.

> You could always create a partition for your /home directory just to confuse you.
Now that's just mean :twisted:

---

### Post by geezerone on 2007-02-23
Delete the swap partition and then create your new 10GB partition. Then create your swap partition. Don't forget you can only have 4 primary partitions but lots of logical partitions for /home or other partitions (without low level boot sector hacking).:)

---

### Post by linux_kid on 2007-02-23
> Delete the swap partition and then create your new 10GB partition. Then create your swap partition. Don't forget you can only have 4 primary partitions but lots of logical partitions for /home or other partitions (without low level boot sector hacking).
Thats a little too confusing for the "Absolute Beginner Talk" section, don't you think?
And you can just have 3 partitions and be fine, /home doesn't need it's own partition :confused:

---

### Post by geezerone on 2007-02-23
Krunk has created his own partitions ok so deleting and creating them wouldn't be beyond him and good practice anyhow :) so no, don't think it is too much esp. with Gparted as quite straightforward.

You are correct, you don't *need* home to have its own partition but is useful in keeping local data safe.

---

### Post by linux_kid on 2007-02-23
Well... I guess not, but a seperate /home is only semi-usefull if you plan to possibly crash your system.

---

### Post by geezerone on 2007-02-23
Who *plans* for a system to crash ;)?  Prevention better than cure anyhow, and a separate partition directory is handy for upgrades to OS but it is down to personal preference I suppose.

---

### Post by krunk on 2007-02-23
thanks for all the help, i've got the drive partitioned properly and ubuntu dual booting with XP :)

I ran into a problem trying to compile a linux IRC client, I used the terminal to get the file and untar it.. but I came to an error - no c compiler in $path .. anyone know how I can get around this?

And also, my internet browser seems to be VERY slow, even compared to when it was running off the livecd, pages are taking forever to load.. it seemed faster on the live cd. I switched over to XP and everything was running at normal speed. Any suggestions on speed probs?

---

### Post by geezerone on 2007-02-23
Glad you got it sorted!

Try [www.getautomatix.com](www.getautomatix.com) for the easy way to install popular apps such as XChat IRC client. Otherwise install xchat in Synaptic (system > administration > synaptic package mgr)

Also see my signature link for installing the latest version of Firefox which should be better speed wise.

Have you enabled the repositories and performed updates?

---

### Post by linux_kid on 2007-02-23
Ok, the /home partition is simply a matter of flavor, conversation closed on that.

You may have slowed the Internet with firestarter or something along those lines, get the new firefox.

Good job on fixing your PC :popcorn:

---

