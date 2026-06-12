---
title: "how do I turn off automatic NTFS mount?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by iansane on 2007-09-20
Hi, I posted this already in another category but felt it should be posted under the right one so here it is again. 

I had none of the problems I have been reading about, that other people have had. (knock on wood).

I installed ntfs config which was allready in the add remove programs applet, Ubuntu mounts the windows partition at start up and any user can see it. I learned how to use "sudo umount" and "sudo mount" from a limited user account. Now I want to turn off the automount so that I can use "sudo" to mount but not worry about other users seeing it. Does this have something to do with the 0,0 numbers at the end or the fstab entry? I want the entry to still be there so I can mount but I don't want it to automount. Thanks

---

### Post by nick_h on 2007-09-20
No, you need to add the noauto option to the 4th column.

There is a good guide [here](http://www.tuxfiles.org/linuxhelp/fstab.html).

---

### Post by iansane on 2007-09-20
thanks nick_h

---

### Post by iansane on 2007-09-20
not exactly sure where to add the noauto. I see it in the entries for the cd drives but they look a lot different. Can I just append it to the end of the entry? here's the entry as is now.

/dev/hda1 /media/XP ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by Dr Small on 2007-09-20
> **iansane said:**
> Hi, I posted this already in another category but felt it should be posted under the right one so here it is again. 

I had none of the problems I have been reading about, that other people have had. (knock on wood).

I installed ntfs config which was allready in the add remove programs applet, Ubuntu mounts the windows partition at start up and any user can see it. I learned how to use "sudo umount" and "sudo mount" from a limited user account. Now I want to turn off the automount so that I can use "sudo" to mount but not worry about other users seeing it. Does this have something to do with the 0,0 numbers at the end or the fstab entry? I want the entry to still be there so I can mount but I don't want it to automount. Thanks
It looks like most of your questions have been answered here:
[http://ubuntuforums.org/showthread.php?p=3397747#post3397747](http://ubuntuforums.org/showthread.php?p=3397747#post3397747)

Please do not make copy threads.

Dr Small

---

### Post by iansane on 2007-09-20
actully, I couldn't find the answer there either. I only had one question. Maybe I went into to much detail to make sure everyone knew exactly what I was looking for. I'm sure the answer is there. I just don't understand the terminology but I'm getting it slowly. I just needed to know to replace the word "defaults" with the word "noauto". The options don't exactly line up in the collums in all the entries and some of them have more stuff than others and some are comma seperated while others are not, so it took a minute to figure out what was options and what was a continuation of the "type" collum.

This is what I had to change.
/dev/hda1 /media/XP ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hda1 /media/XP ntfs-3g noauto,locale=en_US.UTF-8 0 0

notice there's no comma seperating ntfs-3g and defaults. And the other entries are different too. Things aren't as apparent to an absolute newbie as they are to some.

Sorry for making a copy thread and for being so ignorant.

Thanks for the help

---

