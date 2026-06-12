---
title: "error while loading"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by mulkwolf on 2007-05-03
This trip into the linux world has been great!...The latest learning experience is this....

I think my wife shut off the computer when linux was running its every 30 time disk check.

I'm now unable to load into the desktop.. after username and password are entered.

Here's the message.

/etc/gdm/Xsession: Beginning session setup ...

x-session-manager: error while loadin shared library libconf -2.so.4: cannot open shared object file: No such file or directory

So any ideas on where to go to fix?

Thanks,

Greg

---

### Post by louieb on 2007-05-03
Sounds like the the file system is in an confused state. May be time to bring out the heavy stuff and reinstall. If you have a separate /home its as simple as useing the manual partitioning  part of the install. Just reuse and check the format box for the / and swap partition. Reuse the /home partition too but leave the format box unchecked.  
OR if you don't have a separate /home now is a good time to make one.
First thing I would like you to do is get a [Puppy Linux Home - your fast, small and free Linux distro]("http://www.puppylinux.org/user/viewpage.php?page_id=1") or [Knoppix Linux]("http://www.knoppix.net/") live CD and use it to make a copy of your /home folder on a usb stick or some other media. You will copy it back after the reinstall is finished. 
You could use the Ubuntu live CD but both of the above can do the job without using the command line. 
Any way get you data backed up and by the time your finished maybe someone will come along and say louieb is all wet here the easy way to fix it.

---

### Post by mulkwolf on 2007-05-03
I was thinking that might be the case.. I'll get to it later today.  Thanks!!!
Greg

---

