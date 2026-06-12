---
title: "NTFS Journal file Unclean?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by kameneye on 2007-02-10
I've been trying for the past, oh, let's say 3 days to install the latest version of ubuntu (6.10) off of the live cd.  Every single time I try to partition my drive using gparted, an error message saying that my NTFS journal file is unclean.  Gparted then gives me 3 options:

1. run chkdsk /f (done COUNTLESS number of times ](*,))
2. shutdown windows properly (what is the defination of a "proper shutdown"???)
3. run ntfsfix from linux (tried, just for it to tell me that the drive is locked)

Is there something that I'm missing here?  Or am I just doing it wrong?  I really want this file "cleaned" ([SIZE="2"]Whatever that means[/SIZE])

Now stop me if I sound crazy, but if there is no ntfs partition, then theres no journal file, amirite?  It just sounds wrong to delete the partition, but after those maddening hours of waking up at 5 in the morning thinking that I had the solution just makes me want to proverball "ride into the danger zone (Hiiiiiiiiiiighway to the DANGER ZONE!)

p.s. Don't you dare tell me to go to the Gparted Forums, 'cause they told me to go here...

---

### Post by taurus on 2007-02-10
Why don't you boot into XP and defrag your harddrive a few times (3 times) before you use gparted to resize it.  That's how you fix it.

---

### Post by kameneye on 2007-02-10
ok, I'll try that.  There's a new best friend seat with your name on it if this works.

---

### Post by stchman on 2008-05-01
I know this thread is old, but I had the same problem and running the ntfsfix cured the problem.  Apparently there was a error in the  NTFS journal that Windows was unable to fix.

After that I was able to resize the partition no problem.

Amazing that Linux has WAY more NTFS tools that Windows does and it is their file system.

The new gparted LiveCD 0.3.6-7 is an amazing tool.

---

