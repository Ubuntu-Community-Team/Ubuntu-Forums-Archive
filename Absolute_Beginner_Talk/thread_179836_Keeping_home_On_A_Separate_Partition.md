---
title: "Keeping /home On A Separate Partition?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-05-20
Hello,

I just read from someone's post that keeping the /home directory on a separate partition from the rest of the OS was the best Linux advice they ever recieved. That made a lot of sense to me, and I'd like to try it out, especially since I'll likely be upgrading to Dapper inside a month or so.

After some searching, I couldn't really find any information on moving the /home directory to another partition, so I thought I'd come here and ask if anyone could help me out.

My questions:

1) How do I set up a new partition on my hard drive without wiping out my old ones? At the moment, I just have two, the big one that holds all of Ubuntu, and the small "swap" partition that was created during installation.

2) Is there anything special I need to do to get my /home directory moved over (will hidden/system files, etc. copy over, etc.)

3) Will Ubuntu recognize this new partition as my /home correctly if I simply mount it to the directory /home (for instance, I mount my second harddrive to a directory called /harddrive. Basically I want to know if this will work for my /home partition as well, or if there's more that needs to be done.)

4) How do I set Ubuntu to automatically mount my /home partition? This would also help me with my second hard drive since I've just been manually mounting whenever I needed to, which really isn't that much of a hassle since I rarely need to reboot Ubuntu. However, I think I'd rather have my /home mounted whenever I restart, especially since the desktop is stored in my /home (as far as I'm aware), and I'd think GNOME would need that when loading.

Thanks in advance,
Steggy

---

### Post by cleverselfreferentialname on 2006-05-20
Not sure about the other stuff.....I've always done it on install, but you can mount partitions automagically by adding an entry in fstab [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by Mustard on 2006-05-20
Here is an old Hoary Hedgehog guide showing the basics of how to do it..

[http://www.ubuntuforums.org/showthread.php?t=46866](http://www.ubuntuforums.org/showthread.php?t=46866)

I would read through the whole thread so you get an idea of what types of mistakes people make and just to make sure the original guide has proven to be useful for those who tried it.

---

### Post by aysiu on 2006-05-20
I think you're on the right track.

Back up your important files.

Get a live CD.

Use the live CD and a partitioning program (GParted, QTParted, DiskDrake) and resize your / partition to make room for the /home partition. Since your /home partition usually has your files, too (not just your settings), it's a good idea to make it much larger than your / partition, which has only system files. Format the new partition as Ext3. Make note of its location. For the sake of this example, I'm going to say it's /dev/hda5.

Then, with your live CD, use an archiver program to zip (or tar) your /home folder contents (including hidden files) into a .tar.gz. Mount the newly created partition at /newhome and unzip or untar the zipped file to the new partition. Then delete the /home folder from your old partition. 

Edit the /etc/fstab file from the old partition and tack in the appropriate line. It'll probably be something like ```
/dev/hda5 /home ext3 defaults 0 0
``` Then, make sure you ```
sudo chown -R steggy:steggy /newhome
```

Finally, reboot and cross your fingers...

**Edit**: Oh! I like Mustard's link. Read that too.

---

### Post by keheikev on 2006-05-20
I did find some information at catletts website. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) Its not in this section but in a section of the table of contents it describes how this user set it up. I guess what you are doing is after the fact though?
HTH
Keheikev

---

### Post by Steggy on 2006-05-20
Thanks for the help everyone :)  The links and explanations were very helpful, and I think I understand what to do now. I've cleared enough room off my hard drive so I can set up the correct partitions, and I think I'm going to start working on it right now.

Thanks again!

---

### Post by aysiu on 2006-05-20
Just remember--whenever you edit a file like /etc/fstab, you should always back it up first. Good luck.

---

