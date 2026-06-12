---
title: "Redetecting hardware on USB HDD like live CD"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by lilrate on 2006-09-01
Hey All,

I am wondering if there is a simple way to redetect hardware on a installation of Ubuntu on an external hard drive.  I read DaBruGo's post on installing on an external HDD and everything works fine:

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Also in that post there were two mentions of solutions:
[http://www.ubuntuforums.org/showthread.php?p=395865#post395865](http://www.ubuntuforums.org/showthread.php?p=395865#post395865)
[http://ubuntuforums.org/showthread.php?p=689098#post689098](http://ubuntuforums.org/showthread.php?p=689098#post689098)

PoMalin suggested a solution which requires a mini cd as well as the USB drive.  Azz sugguested reconfiguring the video card.  I am wonder if the reconfiguration is required everytime I switch computers?  If I had three computers I wanted Ubuntu on would it require 3 configurations or a reconfiguration everytime I switch to a different computer of the three.

I am wondering if there is a simple configuration change I can make to have Ubuntu have different hardware "profiles" in which I can select which computer I am booting from and prevent and reconfiguring of mount points and video cards.  Say like a boot screen which allows me to choose: 1) "Laptop configuration - Intel Video Care,"  2)"Desktop configuration - GeForce 4200," 3) "Autoconfigure like live CD"

Or do you know of any other good distributions which allow the installation of software on a external HDD which acting as a "Live CD" when switch computers.

Thanks!

Edit:
For your reference this a similar question was asked by Aldar in response to a reinstallation, but not an external hdd in which Azz gave his solution:
[http://www.ubuntuforums.org/showthread.php?p=395865#post395865](http://www.ubuntuforums.org/showthread.php?p=395865#post395865)

Also this question has been brought up a few times in the post by DaBruGo, yet many of the questions go unanswered or lost due to the 44 page thread.  In some responses people say it is not possible.
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by kidders on 2006-09-01
So you want to run the same Ubuntu on multiple computers, eh? Hmmm...

Historically, Linux has been designed to (at least in theory) make this pretty easy. You may have noticed that, if you want to tweak something, the /etc directory is invariably where you go to do it. I have seen Linuxes that seem to do more or less exactly what you said about different hardware profiles, but to my knowledge, Ubuntu is not one of them.

The generic, all-platform solution seems to me to be to make multiple copies of your /etc directory. Granted, virtually all of the content would simply be duplicated, but it would be a one-step way to:

[LIST]
[*]Specify which modules each computer should auto-load
[*]How you want your X server to work (trackpads vs mice Nvidia vs ATI, etc, etc.)
[*]What kind of power management you are interested in
[*]And so on...
[/LIST]

There are various ways of achieving this, but imho the one that's most likely to work quickly with the fewest glitches is what I've outlined here. With any luck you'll like the sound of it!

**STEP 1**
Type "du -hs /etc" to find out roughly how big your /etc is. It shouldn't be inordinately large ... maybe about 15-20 megs. Add 3 or 4 little partitions about twice that size (for safety) on the end of your external hard drive.

**STEP 2**
Format each partition carefully: Use the same filesystem you have on your main hard disk partition, so you're sure the kernel will know how to handle it during the boot process, and give each a specially crafted label. I suggest perhaps using some derivative of a detail about each computer's hardware that you're sure will be available during the boot process.

The idea is that we will replace your /etc (and with it, most of Ubuntu's settings) with a copy chosen on the basis of which computer you happen to be plugged into at the time.

**STEP 3**
Duplicate your /etc a number of times, depending on how many little partitions you created. Be sure to do this in a terminal window, so you have more precise control over exactly what gets copied and any undesired permissions changes that may occur.

[LIST=1]
[*]Make lots of mount points for your /etc partitions with "mkdir /mnt/etc1", "mkdir /mnt/etc2", etc.
[*]Mount them all with "mount /dev/sda5 /mnt/etc1", "mount /dev/sda6 /mnt/etc2", etc.
[*]Now start copying with "cp -dpR /etc/* /mnt/etc1", "cp -dpR /etc/* /mnt/etc2", etc.
[/LIST]

**STEP 4**
Now it's time to diddle one of your startup scripts to "intelligently" mount the correct /etc on top of the "real" one that you've been using up to now.

**NB: I haven't actually tried this myself, so a little trial and error may be required!**

I noticed that /etc/init.d/mountall.sh seems to contain instruction for how to configure your hard disks at boot time. Tweak it so that AFTER the file called /etc/fstab is taken care of, the correct /etc is mounted. I'll get back to what to do here in a minute.

**STEP 5**
Shut down your PC and boot back into it using every one of the machines you intend to use it on. Once you've re-configured Ubuntu for each one, you should never have to do it again.

Should you try to use your Ubuntu on a PC it doesn't know about, our "intelligent" mount will fail, and /etc will simply fall back to the original one sitting in your main disk partition.


**LABELLING STRATEGY**
Brace yourself... this may be tricky to understand!

The reason for this little complication is that, as your computer is booting, it needs to decide on the fly which version of /etc to use. The most convenient solution seems to me to be to find something that's unique about each of your PCs and try to mount the /etc partition with that label.

Imagine, for the sake of argument, that all your computers have a different CPU architecture. That way, you can identify which one you're on, using the contents of the file /proc/cpuinfo. Take a look at it by typing ```
cat /proc/cpuinfo
```

Limit the scope of what you see with ```
cat /proc/cpuinfo | grep "vendor_id"
```

Further refine your "label" with something like ```
cat /proc/cpuinfo | grep "vendor_id" | sed -e 's/[^:]*:[ ]*//'
```

On my machine, doing that leaves me with "AuthenticAMD" ... a perfect partition label. Set it while formatting a disk partition with something like "mkfs.ext3 -L AuthenticAMD /dev/sda5". This would write a blank EXT3 filesystem to the fifth partition on serial device (sd) number 1 (a) and call it "AuthenticAMD".


**SCRIPTING THE AUTOMATIC MOUNT**
Once you've found a suitable place to insert a custom "mount" instruction, you need to figure out how to write it. My provisional suggestion is (see above) /etc/init.d/mountall.sh. Ordinarily, you'd manually mount a partition with an instruction like "mount /dev/hdc1 /mnt/cdrom", giving a device name and a mountpoint in your filesystem. Whatever was at that mountpoint gets the contents of the new filesystem plonked on top of it, until you unmount it again. For scripting purposes, we can assume very little, so I'll refer to "mount" using its full path:

```
/bin/mount -L "AuthenticAMD" /etc
```

This line would do the mount for an AMD-based computer, assuming a filesystem with the specified label existed, hiding the /etc that was already there. The generalised version uses the long line of crap from above:

```
/bin/mount -L `cat /proc/cpuinfo | grep "vendor_id" | sed -e 's/[^:]*:[ ]*//'` /etc
```

That's one nasty little command, but in my example, it would do the job, extracting the correct portion of /proc/cpuinfo and embedding it in the mount command.

You could then follow it with this, for clarity:

```
if [ $? -eq 0 ]
       then echo "Configuration profile loaded successfully"
       else echo "FAILED TO LOAD CONFIGURATION PROFILE"
fi
```

Now that I've written all this out, is seems far more long-winded than it was when it was still in my head! I wonder if anyone will suggest a less labour-intensive version for you to try!!

At any rate, the work should take maybe 30 mins to complete and, once you're done, you will have the ability to embed several completely independent configurations in one external hard disk, without the need for any support media, such as a CD or USB key.

Strictly, there are certain things you should delete at this point for the sake of neatness, but hell ... one thing at a time, eh?

I really hope this is of some use to you :)

---

### Post by lilrate on 2006-09-06
Thanks kidders for the reply!

Your response seems very interesting but I am reluctant to change so much with the little knowledge I know about Linux.  Last time I tried messing with a solution I ended up crashing my x server.  I am wondering if you know of any other distributions where your suggestion has already been preprogrammed in.  Thanks.

---

### Post by kidders on 2006-09-06
I can appreciate that!

As far as I'm aware (and I could well be wrong), Mandriva supports the concept.

One question though...

Are the changes you'd want to make limited to your screen + input devices?

---

