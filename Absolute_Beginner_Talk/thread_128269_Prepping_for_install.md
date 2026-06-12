---
title: "Prepping for install"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by axiomata on 2006-02-11
File me under the super linux newb category.  I've currently got Windows XP Pro, and I'd like to install Ubunto in addition to it.  I have two hard drives, both 80gb.  The first one has the Windows system files and program files.  I recently installed a second hard drive as the first was filling up.  On the second I have My Documents.  I've downloaded and played around with [Partition Logic](http://visopsys.org/partlogic/) to make room for Ubunto on the second hard drive.  Here's where my questions start.

Apparently, when I installed this second hard drive, I set it as a dynamic disk as opposed to the first which is basic.  I'm not sure the difference between these versions but when I try to make a new partition on the second one, the dynamic one, with Partition Logic, a few problems pop up.  If I don't format the newly created partition, just leave it as blank space, then boot up windows, disk management doesn't even see that new space at all.  It just sees that 80gb disk as a 50gb disk.  If I try to format the second partition in FAT, NTFS, or anything else I tried, and boot up windows, it doesn't even recognize the disk at all.

Basically I'm asking what I need to do to prep this second disk for a fresh installation of Ubunto.  Thanks.

---

### Post by heimo on 2006-02-11
I'd just boot from a Ubuntu install CD and see if it can detect both disks and show you the 30GB free space that should be available on the second disk. If I recall correctly, install will give you choice to "use whole disk" or "use empty space" in addition to partitioning manually. And install can actually resize partitions too, but this is always a bit risky and you should have backups of your important files (in any case).

I'd also keep a copy of Windows install CD (if I were you) and Ubuntu Live CD nearby, just in case something goes wrong. But there should be nothing to do to prepare your system any further other than booting from install CD.

EDIT: As GreyFox below is writing, the space should be unpartitioned, if it's somehow allocated for any windows partition / dynamic disk or what-ever, there'll be problems.

---

### Post by GreyFox503 on 2006-02-11
I'd never heard of basic or dynamic disks before, but after reading these:

[http://support.microsoft.com/?kbid=309000]("http://support.microsoft.com/?kbid=309000")

[http://support.microsoft.com/default.aspx?scid=kb;en-us;308424&sd=tech]("http://support.microsoft.com/default.aspx?scid=kb;en-us;308424&sd=tech")

I'd say that you want your disk to be basic (4 partitions).

Once you've got that, To install Ubuntu, just leave whatever space you want to give it unpartitioned.  Some people think they need to create partitions ahead of time, but that's really not necessary.  It's easier to just leave a chunk of unpartitioned space on your disk.  For a full Ubuntu install, you don't need much, 5 - 10 GB would be plenty for the OS and all its programs.  If you can, it would be nice to leave it a little wiggle room, of course.

The install is really easy, the only tricky part is partitioning.  If you have unpartioned space on your drive, you can tell the installer to work its auto-magic, and it will create appropriately sized partitions for you.

[quote=heimo]I'd just boot from a Ubuntu install CD and see if it can detect both disks and show you the 30GB free space that should be available on the second disk[/quote]

Ahh, the straightforward approach.  If the Ubuntu installer can use the 30GB space that Windows can't see, then more power to it.  Then you literally won't have to change anything and can just continue the install immediately.

---

### Post by axiomata on 2006-02-11
OK, thanks for the help guys.  I wouldn't think twice about playing it safe and converting the second hard drive back to basic but I think that would erase it's contents.  And I have a little too much stuff on this second hard drive now to transfer temporarily back to the first hard drive.  I do have a 20gb iPod though.  Would it work to format the ipod, then transfer all my music (about 15gb ... should be enough to allow the rest of my files to fit on the first hard drive) back to the ipod using it as mass storage (this would preserve file names and ID3 tags correct)?  Then once I get the second hard drive back to basic I would transfer my documents back to the second hard drive as well as the mp3s from the ipod.

I'd then do the ubunto setup on the second hard drive, using its built-in partitioning abilities.


A few questions while I'm at it.  GreyFox said the disk should have 4 partitions.  Why not two?  One for my documents and one for ubunto.  Also, once booted in ubunto, I will be able to access all the files in the my documents partition correct?  I don't want to have to copy all my mp3s to the ubunto partition as I don't have that kind of space.

I don't think I'm going to even attempt to install ubunto with this dynamic disk setup.  That [second link](http://support.microsoft.com/default.aspx?scid=kb;en-us;308424&sd=tech) makes it sound that this dynamic disk won't play nice with anything but windows xp so I don't think I'm going to even risk trying to run the setup yet.  (Though, if I do try to, is there an easy way to exit mid-setup should it not see the free space without making any changes to the system?)

Again, thanks for all the help.  I just got done playing with the live CD.  This is gonna be fun when I finally get it to work. :D

---

### Post by bartbes on 2006-02-11
you actually need 3 because linux also needs a swap partition

---

### Post by axiomata on 2006-02-11
Well ... I stayed up until about 9AM installing Ubunto. :D (Actually, most of the time was spent backing up my files and restoring them.)  Anyway, it looks like it's running good.  I used the automatix to install a bunch of stuff, and mounted my ntfs documents.  At this moment, I can only think of one pressing question.  How can I get the back and forward buttons on my MX500 mouse to work with Firefox?

Lookin forward to post-windows life.

---

### Post by GreyFox503 on 2006-02-11
Glad you were able to install it successfully.

[quote=axiomata]How can I get the back and forward buttons on my MX500 mouse to work with Firefox?[/quote] 
I was about to check out the wiki, but it doesn't seem to be working right now...

If you have a question or want to know how to do something, I would search the forums and the wiki (located at wiki.ubuntu.com) for information.  There are lots of HOWTOs already written to accomplish many tasks.

---

### Post by axiomata on 2006-03-01
One last thing ... I hope.

When I installed ubuntu I had already partitioned a portion of my second hard drive that housed My Documents from windows.  Basically, I partitioned it again in the installation of ubuntu which was not neccessary so now I am left with 9,539MB of inaccesible hard drive space.  I took a screenshot of my hard drive in gparted to help.

[img]http://img208.imageshack.us/img208/1032/screenshot2av.png[/img]

What I think I would like to do is absorb that unformatted unknown section in with my main ubuntu partition, /dev/hdb2.  I guessed that since it was a sub-section of the main partition deleting it would just give the main ubuntu partition more space.  However, I get the error that you can see in the screenshot when I try to delete it.  It seems I have to unmount the linux-swap somehow and then try to delete it and I don't know how to do that.

---

