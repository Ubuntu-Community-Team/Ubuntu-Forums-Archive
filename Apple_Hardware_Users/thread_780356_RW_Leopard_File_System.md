---
title: "R/W Leopard File System"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by Officer Dibble on 2008-05-03
I've got a MacBook that won't boot beyond the grey screen and chime. (So I see the grey screen and I hear the chime) After this all it does is a rapid cycle display of the apple logo, and a No-entry type sign, and a Question mark. All of this on the grey background.

I've tried clearing PRAM, etc, but no joy.

There is no problem with the hardware as I can boot from an Ubuntu Live CD with no issues and that runs quite happily.

This problem occurred immediately after installing the software for a ZTE Modem. So what I want to do is go in with Ubuntu and remove the offending files from start-up. What I am finding though is that Ubuntu can read the HDD but can't delete files - so how do I delete files using the Ubuntu live CD, please?

---

### Post by cyberdork33 on 2008-05-03
> **Officer Dibble said:**
> I've got a MacBook that won't boot beyond the grey screen and chime. (So I see the grey screen and I hear the chime) After this all it does is a rapid cycle display of the apple logo, and a No-entry type sign, and a Question mark. All of this on the grey background.

I've tried clearing PRAM, etc, but no joy.

There is no problem with the hardware as I can boot from an Ubuntu Live CD with no issues and that runs quite happily.

This problem occurred immediately after installing the software for a ZTE Modem. So what I want to do is go in with Ubuntu and remove the offending files from start-up. What I am finding though is that Ubuntu can read the HDD but can't delete files - so how do I delete files using the Ubuntu live CD, please?
you cannot write to a hfs+ partition when journaling is enabled, and it can only be disabled from OSX. 

You should use Ubuntu to backup needed files and reinstall...

---

### Post by Officer Dibble on 2008-05-04
> **cyberdork33 said:**
> 
You should use Ubuntu to backup needed files and reinstall...

This isn't what I wanted to hear in all honesty... :(

Thanks for picking up this thread, I thought it was going to be forgotten about. :)

---

### Post by cyberdork33 on 2008-05-04
there may be other more complicated solutions, but it would be easier to reinstall. Not using Time Machine?

---

### Post by Officer Dibble on 2008-05-04
> **cyberdork33 said:**
> there may be other more complicated solutions, but it would be easier to reinstall. Not using Time Machine?

This Macbook is with a visiting friend, so he is in the UK at the moment, but his restore disk(s) are in Japan... I am very willing to try more complicated solutions. :)

All I want to do is remove the files that are corrupting his boot.

---

### Post by cyberdork33 on 2008-05-04
the best way to do things would be to get a hold of a external hard drive that you can do an install of OSX to and boot from there. OSX should be able to access the HFS+ filesystem quite well. you could also boot into firewire disk mode and connect to another mac. In other words, try to use mac solutions already out there before doing anything crazy

I *think* there might be a way to force mounting the drive even with journaling on, and I know that a bug in older linux kernels (~2.6.16) allowed mounting even with journaling turned on... but your files are in danger if you do that (that is why it is disabled in the first place). google around, and try reading the man pages for hfs / hfsplus.

---

### Post by Officer Dibble on 2008-05-05
I've just found this link, would you recognise whether it is using an old kernal exploit or would I get some success from this, please?

[http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/)

In a previous post in this thread you mention 'Time Machine', what does that do, please?

The time you are spending with this issue is incredibly helpful, thank you. :)

---

### Post by cyberdork33 on 2008-05-05
> **Officer Dibble said:**
> I've just found this link, would you recognise whether it is using an old kernal exploit or would I get some success from this, please?

[http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/)

In a previous post in this thread you mention 'Time Machine', what does that do, please?

The time you are spending with this issue is incredibly helpful, thank you. :)
Time Machine is Leopard's backup utility. If you didn't know what it was, you probably weren't using it. I would suggest investing in an external hard drive to use with Time Machine in the future.

That how-to should not mount the filesystem as writable. It can't hurt (too bad) to try though.

Here is a post where I tried to help someone with something similar and it seemed to work. Good Luck!

[http://ubuntuforums.org/showthread.php?t=639778](http://ubuntuforums.org/showthread.php?t=639778)

---

