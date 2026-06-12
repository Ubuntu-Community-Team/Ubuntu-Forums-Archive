---
title: "old /home partion &amp; fresh install"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-26
I'm reading too much and understanding too little. Time to pause.

I have 7.04 all on one partion. I want to have a separate /home partition, and then instead of upgrading to 7.10, I want to do a clean install of 7.10 that will use my old 7.04 /home partition.

I understand how to create a /home partion and have it recognized under 7.04.

What I don't understand yet is how the clean install of 7.10 will import/merge/use the 7.04 /home partition.

Or does the installer actually do that at all? Is the process: do the clean install, then rm -r the created /home & use fstab to mount the old 7.04 partition in its place? (which doesn't quite make sense, because that new /home could have some new config files for apps introduced with 7.10.)

There is also of course a pre-existing swap partition. Does the installer recognize and reuse this?

---

### Post by forestpixie on 2007-10-26
I would sort out the /home partition first and make sure all works ok. Then when you do your reinstall - use manual partitioning

point it at your old /home partition but DON'T let it format obviously :) , same as swap - just tell the install where it is - and I'm fairly sure that you need to use the same user name and password as /home had before

---

### Post by stimpack on 2007-10-26
Yep manual partitioning. I do this every upgrade, retaining my existing /home. I do however use a different username on the new install and copy files over from the old user, as to avoid reusing the old desktop config files. This may be a waste of time, but I am paranoid.

---

### Post by ofb on 2007-10-26
> **forestpixie said:**
> I would sort out the /home partition first and make sure all works ok.

Definitely the plan. I didn't know you could move all that around during a fresh install, actually.

So, the installer automagically handles any necessary updating of the existing /home partion then? That was the part I didn't know, and didn't wish to leave as a mystery.

And yup, same UID etc.

Hypothetical Bonus Question: so, how far can you go between versions before you give the installer an ulcer? Like would this work if you were using a /home partition from 6.10 or 6.04?

---

### Post by ofb on 2007-10-26
> **stimpack said:**
> Yep manual partitioning. I do this every upgrade, retaining my existing /home. I do however use a different username on the new install and copy files over from the old user, as to avoid reusing the old desktop config files. This may be a waste of time, but I am paranoid.

I'm staying the same user precisely to save myself having to reconfigure the desktop to taste again. Otherwise I'd just do a fresh install & import my data files from backup.

Which is essentially what you're doing, unless I'm missing something extra your method does?

[I'm doing a fresh install rather than upgrade mostly to clear accumulated cruft from /etc, and partly in the hope a fresh install is less likely to have issues than an upgrade. The latter may not be true, but the number of threads lately are reminding me of the grim time I had going from 6.04 to 6.10.]

---

### Post by stimpack on 2007-10-26
Yes we doing the same. Except I only want to retain my data in /home and quite like setting up the desktop again :o

---

### Post by ubukool on 2007-10-26
Hi ofb,

Thanks very much for asking this question.  I am about to do a clean install of 7.10 and I have a separate /home partition for 7.04, so what wonderful timing!

All the best for your upgrade :)

---

### Post by ofb on 2007-10-27
Weird - I am in the middle of following the psychocats partitioning howto on my other machine.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I got a 'permission denied' for this line,
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

it needs to be
sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

Couple of very strange things about that:

1. The tutorial has been up for quite a while, but only a few people mention the problem.

2. The largely empty guest account copied over fine - I only got the 'permission denied' for my account.

(hastily typed output:)

/find: .o: Permission denied
/new//.o
/new//.nick/.bash_logout
/new//.nick/.bash_profile
/new//.nick/.bashrc
/new//.nick/
6blocks

add the sudo, and boom, the proper copy operation is proceeding nicely.

---

### Post by ofb on 2007-10-27
And you know what? - it doesn't matter because I just realized the psychocats method is the opposite of what I want.

What he's doing is setting up a new partition for /home, then copying /home into it. Which is a fine method if you have lots of free space.

I don't on this drive, so I was coming at it from a different angle: create a 6 gig partition for the system to move into, while leaving the large /home directory where it is.

Clearly, I should have picked a less busy week to do this. :)

--

Okay, regrouping: 

I have three partitions now. Swap, Ubuntu, and the nice new 6gig.

What I want to do is install 7.10 on the 6gig, and have it use the /home in the existing Ubuntu partition.

I have a feeling that just pointing the installer at the existing Ubuntu partition and saying that is /home now might not work.

What I don't understand yet, and can't divine from that *'find . -depth -print0 | sudo cpio --null --sparse -pvd /new/'* is if the /home partiton has a /home directory in its root, or is it everything that is directly below /home?

If the latter is true, then what I want to do won't work.

Know what I mean? If not please just ask, because I do need an answer to this before I can proceed.

---

### Post by ofb on 2007-10-27
And the answer is mount the 6gig which has the interrupted tranfer inside, and have a look.

Yeah, it's everything underneath /home.

So essentially, this isn't going to work, right?

There's no way to tell the installer that /home is in a /home directory?

---

### Post by avik on 2007-10-27
> And you know what? - it doesn't matter because I just realized the psychocats method is the opposite of what I want.

What he's doing is setting up a new partition for /home, then copying /home into it. Which is a fine method if you have lots of free space.

I don't on this drive, so I was coming at it from a different angle: create a 6 gig partition for the system to move into, while leaving the large /home directory where it is.

That's a tough one.

Just go ahead and install Ubuntu on the new partition.  Boot up, and you won't have your settings.  Once you verified that the actual OS works, then the fun begins.

Take the partition with the old installation + /home directory.  Get rid of everything but the /home directory.  Now you have the following partitions: swap, new Ubuntu, old /home.  So far so good.

Now we don't have to copy the /home directory to a separate partition; it's already by itself.  Mount it as normal, edit /etc/fstab, and reboot.  That should do it.

Don't hold me to it, always back up your data, and think before you act.  The above is my reasoning, but if you find any errors, act accordingly.

---

### Post by ofb on 2007-10-27
> **avik said:**
> Now we don't have to copy the /home directory to a separate partition; it's already by itself.  Mount it as normal, edit /etc/fstab, and reboot.  That should do it.

That is one of the senarios I am rolling around in my head. (And yup, I'm fully backed up, so I can risk a little creative surgery.)

Here's the problem I see: When you install a fresh Ubuntu and direct it at an existing /home partition, surely it must do some modification to it. For example, setting up dot-config directories for newly bundled applications, and presumably some discrete modification for existing applications that are now newer versions.

I'm figuring it does something like "add but don't overwrite".

Do you see what I mean?

---

### Post by forestpixie on 2007-10-27
If you're fully backed up - I'd just make your new partitions install and copy what you need back to your newly created /home afterwards.

---

### Post by avik on 2007-10-27
> **ofb said:**
> That is one of the senarios I am rolling around in my head. (And yup, I'm fully backed up, so I can risk a little creative surgery.)

Here's the problem I see: When you install a fresh Ubuntu and direct it at an existing /home partition, surely it must do some modification to it. For example, setting up dot-config directories for newly bundled applications, and presumably some discrete modification for existing applications that are now newer versions.

I'm figuring it does something like "add but don't overwrite".

Do you see what I mean?

When you do a fresh install, you don't direct it at anything.  It'll create a new /home directory, which you'll promptly replace with the old ones.  The new configuration files and directories will be replaced by the old ones, which is perfectly fine.

> **forestpixie said:**
> If you're fully backed up - I'd just make your new partitions install and copy what you need back to your newly created /home afterwards.

That's a good idea.  Once you have that set up, this way or the harder way, you'll have no trouble reinstalling later on; you'll have a /home directory ready to go!

---

### Post by ofb on 2007-10-27
> **forestpixie said:**
> If you're fully backed up - I'd just make your new partitions install and copy what you need back to your newly created /home afterwards.

I think that's the final choice. Right now I'm trying to understand process and thus my options.

And of course I've had corrupted backups before, so I'm leaving that as the last option if I can't find better.

---

### Post by ofb on 2007-10-27
> **avik said:**
> When you do a fresh install, you don't direct it at anything.  It'll create a new /home directory, which you'll promptly replace with the old ones.  The new configuration files and directories will be replaced by the old ones, which is perfectly fine.

Okay... That was actually my original question that started this thread. 

> What I don't understand yet is how the clean install of 7.10 will import/merge/use the 7.04 /home partition.

Or does the installer actually do that at all? Is the process: do the clean install, then rm -r the created /home & use fstab to mount the old 7.04 partition in its place? (which doesn't quite make sense, because that new /home could have some new config files for apps introduced with 7.10.)

What I thought I was being advised was point the installer at the existing /home partition and don't format it. Which I assumed would mean the installer does do some configuration to that partition, although perhaps it only means you get your fstab sorted for you.

This is the detail I'd like to sort out. I can't find documenation on what the installer process is at that point.

---

### Post by avik on 2007-10-27
> Or does the installer actually do that at all? Is the process: do the clean install, then rm -r the created /home & use fstab to mount the old 7.04 partition in its place? (which doesn't quite make sense, because that new /home could have some new config files for apps introduced with 7.10.)

> What I thought I was being advised was point the installer at the existing /home partition and don't format it. Which I assumed would mean the installer does do some configuration to that partition, although perhaps it only means you get your fstab sorted for you.

Once again, you don't point the installer at anything.  You only make sure the /home partition is preserved.  Then yes, you get rid of the new /home and mount the old partition in its place.  Any new apps will recreate their configuration.  At least that's how it seems to be.  It worked perfectly for me.  I reinstalled, got the old /home partition mounted, and from then on, I was back to having all my old configurations.

---

### Post by ofb on 2007-10-27
I have been to the land of Much Reading, and have returned with a game plan. 


1. I found installer screenshots that show you choose the mount points for each partition, just before choosing whether to format these partitions. However you do not have the option of of declaring a folder within a partition as a mount point.

ie, you can say hdb3 is /home, but you cannot say hdb3/home is /home.

Ubiquity simply doesn't offer that level of finesse yet.


2. While I'm sure you can replace a fresh /home with an old one after the install and have it work, at some point this going to be problematic. For example, upgrade from 6.04 to 6.10 to 7.04 to 7.10, doing the same post-install-remount of the old /home each time. A few of your dot-config files will be going unaltered from 6.04 to 7.10. 

You're eventually going to run into the same troubles that people run into when they swap distros while maintaining their /home partition. It'll be nothing that can't be fixed, but you will have to fix it.

[Note - I haven't yet found the documentation about just what Ubiquity does to an existing /home partition. I found lots of general description, and much interesting discussion about making /home partition detection a future feature, but I haven't found the gritty details about the copy process yet.]


3. I'm backed up, and I'm curious -- time to experiment. Here's the plan.

-3a. Boot the LiveCD and mount the now-inactive Ubuntu partition.

-3b. In that partition, create directory /christmas, and move everything except /home into it. This will be a little present to ourselves should things go badly wrong and we wish to salvage the old install.

-3c. Move everything inside /home (except data files) to /.

The point of "except data files" is to save a whole lot of time during this experiment. If the experiment succeeds, then /home/home/user/'data files' will be moved to /home/user/'data files' afterwards.

-3d. Now do the install, choosing Manual Partiton, and mounting that partition as the new /home.

-3e. Report back.


Anyway, that's the plan. I'm going to make dinner and think about it. Please feel free to post cautions and corrections in the meanwhile.

---

### Post by ofb on 2007-10-28
Report time: Yeah, it worked. Hully-gee, huh?

So, let's do summary & process report.


Objective: 

Take an existing Ubuntu installation without a separate /home partition, and make it into a fresh install with a separate /home partition.

In my case this was done while going from 7.04 to 7.10. If you want to do this without changing to a new version, use the psychocat method *if you have enough space to copy your entire /home directory.* 

If you don't, well you could use this method to make a fresh install of the same version, but be aware that you do need to re-install all your applications that were not included with Ubuntu by default -- your /home only has the configuration files for those apps, not the apps themselves. So why not just wait till the next version of Ubuntu comes out?


Process:

The psychocats directions were used to carve out a small partition for the new / to go into.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I used 6 gigs. Most people suggest 5-10. The base install of Ubuntu is about 4 gigs -- you only really need a large / partition if you run a lot of very big applications like games. UT2004, for instance, can easily take up 8 gigs after adding lots of maps. If you've got a nice new enoromous harddrive with bags of space, why not go for 20 gigs and have plenty of room for future expansion?

So, after psychocats's helpful advice, I have three partitions: the new slice, the extisting Ubuntu, and Ubuntu's swap.

Run 'sudo fdisk -l' to look at your partition list. Write it down for later use.

Now it's time for surgery. If you are not fully backed up already, then for petesakes do that first.

What we're going to do is get rid of everything except /home, then move everything in /home up one level so it becomes root on that partition. That way when you do the new install, you just tell the installer that this partition is to be mounted as your new /home.

Boot with the 7.10 LiveCD, because we can't take apart a functioning system.

In the following notes, my exisitng Ubuntu partition is called hdb1 - yours will be different. First we need to mount that partition so we can work on it.

sudo mkdir work

sudo mount -t ext3 /dev/hdb1 /home/ubuntu/work

Do Alt-F2, and enter 'gksudo nautilus'

In nautilus, change preferences to list, and 'show hidden files'. And make the sidepane show directory tree while you're at it just to make life easier.

Once inside /home/ubuntu/work, you'll be looking at your familiar old Ubuntu file system.

Create directory /home/ubuntu/work/christmas, and move everything except /home/ubuntu/work/home into it. This will be a little present to ourselves should things go badly wrong and we wish to salvage the old install. [Things did not go badly wrong, so I have not actually tried salvaging an old install with this.]

Now move everything inside /home/ubuntu/work/home to /home/ubuntu/work.

PROBABLY IMPORTANT: Note that I am making moves and not copies. I don't know exactly how nautilus handles move & copy, but I do know that the CLI command mv preserves ownership and cp does not. So I didn't risk copy. Don't have enough space for that anyway.

EXTRA: Earlier in this thread I suggested just moving everything but the personal data files to save time. It doesn't save time. The moves are instant. I was confusing moves on ext3 with moves on fat32, where you do have to wait for a byte-by-byte process to complete.

Okay, have one more look at 'sudo fdisk -l', and really you should write it down this time. For me:

hdb1 is my newly organized /home partiton
hdb3 is soon to be /
hdb5 is my swap

Close nautilus and terminal, and unmount /home/ubuntu/work by right-clicking on desktop.

And get this error: 'Cannot open /media/.hal-mtab'

Back in terminal: sudo umount /home/ubuntu/work

Surgery is complete. Close that terminal, and double-click the Install icon to proceed.

Once you get to partitioning (right about after selecting time zone), select 'Manual' from the partitioning options.

Next panel shows your partitions, with columns for mount points & formatting check-boxes.

Right-click the desired /home partition, and select Edit. Then for Mount Point, use the drop-down to select /home. Do the same for the little partition that is going to be /. Leave swap alone.

ONLY make a check-mark for formatting the desired / partition, **not** the /home partition. Proceed.

Next panel is 'Migrate Documents and Settings' -- it says 'there were no users or operating systems suitable to import from.' Because, I think, this only works for XP so far, not other Linux distros. So it can't see your /home directory. So don't worry about it, and carry on.

Next panel is 'Who Are You?' Enter the same names and password and computer name that you used to use.

Next panel tells you all the changes you are about to apply. As a curiosity, note that it says it will format the reused Swap too, even though you were unable to select it for formatting back in the partitioner. Proceed.

Now is a good time to take the cat for a walk, do dishes, and brew fresh coffee. When you come back, the install should be done.

After you reboot into your new system with your old /home configs, what you should see is a desktop largely like you left it, except you can expect custom icons and themes to be broken. Those won't work till you put them back in.

Also you have to install all the apps you had added previously, but your personal configurations for these will be there waiting for them.

So, after I got Nvidia enabled and general updates run, and re-enabled the repositories I use, and ran updates again, I put Opera, Konqueror, and Claws-Mail back in to test that things did indeed remember configurations as hoped. They did. Then I installed all my other missing apps. About half of these had left broken icons in the Menu, which provided a handy trail of bread crumbs. The rest was from memory.

You can get rid of /home/christmas and /home/home now.

At least I hope so. My new install seems to be working fine.

IMPORTANT DISCLAIMER: Advice from some random guy on the net is just advice from some random guy on the net. In the end, only you are responsible for what you do with it. Keep your brain turned on, and be willing to take responsibility for whatever happens.

And at least wait a day or two so people can point out errors & say what a bad idea all this is.

---

### Post by forestpixie on 2007-10-28
woo hoo - well done - bet you're glad that's over :D

---

### Post by ofb on 2007-10-28
> **forestpixie said:**
> woo hoo - well done - bet you're glad that's over :D

I'm still wound-up, so more like surprise that there isn't some Horrible Mess that I need to sort out.

Very worth adding: Well before all this I made a backup of /etc, so I can extract any custom settings I'd made & forgotten, like in fstab & rc.local & hosts.

---

