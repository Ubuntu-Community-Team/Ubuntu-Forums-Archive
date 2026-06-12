---
title: "Mount Mac Partition at Startup"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by kennethsime on 2010-10-13
As many of us dual-booters, I keep most of my files on my mac partition. Specifically, my music. One of my favorite things to do is to point Rhythmbox to my iTunes music folder, and just play from there. iTunes keeps it up to date/organized (I rip/add music on my mac partition), and when I'm on Ubuntu Rhythmbox keeps right up (mostly). However, I do have to manually mount my mac partition before Rhythmbox will play, and it seems to work better if I do it before I launch the application.

So, I ask: is there a simple, clean way to mount my mac partition at startup?

---

### Post by renzokuken on 2010-10-13
the easiest way is to add a mount point in your fstab file. this way, when ubuntu loads it automatically mounts the partition at your specified location everytime you boot.

sadly, having never done this for a mac partition (only for XP) i wouldnt know the settings you have to specify in the fstab file. that might be a start for some googling research.

failing that, could you not just create a script to run the mount commands you use now and set that script to execute on login?

sorry, not much help i know but it might be a start

---

### Post by MisterGaribaldi on 2010-10-13
Well... *three* things:

1. You need to install the HFS/HFS+ components to be able to access Mac-formatted partitions;
2. HFS+ Journaled is the default filesystem and has been since 10.3.
3. Linux HFS/HFS+ support does not include WRITE support for HFS+ Journaled filesystems.

So, the question here is do you need to be able to write data TO your Mac partition. At present, there's no really clean solution for this. I think that Journaling can be disabled on an HFS+ Journaled filesystem (making it capable of being written to) but I have no idea how to make that happen.

---

### Post by pc_michael on 2010-10-13
I do exactly the same thing you do, Kennethsime.  Here's how I did it:

[LIST=1]
[*]Create the folder where you want to mount the drive.  I did mine at /media/MacintoshHD
[*]Edit your fstab by opening Terminal and typing sudo gedit /etc/fstab
[*]Add the following line at the end.  Here my Mac partition is at /dev/sda2:

```
/dev/sda2	/media/MacintoshHD	hfsplus	defaults	0	0
```

[color=red]**Note that the large spaces between those arguments are tabs**[/color]

[*]Save your fstab and reboot
[*]Profit
[/LIST]

---

### Post by rduplain on 2010-10-18
> **pc_michael said:**
> 
[LIST=1]
[*]Create the folder where you want to mount the drive.  I did mine at /media/MacintoshHD
[*]Edit your fstab by opening Terminal and typing sudo gedit /etc/fstab
[*]Add the following line at the end.  Here my Mac partition is at /dev/sda2:

```
/dev/sda2	/media/MacintoshHD	hfsplus	defaults	0	0
```
[/LIST]

I set my fstab slightly differently:

```
UUID=cea5d65a-62b5-33fa-b6a5-8c7426e66606 /media/MacintoshHD hfsplus defaults 0 0
```

If you only have one drive, it doesn't matter that much, but using UUIDs are unique to the drive and will be robust to drive additions, e.g., SD cards & USB drives.

You can find the UUID with [FONT="Courier New"]ls -l /dev/disk/by-uuid/[/FONT] and looking for the match to the target partition, in my case /dev/sda2.  You can get a lot of information from gparted here if you don't know which partition you want (but do not to make partition edits!).

> **pc_michael said:**
> 
[color=red]**Note that the large spaces between those arguments are tabs**[/color]


Spaces should work just as well as tabs.


> **pc_michael said:**
> 
Save your fstab and reboot


You could reboot, but you don't have to.  After setting fstab:

```

sudo mount -a
ls /media/MacintoshHD/ # should show files

```

I recommend doing this to be sure that you set fstab correctly.

-Ron


PS - You might have to install the hfsplus package if mounting fails.

---

### Post by kesiev on 2010-10-18
Ow! This topic fits my recent needings too... :)
Is there a way to mount the unjournaled hfsplus partition at boot with read/write rights for users too? I'm able to write the partition but just as super user.

---

### Post by srs5694 on 2010-10-18
> **kesiev said:**
> Ow! This topic fits my recent needings too... :)
Is there a way to mount the unjournaled hfsplus partition at boot with read/write rights for users too? I'm able to write the partition but just as super user.

Exactly the same procedure described by others for read-only access will work. The trick is user ID and group ID numbers. The best solution is probably to set your Ubuntu accounts to use the same UID, and perhaps GID, numbers as are used under OS X. You can do this with usermod, but you'll then have to change the ownership of all your files:

```

sudo usermod -u 1234 -g 5678 fred
sudo chown -R fred: /home/fred

```

This example changes the user fred's UID value to 1234 and GID value to 5678. You'll need to figure out the correct values based on whatever OS X is using. (Try examining files you know were created by your normal user in OS X; but if you think the value is 0, it's not; that's the root account, and you should never set any other account to use UID 0.)

After you make the UID/GID change, log out immediately. In fact, this change is best made from a direct root login, but that's discouraged with a default Ubuntu install. (In principle, you could boot to single-user mode, though.)

---

### Post by kesiev on 2010-10-18
Clever suggestion! It worked! Thank you very much (and added to Delicious too). I've seen that the user is no longer shown on the login dialog as a list - but doesn't matter for now (obviously help is appreciated!)

Really, very very interesting trick! Thank you again!

---

### Post by kesiev on 2010-10-18
Partially self-answered. I've done quite like the suggested workaround here [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/70850"):

```

sudo vi /etc/login.defs
change UID_MIN to 1 *<--- (I've put 500 instead of 1)*

```

...and my username appeared. I'm not sure that is clean enough but is working for now. Is there a cleaner way to do the same thing?

---

### Post by rduplain on 2010-10-19
Unless you are planning on syncing several account IDs between Mac OS X and Ubuntu, I'd recommend using usermod manually for the accounts you need, as @srs5694 shows above.

---

### Post by kesiev on 2010-10-19
...That is what I did... and worked fawlessy. The only drawback is that the user will not show up on the login screen as a list, since only UID>=1000 are shown. Changing login.defs as I said, the user will show up but I think that, since Ubuntu system users have UID>=500, eventually system users will show up a day too - that is what I'd like to avoid.

For now I've changed the user UID and the login.defs file and is still working. If there is a way for doing better, I'll surely switch to that solution.

---

