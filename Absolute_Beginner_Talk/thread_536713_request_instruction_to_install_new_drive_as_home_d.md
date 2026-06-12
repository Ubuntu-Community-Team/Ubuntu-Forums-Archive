---
title: "request instruction to install new drive as home dir"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by wog on 2007-08-28
Okay, I put in the new drive. That was the easiest part. gparted actually made accessing and reformatting the new drive pretty damned easy, too. I formatted it as ext3, assuming that's not a problem.

I made a dir in /home and mounted the new drive pointing to that dir.

But when I tried to cp the contents of my old home dir into that drive, every dir in the old home was omitted from the cp process. How do I cp the dirs from the old home to the new one?

Eventually I'm going to need help with editing the startup files so my new home dir is always the new drive, but that can wait until I have this current step completed.

Can anyone help?

---

### Post by southernman on 2007-08-28
Hi wog,

Psychocats has a good tut on what your needing to do... you've got most of it done but read through it just the same if your unsure. The end of the tut is prolly what you want.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by wog on 2007-08-28
Okay, I have a problem. 

The link to [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) seems to apply to me more than the original page, and it's easier to parse as well.

First, for the complicated line starting with "find", I'm not sure where I'm supposed to be when I do this command. I assume I'm supposed to be in my old home directory.

Then I get an error message.

When I type in:```
find . -depth -print0 | cpio –null –sparse -pvd /home/james2/
```
I get: 

cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

I have no idea what I did wrong or what I'm supposed to do. Can anyone see what I did wrong?

---

### Post by southernman on 2007-08-28
It's why I suggested the link I did.

Quote from the comments section of the link you gave:> 

    I created another tutorial based on this one (which actually links to this one as being for intermediate to advanced users). My tutorial includes screenshots on the resizing process and doesn&#8217;t contain any typos (I hope).

    I also ran into the /home directory (mount point) not existing when I followed these instructions, so I tried to correct that in my tutorial:

    [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

I've not had to do this cause of setting up a /home partition at installation so I can't really offer much help but steering you.

[http://www.mkssoftware.com/docs/man1/cpio.1.asp]("http://www.mkssoftware.com/docs/man1/cpio.1.asp")

---

### Post by wog on 2007-08-28
Okay, now this is weird.

I put in the line:```
find . -depth -print0 | cpio -pvd --null --sparse /home/james2/
```but it failed.

Okay, that makes sense. It just needs sudo at the start of the line, right?

It still fails. I get line after line of Permission Denied. With sudo.

Okay, now what the hell does it mean when I can't do something as super user?

---

### Post by stevebakerj on 2007-08-28
I personally prefer the method described here:

[http://www.funtoo.org/en/articles/linux/partitioning/1/](http://www.funtoo.org/en/articles/linux/partitioning/1/)

I have used this method on several occasions with complete success.

---

### Post by wog on 2007-08-28
Okay, having the extra step of going to ```
sudo init 1
``` helped immensely. That went without incident. But I haven't edited my /etc/fstab yet, and I'm wondering what the line 
```
/dev/hdb1   /home   ext3   1   2
```
is going to do. I mean, I understand the first part is the actual location being mounted, and the second part is where it's mounted to, and the third part is the partition format, but what about those numbers? What do they mean?

I mean, I'll edit my /etc/fstab, even without knowing what this line is going to mean, hoping it won't mess up my system in any way, but the only way this line is going to go from being magical to being logical is by knowing what it means, and having just set up a new partition through root has made me more than a little agitated.

being in root still scares the beejezus out of me. I have no more bejezus left, probably until I eat and sleep at least once each.

Edit: actually, the two tutorials differ. The line for the tutorial formatting as ext2 edits /etc/fstab as the above, while the tutorial formatting as ext3 uses the /etc/fstab line ```
/dev/hdb1   /home   nodev,nosuid   0   2
```
Will either of those /etc/fstab lines work, or should I use this line because I formatted the new partition as ext3?

---

### Post by stevebakerj on 2007-08-28
fstab explained:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

and i would go with

```
/dev/hdb1   /home   ext3   1   2
```

---

### Post by wog on 2007-08-28
I went with the fstab line with the numbers, and rebooted.

I was doing good up until I rebooted.

Now the system won't start. It claims I have no home directory. It asks if I'd like to be root so I can see if I can fix things, and when I say yes, it tells me my session was less than 10 seconds and I end up at the login screen again. Poof.

So I got out my trusty Ubuntu LiveCD and stuffed it into the drive. It's from Dapper, but it should still work, right? I mounted the problem drive and tried to see what was different. Well, one thing is these UID numbers before the other entries. I don't know what those are, but there's a note before each partition entry that says they were converted during the update to Edgy. Hm.

All I can really do is remove the tabs I put in and insert a space between each entry. I don't know that'll do anything, but as I mentioned before, this is all black magic to me, I don't understand it, and I know I should change something or I'll get exactly the same result as I got before.

So I save and then reboot. The system forces fsck to run. And now XWindows won't start. I don't know what's wrong, and I don't know how to find it to fix it.

This is why I refuse to put my email on the Linux box, and why the Linux box has only Linux on it.

Anyone have a clue about what I should do next, or am I forced to admit defeat and reinstall from scratch?

---

### Post by wog on 2007-08-31
Long story short, I reinstalled over the boot partition and then did the mounting instructions that got me into this mess in the first place. As soon as I came out of single user mode I went through login and password and ended up right back on my old desktop! Thanks to the fact that it was in a completely separate drive, it was untouched by my reinstallation.

I imagine there are a few things broken by the old home directory sitting on top of a new boot install. Will "sudo apt-get -f install" fix those discrepancies, or will I have to do something else to match my old home directory up with my new install?

Additionally, there seems to be some sort of UUID number for the other two partitions (boot and swap) in /etc/fstab. Am I going to need to generate a number for my new home partition, and if so how and with what? Or is that number floating around somewhere on the machine and I just need to find it and write it in?

---

### Post by southernman on 2007-08-31
[edited] removed fluffy unneeded content so I don't get a spankin again! ;)

*back on topic*

Not sure what to tell you at this point. Both howto's you looked at have been used by many people successfully.

As for finding your UUID's. Yeah, they are just floating around out there in your computers super nova. ;) Find them by running "blkid"

Good luck... hope the blkid thing will get you where you want to be.

---

### Post by wog on 2007-08-31
I worked out a short-term solution. The /etc/fstab line I eventually went with was:

/dev/hdb1 /home ext3 nodev,nosuid 1 2

I don't know what the 1 and 2 at the end do, so I don't really know if these numbers are safe to remain with, but the machine boots up and lets me login, and it finds the new /home drive, so I can cope.

Of course, now I can't get into X-windows (my system is assuming I have something other than my nVidia card), so I'm not completely in the clear. But I'm closer!!! :)

---

