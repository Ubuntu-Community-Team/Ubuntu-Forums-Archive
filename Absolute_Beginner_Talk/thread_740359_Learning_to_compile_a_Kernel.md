---
title: "Learning to compile a Kernel"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by puterboy on 2008-03-30
So I'm having problems on a 2nd computer of mine installing a driver, and I came across a possible solution: compiling my own kernel. I figure, might as well, as this is a 2nd computer I installed Ubuntu on today, so I'll give it a try!

So my question is:

With the latest 2.6.24.4 kernel out, I wanna compile it. I've found 1,000 howtos, but I can't seem to find a comprehensive source for my questions about compatibility (will the compiled kernel be usable within Ubuntu without some sort of patches?), and other questions. Can I compile the latest kernel and still maintain the Ubuntu GUI and stuff? And is there a super-site that explains everything, so I'm not making tons of posts here?

---

### Post by skymera on 2008-03-30
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Follow that guide, it's awesome.

---

### Post by c-ron on 2008-03-30
Check out:

The Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
which is based off of an older thread: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)
and this has more add'l options: [http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)

A good general rule to to make sure that your hard disk controller and filesystem types are built in to the kernel (ie NOT as modules).

Hope this helps!

---

