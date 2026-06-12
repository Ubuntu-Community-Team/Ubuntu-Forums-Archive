---
title: "Installation and partition"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-02-16
I defragged my hard drive that I'm going to put Ubuntu on (separate from the windows hd). So I think i'm ready for installation. My linux harddrive is abou 150 gb big with 90gb free. I want to use 50gb of this free space. I started installing and everything went smoothly until I got to the partition part. It's like I can only partition the harddrive with stuff on it and I definitely don't want to get rid of any of my windows stuff. Or is the partition just splitting it in half and whatever I leave to my windows part, linux uses the other? I don't have the best idea of what I'm doing so I'm not pulling the trigger until I do.

---

### Post by taurus on 2007-02-16
Before you click the install icon, you can use gparted, System -> Administrator, on the LiveCD to resize your harddrive.  Then, tell the installer to use that partition to install Ubuntu on.

---

### Post by Yellowbelly on 2007-02-16
ok, I tried to partition the harddrive but some error came up that said it couldn't do it. I don't think it gave any clear details on why though.

edit: I tried it again and it said that it couldn't part drives that are managed by Windows Dynamic Disk. What is this and how do I get around it?

---

### Post by Yellowbelly on 2007-02-16
I got a friend over to try to partition it but I think it worked too well. He partitioned it too much and now my windows partition is close to full but then in gparted it shows that the hard drive is almost completely full instead of showing an unallocated part. The weird thing about this is we tried to partition it to see if it'd work but we thought it froze because it took a loooooooooong time so we just canceled it but i guess it partitioned it weirdly and I think my hd is messed up. I need help.

---

### Post by bodhi.zazen on 2007-02-16
Try the gparted live CD

This version of gparted is somewhat newer and may be of assistance.

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Also it would help if you could list your current partition table.

---

### Post by Yellowbelly on 2007-02-16
hdd1: 40gb. 1 partition at about 1-2gb of unallocated from windows and  the second big partition is just the rest of the harddrive with 5-6gb left of freespace. Windows is on this hd.
hdd2: Same as above except windows is not on this
hdd3: 160gb. Used to be no partitions just used 50-60gb of it and I have 90.7 left. After the weird partition thing my friend did, according to windows the hd is now at 60gb big I only have 1.8gb left. On the graph, when I try to partition it in ubuntu, it says 147gb are used and just a big of space left so I don't want to try and repartition it because I don't think it'll let me and I don't want to get rid of any space.

---

### Post by bodhi.zazen on 2007-02-16
You will have to be more specific then that.

I can not follow your partitioning at all, nor can I understand what you want.

Please use standard terminoloy when referring to your partitions.

hdd refers to the 4th HD

I can not determine from your post if you are talking about 3 hard drives, or 1 hard drive, or even what partitions you are trying to make ...

See here for basic partitioning information and try again ...

[http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

---

### Post by Yellowbelly on 2007-02-16
Alright. I have 3 hard drives. Replace the hdd's in my post above: hdd1=hda, hdd2 = hdb, hdd3 = hdc. The hard drive I want to partition is hdc but there's a problem. It's like there is only 1 partition on the hard drive and I can only resize it, which is make it smaller. If I make it smaller, there is unallocated space. The unallocated space is where I want to make another partition and put Linux on. I couldn't even resize or partition the hard drive because it said it was being managed by Windows Manager Disk or something like that. Some how my friend got around it a little and we tried again but it took so long we thought it froze and he had to go so we canceled the operation. I thought it would go back but now it says that hdc is using up 149gb of space rather than the 60gb it originally was. I go back to windows and it says that the harddrive is now only 60gb which kinda makes since. I guess it half worked but now I don't know how I can repartition it or fix it from saying it's using 149gb. I really don't know what just happened.

---

### Post by bodhi.zazen on 2007-02-16
> **Yellowbelly said:**
> Alright. I have 3 hard drives. Replace the hdd's in my post above: hdd1=hda, hdd2 = hdb, hdd3 = hdc. The hard drive I want to partition is hdc but there's a problem. It's like there is only 1 partition on the hard drive and I can only resize it, which is make it smaller. If I make it smaller, there is unallocated space. The unallocated space is where I want to make another partition and put Linux on. I couldn't even resize or partition the hard drive because it said it was being managed by Windows Manager Disk or something like that. Some how my friend got around it a little and we tried again but it took so long we thought it froze and he had to go so we canceled the operation. I thought it would go back but now it says that hdc is using up 149gb of space rather than the 60gb it originally was. I go back to windows and it says that the harddrive is now only 60gb which kinda makes since. I guess it half worked but now I don't know how I can repartition it or fix it from saying it's using 149gb. I really don't know what just happened.

Now I understand.

Does hdc have anything on it you need to keep ?

If so, your first idea is a good one. resize (shrink) the partition and leave unallocated space (from windows). Then boot Ubuntu and install into the unallocated space. The install should partition and format the space for you.

===============

If not, delete all your partitions from windows and format with the Ubuntu live CD.

I am guessing part of your problem is that the windoes partitioning  tool does not play well with Linux ...

---

### Post by Yellowbelly on 2007-02-17
> **bodhi.zazen said:**
> Now I understand.

Does hdc have anything on it you need to keep ?

If so, your first idea is a good one. resize (shrink) the partition and leave unallocated space (from windows). Then boot Ubuntu and install into the unallocated space. The install should partition and format the space for you.

===============

If not, delete all your partitions from windows and format with the Ubuntu live CD.

I am guessing part of your problem is that the windoes partitioning  tool does not play well with Linux ...

The only thing HDC has is Doom3. I borrowed the CD's from a friend and now he's in scotland. I downloaded a whole bunch of stuff...mmm games but I couldn't ever get them to work and i can reinstall America's Army painlessly especially since I can't play it because of the stupid school network. I think reformatting is the only way I can go. I'll play around with the new Gparted but i dunno if I can do anything other than reformat.

---

### Post by Erlander on 2007-02-17
If you can park the stuff you want on another HD and then delete the partitions.  Then you can allocate some of the disk to a windows partition and put your windows stuff back.  Then the unallocated space can be given to a linux partition.

In my opinion that's the safest way.

Rob

---

### Post by bodhi.zazen on 2007-02-17
> **Erlander said:**
> If you can park the stuff you want on another HD and then delete the partitions.  Then you can allocate some of the disk to a windows partition and put your windows stuff back.  Then the unallocated space can be given to a linux partition.

In my opinion that's the safest way.

Rob

Good idea :p

Why didn't I think of that #-o

---

