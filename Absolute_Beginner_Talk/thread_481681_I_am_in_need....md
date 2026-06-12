---
title: "I am in need..."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by miguel1986 on 2007-06-22
I have two partitions: hda1 (my Windows XP) and hda5. I would like to install my Ubuntu into the hda5 partition and the swap into another partition. How should I proceed to create another partition from the hda5 partition? Please, I am new to these things, so whoever respond in detail, showing me the ways.
I would be very, very grateful with any help.

---

### Post by Inxsible on 2007-06-22
Please be patient for replies. Do not start multiple threads for the same issue. Here is your previous thread

[http://ubuntuforums.org/showthread.php?t=481649](http://ubuntuforums.org/showthread.php?t=481649)

---

### Post by Tsen on 2007-06-22
Okay, boot up the live CD of Ubuntu, go to System->Administration->GParted (Might be called GNOME Partition Editor)

Open this up, then right click hda5 and select "Resize/Move".  Shrink it to leave about 1000 MB of space after hda5.  Click "Apply".  Then right click the new empty space, create a new partition and set the file system to "Linux-SWAP", and you're done!

---

### Post by miguel1986 on 2007-06-22
Okay, I'll try to do it now.
Please, if possible, can you explain me more about this partitioner setup process?
Thank you. I'll try it.

---

