---
title: "Unable to mount NTFS"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-02-26
I cant mount external HDD.
This is the error:

$logfile indicates unclean shutdown (0, 0)

failed to mount '/dev/sda1': operation not supported

mount is denied because ntfs logfile is unclean. choose one action:

   boot windows and shutdown it cleanly, or if you have a removable

   device then click the 'safely remove hardware' icon in the windows

   taskbar notification area before disconnecting it.

or

   run 'ntfsfix' on linux unless you have vista, then mount ntfs with

   the 'force' option read-write, or with the 'ro' option read-only.

or

   mount the ntfs volume with the 'ro' option in read-only mode.

error: could not execute pmount

What to do?

---

### Post by netkid91 on 2007-02-26
Boot Windows and run chkdisk, simple enough.

---

### Post by tyeo098 on 2007-03-26
Yea but what if we cant get into windows?

---

### Post by HaoTian on 2007-05-24
That's great... no one has answered this.  I've hit this wall, too, and it's a major pissoff.

I think it's real nice that a linux program tells us to boot into Windows... the whole reason many of us run Ubuntu is because we don't want to run Windows anymore.

So... to re-iterate the question posed above... How do you run chkdisk on a disk when you don't run Windows anymore?

---

### Post by Terl on 2007-05-24
The original question asked about ntfs which is windows, hence the "reboot windows" message.

I do not understand the last two posts.  

Hao Tian:  If you do not have windows, why are you asking about ntfs problems?  Is there another issue you have?  The error message in original post also said this:  > run 'ntfsfix' on linux

tyeo098:  Why can you not boot into windows.

It seems like there are different issues in this thread.

---

### Post by Churnd on 2007-05-24
> **HaoTian said:**
> That's great... no one has answered this.  I've hit this wall, too, and it's a major pissoff.

I think it's real nice that a linux program tells us to boot into Windows... the whole reason many of us run Ubuntu is because we don't want to run Windows anymore.

So... to re-iterate the question posed above... How do you run chkdisk on a disk when you don't run Windows anymore?

Linux does fsck, but that doesn't support NTFS.  NTFS isn't an officially supported format for linux.  Write access is still experimental.

If you don't use windows anymore, you don't need NTFS.  Reformat that drive ext3 or whatever, then you can do linux diags.

---

### Post by Dzenhax on 2007-05-24
What's up dude.

     Need a little info.  How come you can't boot into windows?  Maybe you had two partitions and erase the one with the OS on it leaving the other for your data?

     You have a few options.  

1.  You can reinstall win on the Ubuntu partition, fix ntfs, and reinstall Ubuntu over win when it's finished.

2.  Get a copy of ERD commander and boot up a skeleton windows.  Then back your data up to an external HD.

3.  Is this a desktop computer?  Pull your hard drive, put it in another computer as the slave hd.  Most computers can hold two hard drives.  Pull your data off or repair the ntfs file system.  If you are never going to use windows again, Pull your data off, convert the partition to fat32 and put the data back on.  Although Linux has become good at dealing with ntfs its still risky.

4.  They say knoppix is great at fixing broken windows, but I don't have any experience with it.

5.  Lastly, dual boot windows and Ubuntu.

You can Google on how to do just about any one of these.

Hope something in there helps.

Dzen

AND LATER,

Duh,

    Just caught the external HD part.  Dude, can you hook it up to a buddy's windows box just to clean it up?  Have you ever been able to mount it under linux?

What does your /etc/fstab look like?  The problem may be there.  When I had fstab problems I got help here:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

OK, Hope THAT helps.

Dzen again.

---

### Post by Dzenhax on 2007-05-26
Forgot about this page.  Maybe it'll help anyone with this problem.  From the 400 views to this page, I guess many people have this problem.

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

Enjoy,

---

### Post by DJ Wings on 2007-05-26
Knoppix is just a live CD. The only difference is that it holds 2 gigabytes of software, with recovery tools out the wazoo. Otherwise, it's just your average Live CD. (And it runs really fast.) I doubt it will help.

---

### Post by drowner on 2007-05-26
> **HaoTian said:**
> That's great... no one has answered this.  I've hit this wall, too, and it's a major pissoff.

I think it's real nice that a linux program tells us to boot into Windows... the whole reason many of us run Ubuntu is because we don't want to run Windows anymore.

So... to re-iterate the question posed above... How do you run chkdisk on a disk when you don't run Windows anymore?

Hi There!

If you don't run windows anymore, its clear you don't need that partition, right? I mean, NTFS is a windows-only filesystem, so if you want it fixed, you use windows. Makes sense?

If you don't use windows you have NO use for an NTFS file system.

Furthermore, noone has to answer this. People aren't here at your whim, buddy.

Whats your problem?

---

### Post by DJ Wings on 2007-05-26
[quote=drowner]If you don't use windows you have NO use for an NTFS file system.[/quote]
He probably wants it fixed so he can back up his files and then format it as EXT3 or VFAT.

---

### Post by drowner on 2007-05-26
> **DJ Wings said:**
> He probably wants it fixed so he can back up his files and then format it as EXT3 or VFAT.

Youre too nice

---

