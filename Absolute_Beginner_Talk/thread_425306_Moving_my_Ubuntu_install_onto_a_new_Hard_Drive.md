---
title: "Moving my Ubuntu install onto a new Hard Drive"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by phatalbert on 2007-04-27
I have Ubuntu Feisty Fawn 7.04 installed right now, and it's working fine. I just received a new hard drive, though, and wanted to start using that in my laptop instead of the current one. Is there any way I can move my install onto the new hard drive, preserving all my settings and installed programs?

Would I just copy the whole filesystem over? What command would I use to do that, and move all the hidden/protected files?

Thanks!

---

### Post by lamalex on 2007-04-27
try ghost4linux. it should just image your drive over to the new one.

---

### Post by laidback on 2007-04-27
All your own settings are in your home directory within the hidden area. Using the file manager choose View>Hidden Files. This will display all files beginning with . (dot) which are normally not displayed. Within .Mozilla, for example, are all you settings for the web browser Firefox. If you search around you'll find an html file called bookmarks which has your bookmark list. If you copy eveything in your home directory you should preserve your own settings etc (not sure about passwords).

I have copied my entire disc to clone it, but you need a USB hdd to do it my way, you haven't mentioned having one. I use Gparted (it's on your system, maybe under Gnome partition Editor) but to copy the disc you'll need to boot from a Live CD as you cannot copy a mounted disc. It's like swapping water between 2 buckets, you need a third one.

---

### Post by dstew on 2007-04-27
To make an exact copy of a disk, you can use the **dd** program. See this Wikipedia page for instructions:[http://en.wikipedia.org/wiki/Dd_(Unix)](http://en.wikipedia.org/wiki/Dd_(Unix)). You make an image file of the old disk, and then put that on the new (unformatted) disk. The dd program reproduces the format of the original disk. However, I do not  know if this will work if the new disk has a different geometry from your old disk.

---

### Post by phatalbert on 2007-04-27
> **laidback said:**
> All your own settings are in your home directory within the hidden area. Using the file manager choose View>Hidden Files. This will display all files beginning with . (dot) which are normally not displayed. Within .Mozilla, for example, are all you settings for the web browser Firefox. If you search around you'll find an html file called bookmarks which has your bookmark list. If you copy eveything in your home directory you should preserve your own settings etc (not sure about passwords).

I have copied my entire disc to clone it, but you need a USB hdd to do it my way, you haven't mentioned having one. I use Gparted (it's on your system, maybe under Gnome partition Editor) but to copy the disc you'll need to boot from a Live CD as you cannot copy a mounted disc. It's like swapping water between 2 buckets, you need a third one.

I have an external USB HDD, but your method sounds much easier. Would it preserve all my installed programs, Firefox extensions, and drivers? If it does, then, that's what I'll do.

---

### Post by laidback on 2007-04-27
Call for dinner, I'll get back to you with the details of what I do.

---

### Post by laidback on 2007-04-27
The basic idea is to:-
1 create a copy of your current partition onto the USB hdd 
2 replace your current hdd with the new one
3 install a fresh Ubuntu onto the new drive, formatted as per original hdd including swap
4 copy back the original partition, that was saved on the USB hdd, onto the new drive.
5 reboot into clone

there is a little more to it within the detail but you get the idea?

I'm assuming that you have a single partition installation of Ubuntu, but if you don't I see no reason why the method cannot be extended to more partitions as needed.

You need space on the USB hdd, as much as in the Ubuntu partition on your main drive. The reason for this is that Gparted will copy the partition as is, no compresssion. 

You also need a Live CD version of Ubuntu or the Live CD version of Gparted (preferred), this is used to format the USB partition and copy the original Ubuntu partition back and forth. You cannot copy mounted partitions.

(The writing is far more complex than the doing, but please be aware that I'm no guru/expert, just an enthusiast. I have used this method on my own system to create clones to use on the original pc and also to create a clone to use on a similar backup pc)

Here we go then :-

1 Boot your pc from the Ubuntu Live cd or Gparted Live cd
( Within Gparted you will see both your Ubuntu hdd and your USB hdd)
2 On your USB hdd create a partition the same size and type as your Ubuntu partition, not smaller.
3 Copy the Ubuntu partition into the USB partition. (it's a copy paste type action)
4 Shutdown and replace the hdd
5 Install a fresh copy of Ubuntu (same version) onto the new hdd, same partitions/sizes as before
(I'm not certain that step 5 couldn't equally well be achieved by hand within Gparted saving the Ubuntu reload but I'm concerned to make things exactly the same as before, that's the purpose)
6 Reboot using Gparted
7 Copy back onto the new Ubuntu hdd partition your old Ubuntu partition from the USB hdd, the new partition must be at least as big as the old otherwise it won't fit. Use Gparted's copy command again here.
8 Reboot to new hdd to see your old system on the new hdd.


It sounds very long winded but actually isn't really. I started using the USB partition copies as a method of backing up my hdd. After that I tried to clone my system from the backups so that I would be able to run from my spare pc if needed. I was amazed when it worked. I wouldn't expect such good result if you are moving hardware platforms as well, i.e. from Socket A system to a 939 system, the original installation cannot be expected to work correctly on the new platform. In these cases copying over subdirectories from /home or possibly /home itself is all I would attempt. (I'm tyimg that at present and have found that .Mozilla and .Evolution copied over fine). But in your case as you're copying back onto the same pc/laptop then you won't have a hardware issue.

Gparted is called Gnome partition manager in Ubuntu 6.06
Note that your original hdd is safe, nothing has been done to it so you can always go back and try something else if this doesn't work.
You will have a copy of your original Ubuntu partition remaining on the USB hdd. You can access this just like any other partition from within file manager. This is one of the aspects of this method of backup that I like. My older files/system are available online as I need. And since I run a 3 cycle backup I have 3 versions of my hdd available on my USB hdd at any one time. I name these partitions and put a readme file at / for my information.

I do hope that this works for you, or you may now be put off and use one of the other systems described by others who I am sure are far more knowledgeable than I.

Perhaps you would be kind enough to post a note to let me know how you got on. I'd like to hear if there were problems as my experience/use will not have covered all eventualities.

Kindest Regards
Laidback

---

### Post by phatalbert on 2007-04-27
Thanks so much!

Just to verify, this should work even if my new hard drive is a different size than either my USB HDD or my old hard drive?

---

### Post by laidback on 2007-04-28
Yes. When you copy back from the USB hdd the partition needs to as big as the original, bigger should be fine. Gparted can be used to resize if you're not happy.
If the partition in your new drive isn't big enough (as viewed via Gparted after installation of new Ubuntu) you can use Gparted to resize it.
My main concern would be that the partitions on the new drive don't have the same id's as the old, e.g. hda1, hda2 etc. as this might cause issues when booting from the cloned version which is expecting the old id's to be used. In practice this didn't cause me any problems but who knows. I suspect that there is a way around it, I guess that Grub could be used to update the MBR., and/or one could edit fstab (I think that's what it's called), the file description table, but I haven't needed to do either of these.

In any event the original is preserved, so you can always reinstall that hdd and follow another path.
I'm not suggesting that this is a cure all, it is just a simple way I devised to deal with issues similar to your own for myself who has limited knowledge.

---

### Post by theDaveTheRave on 2007-05-31
Just a thought on the use of a USB HDD to copy over an existing instalation.

why not invest in one of those USB holders for HDD then you could create a copy in the way suggested and note have to worry about having to mess arround reinstalling the OLD version of Ubuntu, then copying the image back to the new HDD from the USB HDD?

It is just a thought, I don't know if it would work, or if it is even a reasonable idea, but could be worth playing with at some point.

Dave

---

### Post by Ocxic on 2007-05-31
this is in a laptop right???
ever think of removing your cdrom, and slapping in your new drive and copying that way,, I've done it b4, so you should be able to.. i think

---

