---
title: "ubuntu 7.10 fsck help"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by nymlord on 2008-03-16
so ive read around on all forums about fsck and how to disable it, ur prob wondering why i wanna disable it and ill tell u why. every 30 restarts it forces a test, test fails and i cant do anything but reinstall the OS which is quite annoying.. so! i found out u can run fsck from the live cd, but! i dont know how to do that, yes i have the command, 

sudo e2fsck -c -p -f -v /dev/sda1 

my question is,. when im in the live cd, i have to run the fsck test in the terminal of course, but how do i know that its running the test on my hardrive and not on the live cd ? 

i have been having problems with the fsck for a very long time now, and its really bugging me. these are the problems it always keeps on repeating.

Warning /etc/modprobe.d /alsa-base.save line 41 ignoring bad line starting with sudo

failed to allocate memory resource ( which really doesnt sound to good)

so im wondering if there is anyone clever out there to help me, because i really dont wanna restart the whole OS AGAIN, and AGAIN... 
if there is no solution to fix this problem, then how the **** can i disable fsck so it can just get out of my life and leave me alone :P ???



thank you for ur time! :popcorn:

---

### Post by durand on 2008-03-16
[http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager](http://ubuntuforums.org/showthread.php?t=295262&highlight=bonager)

This neat app might help :)

For the live cd, you can find the partition ubuntu is installed on by this command:
> sudo fdisk -l
It should be one of the ext3 partitions, I think. This would replace /dev/sda1 in your e2fsck command.

---

### Post by nymlord on 2008-03-16
thanks man! :D

---

