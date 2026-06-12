---
title: "Help re-partitioning my hdd"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-02-22
Hi, I recently installed Ubuntu 7.10 dual booting Windows Vista, and I partitioned it 50/50. I now want to add a little more to Vista. I have been told to insert the Live CD and run **sudo gparted** from Terminal. I did so with no problems. My problem is; how can I choose which partition to take from to add to another? I pretty much need step by step instructions on how to do everything from the time the gparted window opens onward. I've identified which ones I want to change. Thanks much! CloudFX

---

### Post by em3raldxiii on 2008-02-23
Well, I am at work, so I can't give you everything you need, but I can start.  

First off, if your Linux partition is directly AFTER your Vista partition, then you cannot shrink your Linux partition to add it to your vista.  As far as I know, it's pretty much impossible to shrink a partition by moving the "start" of the partition further.

Now, if you have another partition somewhere that has a bunch of room at the end, you can shrink that partition from the END, and then use the newly unpartitioned space for a NEW partition which you can format to NTFS or whatever for use under VISTA.

Now, if you are hell-bent on increasing the size of your Vista partition at the expense of messing with your Ubuntu installation, you will need to remove the partition directly after the VISTA installation, expand the VISTA partition, and then re-add a new smaller partition where the one you removed was.  If that one had anything on it, it will be gone, so you may have to re-install Ubuntu if it had the root (or "/") partition on it.

---

### Post by bodhi.zazen on 2008-02-23
The limitations em3raldxiii mentions are for outdated versions of gparted.

With new versions of gparted, as on Ubuntu 7.10, you will have no problem. You need to do it in two steps.

Run gparted with ```
gksu gparted
```

Select the partition to downsize by clicking it with your mouse -> make it smaller -> run the "operation"

Step 2 (after downsizing) select your Windows partition -> make it bigger -> run the operation.

done

---

### Post by Yoke &amp; Chung on 2008-02-23
> **bodhi.zazen said:**
> The limitations em3raldxiii mentions are for outdated versions of gparted.

With new versions of gparted, as on Ubuntu 7.10, you will have no problem. You need to do it in two steps.

Run gparted with ```
gksu gparted
```

Select the partition to downsize by clicking it with your mouse -> make it smaller -> run the "operation"

Step 2 (after downsizing) select your Windows partition -> make it bigger -> run the operation.

done

If Vista is the first partition following by the Ubuntu partition, can you still shrink Ubuntu and expand Vista to use the free space? 

Correct me if I am wrong, as far as I know, it cannot be done. If the setup is as above, you can shrink Vista and expand Ubuntu but not the other way round. Unless the first partition is Ubuntu and Vista is the 2nd partition, then you can use Gparted to shrink Ubuntu and use Vista built-in partitioner to expand to use the free space.

---

### Post by bodhi.zazen on 2008-02-23
No, that is what I am saying

Newer versions of gparted can resize, ie expand the partitions regardless of which order they are in.

If the vista is /dev/sda1 and ubuntu /dev/sda2 you an shrink sda1 and increase the size of sda2, or shrink sda2 and increase sda1, what ever you like

Older version of gparted could not do this.

See this thread where I walked a user through doing exactly this with the Ubuntu 7.10 live CD :

[http://ubuntuforums.org/showthread.php?t=703240](http://ubuntuforums.org/showthread.php?t=703240)

Sorry it is so long, but it shows you can resize the partitions. You need to do it in two steps, not all at once (ie not in a single "operation")

---

### Post by Yoke &amp; Chung on 2008-02-23
Thanks, I learn something new today :-)

---

### Post by CloudFX on 2008-02-23
Thank  you so much! I did not know it was that simple. 

I just have two questions. First, do I have to run gparted from the Live CD, and also, is there a difference between the command **gksu gparted **and **sudo gparted**?

---

### Post by CloudFX on 2008-02-23
bump

---

### Post by bodhi.zazen on 2008-02-23
Yes, you must resize from a live CD. You can not resize a mounted partition, thus you can not resize your Ubuntu partition while running from HD.

On a live CD, sudo gparted == gksu gparted, does not matter.

You should use gksu (or kdesu if running KDE) for graphical applications. It usually does not matter to be honest, but if it does it can be problematic.

The issue is best discussed here : 

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by CloudFX on 2008-02-24
Ok, thanks very much for that. I am now being faced with the problem you said was outdated. I have 20gb of unallocated space which I removed from the Ubuntu partition, but I am unable to add that to my Vista partition. Is there anything that I can do, or am I stuck with what I had before?

---

### Post by bodhi.zazen on 2008-02-24
Screen shot ?

Can you confirm the live CD you are using ?

---

### Post by CloudFX on 2008-02-24
I'm using the Ubuntu 7.10 Gusty Gibbon Live CD, downloaded about a month ago. I did the thing to make sure the CD had no defects. I'm on Windows right now, but I'll be on Ubuntu later. I get a screeny then. Thanks so much for your assistance.

---

### Post by bodhi.zazen on 2008-02-24
OK, My initial guess it you are trying to do everything in a single step. You need to downsize the first partition and apply the changes, then increase the size of the second partition and apply the changes.

My other guess is you have a logical partition and need to resize the logical partition first.

Third would be your partition is mounted, particularly swap.

Screen shot should help.

---

### Post by CloudFX on 2008-02-24
Ok, in that case I'll go into Ubuntu right now. Also, I've already downsized the first partition and I have 20gb of unallocated space. I'm not sure what a logical partition is, so I'll need help with that if it's the case. Also, I do believe that the partition is mounted, so I'll need to find out how to unmount it. I'm goign to get a screen shot right now.

---

### Post by Taum on 2008-02-24
I'm in a similar boat.

I have one hd, partitioned for Ubuntu (hd1) and Win (hd2) but I have no ability to choose which OS to boot from.  Me thinks I did something wrong and will have to go back and reformat the Win side of things and repartition more smarter, but I wanted to see if there were any known tips/tricks for getting a dual booting prompt at start up.

---

### Post by CloudFX on 2008-02-24
Here are the screen shots

Here you can see that there is 20gb of unallocated space

[IMG]http://i28.tinypic.com/ezhpao.png[/IMG]

and here you can see that I am only able to add 4mb of space, instead of 20gb.

[IMG]http://i27.tinypic.com/2z8or9t.png[/IMG]

---

### Post by bodhi.zazen on 2008-02-24
Yea, sda4 is an extended partition. You need to shrink that one as well, moving the unallocated space out of it (see how 6 , 7 , and 5 are listed under 4 ? if that makes sense).

Then resize sda3

See this link for partitions : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018) 

You may also want to move your partitions to consolidate them.

---

### Post by CloudFX on 2008-02-24
Ah, I understand (i think).So what I need to do is shrink the sda4 partition down 20gb, then it will be available to add to the Vista partition? Will it automatically take the unallocated space?

Sorry about all these questions - I need to be sure of everything before I make such a big change :)

EDIT: I am unable to resize the sda4 partition. When I select it, it doesn't let me click resize/move.

---

### Post by Taum on 2008-02-24
> **CloudFX said:**
> Ah, I understand (i think).So what I need to do is shrink the sda4 partition down 20gb, then it will be available to add to the Vista partition? Will it automatically take the unallocated space?

Sorry about all these questions - I need to be sure of everything before I make such a big change :)

EDIT: I am unable to resize the sda4 partition. When I select it, it doesn't let me click resize/move.

Did you unmount it?

---

### Post by em3raldxiii on 2008-02-24
> **Taum said:**
> I'm in a similar boat.

I have one hd, partitioned for Ubuntu (hd1) and Win (hd2) but I have no ability to choose which OS to boot from.  Me thinks I did something wrong and will have to go back and reformat the Win side of things and repartition more smarter, but I wanted to see if there were any known tips/tricks for getting a dual booting prompt at start up.

This is actually a different problem, believe it or not.  Basically you are going to need to fix GRUB which is the boot-loader that allows you to boot different operating systems at startup.  If Windows is already installed on your WIN partition, then you should be able to search for "FIX GRUB" or something like that here on the forums.

If Windows is not installed (or got severely broken), then you will need to re-install it on your appropriate partition.  But Windows is silly in that it overwrites your boot loader with it's own, effectively making it impossible for you to boot into Linux - at which point you can fix it by re-installing GRUB.  This is a relatively painless process and again, you can get help by searching for "Installing windows after linux", or "fix grub".

Good luck :D

---

### Post by bodhi.zazen on 2008-02-24
> **CloudFX said:**
> Ah, I understand (i think).So what I need to do is shrink the sda4 partition down 20gb, then it will be available to add to the Vista partition? Will it automatically take the unallocated space?

Sorry about all these questions - I need to be sure of everything before I make such a big change :)

EDIT: I am unable to resize the sda4 partition. When I select it, it doesn't let me click resize/move.

It is because of the swap partition (sda7)

Try this :```
swapoff /dev/sda7
```

Then you should be able to resize ;)

---

### Post by CloudFX on 2008-02-25
Sorry, am I supposed to type that into Terminal? I'm very unfamiliar with linux terms and things similar, so I apolgize for the stupid questions.

---

### Post by bodhi.zazen on 2008-02-25
np

sudo swapoff /dev/sda7

if needed

sudo umount /dev/sda7

---

### Post by CloudFX on 2008-02-25
beautiful! Also, from the screenshots you gave me, were u able to tell if my sda3 (vista) partition is unmounted? I used right click > unmount, and one of the columns dissapeared, so I assumed it unmounted itself.

---

### Post by bodhi.zazen on 2008-02-25
looks OK, usually the "lock" = mounted

---

### Post by CloudFX on 2008-02-25
Thanks much, I'm doing work on Vista right now but that's my next priority. I'll give you the info on my results then.

---

### Post by CloudFX on 2008-02-25
Ok, Ive taken screenshots of my latest issue. I am now able to resize the sda4 partition, but check out how much I can resize it.

[IMG]http://i30.tinypic.com/2lcpkpv.png[/IMG]

[IMG]http://i25.tinypic.com/120thqs.png[/IMG]

---

### Post by bodhi.zazen on 2008-02-25
Not sure, try putting the free space in front of the partition.

Like this (you need to move your partitions)

[http://i32.tinypic.com/167o77q.png](http://i32.tinypic.com/167o77q.png)

See how the unallocated space is in the front ?

---

### Post by CloudFX on 2008-02-26
How do u move it?

---

### Post by bodhi.zazen on 2008-02-26
You should have the option to resize / move a partition or perhaps the unallocated space itself.

See here : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Scroll down to section 3

---

### Post by CloudFX on 2008-02-26
I see, so I just have to drag that bar to the far left?

---

### Post by bodhi.zazen on 2008-02-26
Hope so ...

---

### Post by CloudFX on 2008-02-27
I am unable to resize/move an unallocated partition. Should I turn the unallocated space into a new partition, and then try to move it? Also, if I select my sda/6 partition, it is already on the far left and cannot be moved any more. I'm afraid that the new partition will be the same.

---

### Post by dstew on 2008-02-27
> I am unable to resize/move an unallocated partition.You are confusing unallocated space with an empty partition. You can only move partitions, not unallocated space. There is no such thing as an "unallocated partition", only unallocated space.> Should I turn the unallocated space into a new partition, and then try to move it?Yes!

---

### Post by CloudFX on 2008-02-28
K I'll get to that then.

---

### Post by CloudFX on 2008-02-28
K, I turned my unallocated space into a partition, but I still cant move it. Here are some screen shots.


The highlighted one is the unallocated space that I turned into a partition (I used NTFS because that's what my Vista partition format is, am I correct in doing that?
[IMG]http://i26.tinypic.com/1zoyfc9.png[/IMG]

You can see that I have no ability to move it left or right, only make it smaller.
[IMG]http://i28.tinypic.com/35mjpfl.png[/IMG]

One thing I noticed was that I have the ability to copy the new partition and paste it into Vista. Should I do that?

---

### Post by dstew on 2008-02-28
I think by move it means to slide it back and forth. That means you need to have some unallocated space on either side. I don't think you can jump it over other partitions into a different space.> One thing I noticed was that I have the ability to copy the new partition and paste it into Vista. Should I do that?I am not sure what you mean by this. Vista is an operating system, and a partition is a disk volume.

---

### Post by warbird on 2008-02-28
just move all the partitions in the extended partition together, to the beginning of the extended partition. Then resize the extended partition, so the free space is outside the extended, move the extended to the end of the HD (i think you have to rightclick the unallocated space). then things will look like this:
(Vista-------)(unallocated------)(extended------)
then you just resize the vista partition

---

### Post by CloudFX on 2008-02-28
> **dstew said:**
> I think by move it means to slide it back and forth. That means you need to have some unallocated space on either side. I don't think you can jump it over other partitions into a different space.I am not sure what you mean by this. Vista is an operating system, and a partition is a disk volume.

Do you see how it says the big words COPY on my screenshot? When I click that button over top of the empty partition, and i select the Vista partition, the PASTE icon becomes available.

---

### Post by bodhi.zazen on 2008-02-28
NO

I think that will overwrite your Vista partition.

I think you need to delete this new partition, delete or move swap, and move sda5 (the FAT partition) thus consolidating the unallocated space at the end of the extended partition.

Then resize the extended partition

Then add the unallocated space to Vista

Then add back a swap partition.

---

### Post by CloudFX on 2008-02-28
Ok, that sounds like it might get me somewhere. But first, I have a few questions.

What exactly is the swap partition? Also, when I resize the extended partition (by this, I'm assuming thats sda4), will it automatically detect and take the unallocated space?

Thanks!

---

### Post by bodhi.zazen on 2008-02-28
Swap is hard drive space your system uses as RAM when the RAM is full, like the Windows page system.

Hopefully when you resize your extended partition the unallocated space will move outside of it and you can then add it to Vista.

---

### Post by CloudFX on 2008-02-29
I'm now being faced with something very odd. From vista, I can see three different partitions now. My regular one, my recovery one, and now the empty, unallocated space as an empty drive which as far as I know, I can access from Vista. I believe this is because Vista recognized the NTFS partition, even though it was in the sda4. I'm on vista right now, but im going into Ubuntu soon to see whats up. Do you think this is a good or bad sign?

Ok, I've removed the new partition, and now it's at the bottom of the list. But when I try to shrink sda4, it still shows me an improper amount, in megabytes instead of gigabytes.

---

### Post by CloudFX on 2008-03-01
bodhi.zazen, thank you very much for your assistance. I no longer plan to add more space to my Vista partition, as the reason I didn't use Ubuntu at first was because I could not connect my wireless card. Dell has released firmware that allows people to, and for that reason I can freely use Ubuntu. Again, thanks so much for helping me this past week. Your work is greatly appreciated!

---

### Post by bodhi.zazen on 2008-03-01
You are most welcome, I am sorry you had so much trouble. 

Glad to see it worked out, although not the way we planned ;)

and ...

Welcome to Ubuntu.

---

