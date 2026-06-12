---
title: "How to access files on HFS filesystem in Ubuntu"
date: 2008-10-20
forum: Apple Hardware Users
---

### Post by commonmanthemes on 2008-10-20
Hey everyone, I need some help backing up a friend's dead PowerBook G4 with an HFS filesystem.  Basically, I can mount the drive but cannot copy over any of the files from the folders inside of the user account.  I have tried everything from changing the permissions in the GUI to a million different chown variations, all with the same result - no go because the drive is read only.

Please help.  I'll be on this board all day.

---

### Post by Kooothor on 2008-10-20
Hi, 

Have you tried mounting it with forcing read-write ?

must be something like :

# mount -t hfsplus -w and then something else to force rw, go to man mount.

Also do a modprobe hfsplus if the output of lsmod | grep hfs is empty.

---

### Post by MikeTheC on 2008-10-20
It's quite possible the HDD is using HFS+ Journaled, and unfortunately the only way I've seen to correct this is to do so within the Mac OS X environment.

So...

If you or your friend have access (even if it's just temporary) to another Mac running Mac OS X 10.4 or later, get the HDD attached and, once it's mounted, try the following:

**Applications** > **Utilities** > **Terminal**, and then type:

[font="Courier New"]cd /Volumes[/font]
[font="Courier New"]ls[/font] (just to verify the drive appears there)
[font="Courier New"]diskutil disableJournal <volume name>[/font]

Note that, depending on how the drive is labeled, you might want to tab auto-complete to get a valid-usable version of the name (valid for purposes of your Terminal's shell functionality).

It should take just a moment for journaling to be disabled. Once it is, "eject" the disk, disconnect it from the Mac, and then attach it to your Linux box.

Good luck!

---

### Post by tiresia on 2008-10-20
Linux can read and write HFS+ 
If HFS+ is journaled, Linux can only read from not write on it.

But here it looks different. You can't access the user's data because of the permissions (you are not the owner).
You can do it as root, i.e. prefacing the copy command with sudo.
If you want to back up all the file in iTunes of the user 'Tom' from a Volume mounted on /media/disk1 to a HD mounted on /media/disk2

```
sudo cp -r /media/disk1/Users/Tom/Music/iTunes /media/disk2
```

After that most probably the owner of the files is 'root'. Change it with 'chown'

---

### Post by cyberdork33 on 2008-10-20
and you cannot change the permissions on the existing files because the filesystem is read-only.

---

### Post by jwhendy on 2008-10-23
There is a nice solution I've found to this problem in just three steps:

1. As stated, turn off journaling. You can boot into OS X, and enter 'diskutil disableJournal <volume name>' as stated before in a terminal or another method is to open Disk Utility, click your OS X drive partition, hold Option down and click the File menu. 'Disable Journaling' will be an available option.


2. Boot into linux and edit your /etc/fstab (as root). I believe my line is (not on my linux box right now):
```
/dev/sda2  /media/Macrophage   hfsplus   user,rw   0  0
```

-Replace '/dev/sda2' with whatever your OS X partition is
-Create the directory wherever you want to mount the drive (mine is /media/Macrophage). Make sure it exists before you mount - simply putting it in fstab will not create it for you.


3. Now for the key trick I picked up. Edit your username, password, and userID in Linux. Create a new account for yourself and use the exact login/password you use for OS X. If you'd rather not create a new account, your should be able to:

```
usermod -l os_x_username current_username
```

This will replace your current username with the one you enter for OS X. Fill in the variables above to match what yours are. If you took this route vs. creating a new account, remember to change your password.

Lastly, you need to change your UID to match the one used in OS X (OS X uses 501 for the first admin account created). My username is 'zenbook', so after creating my account, I run as root:

```
usermod -u 501 zenbook
```

I use Zenwalk, and the first account created has a UID of 1000 by default, so I have to run the above to match it with my OS X account UID. You are basically tricking OS X by matching all of the user stats with the ones maintained on the Mac side.

Before embarking on this entirely, run 'id' from the command line to see what your current UID is. If it is currently 501, then I just typed a whole lot of explaining for nothing because mismatched UIDs are obviously not the problem...

When all done, to test just type: ```
mount /dev/sda2
```

Hope this helps you out!



-John

P.S. I thought this was for you... after re-reading, I realize now that this is for a friend, so you should go through all of the steps with HIS login/password - just create a separate account on your machine to match his info (vs my usermod option), do your backup work, and when you're sure everything's all set, you can just delete the account.

---

### Post by king20878 on 2008-10-27
One other thing you might want to check is if the drive is being unmounted cleanly.  Linux will mount it read-only if it appears to have been unmounted improperly.  You should see a line in dmesg about it.  Running fsck.hfsplus on it fixes the problem.  

This was causing me fits with the external drive I use for my AppleTV until I figured out what was going on.

---

